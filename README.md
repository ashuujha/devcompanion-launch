# Dev Companion · free offline developer companion

[Try the preview](https://ashuujha.github.io/devcompanion-launch/) ·
[Setup and privacy](https://ashuujha.github.io/devcompanion-launch/guide.html) ·
[Downloads](https://github.com/ashuujha/devcompanion-launch/releases) ·
[First-session feedback](https://github.com/ashuujha/devcompanion-launch/issues/new/choose)

A persistent local assistant for development work. Continue a conversation,
recover remembered project context, get a useful briefing as code changes,
and review a proposed action before approving it.

This repository hosts the public launch page, binary releases and feedback.
**The application source is currently private.** This is a free early preview;
it is not an announcement of publicly available application source.

## First session

Download and verify the Linux x86_64 archive from Releases. Install its binary
into your PATH. Install [Ollama](https://ollama.com/download), start its local
server and download a model:

```sh
ollama pull qwen3:4b-instruct-2507-q4_K_M
cd your-git-project
devcompanion init --goal "Finish the login flow"
devcompanion start
```

`start` combines local conversation and project awareness. `/file PATH` attaches
a repository text file; `/remember TEXT` saves an intention; `/quiet` pauses
awareness; `/quit` ends the session. Capture relevant commands in another terminal
with `devcompanion run -- COMMAND`.

The companion uses a downloaded model. It can produce a proactive briefing
after a relevant edit or recorded command result, with a 10-second edit debounce
and at most one automatic inference per 90 seconds. Idle observation invokes no model.

## Control and memory

User intentions, conversation, code fingerprints, assistant interpretations and
command outcomes persist locally in SQLite. Earlier interpretations retain their
original code state. Model suggestions cannot directly run commands.

Register permitted checks, then inspect and approve a proposal:

```sh
devcompanion check add tests -- npm test
devcompanion plan "What should I check before finishing?"
devcompanion proposals
devcompanion approve 1
```

Use the proposal ID displayed for your session. Outdated code, changed action
definitions, unregistered model actions and repeated approvals are refused.

## What is verified

- Nineteen integration tests exercise persistence, project isolation, dirty
  edits, check freshness, timeout/descendant cleanup, output bounds, local
  streaming, action approval and context retrieval.
- A real local model explained a reproduced addition bug from a test failure
  and attached source. A continuing session generated a briefing after an edit.
- An isolated network smoke test denied external connectivity and completed
  a local-model answer.
- Linux x86_64 static binary. macOS validation remains pending.

## Known limits

Small models can make mistakes. Memory retrieval is currently lexical and based
on recency, with no semantic memory graph. Actions are currently registered checks,
and code editing is manual. Captured commands are bounded noninteractive jobs;
use ordinary terminal tools for servers and interactive programs.

Initial runtime/model downloads require internet. Core operation afterward is
offline. Your chosen checks may themselves require network services. There is
no application usage transmission or desktop capture. Read the guide before
sharing sensitive source or output.

Please report whether it helped a real development task using the feedback
template. Downloads, stars and verified users are different measurements;
no adoption count is claimed.
