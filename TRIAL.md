# Try one useful work session

This free Linux x86_64 preview needs Git. A downloaded local model is needed
only for explanations and corrections. The application source is private.

1. Install the [verified archive](https://github.com/ashuujha/devcompanion-launch/releases/tag/v0.5.0)
   using the [guide](https://ashuujha.github.io/devcompanion-launch/guide.html).
2. In your own existing Git project, run:

   ```sh
   dot setup --check
   dot setup --yes --presence --proactive --goal "Your actual task"
   dot trial start
   dot shell
   ```

3. Work normally inside this explicitly observed shell. Use one real test/build
   failure if it occurs. Type `exit` to leave. This shell and the optional
   editor adapter are the sources of errors; ordinary terminals aren't watched.
4. Check `dot desk` and `dot proactive list`. A new failure may receive an
   explanation even with no chat open. Use `dot proactive show ID` to inspect
   the observation, hypothesis and evidence. A relevant source change makes
   earlier explanations historical. No automatic commands or code edits run.
5. Rate what you actually observed:

   ```sh
   dot trial rate INCIDENT_ID helpful
   # Or: incorrect / noisy
   dot proactive rate INSIGHT_ID useful
   # Or: noisy / missed
   dot trial missed --note "Short private description"
   dot trial finish helped
   # Or: blocked / neutral
   dot trial report --json
   ```

   Replace IDs with those printed by your session. Record a missed problem only
   if one occurred. The final report contains aggregate counts, not code, paths,
   identity, command output or private notes. Nothing uploads automatically.

Share one useful moment, one blocker, unnecessary interruptions and whether you
would return through [first-session feedback](https://github.com/ashuujha/devcompanion-launch/issues/new/choose).
You can optionally paste the aggregate report after reviewing it. Never paste a
private database or project export into a public issue.

For reminders without a model, omit `--proactive` from setup and use
`dot remind add --in 20m "Your reminder"`. `dot quiet 30` pauses interruptions;
`dot proactive disable` stops investigation; `dot presence disable` disables
this project. The guide explains the remaining controls and limits.

We are seeking the first ten independent developer trials. Scripted maker
fixtures and download counts are not users or adoption evidence.
