# Copilot Instructions

## Repository shape

- This is a static study-group website and document repository, not a compiled application.
- `README.md` is the source of truth for the meeting schedule, presenters, topics, and reference links.
- `index.html` is a self-contained GitHub Pages notes page. Its CSS, diagrams, and JavaScript are kept in the same file; preserve that structure when editing the page.
- `pdf/` contains presentation/reference PDFs. Add new materials there and link them from the relevant `README.md` schedule row.
- `.github/workflows/keep_alive.yml` periodically commits a generated timestamp to `heartbeat.txt`; do not treat that file as hand-maintained content.

## Making changes

- Schedule edits are table-row changes in `README.md`. Preserve the existing columns and link style, and keep topic names, presenter names, dates, and PDF filenames aligned.
- Use repository-relative PDF links where practical. Existing historical rows may use absolute GitHub links, so do not rewrite unrelated rows.
- For `index.html`, follow the existing inline design system: CSS custom properties in `:root`, the Noto Sans TC and IBM Plex Mono fonts, responsive media queries, and the existing interactive diagram patterns.
- Keep user-facing content compatible with the page's current Traditional Chinese presentation unless the requested topic specifies another language.
- Do not add a framework, package manager, or build step for a content-only change.

## Validation and workflows

- There is no project-specific build, test, or lint command. For HTML changes, open `index.html` directly or serve the repository with a simple static server and check the page and interactive controls in a browser.
- For schedule/PDF changes, verify the Markdown table renders correctly and every newly added local PDF link points to an existing file.
- GitHub Actions are operational rather than application builds: `meeting_reminder.yml` sends the weekly Discord reminder using `DISCORD_WEBHOOK_URL`, while `keep_alive.yml` commits and pushes `heartbeat.txt` on its monthly schedule.
- Keep commits focused. Check `git status` before and after edits, and avoid modifying the generated heartbeat unless the workflow is the intended change.