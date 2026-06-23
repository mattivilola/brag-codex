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

The upstream repository did not include a top-level license file at the commit used for this clone. Before publishing this repository as open source, verify the upstream content and bundled media license terms, then add the intended license and any required third-party notices.
