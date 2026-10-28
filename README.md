# Mehak Sharma's Portfolio

**Live portfolio: https://meksharma.github.io/**

## Source of truth and publishing

The final site is published from the public repository
**https://github.com/meksharma/meksharma.github.io**, branch **`master`**, folder
**`/`**, using GitHub Pages' branch-based deployment.

The older repository, `meksharma/mehaks-portfolio-showcase-2026` (`main`), is a
separate showcase copy. Pushing there does **not** update the final root URL.
Use the canonical repository above for future work.

This is a static HTML/CSS/JavaScript site. There is no package installation,
application build, private API key, or chat-session dependency needed to run it.
The WebGL device demos require internet access to pinned Three.js 0.180.0 modules
on jsDelivr/esm.sh and the Draco decoder on jsDelivr.

## Continue with another AI or developer

Give your assistant this repository URL and ask it to read this README and
[AGENTS.md](AGENTS.md). Anyone can read or clone the public source:

```sh
git clone https://github.com/meksharma/meksharma.github.io.git
cd meksharma.github.io
git switch master
```

Editing and publishing require your own GitHub login with write permission.
Authenticate locally with `gh auth login` or your Git client; never paste tokens,
passwords, recovery codes, or session credentials into chat or source files.
If someone else maintains the site, invite their GitHub account as a collaborator
through repository Settings, or have them open a pull request from a fork.
Public visibility does not grant publishing access.

Retain access to the personal `meksharma` GitHub account, its recovery email, and
two-factor recovery methods. Losing access to this AI account does not remove
GitHub access. A source backup can be restored elsewhere, but cannot confer
ownership of the `meksharma.github.io` address.

## Local preview

Serve the repository over HTTP; opening HTML as `file://` can break ES modules:

```sh
python3 -m http.server 8080 --bind 127.0.0.1
```

Open http://127.0.0.1:8080/ in your browser. Node.js 22 is used in CI for validation.
Python is only an optional local static server.

## File map

| File | Purpose |
|------|---------|
| [index.html](index.html) | Main content, navigation, case studies, media and cache keys |
| [styles.css](styles.css) | Responsive layout, typography, reveals and specialties icons |
| [script.js](script.js) | Navigation, reveals, builds reel, media controls, image viewer |
| [chat.js](chat.js) / [chat.css](chat.css) | Local scripted assistant; no AI backend or credentials |
| [cv.html](cv.html) / [Mehak-Sharma-CV.pdf](Mehak-Sharma-CV.pdf) | Editable CV and downloadable one-page PDF |
| [404.html](404.html) | Missing-page screen |
| [portfolio-share.html](portfolio-share.html) | Legacy standalone share page; not the main site |
| `*-3d.js`, [phone-3d.js](phone-3d.js) | Three.js device presentations |
| [Demos/](Demos/) and root images/videos/models | Committed runtime media |
| [THIRD_PARTY_NOTICES.txt](THIRD_PARTY_NOTICES.txt) | Model license attribution; preserve it |
| [scripts/check-assets.js](scripts/check-assets.js) | Local asset references in all four HTML pages |
| [.github/workflows/site-integrity.yml](.github/workflows/site-integrity.yml) | Asset validation on pushes and pull requests |

## Approved behavior and content

- Order: hero, introduction with desktop specialties, Experiments, How I work,
  case studies, contact.
- Specialties appear beside the introduction only at desktop widths (1024px+),
  vertically centered with an asymmetric gap. Hide them on mobile.
- Icons use independent finite animations and respect reduced-motion preferences.
- Keep normal vertical scrolling. Do not restore vertical CSS scroll snapping or
  listeners that change snap targets: they previously caused section jumping.
- The horizontal builds reel and smooth navigation links are intentional.
- Main heading: "Experimenting with AI"; navigation label: "Experiments".
- Project 2's complete Teams Search hero is `Hero Image 23.png`.
  `Hero Image 22.png` was a gradient-only source export, not the hero.
- The assistant says Mehak is open to design leadership opportunities and can
  start following a one-month notice period. Do not add employment details.
- Microsoft CV role: Lead Product Designer, Suzhou. This work location is distinct
  from the personal location shown in the contact section.
- Favicon: purple M, using `favicon.png` and `apple-touch-icon.png`.
  Keep repository-relative icon paths.

## Validate and publish

```sh
node scripts/check-assets.js
for file in *.js scripts/*.js; do node --check "$file" || exit 1; done
git diff --check
```

Preview desktop and mobile layouts, reduced motion, navigation/menu, scrolling,
chat availability answers, images, videos, WebGL demos, favicon and CV download.
New runtime assets must be committed, including media loaded inside JavaScript.
Do not add unused source exports, private files, credentials or design dumps.
Update HTML query-string cache keys when changing referenced CSS, JS or an image.

Before publishing, check `git remote -v` and `git status`. In the **canonical**
repository, commit the intended files and push `master`:

```sh
git pull --ff-only origin master
git add -- path/to/changed-file
git commit -m "Describe the portfolio change"
git push origin master
gh run list --repo meksharma/meksharma.github.io --branch master --limit 5
```

Confirm both **Site integrity** and **pages build and deployment** succeed for the
new commit. Then verify https://meksharma.github.io/ serves the changed content
and asset versions. A local preview or a commit alone is not a published change.

## CV PDF maintenance and warning

Update the HTML and downloadable PDF together. Export `cv.html` with Chrome's
Print > Save as PDF (A4, background graphics, no headers/footers), or use Chrome's
headless `--print-to-pdf` with `--no-pdf-header-footer`. Confirm it remains one page,
has the expected text and working canonical portfolio link before committing.

**Outstanding warning:** an email provider flagged the October 16, 2026 PDF as a
virus. Local structural inspection found no JavaScript, embedded files or launch
actions, but no antivirus clearance was established. Do not claim it is
malware-free, bypass email warnings, or upload personal CV data to external
scanners without the owner's permission. The [online CV](https://meksharma.github.io/cv.html)
is an alternative while the attachment warning is investigated.

## Portable backup

Create a source-and-assets backup from the committed canonical repository:

```sh
git archive --format=zip --output=../mehak-portfolio-source.zip HEAD
```

The archive needs no chat history or local session folder. It excludes Git
history; clone the repository or use `git clone --mirror` if history is needed.
