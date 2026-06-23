# brag for Codex

`brag` turns the current project website or app into a short, polished, shareable launch video using Hyperframes.

This repository is a Codex-compatible clone of the original [`latent-spaces/brag`](https://github.com/latent-spaces/brag) project. It preserves the original `/brag` workflow, references, bundled music/SFX assets, examples, and Hyperframes handoff model, adapted so Codex can load it as a skill.

## Install

Copy the skill folder into your Codex skills directory:

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
rsync -a --exclude '.DS_Store' skills/brag/ "${CODEX_HOME:-$HOME/.codex}/skills/brag/"
```

Restart Codex after copying so the skill is discovered.

## Use

From any project directory, ask Codex:

```text
Use $brag to make a launch video for this project.
```

You can steer the output:

```text
Use $brag with --tone "fake Series A launch from 2016"
Use $brag with --tone polished --format vertical
Use $brag with --duration 18 --no-sfx
```

The skill writes a `brag-output/` folder with:

- `brag-plan.md`
- `composition-brief.md`
- `share-copy.txt`
- `composition/`
- `brag.mp4` after rendering

## Requirements

- Codex with skill support
- Node.js 22+
- FFmpeg on `PATH`
- Hyperframes CLI via `npx hyperframes`

Check Hyperframes before rendering:

```bash
npx hyperframes doctor
```

## Test

Run the structural validator:

```bash
uv run --with pyyaml python ~/.codex/skills/.system/skill-creator/scripts/quick_validate.py skills/brag
```

Check the local render toolchain:

```bash
npx hyperframes doctor
```

Install the skill into Codex:

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
rsync -a --exclude '.DS_Store' skills/brag/ "${CODEX_HOME:-$HOME/.codex}/skills/brag/"
```

Restart Codex, open any web app project, then ask:

```text
Use $brag with --duration 15 --tone polished to make a launch video for this project.
```

Expected result: a `brag-output/` directory containing `brag-plan.md`, `composition-brief.md`, `share-copy.txt`, `composition/`, and, after render approval, `brag.mp4`.

Optional frame analysis: Hyperframes `snapshot --describe` uses `GEMINI_API_KEY` when set. Source your shell profile before testing if needed:

```bash
source ~/.zshrc
```

## What's included

- `skills/brag/` - Codex skill, references, scripts, bundled music, and SFX
- `examples/` - original fake product sites and generated benchmark videos
- `docs/` - adapted launch/demo site
- `PRODUCT.md` - original product/design brief, lightly adapted for Codex

## Attribution

This project is based on the original [`latent-spaces/brag`](https://github.com/latent-spaces/brag), fetched from upstream commit `9b5a758fb1c0f68cab124ccb4b960864ea03235a`.

Original credits from upstream:

- Music: [ende.app](https://ende.app/en) "Happy Beats / Business Moves"
- Sound effects: [Kenney](https://kenney.nl/)
- Video generation: [Hyperframes](https://hyperframes.heygen.com/)
- Fake demo sites: [Impeccable](https://impeccable.style/)

## License note

This Codex adaptation is released under the MIT License. Third-party and upstream-derived content, including bundled media, remains subject to its original rights and license terms.

If this repository includes material that should not be redistributed for IPR or licensing reasons, contact the repository owner on X or GitHub and the material will be removed.
