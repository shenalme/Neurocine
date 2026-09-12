# Hosting this folder

Everything here is already built. There is nothing to install, compile or run.
Just put these files on any static host that serves over **HTTPS** — the webcam
will not work over plain HTTP.

The build uses relative asset paths, so the same folder works at a domain root
(`https://something.pages.dev/`) or in a sub-folder
(`https://you.github.io/my-study/`) without any changes.

---

## Option A — Cloudflare Pages (fastest, no Git)

1. Zip this folder's **contents** (or keep the zip you were given).
2. Sign in at <https://dash.cloudflare.com> — the free plan is enough.
3. **Workers & Pages → Create → Pages → Upload assets**.
4. Name the project, drag in the zip or folder, and deploy.
5. You get `https://<project>.pages.dev` with HTTPS already set up.

To update later, open the project and create a new deployment with a new upload.

## Option B — GitHub Pages (no build step needed)

1. Create a new repository on GitHub, ticking "Add a README file".
2. **Add file → Upload files**, then drag in everything from this folder —
   `index.html`, `assets/`, `mediapipe/`, `videos/`, `.nojekyll`.
   Commit.
3. **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
   branch `main`, folder `/ (root)`. Save.
4. After a minute or two the site is at
   `https://USERNAME.github.io/REPOSITORY/`.

Keep `.nojekyll` — without it GitHub's Jekyll step can drop files.

## Option C — Netlify

Sign in, then drag this folder onto the Sites list (or use **Add new site →
Deploy manually**). You get an HTTPS URL immediately.

---

## Changing the video

`videos/test-video.mp4` is the placeholder stimulus. To swap it without
rebuilding, replace that file with your own MP4 using **exactly the same
filename**, then redeploy. Use H.264 in MP4 for the widest browser support.

To change the filename, the calibration timings, the pass mark or anything else
in `src/config.ts`, you need the source project and a rebuild.

## Checking it works

Open the URL, allow camera access, and run through calibration. The placeholder
video is a moving dot with a burned-in clock, so after the run you can open the
downloaded CSV and confirm `gazeX`/`gazeY` roughly follow the dot at the
matching `videoTime`.

First load pulls about 18 MB of model and wasm files, so the camera screen can
sit on "Starting the camera" for a few seconds the first time. It is cached
afterwards.
