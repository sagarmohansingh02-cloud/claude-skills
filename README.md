# claude-skills

Agent skills for video and motion design work, built and used in production. Each skill is a folder with a `SKILL.md` that Claude Code (and other agents that support the skills format) loads when the task matches.

## Skills

| Skill | What it does |
|---|---|
| [product-video](skills/product-video/SKILL.md) | Directs a product video, launch film or UI motion graphic so it looks premium instead of like generic AI motion graphics. It covers brand constraints, design before motion, eased motion, flowing transitions, BPM-first music and subtractive sound, plus a direction loop: reference → context → 3 storyboards → stills → render → director notes. Pairs with [HyperFrames](https://github.com/heygen-com/hyperframes) for the build. |

## Install

With the [skills CLI](https://skills.sh):

```bash
npx skills add sagarmohansingh02-cloud/claude-skills --skill product-video
```

Or copy a skill folder by hand:

```bash
git clone https://github.com/sagarmohansingh02-cloud/claude-skills
cp -R claude-skills/skills/product-video ~/.claude/skills/
```

## Credits

`product-video` synthesizes ideas from leo ([@leomeethewoo](https://x.com/leomeethewoo)) and Rexan Wong ([@rexan_wong](https://x.com/rexan_wong)), paraphrased and credited in its [sources](skills/product-video/references/sources.md), together with lessons from building the [Cache](https://github.com/sagarmohansingh02-cloud/cache) launch film.

## License

[MIT](LICENSE)
