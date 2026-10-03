# Working in Paper (MCP)

Lessons from real redesigns of 40+ screen app files. Read once before touching a file.

## Order of operations

1. `get_guide("paper-mcp-instructions")` once per session; `get_font_family_info` before first typography.
2. `open_file` → `get_basic_info` (artboards, pages, tokens). Screenshot 3–4 representative screens (welcome, home, a list, a form step) before deciding anything.
3. **Archive first.** `create_page("Archive · Before <redesign name>")`, then `duplicate_nodes` every artboard with `parentId: "root_node_<pageId>"`. Do it in batches of ~24 — a large batch result overflows and gets saved to a file (that's fine; count `"sourceId"` occurrences to confirm).
4. **Token pass** with `set_tokens` (update existing values, put the original hex in each description). One call restyles every token-linked layer in the file.
5. **Literal sweep**: `find_nodes` with `styleName` + exact hex for colours that bypass tokens (old greys, an off-brand red), then one batched `update_styles`.
6. **Component pass**: find CTAs via `find_nodes({styleName:"background-color", styleValue:"--color-accent"})` (layers are usually named "Primary action", "Continue", etc.) → pill radius, no shadow. Cards via their shadow value → hairline border + faint shadow.
7. **Design pass**, one screen at a time: `get_tree_summary` (depth 1–2) → replace/insert sections with `write_html` (one visual group per call) → screenshot → fix.
8. `finish_working_on_nodes` at the end.

## Traps (and what to do)

- **Tokens are file-wide.** Changing a token value also recolours archive pages. Tell the user; keep originals in token descriptions. Creating parallel tokens and repointing layers avoids it but costs hundreds of `find_nodes` results — usually not worth it.
- **`find_nodes` caps at 200 results** and each result is verbose. Always pass `pageId` and a `styleName` filter. Avoid bare hex searches like `#111111` without `styleName` — wildcard matching returns noise (`flexGrow: 1`).
- **SVG `stroke`/`fill` attributes are not searchable.** Icons with hard-coded colours must be found via `get_children` on the SVG and fixed with `update_styles({stroke:"var(--color-ink)"})` per path. Budget for this only on hero screens.
- **No rich text.** One colour per text node. For an accent word, split into a flex row of text nodes with `gap ≈ 0.26 × font-size`. Inline `<span>` styling collapses into a single style.
- **`write_html` replace drops absolute positioning context.** If the replaced node was absolutely positioned (common for centred step counters and screens built freeform), the new node lands in flow. Re-apply `position:absolute; left; top` from `get_computed_styles` of the original before replacing.
- **Freeform screens.** Some artboards position every child absolutely. Read `get_computed_styles` (left/top/width) for the regions you replace and give the new HTML the same absolute box.
- **Screenshot render lag.** A freshly written node sometimes doesn't appear in the next screenshot. Check `get_node_info` (size/position); if it's right, re-screenshot instead of rewriting.
- **Reuse instead of rewriting.** `<x-paper-clone node-id="…" />` inside `write_html` copies a finished component (tab bar, stat row, action tiles, step bar) to another screen or a style-guide screen. Clones of absolutely positioned nodes need `style="position:relative;left:0;top:0;width:100%"`.
- **Artboard height.** When a screen (e.g. a style guide) grows, set `height:"fit-content"; maxHeight:"none"` instead of guessing a pixel height.
- **Duplicate actions.** When you add a centre FAB to the tab bar, delete header "+" buttons that do the same thing.
- **`color-mix`** works in Paper styles; if a value is dropped, fall back to a literal `rgba()` of the accent.

## Tab bar migration recipe

1. `find_nodes({textValue:"<one tab label>"})` → every tab bar instance.
2. `get_node_info` → parent chain → find the tab bar frame on each screen (usually named "Tab bar" / "Bottom navigation").
3. `write_html` replace with the floating bar from `components.md` §10, marking the correct tab active per screen. For absolutely positioned screens, wrap with the same `left/top/width` as the old bar and nudge `top` so the pill clears the home indicator.

## Style-guide screen

If the file has a foundations/visual-language artboard, rebuild its content as: type specimen (with an accent-word headline sample) → colour swatches with hex → status chips → controls (primary + secondary pill, segmented control, step bar) → data (ring card, stat row) → navigation (tab bar clone). This keeps the file self-documenting for the next designer.
