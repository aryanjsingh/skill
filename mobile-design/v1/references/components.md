# Components (paste-ready)

HTML uses inline styles and CSS variables so it can go straight into Paper `write_html` (or any web page). Variable names assume the app's tokens are named `--color-ink`, `--color-muted`, `--color-subtle`, `--color-canvas`, `--color-surface`, `--color-border`, `--color-white`, `--color-accent`, `--color-accent-soft`, `--color-accent-light`, `--color-accent-dark`, `--color-success`, `--color-warning`, `--font-sans` (see `tokens.md`). If the file you are editing names its accent differently (e.g. `--color-brand`), substitute that name.

Paper rules that shaped these snippets: flex + gap only (no margin, no grid), one text colour per text node (split nodes for an accent word), SVG icons inline, decorative layers absolute.

## Contents
1. Accent-word headline
2. Greeting + headline block
3. Stat row
4. Action tiles (primary gradient + secondary)
5. Section header
6. Card with progress ring (list size)
7. Hero ring card with 3 stats
8. Segmented control
9. Step progress bar
10. Floating tab bar with centre FAB
11. Success medallion hero
12. Status chips
13. Secondary pill button
14. Progress ring maths
15. React Native notes

---

### 1. Accent-word headline
```html
<div layer-name="Headline" style="display:flex;flex-direction:column;color:var(--color-ink);font-family:var(--font-sans);font-size:34px;font-weight:650;letter-spacing:-0.035em;line-height:38px;">
  <div style="display:flex;gap:9px;"><div>You have</div><div layer-name="Accent" style="color:var(--color-accent);">3 tasks</div></div>
  <div>today.</div>
</div>
```
Gap ≈ 0.26 × font-size (9px at 34, 10px at 40, 12px at 48) stands in for the space between nodes.

### 2. Greeting + headline block
```html
<div layer-name="Screen heading" style="display:flex;flex-direction:column;gap:6px;padding:18px 24px 20px;flex-shrink:0;">
  <div style="color:var(--color-muted);font-family:var(--font-sans);font-size:15px;font-weight:500;letter-spacing:-0.01em;line-height:20px;">Good morning, Alex</div>
  <!-- headline from §1 -->
</div>
```

### 3. Stat row
```html
<div layer-name="Stat row" style="display:flex;align-items:stretch;background-color:var(--color-white);border:1px solid var(--color-border);border-radius:20px;padding-block:14px;box-shadow:0px 2px 12px rgba(0,0,0,0.04);">
  <div style="display:flex;flex-direction:column;align-items:center;gap:2px;flex:1;">
    <div style="color:var(--color-ink);font-family:var(--font-sans);font-size:22px;font-weight:700;letter-spacing:-0.02em;line-height:28px;font-variant-numeric:tabular-nums;">24</div>
    <div style="color:var(--color-muted);font-family:var(--font-sans);font-size:12px;font-weight:500;line-height:16px;">Total</div>
  </div>
  <div style="width:1px;background-color:var(--color-border);flex-shrink:0;"></div>
  <!-- repeat column; colour the most important value in the accent -->
</div>
```

### 4. Action tiles
```html
<div layer-name="Actions" style="display:flex;gap:12px;">
  <div layer-name="Primary tile" style="display:flex;flex-direction:column;justify-content:space-between;flex:1;height:132px;padding:16px;border-radius:20px;background-image:linear-gradient(155deg,var(--color-accent-light) 0%,var(--color-accent) 55%,var(--color-accent-dark) 100%);box-shadow:0px 16px 30px -14px color-mix(in srgb, var(--color-accent) 60%, transparent),inset 0px 1px 0px rgba(255,255,255,0.25);">
    <div style="display:flex;justify-content:space-between;align-items:flex-start;">
      <div style="display:flex;width:38px;height:38px;border-radius:12px;background-color:rgba(255,255,255,0.18);align-items:center;justify-content:center;"><!-- white 20px icon --></div>
      <div style="display:flex;padding:4px 8px;border-radius:999px;background-color:rgba(255,255,255,0.2);color:#FFFFFF;font-family:var(--font-sans);font-size:11px;font-weight:600;line-height:14px;">Now</div>
    </div>
    <div style="display:flex;flex-direction:column;gap:2px;">
      <div style="color:#FFFFFF;font-family:var(--font-sans);font-size:17px;font-weight:650;letter-spacing:-0.015em;line-height:22px;">Quick start</div>
      <div style="color:rgba(255,255,255,0.82);font-family:var(--font-sans);font-size:13px;line-height:17px;">Start in one tap</div>
    </div>
  </div>
  <div layer-name="Secondary tile" style="display:flex;flex-direction:column;justify-content:space-between;flex:1;height:132px;padding:16px;border-radius:20px;background-color:var(--color-white);border:1px solid var(--color-border);box-shadow:0px 2px 12px rgba(0,0,0,0.04);">
    <div style="display:flex;width:38px;height:38px;border-radius:12px;background-color:var(--color-surface);align-items:center;justify-content:center;"><!-- ink 20px icon --></div>
    <div style="display:flex;flex-direction:column;gap:2px;">
      <div style="color:var(--color-ink);font-family:var(--font-sans);font-size:17px;font-weight:650;letter-spacing:-0.015em;line-height:22px;">Plan ahead</div>
      <div style="color:var(--color-muted);font-family:var(--font-sans);font-size:13px;line-height:17px;">Set it up for later</div>
    </div>
  </div>
</div>
```

