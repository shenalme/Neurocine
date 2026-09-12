# Hosting this folder

Everything here is already built. There is nothing to install or compile. Put
these files on any static host that serves over **HTTPS** — the webcam will not
work over plain HTTP.

Relative asset paths are used throughout, so the same folder works at a domain
root (`https://something.pages.dev/`) or in a sub-folder
(`https://you.github.io/my-study/`) with no changes.

## GitHub Pages

1. Create a **public** repository (Pages on private repos needs a paid plan).
2. **Add file → Upload files**, drag in `index.html` and the `assets`,
   `mediapipe` and `videos` folders. Commit.
3. **Settings → Pages → Source: Deploy from a branch**, branch `main`,
   folder `/ (root)`. Save.
4. After a minute the site is at `https://USERNAME.github.io/REPOSITORY/`.

## Cloudflare Pages

**Workers & Pages → Create → Pages → Upload assets**, name the project, drag in
this folder or its zip, deploy. Served at `https://<project>.pages.dev`.

## Netlify

Drag this folder onto the Sites list, or **Add new site → Deploy manually**.

## Changing the video

Replace `videos/test-video.mp4` with your own MP4 using the same filename, then
redeploy. Changing the filename or any setting in `src/config.ts` needs the
source project and a rebuild.

## First load

About 18 MB of model and wasm files download the first time, so the camera
screen can sit on "Starting the camera" for a few seconds. It is cached after
that.
