# FoxFlash Catalog

A static React app showing FoxFlash's ECU coverage (6,128 entries) with
editable, service-based pricing by primary reading method (OBD / Bench /
Boot-JTAG / BDM).

## Deploy to GitHub Pages

1. Create a new repo on GitHub and push everything in this folder to it
   (keep the `docs/` folder as-is — it's already built and ready to serve).
2. In the repo, go to **Settings → Pages**.
3. Under "Build and deployment", set **Source** to "Deploy from a branch",
   choose your default branch (e.g. `main`) and the **`/docs`** folder, then
   save.
4. GitHub will give you a URL like `https://<username>.github.io/<repo>/`
   within a minute or two — that's your live app.

## Making changes later

The site is a static bundle (`docs/bundle.js` + `docs/index.html`) — you
don't need Node.js installed just to host it. But if you want to edit the
app itself:

- Source lives in `src/App.jsx` (the whole app) and `src/index.jsx` (just
  mounts it to the page).
- Install dependencies once: `npm install`
- Rebuild after any edit: `npm run build`
- Commit and push the updated `docs/bundle.js`.

## Notes on the data

ECU coverage data was parsed from FoxFlash's published PDF list. A few
hundred entries list OBD as a connection option but only support
Write/Verify, not a full Read — those are flagged with `OBD*` in the app
and automatically price/badge using the next best method (Bench, then
Boot/JTAG, then BDM). You can manually correct the primary method on any
row using the dropdown badge on the left.
