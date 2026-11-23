# ArcScribe

A free, offline-first note-taking app for tablets with pencil support. It runs in the browser and installs to the home screen as an app (PWA). There is no build step: the files in this folder are the app.

## Run it on your computer

Any static file server works, for example:

```
python3 -m http.server 8000
```

Then open http://localhost:8000. (Opening `index.html` directly with `file://` will not work for PDF import, OCR or offline mode.)

## Deploy to GitHub Pages

1. Put all the files from this folder in the repository (including the `tess` folder and the `.nojekyll` file).
2. On GitHub, open **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**, choose branch **main** and folder **/ (root)**, then click **Save**.
4. After a minute or two, the app is at `https://<your-username>.github.io/<repository-name>/`.

## Updating the app

- Change the files and push to `main`. GitHub republishes automatically within a minute or two.
- Increase `RELEASE` at the top of `sw.js` with every update. Installed copies then show **"A new version of ArcScribe is ready — Update now"** and keep all notes.

## Install on a tablet

Open the site in Safari (iPad) or Chrome (Android), then **Share → Add to Home Screen** (or **Install app**).

## Where notes are stored

- Notes live in the browser's IndexedDB on each device. Nothing is uploaded anywhere.
- Use **⋯ → Back up all notebooks** regularly and keep the file safe. **Restore from backup** adds those notebooks back.
- When the data format changes, ArcScribe upgrades it automatically and keeps a copy of the previous data (`db-before-v3`) in IndexedDB.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app (HTML, CSS and JavaScript) |
| `sw.js` | Offline cache and update check |
| `manifest.webmanifest`, `icon-*.png` | Install details and icons |
| `pdf.min.js`, `pdf.worker.min.js` | PDF.js 3.11 for importing PDFs |
| `jspdf.umd.min.js` | jsPDF 2.5 for exporting notes as PDF |
| `tess/` | Tesseract.js 5 and English data for OCR |

## Features that need outside services (later phase)

AI chat, AI summaries and AI-generated quizzes need an AI service (for example a free Google Gemini API key). Cloud sync and sharing need a backend (for example Firebase). Everything else works offline for free.
