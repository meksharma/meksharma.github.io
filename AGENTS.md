# Portfolio maintenance

Read [README.md](README.md) for the architecture, file map, approved behavior,
validation, publishing, CV warning and access handoff.

- Canonical live source: `meksharma/meksharma.github.io`, branch `master`.
  The separate showcase repository's `main` branch does not publish the root URL.
  Inspect the current remote before changing or pushing anything.
- No npm build or private backend is needed. Preview with a static HTTP server.
- Keep normal vertical scrolling, desktop-only specialties, independent icon
  animations and reduced-motion behavior. Do not reintroduce section snapping.
- Use the existing SF font stack and typography tokens.
- Change CV HTML and PDF together; do not certify the flagged PDF as virus-free.
- Run the README validation commands and browser checks for affected behavior.
- Commit intended runtime assets, not unrelated source exports or private files.
- Never store GitHub credentials in the repository. Public source access does
  not authorize pushes; the owner or authorized collaborator must authenticate.
- Publishing is complete only after successful Pages deployment and live checks.
