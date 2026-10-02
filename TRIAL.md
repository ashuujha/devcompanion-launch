# Try one useful work session

This free Linux x86_64 preview needs Git. A downloaded local model is needed
only for explanations and corrections. The application source is private.

1. Install the [verified v0.7 archive](https://github.com/ashuujha/devcompanion-launch/releases/tag/v0.7.0)
   using the [guide](https://ashuujha.github.io/devcompanion-launch/guide.html).
   Existing installations can use `dot update`. For the optional desktop, check
   GTK readiness with `dot desktop check`.
2. In your own existing Git project, run:

   ```sh
   dot setup --check
   dot setup --yes --presence --proactive --goal "Your actual task"
   dot trial start
   dot desktop
   ```

3. Give it one actual, bounded project task. Close the panel while work runs,
   then open the dot and work desk. Inspect the report, recorded source ranges
   and diff. Approve a patch only after review; register and run a relevant
   named check separately. For an explanation without changes, say
   "Analysis only, no code changes." Return later and inspect recorded outcomes.
4. To feed actual terminal errors, run `dot shell` in another terminal in the
   same project and work inside that explicitly captured session. Type `exit`
   to leave. The optional editor adapter is another source of errors; ordinary
   terminals and arbitrary screens aren't watched. A new failure may receive
   an explanation even with no chat open. Inspect it in the work desk or with
   `dot proactive list` / `dot proactive show ID`. A relevant source change
   makes earlier explanations historical. No automatic commands or edits run.
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

Share one useful moment, one blocker, unnecessary interruptions, whether the
project goal and inspected evidence matched your task, and whether you
would return through [first-session feedback](https://github.com/ashuujha/devcompanion-launch/issues/new/choose).
You can optionally paste the aggregate report after reviewing it. Never paste a
private database or project export into a public issue.

For reminders without a model, omit `--proactive` from setup and use
`dot remind add --in 20m "Your reminder"`. `dot quiet 30` pauses interruptions;
`dot proactive disable` stops investigation; `dot presence disable` disables
this project. The guide explains the remaining controls and limits.

The desktop's Speak a goal button uses local speech recognition and puts the
recognized text in the composer for review. Click again for a follow-up; Esc
cancels recording. CLI voice also supports a persistent or continuous session.
Physical microphone comfort and larger-project model accuracy remain unproven.
`dot desktop install --login` optionally adds quiet graphical login presence;
`dot desktop uninstall` removes our entries and keeps project data.

We are seeking the first ten independent developer trials. Scripted maker
fixtures and download counts are not users or adoption evidence.