### 5. Section header
```html
<div style="display:flex;justify-content:space-between;align-items:baseline;padding-top:10px;">
  <div style="color:var(--color-ink);font-family:var(--font-sans);font-size:17px;font-weight:650;letter-spacing:-0.015em;line-height:22px;">Upcoming</div>
  <div style="color:var(--color-accent);font-family:var(--font-sans);font-size:14px;font-weight:600;line-height:20px;">See all</div>
</div>
```

### 6. Card with progress ring (52px)
```html
<div layer-name="Item card" style="display:flex;align-items:center;gap:14px;padding:14px 16px 14px 14px;background-color:var(--color-white);border:1px solid var(--color-border);border-radius:20px;box-shadow:0px 2px 12px rgba(0,0,0,0.04);">
  <div layer-name="Progress ring" style="display:flex;position:relative;width:52px;height:52px;flex-shrink:0;align-items:center;justify-content:center;">
    <svg width="52" height="52" viewBox="0 0 52 52" style="position:absolute;left:0;top:0;"><circle cx="26" cy="26" r="22" fill="none" stroke="var(--color-surface)" stroke-width="5"/><circle cx="26" cy="26" r="22" fill="none" stroke="var(--color-accent)" stroke-width="5" stroke-linecap="round" stroke-dasharray="138.23" stroke-dashoffset="46.08" transform="rotate(-90 26 26)"/></svg>
    <div style="position:relative;color:var(--color-ink);font-family:var(--font-sans);font-size:12px;font-weight:700;letter-spacing:-0.03em;line-height:16px;font-variant-numeric:tabular-nums;">8/12</div>
  </div>
  <div style="display:flex;flex-direction:column;gap:3px;flex:1;min-width:0;">
    <div style="color:var(--color-ink);font-family:var(--font-sans);font-size:16px;font-weight:600;letter-spacing:-0.015em;line-height:21px;">Morning run</div>
    <div style="color:var(--color-muted);font-family:var(--font-sans);font-size:13px;line-height:18px;">Today · 6:30 AM · Riverside Park</div>
  </div>
  <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="var(--color-subtle)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" style="flex-shrink:0;"><path d="m9 5 7 7-7 7"/></svg>
</div>
```

