# skill

A public collection of the [Claude skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) we write and use day to day.

A skill is a folder with a `SKILL.md` file (plus optional reference docs) that teaches Claude how to do one kind of work well, the same way every time. Claude reads the short description, decides when the skill applies, and loads the rest only when it needs it.

## Skills

| Skill | Version | What it does |
|---|---|---|
| [mobile-design](mobile-design/) | [v1](mobile-design/v1/) | Our default design system for mobile apps. It covers neutral surfaces, one brand accent, pill buttons, a floating tab bar, progress rings, stat rows and more. Works in Paper, React Native, Expo, SwiftUI and mobile web. |

`mobile-design` is our first skill. More will follow.

## Using a skill

### Claude Code

Copy the version you want into your skills folder:

```bash
git clone https://github.com/aryanjsingh/skill.git
mkdir -p ~/.claude/skills/aryan-mobile-design
cp -R skill/mobile-design/v1/. ~/.claude/skills/aryan-mobile-design/
```

To scope a skill to one project instead, put it in that project's `.claude/skills/` folder. Claude picks skills up automatically. Ask for the kind of work the skill covers, or name it directly.

### Claude.ai and the API

Zip the version folder (the one that contains `SKILL.md`) and upload it as a custom skill.

## How this repo is organised

```
skill/
└── <skill-name>/
    ├── README.md          what the skill is, and a changelog
    └── v1/                a complete, installable skill
        ├── SKILL.md
        └── references/    detail Claude loads only when needed
```

Each skill gets its own folder. Each release lives in its own version folder (`v1`, `v2`, ...) and is never edited after release. Improvements go into a new version, so anyone can pin the version they rely on.

## Contributing

Spotted something wrong, or have an idea for a skill? Open an issue or a pull request.
