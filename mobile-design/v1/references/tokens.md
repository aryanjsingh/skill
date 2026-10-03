# Tokens

## Contents
1. Light theme
2. Dark theme
3. Accent options
4. Type scale
5. Spacing, radius, size
6. Shadows & effects
7. As CSS variables / Tailwind v4 / React Native

## 1. Light theme (default for forms, consent, utilities)

| Token | Value | Role |
|---|---|---|
| canvas | `#F7F7F5` | Screen background (warm off-white) |
| card / white | `#FFFFFF` | Cards, secondary pills, tab bar base |
| surface | `#EFEFED` | Recessed wells: avatar circles, progress tracks, segmented track, date tiles |
| border | `#E7E7EA` | 1px card edges, dividers, secondary pill border |
| ink | `#0A0A0A` | Primary text and icons (19:1 on white) |
| muted | `#6B6B70` | Secondary text, inactive icons (5.3:1 on white, 4.9:1 on canvas) |
| subtle | `#A1A1A6` | Placeholders, disabled, chevrons only — never body copy |

## 2. Dark theme (media, fintech, social, wearables)

| Token | Value | Role |
|---|---|---|
| base | `#0E0E0E` (range `#000`–`#141414`) | Screen background, neutral not blue-grey |
| card | `#1C1C1E` | Cards, list rows |
| raised | `#2C2C2E` | Inputs, tiles, active segment, stat wells |
| hairline | `rgba(255,255,255,0.06)` | Borders and dividers |
| text | `#FFFFFF` | Primary text; white pill CTA fill |
| muted | `#8E8E93` | Secondary (5.2:1 on card) |

Dark elevation = step the surface lighter (`#0E0E0E` → `#1C1C1E` → `#2C2C2E`). Don't add shadows on dark. Glows (accent at 30–50% blur) behind hero objects are the exception.

## 3. Accent (one per product)

Use the product's brand colour. If none exists, pick one by mood:

| Accent | Hex | Fits |
|---|---|---|
| Hot red | `#FF3C5A` / `#F4141E` | Social, camera, forms that need energy |
| Orange | `#F6622A` | Health, AI image, energy |
| Orchid | `#D774CD` | Creator, community |
| iOS blue | `#109EFD` | Fitness, utility, native feel |
| Periwinkle | `#5373F4` | Productivity on dark navy |
| Mint | `#2FB67E` | Money, growth |
| Deep teal | `#084E49` | Services, calm, premium (white text 9.6:1) |
| Violet | `#957CFF` | Education, analytics |

Derived from the accent:
- `accent-soft` = accent at ~8–10% on white (e.g. red → `#FDEBEC`): active tab pill, selected rows, medallion ring.
- `accent-light` / `accent-dark` = accent ~15% lighter / ~12% darker, for the hero-tile and medallion gradient `linear-gradient(155deg, accent-light 0%, accent 55%, accent-dark 100%)` (e.g. red `#FF4A52 → #F4141E → #D90C15`).
- Glow: `0 16px 30px -14px accent@60%`.

Semantic (always with a word or icon): success `#16B364`, pending/warning `#E8A23B`, danger = accent if accent is red, else `#ED455A`.

## 4. Type scale (SF Pro / Inter)

| Role | Size / line | Weight | Tracking |
|---|---|---|---|
| Hero number | 40 / 44 | 700 | −0.02em, tabular |
| Display headline | 34–40 / 38–44 | 650 | −0.035em |
| Ring value (large) | 22 / 24 | 700 | −0.03em, tabular |
| Stat value | 22 / 28 | 700 | −0.02em, tabular |
| Section title | 17 / 22 | 650 | −0.015em |
| Card title | 16 / 21 | 600 | −0.015em |
| Body | 15 / 20 | 400 | −0.01em, muted |
| Label / meta | 13 / 18 | 500 | 0 |
| Caption / stat label | 11–12 / 14–16 | 500 | 0 |
| Tab label | 10 / 13 | 500 (600 active) | 0 |
| Eyebrow (style guides) | 12 / 16 | 600 | +0.06em uppercase |

## 5. Spacing, radius, size