### 7. Hero ring card with 3 stats (78px ring)
```html
<div layer-name="Progress card" style="display:flex;align-items:center;gap:18px;padding:16px 18px;background-color:var(--color-white);border:1px solid var(--color-border);border-radius:20px;box-shadow:0px 2px 12px rgba(0,0,0,0.04);">
  <div style="display:flex;position:relative;width:78px;height:78px;flex-shrink:0;align-items:center;justify-content:center;">
    <svg width="78" height="78" viewBox="0 0 78 78" style="position:absolute;left:0;top:0;"><circle cx="39" cy="39" r="33" fill="none" stroke="var(--color-surface)" stroke-width="7"/><circle cx="39" cy="39" r="33" fill="none" stroke="var(--color-accent)" stroke-width="7" stroke-linecap="round" stroke-dasharray="207.35" stroke-dashoffset="69.12" transform="rotate(-90 39 39)"/></svg>
    <div style="display:flex;flex-direction:column;align-items:center;position:relative;">
      <div style="color:var(--color-ink);font-family:var(--font-sans);font-size:22px;font-weight:700;letter-spacing:-0.03em;line-height:24px;font-variant-numeric:tabular-nums;">67%</div>
      <div style="color:var(--color-muted);font-family:var(--font-sans);font-size:10px;font-weight:500;line-height:12px;">done</div>
    </div>
  </div>
  <div style="display:flex;flex-direction:column;gap:10px;flex:1;min-width:0;">
    <div style="color:var(--color-ink);font-family:var(--font-sans);font-size:17px;font-weight:650;letter-spacing:-0.015em;line-height:22px;">8 of 12 done</div>
    <div style="display:flex;align-items:stretch;gap:10px;">
      <div style="display:flex;flex-direction:column;gap:1px;flex:1;"><div style="color:var(--color-success);font-family:var(--font-sans);font-size:17px;font-weight:700;line-height:22px;">8</div><div style="color:var(--color-muted);font-family:var(--font-sans);font-size:11px;font-weight:500;line-height:14px;">Done</div></div>
      <div style="width:1px;background-color:var(--color-border);flex-shrink:0;"></div>
      <!-- Pending (warning), Failed (danger) -->
    </div>
  </div>
</div>
```

### 8. Segmented control
```html
<div layer-name="Segmented control" style="display:flex;padding:4px;gap:2px;border-radius:999px;background-color:var(--color-surface);">
  <div style="display:flex;flex:1;justify-content:center;align-items:center;height:34px;border-radius:999px;background-color:var(--color-white);box-shadow:0px 1px 3px rgba(0,0,0,0.08);color:var(--color-ink);font-family:var(--font-sans);font-size:13px;font-weight:600;line-height:16px;">All 12</div>
  <div style="display:flex;flex:1;justify-content:center;align-items:center;height:34px;color:var(--color-muted);font-family:var(--font-sans);font-size:13px;font-weight:500;line-height:16px;">Pending 3</div>
  <div style="display:flex;flex:1;justify-content:center;align-items:center;height:34px;color:var(--color-muted);font-family:var(--font-sans);font-size:13px;font-weight:500;line-height:16px;">Failed 1</div>
</div>
```

### 9. Step progress bar
5 steps → 22px segments; 6 steps → 18px. Done = accent, todo = `rgba(10,10,10,0.1)` (dark theme: `rgba(255,255,255,0.15)`).
```html
<div layer-name="Step progress · 2 of 5" style="display:flex;gap:4px;align-items:center;">
  <div style="width:22px;height:5px;border-radius:999px;background-color:var(--color-accent);"></div>
  <div style="width:22px;height:5px;border-radius:999px;background-color:var(--color-accent);"></div>
  <div style="width:22px;height:5px;border-radius:999px;background-color:rgba(10,10,10,0.1);"></div>
  <div style="width:22px;height:5px;border-radius:999px;background-color:rgba(10,10,10,0.1);"></div>
  <div style="width:22px;height:5px;border-radius:999px;background-color:rgba(10,10,10,0.1);"></div>
</div>
```
Centre it in the nav row (back · bar · Save). If the original counter was absolutely positioned, re-apply `position:absolute; left:(rowWidth − barWidth)/2`.

### 10. Floating tab bar with centre FAB
```html
<div layer-name="Tab bar" style="display:flex;justify-content:center;padding:8px 16px 6px;flex-shrink:0;">
  <div layer-name="Floating bar" style="display:flex;align-items:center;justify-content:space-between;width:100%;padding:7px;border-radius:999px;background-color:rgba(255,255,255,0.88);border:1px solid var(--color-border);backdrop-filter:blur(20px);box-shadow:0px 8px 24px rgba(0,0,0,0.07);">
    <div layer-name="Tab · Home (active)" style="display:flex;flex-direction:column;align-items:center;gap:2px;width:64px;padding-block:6px;border-radius:999px;background-color:var(--color-accent-soft);">
      <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="var(--color-accent)" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round"><path d="m3 10 9-7 9 7v11h-7v-7h-4v7H3z"/></svg>
      <div style="color:var(--color-accent);font-family:var(--font-sans);font-size:10px;font-weight:600;line-height:13px;">Home</div>
    </div>
    <div layer-name="Tab · Activity" style="display:flex;flex-direction:column;align-items:center;gap:2px;width:64px;padding-block:6px;">
      <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="var(--color-muted)" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="5" width="18" height="16" rx="3"/><path d="M7 3v4m10-4v4M3 11h18"/></svg>
      <div style="color:var(--color-muted);font-family:var(--font-sans);font-size:10px;font-weight:500;line-height:13px;">Activity</div>
    </div>
    <div layer-name="FAB" style="display:flex;width:54px;height:44px;border-radius:999px;background-color:var(--color-accent);align-items:center;justify-content:center;box-shadow:0px 8px 16px -6px color-mix(in srgb, var(--color-accent) 60%, transparent);">
      <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="#FFFFFF" stroke-width="2.2" stroke-linecap="round"><path d="M12 5v14M5 12h14"/></svg>
    </div>
    <!-- two more inactive tabs -->
  </div>
</div>
```
For absolutely-positioned screens wrap with `position:absolute;left:0;top:744px;width:390px` (adjust top so the pill clears the home indicator).

