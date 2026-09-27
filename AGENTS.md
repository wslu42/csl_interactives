# AGENTS.md

## Project

CSL Interactives is a static web portal for small Chinese-learning interactive activities.
The root page is the portal. Each activity lives in its own first-level subdirectory.

## Structure

- `index.html` is the portal landing page.
- `games/<activity-name>/` contains one self-contained activity.
- `assets/` contains portal-wide styles and visual assets.
- Activity-only audio, images, CSS, and JavaScript stay inside that activity's directory.
- Use relative paths so the site works on static hosting such as GitHub Pages.

## Development principles

- Keep the site dependency-free: use plain HTML, CSS, and JavaScript unless explicitly requested otherwise.
- Make layouts responsive and touch-friendly.
- Preserve Traditional Chinese (`zh-Hant`) as the default UI language.
- Use accessible semantic HTML, visible focus states, meaningful button labels, and `aria-live` for changing game results where appropriate.
- Respect `prefers-reduced-motion`; animation must not be required to use an activity.
- Do not use external CDNs or trackers without explicit approval.

## Adding an activity

1. Create `games/<activity-name>/`.
2. Include an `index.html` and activity-local assets as needed.
3. Add a tile to the root portal page.
4. Include a clear "返回入口" link in the activity.
5. Verify all asset paths from the repository root and static hosting.

## Audio and media

- Keep media files close to the activity that uses them.
- Use descriptive, lowercase, hyphenated filenames.
- Provide a browser-native fallback when prerecorded audio cannot load.

## Git handling

- Inspect `git status` before making changes and preserve unrelated user changes.
- Do not use destructive commands such as `git reset --hard`, `git clean`, or force pushes unless explicitly requested.
- Keep each commit focused on one logical change.
- Use clear imperative commit messages, for example: `Create portal landing page`.
- Do not commit generated temporary files, local editor settings, test artifacts, or secrets.
- Do not change Git configuration, remotes, branches, or deployment settings unless explicitly requested.
- Before committing, review the diff and verify affected navigation, assets, and interactions.

## Branch naming

- Use lowercase, hyphenated branch names in the format `<type>/<short-description>`.
- Allowed types: `feat/` (new functionality), `fix/` (bug fixes), and `chore/` (documentation, maintenance, and repository structure).
- Examples: `feat/portal-landing-page`, `fix/audio-paths`, `chore/project-guidelines`.
- Do not use vague branch names such as `update`, `test`, or `new-branch`.

## Collaboration

- Treat user requests as the source of product intent; ask for clarification only when a decision would materially change scope, design, or behavior.
- State important assumptions before implementing them.
- Share a concise plan before multi-file, structural, or user-visible changes.
- Respond to users in Traditional Chinese as used in Taiwan by default.
- Accept user requests, code comments, and engineering discussion in either Traditional Chinese or English.
- Report what changed, how it was verified, and any known limitations when work is complete.
- Preserve user-authored work and unrelated changes.
- Create a focused Git commit after completing a verified logical change, unless the user asks not to commit.
- Do not create pull requests, deploy, change remotes, push changes, or make external communications unless explicitly requested.
- When multiple agents work in parallel, assign clear file ownership and avoid overlapping edits.
- Record decisions that affect future work in `README.md` or another project document when requested.

## Verification

- Test portal navigation to every activity and its return link.
- Test narrow mobile and desktop viewport widths.
- Confirm there are no browser-console errors or missing assets.
- Confirm keyboard navigation works for interactive controls.
