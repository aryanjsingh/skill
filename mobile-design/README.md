# mobile-design

Our default design system for mobile apps, packaged as a Claude skill. Point Claude at an app (a Paper file, a React Native or Expo codebase, or just an idea) and it designs or redesigns the screens in one consistent style. The result looks premium and calm, with dense information.

## The look in one paragraph

Neutral surfaces do the quiet work and one brand accent does the talking. Light apps sit on a warm off-white canvas (`#F7F7F5`) with white cards on 1px hairlines. Dark apps sit on neutral near-black. Each headline puts its key word in the accent ("You have **3 tasks** today."). Every button, chip, filter and tab bar is a pill. Data shows up as objects: progress rings, 3-column stat rows, segmented progress bars and status chips. Glows, gradients and a soft accent wash at the top of the screen are kept for hero moments.

## What Claude gets

| File | Contents |
|---|---|
| `SKILL.md` | Principles, workflow, 14 signature patterns, 8 screen recipes, type and icon rules, review checklist |
| `references/tokens.md` | Light and dark palettes, accent options by mood, type scale, spacing, radius, shadows. Includes CSS, Tailwind v4 and React Native themes |
| `references/components.md` | Paste-ready markup for every pattern (headline, stat row, action tiles, progress rings with the maths, segmented control, step bar, floating tab bar with centre button, success medallion, status chips) plus React Native notes |
| `references/paper-workflow.md` | How to restyle a whole app file in Paper without breaking it, and the traps we hit doing it |

## Install

```bash
mkdir -p ~/.claude/skills/aryan-mobile-design
cp -R v1/. ~/.claude/skills/aryan-mobile-design/
```

Then ask for something like "redesign the home screen of this app", "design onboarding for a habit tracker", or "apply my mobile design system to this Paper file".

## Versions

| Version | Notes |
|---|---|
| [v1](v1/) | First release, and our first skill ever. We built it while redesigning a 48-screen mobile app end to end in Paper. It covers light and dark themes, home, list, detail, wizard, success, empty-state, onboarding and paywall screens, and the full Paper workflow. |
