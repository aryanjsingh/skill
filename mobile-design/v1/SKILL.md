---
name: aryan-mobile-design
description: Aryan's mobile app design system — the default visual language for every mobile app he designs or redesigns. Premium startup-grade iOS/Android UI: neutral light (#F7F7F5) or near-black surfaces, ONE saturated brand accent, a key headline word in the accent, pill CTAs, floating pill tab bar with a centre + FAB, progress rings, 3-column stat rows, segmented controls, step-progress bars, success medallions, glows and top-of-screen accent washes. Use this whenever the user asks to design, redesign, restyle, polish or "level up" mobile app screens, build a new app UI, apply "my design system" / "our mobile style" to an app, or work on app screens in Paper, Figma-like canvases, React Native, Expo, SwiftUI or mobile web — even if they don't name the system.
---

# Aryan mobile design system

The default look for every mobile app Aryan designs. It is premium, calm and dense: neutral surfaces do the quiet work, a single brand accent does the talking, and data is shown as objects (rings, stat rows, chips) rather than paragraphs. It works for any domain — fintech, health, social, productivity, utilities, forms and consent flows — by swapping the accent and the content, never the structure.

## Core principles (the why)

1. **One accent per product.** Use the product's brand colour (or pick one from `references/tokens.md`) and spend it only where attention should go: primary CTA, active tab, hero number, one key word in the headline, progress fills. Everything else is neutral. Restraint is what makes it look expensive; a second accent makes it look like a template.
2. **Neutral, not tinted, surfaces.** Light: warm off-white canvas, pure white cards. Dark: neutral near-black, never blue-grey. Elevation in dark mode = a lighter surface step, not shadows.
3. **Show data as objects.** Progress → ring or segmented bar. Counts → 3-column stat row with hairline dividers. Status → coloured dot or chip with a word. Steps → segmented progress bar. A screen should be scannable in two seconds.
4. **Hierarchy through contrast, not decoration.** Big tight headlines (34–40px, weight 650, −3.5% tracking), small muted labels (11–13px), tabular numbers. Cards get a 1px hairline and a whisper of shadow — not heavy drop shadows.
5. **Delight is earned.** Glows, gradients, 3D objects and top washes appear on hero moments (home, success, paywall, onboarding, empty states) — not on every card.
6. **Everything tappable is a pill.** Buttons, chips, segmented controls, tab bars: full radius.

## Workflow

1. **Read the product first.** What does the app do, who uses it, what is the one number they care about? Find the existing brand colour and font. Keep the brand accent; propose one only if none exists.
2. **Choose the theme.** Light for trust, forms, consent, utilities; dark for media, fintech, social, gaming, wearables. If the existing app is light, stay light unless asked.
3. **Set tokens** (`references/tokens.md`). When restyling an existing file, prefer updating existing token values over inventing parallel names, and record each original value in the token description so it can be restored.
4. **Global pass** (cheap, broad): canvas, text colours, borders, card style, CTA pills, secondary pills. Hunt down hard-coded colours that bypass tokens.
5. **Design pass** (where the quality comes from): rebuild the hero screens with the patterns below — Home/dashboard, the main detail screen, lists, success, onboarding, empty states, wizards. Rebuild a section when its structure is wrong (e.g. a progress bar that should be a ring) instead of nudging styles.
6. **Review every redesigned screen** with a screenshot against the checklist at the bottom. Fix before moving on.
7. **Update the app's foundations/style-guide screen** (if it has one) so it documents the system as applied.

Before destructive edits to an existing design file, copy the original screens to an archive page/folder so nothing is lost.

## Signature patterns

Exact HTML/CSS for each is in `references/components.md` (paste-ready for Paper `write_html`, portable to React Native / web).

