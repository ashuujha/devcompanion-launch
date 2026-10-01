# Dev Companion — local developer workflow preview

Dev Companion keeps a small, private work desk for an opted-in Git project. It can
stay available after chat closes, notice a real terminal failure or an enabled
VS Code diagnostic, and keep that incident with its source evidence. You can ask
a local model to investigate and prepare a correction for review. Reminders and
focus breaks remain available between conversations. The pet and companion name
are optional ways to make it feel familiar; the work ledger is the point.

**v0.4.0 workflow preview for Linux x86_64.** This repository contains public
launch assets, feedback templates and binary releases. The application source
is currently private.

- [Download, checksums and release notes](https://github.com/ashuujha/devcompanion-launch/releases/tag/v0.4.0)
- [Setup, update and privacy guide](https://ashuujha.github.io/devcompanion-launch/guide.html)
- [Recorded v0.4 local-model workflow](https://ashuujha.github.io/devcompanion-launch/demo.txt)
- [First-session feedback](https://github.com/ashuujha/devcompanion-launch/issues/new/choose)

## Start with a real project

Verify and install the [Linux archive](https://github.com/ashuujha/devcompanion-launch/releases/download/v0.4.0/devcompanion-0.4.0-linux-x86_64.tar.gz)
using the guide. Ollama and a downloaded local model are needed for conversation
and proposed corrections; presence, reminders and incident recording do not
call the model. In an existing Git repository:

```sh
dot init --goal "Finish the current bug fix"
dot presence install       # once per Linux user account
dot presence enable        # only this initialized project
dot shell                  # opt-in Bash session; captures commands typed here
```

`dot` opens the work desk and conversation. `dot desk` shows open incidents,
reminders and recent activity without starting a chat. Start `dot shell` only
for terminal work you want recorded. It leaves ordinary terminal commands under
your control; it does not run suggested commands. `dot presence disable` stops
background observation for this project; `dot presence uninstall` removes the
login service. Both require your explicit action.

For VS Code, download the optional
[diagnostics extension](https://github.com/ashuujha/devcompanion-launch/releases/download/v0.4.0/dot-developer-companion-0.1.0.vsix),
install it with `code --install-extension dot-developer-companion-0.1.0.vsix`,
trust the workspace and run **Dot: Enable Editor Diagnostics for Workspace**.
The editor must be open to supply diagnostics. The extension sends bounded
messages, file paths and line numbers for the enabled Git project, not source
buffers. Disable it from the command palette when you want it to stop.

## Follow a problem

- `dot desk` or `/incidents` shows the evidence. `/incident ID` shows a specific
  error, its original location and later status.
- `/fix ID` asks the downloaded local model to prepare a small correction. Read
  the task report and diff with `/review ID`; `/apply ID` is a separate approval.
- Register and run a relevant named check explicitly, for example
  `dot check add tests -- npm test` and `dot verify tests`. A successful check
  for the current code is distinct from an editor diagnostic disappearing or an
  old passing result. A correction itself does not prove recovery.
- `/remind 20m Check the migration`, `dot remind snooze ID --in 10m`, and
  `dot remind done ID` keep small commitments visible. `/focus 25` schedules
  one break reminder; `/quiet 30` pauses desktop interruptions.

Optional English voice is an explicit turn, not continuous listening:
`dot voice setup` installs local Whisper and Piper components once, then
`/voice` or `dot voice ask` records when requested and speaks a short answer.
The generated-audio transcription and synthesis path has been tested; microphone,
playback and listening comfort still need hands-on validation.

## Evidence and limits

The v0.4 workflow has exercised real PTY capture, opted-in editor diagnostics,
a login user service and a desktop reminder with chat closed. In the
[recorded v0.4 fixture](https://ashuujha.github.io/devcompanion-launch/demo.txt),
a real failed Python test became an incident; a downloaded local model proposed
a small correction, the maker reviewed and applied it, and the unchanged named
check passed on current code. A returning voice turn used that saved evidence.
This is one scripted fixture, not a general coding quality or adoption benchmark.
The v0.4 evaluation used local engines but was not network-isolated.

The login service does not make model calls, run checks, capture the screen or
listen to the microphone. Shell observation is limited to an explicit `dot shell`
session; output and entered commands can contain secrets. VS Code diagnostics
may be stale until the editor updates them. Local models can make mistakes;
review diffs and run the checks that matter. Initial runtime, model, extension
and voice downloads need internet. Ordinary inference stays local, with no silent
cloud fallback or application telemetry. Your own checks may use the network.

The archive contains a static CLI, MIT application license, dependency notices
and quickstart. It contains no application source, model weights or private logs.
