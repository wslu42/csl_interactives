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
5. Update the portal's activity count and the activity list in `README.md`.
6. Keep the imported game's intended rules and content; document browser limitations honestly in the activity and README. Do not advertise unsupported input modes as working.
7. Verify all asset paths from the repository root and static hosting, including the GitHub Pages repository subpath. The return link is normally `../../`.
8. Before delivery, test the new tile, every existing activity link, the new activity's return link, mobile and desktop layouts, keyboard controls, game start/input/results/replay, and console errors or missing assets. Record any checks that could not be completed.
9. Review the exact diff, create a focused commit, push only the task branch, and submit a pull request targeting `main`, following the workflow below. Report the PR URL, validation, and known limitations; do not merge or deploy unless explicitly requested.

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
- Do not change Git configuration, remotes, or deployment settings unless explicitly requested. Create a task branch as part of the commit/PR workflow; do not rewrite existing branches.
- Before committing, review the diff and verify affected navigation, assets, and interactions.

## Branch naming

- Use lowercase, hyphenated branch names in the format `<type>/<short-description>`.
- Allowed types: `feat/` (new functionality), `fix/` (bug fixes), and `chore/` (documentation, maintenance, and repository structure).
- Examples: `feat/portal-landing-page`, `fix/audio-paths`, `chore/project-guidelines`.
- Do not use vague branch names such as `update`, `test`, or `new-branch`.

## Pull request workflow

- By default, complete requested repository changes with a focused commit, push the task branch, and submit a pull request after verification. Respect explicit instructions such as no commit, local-only, or no PR. Never push directly to `main`, merge a pull request, or deploy unless explicitly requested.
- By default, create every pull request from a branch based on the latest `origin/main`, with `main` as its base branch.
- Do not create a pull request whose base is another feature, fix, chore, or open pull-request branch unless the user explicitly asks for a stacked PR.
- Before creating a pull request, fetch `origin`, verify the intended base and head branches, and review the exact diff against the intended base.
- When a preceding pull request is merged, update any follow-up branch from the new `origin/main` before opening its pull request; do not merge follow-up work into a stale former base branch.
- After creating a pull request, verify its URL, base branch, head branch, and mergeability through GitHub.
- State the intended merge order when the user explicitly requests stacked pull requests.

## Collaboration

- Treat user requests as the source of product intent; ask for clarification only when a decision would materially change scope, design, or behavior.
- State important assumptions before implementing them.
- Share a concise plan before multi-file, structural, or user-visible changes.
- Respond to users in Traditional Chinese as used in Taiwan by default.
- Accept user requests, code comments, and engineering discussion in either Traditional Chinese or English.
- Report what changed, how it was verified, and any known limitations when work is complete.
- Preserve user-authored work and unrelated changes.
- Create a focused Git commit after completing a verified logical change, unless the user asks not to commit.
- Follow the default commit/push-task-branch/PR workflow above. Deployments, merges, remote changes, and other external communications still require an explicit user request.
- When multiple agents work in parallel, assign clear file ownership and avoid overlapping edits.
- Record decisions that affect future work in `README.md` or another project document when requested.

## Verification

- Test portal navigation to every activity and its return link.
- Test narrow mobile and desktop viewport widths.
- Confirm there are no browser-console errors or missing assets.
- Confirm keyboard navigation works for interactive controls.