| Pattern | Spec in one line | Use on |
|---|---|---|
| Accent-word headline | 2 lines, 34–40/38–44, wt 650, −0.035em; ONE word or number in the accent ("You have **3 tasks** today.") | Home, onboarding, success, empty states |
| Top accent wash | `linear-gradient(180deg, accent@12% 0%, accent@4% 20%, transparent 34%)` on the screen | Home, welcome, sign-in, empty state |
| Hero glow | radial accent@12–13% behind the hero object, or a soft coloured drop under the hero card | Onboarding illustration, success medallion, primary tile |
| Pill CTA | full width, 50–56px, 15–16px wt 600–650, accent fill, no shadow; secondary = white + 1px border | Bottom of every task screen |
| Floating tab bar | pill inset 16px, white@88% + blur 20px, 1px border, `0 8 24 rgba(0,0,0,.07)`; active tab = accent-soft pill + accent icon/label; centre accent FAB 54×44 pill with + | All root tabs |
| Stat row | white card, 3 equal columns, value 22 bold tabular over 11–12 muted label, 1px dividers | Home, hubs, profiles |
| Progress ring | 5–8px stroke, round caps, track = surface, fill = accent, value centred (tabular) | Goals, completion, any x/y |
| Segmented control | track = surface pill, 4px padding; selected = white pill + `0 1 3 rgba(0,0,0,.08)` | Filters, time ranges, categories |
| Step progress | N pills 18–22×5, gap 4, done = accent, todo = ink@10% | Wizards (replaces "2 of 5" text) |
| Action tiles | two equal tiles side by side, ~132px tall: primary = accent gradient + glow + small chip; secondary = white bordered | Home quick actions |
| Status chip | dot + word: success green, pending amber, danger red — always with a word | Lists, hubs, records |
| Success medallion | 96px accent-soft circle with glow → 68px accent-gradient circle → white check; centred headline with accent word | Receipts, completion, done states |
| Paywall | hero object + glow, 2-line headline with accent number, 3 sparkle benefits, plan cards (selected = 1.5px accent border + "Best value" tag), accent CTA, quiet "Restore" link | Monetised apps |
| Bottom sheet | top radius 28, grabber 36×4, blur + dim behind | Pickers, confirms |

## Screen recipes

- **Home / dashboard**: status bar → logo row + avatar → muted greeting (15px) → accent-word headline → stat row → two action tiles → section header (title + accent "See all") → 2 cards with rings → floating tab bar. Add the top wash.
- **List**: title (34px) → segmented control → cards (date tile or ring on the left, title + muted meta, chevron) → floating tab bar. Remove duplicate "+" buttons when the tab bar has a FAB.
- **Detail / hub**: back + more buttons (white circles) → 2-line title → meta rows with icons → ring card with a 3-stat row → segmented filter → people/item rows (initials on a tinted circle, status line with icon) → CTA pill + square secondary.
- **Wizard step**: back · step-progress bar (centred) · Save/Help → title → fields as white bordered cards (small label over value) → CTA pinned at the bottom.
- **Success**: medallion + glow → centred accent headline + one muted line → receipt/summary card → primary + secondary pills.
- **Empty state**: wash + accent headline ("Let's set up your **first project.**") → illustration → one-line explainer → the same action tiles as Home → tab bar.
- **Onboarding / welcome**: logo, illustration with glow, accent-word headline, one muted sentence, single CTA, quiet sign-in link.
- **Dark variant**: same structures; base `#0E0E0E`, cards `#1C1C1E`, raised `#2C2C2E`, hairline white@6%, white pill CTA or accent CTA, accent glows behind hero objects.

## Type

System grotesk (SF Pro / Inter). Hero number 40 bold · display 34–40/650 · section 17/650 · card title 16/600 · body 15/400 muted · label 13/500 · caption 11–12/500 · tab 10/500. Tight tracking on large type (−0.03 to −0.035em), none on small. Always `font-variant-numeric: tabular-nums` for numbers, money and counts.

## Iconography & imagery

1.5–1.8px outline icons, 20–24px, single colour (muted inactive, accent active, ink on cards). Emotion comes from glossy 3D objects (badges, medals, coins, mascots, device renders) and memoji/photo avatars — use flat illustration only when the brand is playful or wellness-oriented.

## Working in Paper

Read `references/paper-workflow.md` before editing a Paper file — it lists the traps hit in practice (shared tokens across pages, SVG strokes not searchable, absolute layouts losing position on replace, screenshot render lag, no rich text, the 200-result search cap) and the efficient order of operations.

## Working in code

`references/tokens.md` has the tokens as CSS variables, a Tailwind v4 `@theme` block and a React Native theme object. `references/components.md` ends with React Native equivalents (react-native-svg ring, BlurView tab bar, nested-Text accent headline).

## Review checklist (run on every redesigned screen)

- Exactly one accent, covering at most ~10% of the screen; no second brand colour.
- At most one accent word/number per headline.
- Body text ≥ 4.5:1 contrast; muted text not below 13px for long copy; status never shown by colour alone.
- Cards: 20px radius, 1px border, faint shadow — consistent across the screen.
- All buttons, chips, segments and tab bars are pills; one primary CTA per screen.
- Numbers tabular; stat labels muted and small; rings show their value.
- Tab bar floats with a visible inset; active state is a filled pill; nothing overlaps the home indicator.
- Nothing clipped at 390px width; no awkward wraps inside tiles.
- Old patterns removed (underline tabs, "2 of 5" text, flat full-width tab strips, heavy coloured CTA shadows).

## Content rules

Use the product's own brand, content and data. Don't invent business facts — derive stats and labels from content already on the screens, or mark them as placeholders and say so.
