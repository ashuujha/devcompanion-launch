# Dev Companion — free offline developer preview

A personal terminal companion for development work. Name it, choose a text pet,
response style and downloaded local brain, then carry goals and decisions across
sessions. Give it a development goal and return to changes you can review.
Inference, conversation, memory and project awareness stay on your machine.

**Linux x86_64 preview 0.3.0.** Application source remains private. This repository
contains public launch assets, feedback templates and binary releases.

- [Download and checksums](https://github.com/ashuujha/devcompanion-launch/releases/tag/v0.3.0)
- [First-session setup and privacy](https://ashuujha.github.io/devcompanion-launch/guide.html)
- [Recorded offline workflow](https://ashuujha.github.io/devcompanion-launch/demo.txt)
- [First-session feedback](https://github.com/ashuujha/devcompanion-launch/issues/new/choose)

## Start with your own project

Install the CLI and local Ollama runtime using the guide. Download a model once:

```sh
ollama pull qwen3:4b-instruct-2507-q4_K_M
```

Skip the pull if `ollama list` already shows it. Open a terminal in your actual
Git project and launch:

```sh
dot companion --name Pixel --pet cat --style mentor
dot
```

First use asks before enabling the project. At the prompt, describe your actual
task. `/help` lists actions; `/home` refreshes your personal dashboard; `/quit`
returns to the shell. `devcompanion` supports the same commands.

## What 0.3 adds

- Named dot/cat/fox/robot pets or imported text avatars; styles, preferences and
  local model selection persist. A live `/model NAME` switch saves the new brain.
- Editable goals and decisions; keyword search and optional local CPU embeddings.
  Learning proposes guidance from saved user statements, with source evidence.
  It is off by default; proposals need acceptance before they guide responses.
- Reviewed edits and new files, explicit registered checks, separately reviewed
  revisions from actual failures, and rollback that refuses later edits.
- CPU/context/token/retention/cooldown controls, actual local response measurements,
  editable usefulness ratings, and explicit suggestions based on current evidence.
- Opt-in Bash and VS Code process-task adapters, private project JSON export and
  consistent whole-database backup without overwrites.

Local work continues after closing chat while the laptop stays on. Background
investigation is bounded and cannot run model-generated commands or apply code
without explicit approval. Proactive awareness uses the selected Git project
and commands you choose to record. It does not capture desktop activity, ambient
terminal history or unsaved editor buffers.

## Demonstrated behavior and limits

The static binary passed 52 integration tests, formatting, clippy and real terminal
checks. A real continuing session without external connectivity exercised model
switching, identity, reviewed learning, optional semantic retrieval and actual
CPU token/timing measurements. See the demo and release notes for task evidence.
These are scripted fixtures, not a general coding-quality benchmark.

Small models can make mistakes, repeat irrelevant context or give poorly worded
explanations. Review actual diffs and relevant checks. Changes are bounded to
three small text files and eight investigation turns. Larger changes, broader
local tools, full editor awareness and a graphical desktop pet remain future work.
macOS validation is pending. Useful adoption and retention are not established.

No application telemetry or silent cloud fallback is present. Initial downloads
need internet; chosen developer commands can themselves depend on network services.
Exports and backups contain private content; keep them private. Feedback here is
public, so remove private code and secrets before posting.

The archive contains the static CLI, an MIT application license, dependency
notices and quickstart. It contains no application source or model weights.