- Screen gutter 24px (16–20 on dense screens). Gap between cards 12px. Inside cards 14–20px. 4pt grid.
- Radius: tiles/inputs 12–14 · cards 20 · sheets 28 · hero icon squircle 22% · everything tappable full pill (999px).
- CTA height 50–56. Tab bar: pill inset 16px, 7px inner padding, tab items 64 wide, FAB 54×44. Avatar 36–44. Ring 52 (list) / 78 (hero).

## 6. Shadows & effects (light theme)

| Name | Value | Use |
|---|---|---|
| card | `0 2px 12px rgba(0,0,0,0.04)` + 1px border | All cards |
| float | `0 8px 24px rgba(0,0,0,0.07)` | Floating tab bar, sheets |
| segment | `0 1px 3px rgba(0,0,0,0.08)` | Selected segment pill |
| accent glow | `0 16px 32px -14px accent@55%` | Primary hero card/tile |
| FAB glow | `0 8px 16px -6px accent@60%` | Centre + button |
| medallion glow | `0 18px 40px -12px accent@45%` | Success badge |
| top wash | `linear-gradient(180deg, accent@12% 0%, accent@4% 20%, transparent 34%)` | Hero screens |
| hero radial | `radial-gradient(60% 32% at 50% 30%, accent@13%, transparent)` | Behind onboarding illustration |

CTAs have **no** shadow (flat accent pill) except the single hero card on Home.

## 7. Code

### CSS variables
```css
:root{
  --canvas:#F7F7F5; --card:#FFFFFF; --surface:#EFEFED; --border:#E7E7EA;
  --ink:#0A0A0A; --muted:#6B6B70; --subtle:#A1A1A6;
  --accent:#F4141E; --accent-soft:#FDEBEC; --accent-light:#FF4A52; --accent-dark:#D90C15; /* example accent: replace with the product's brand colour */
  --success:#16B364; --warning:#E8A23B;
  --radius-card:20px; --radius-tile:14px; --radius-sheet:28px; --radius-pill:999px;
  --shadow-card:0 2px 12px rgba(0,0,0,.04); --shadow-float:0 8px 24px rgba(0,0,0,.07);
}
```

### Tailwind v4
```css
@theme{
  --color-canvas:#F7F7F5; --color-card:#FFFFFF; --color-surface:#EFEFED; --color-border:#E7E7EA;
  --color-ink:#0A0A0A; --color-muted:#6B6B70; --color-subtle:#A1A1A6;
  --color-accent:#F4141E; --color-accent-soft:#FDEBEC; --color-accent-light:#FF4A52; --color-accent-dark:#D90C15; /* example accent */ --color-success:#16B364; --color-warning:#E8A23B;
  --radius-card:20px; --radius-tile:14px; --radius-sheet:28px;
  --shadow-card:0 2px 12px rgba(0,0,0,.04); --shadow-float:0 8px 24px rgba(0,0,0,.07);
}
```

### React Native
```ts
export const theme = {
  light: { canvas:'#F7F7F5', card:'#FFFFFF', surface:'#EFEFED', border:'#E7E7EA', ink:'#0A0A0A', muted:'#6B6B70', subtle:'#A1A1A6' },
  dark:  { canvas:'#0E0E0E', card:'#1C1C1E', surface:'#2C2C2E', border:'rgba(255,255,255,0.06)', ink:'#FFFFFF', muted:'#8E8E93', subtle:'#636366' },
  accent:'#F4141E', accentSoft:'#FDEBEC', accentLight:'#FF4A52', accentDark:'#D90C15', // example accent: use the product's brand colour success:'#16B364', warning:'#E8A23B',
  radius:{ tile:14, card:20, sheet:28, pill:999 },
  type:{ display:{fontSize:34,lineHeight:38,fontWeight:'650',letterSpacing:-1.2}, section:{fontSize:17,lineHeight:22,fontWeight:'650'}, body:{fontSize:15,lineHeight:20}, label:{fontSize:13,lineHeight:18,fontWeight:'500'}, caption:{fontSize:11,lineHeight:14,fontWeight:'500'} },
  shadow:{ card:{shadowColor:'#000',shadowOpacity:0.04,shadowRadius:12,shadowOffset:{width:0,height:2},elevation:1} },
} as const;
```
