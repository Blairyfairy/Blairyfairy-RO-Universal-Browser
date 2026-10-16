# Blairyfairy Ragnarok Online Universal Browser Gateway

**By Blair Page (Blairyfairy)** · https://blairyfairy.github.io/BlairPage/

## What this is

A branded GitHub Pages gateway designed to deploy the **real open-source roBrowserLegacy Ragnarok Online client**, offer a server connection profile generator, and document a secure WebSocket-to-TCP bridge. This is **not** an original Ragnarok clone and is **not** an official Gravity client.

## What it is not

This is **not** a universal one-click client for arbitrary private servers. An RO server must be compatible with the selected roBrowser version, packet version and game assets, and an authorized WebSocket bridge must be available. GitHub Pages cannot host the TCP server or proxy. No game server, game files, player accounts or game credentials are bundled. The real upstream client is fetched at GitHub Actions build time; this ZIP does not itself include compiled roBrowser.

## Publish

1. Create a repository, e.g. `Blairyfairy-RO-Universal-Browser`.
2. Upload this package's contents to the root of `main`.
3. Under **Settings → Pages**, choose **GitHub Actions**.
4. Run the `Build roBrowser and publish Pages` workflow and inspect its logs.
5. Open `https://blairyfairy.github.io/Blairyfairy-RO-Universal-Browser/` after deployment.
6. Enter the server operator's approved host, port, packet version, WSS proxy and HTTPS asset service in the form.
7. Download `Config.local.js`; review and adapt it to the upstream `Config.local.js.example`, then put it in `server-config/Config.local.js` and redeploy.
8. Use the published client entrypoint. If upstream's `dist/Web/` does not place a root `index.html`, adjust the launcher path to the built demo/app entrypoint shown in the workflow logs.

**Note:** The config form only generates a deployable config and tests a WSS handshake. It does not dynamically reconfigure roBrowser at runtime, verify gameplay, or accept account passwords.

## Technical docs

- [Setup](docs/setup.html)
- [Homunculus](docs/homunculus.html)
- [roBrowserLegacy upstream](https://github.com/MrAntares/roBrowserLegacy)
- [wsProxy upstream](https://github.com/MrAntares/roBrowserLegacy-wsProxy)
- [rAthena](https://github.com/rathena/rathena)

## Security

Never collect player passwords on the portal or store them in GitHub. Restrict bridge targets to known approved host:port pairs, protect proxy against abuse, terminate TLS to serve WSS, and never commit proprietary game assets without redistribution rights.

## Credits and rights

Portal design, integration workflow, and documentation: **Blair Page / Blairyfairy**. roBrowserLegacy, rAthena and proxy implementations are separate upstream projects with their own licenses and authors. Ragnarok Online trademarks and original game assets belong to their respective rights holders. This project is unaffiliated with Gravity.