### 11. Success medallion hero
```html
<div layer-name="Success hero" style="display:flex;flex-direction:column;align-items:center;gap:16px;padding:8px 24px 22px;">
  <div style="display:flex;width:96px;height:96px;border-radius:999px;background-color:var(--color-accent-soft);align-items:center;justify-content:center;box-shadow:0px 18px 40px -12px color-mix(in srgb, var(--color-accent) 45%, transparent);">
    <div style="display:flex;width:68px;height:68px;border-radius:999px;background-image:linear-gradient(160deg,var(--color-accent-light) 0%,var(--color-accent) 60%,var(--color-accent-dark) 100%);align-items:center;justify-content:center;box-shadow:inset 0px 1px 0px rgba(255,255,255,0.35);">
      <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="#FFFFFF" stroke-width="2.6" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12.5l4.5 4.5L19 7.5"/></svg>
    </div>
  </div>
  <div style="display:flex;gap:9px;color:var(--color-ink);font-family:var(--font-sans);font-size:34px;font-weight:650;letter-spacing:-0.035em;line-height:38px;"><div>You’re all</div><div style="color:var(--color-accent);">set.</div></div>
  <div style="color:var(--color-muted);font-family:var(--font-sans);font-size:15px;line-height:20px;">We saved a copy to your account.</div>
</div>
```
Pair with a screen background `radial-gradient(70% 26% at 50% 16%, accent@12%, transparent)`.

### 12. Status chips
```html
<div style="display:flex;align-items:center;gap:6px;padding:6px 10px;border-radius:999px;background-color:var(--color-white);border:1px solid var(--color-border);">
  <div style="width:8px;height:8px;border-radius:999px;background-color:var(--color-success);"></div>
  <div style="color:var(--color-ink);font-family:var(--font-sans);font-size:12px;font-weight:500;line-height:15px;">Done</div>
</div>
```

### 13. Secondary pill button
`height:52px; border-radius:999px; background:white; border:1px solid var(--color-border); ink 16/600 label`. Primary = same without border, accent fill, white label, no shadow.

### 14. Progress ring maths
Circumference `C = 2πr`. `stroke-dasharray = C`, `stroke-dashoffset = C × (1 − progress)`, `transform = rotate(-90 cx cy)` so it starts at 12 o'clock.
- r=22 (52px ring, 5px stroke): C = 138.23 → 8/12 → 46.08; 14/20 → 41.47; 3/4 → 34.56.
- r=33 (78px ring, 7px stroke): C = 207.35 → 67% → 69.12.

### 15. React Native notes
- Ring: `react-native-svg` `<Circle>` with the same dasharray/offset maths; animate `strokeDashoffset` with Reanimated.
- Floating tab bar: custom `tabBar` in React Navigation / Expo Router `Tabs`; `expo-blur` `BlurView intensity={40} tint="light"`, `position:'absolute', left:16, right:16, bottom: insets.bottom + 4`, `borderRadius:999`, `overflow:'hidden'`. Add `paddingBottom` to screen content so lists scroll under it.
- Segmented control: `Pressable` row on a `surface` track; animate the white selected pill with `useAnimatedStyle` translateX.
- Accent-word headline: nested `<Text>` works in RN — `<Text style={display}>You have <Text style={{color:accent}}>3 tasks</Text>{'\n'}this week.</Text>`.
- Glow shadows: iOS `shadowColor = accent, shadowOpacity .5, shadowRadius 16, shadowOffset {0,12}`; Android has no coloured shadow — fake with a blurred accent `View` behind, or skip.
