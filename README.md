# JWT Decoder

A client-only JWT decoder. Paste a JWT, see its header and payload. No server-side decoding, no analytics, no token transmission.

Live: <https://crusher-labs.github.io/jwt-decoder/>

## Privacy

This tool is intentionally **client-only**. The token you paste never leaves your browser.

- The tool's own code (`index.html`) decodes the JWT in JavaScript using `atob()` and `JSON.parse()`. Verified with `grep`: no `fetch`, no `XMLHttpRequest`, no `navigator.sendBeacon`, no `WebSocket`, no `crypto.subtle` calls touch the token.
- The page does load three sets of external resources via CDN: Google Fonts (Inter), and the `crusher-ui-kit@0.1.6` static assets from jsDelivr. **None of these calls carry the user-pasted token.** They are fired at page load, before any input, and the resource URLs are static.
- The framework code (`crusher-ui-kit@0.1.6`) is loaded as `crusher-ui.standalone.esm.js`. It manages the theme/mode switcher and persists *only* the user's UI preferences to `localStorage.crusher_prefs` (schema `{ mode, brand, v:1 }`). It does not read the token or make any token-related network call.
- The tool does **not** persist the token anywhere. After you close the tab, nothing remains.

If you want maximum assurance, take the page offline (`File → Save As`) and open the saved copy. The decoder still works without an internet connection once the page is cached.

## What it does

- Splits a JWT on `.` into header / payload / signature parts.
- Base64url-decodes the header and payload parts.
- JSON-parses each and pretty-prints them.
- Does **not** verify the signature. Use a dedicated server-side library for verification — JWT signature verification on the client is not meaningfully more trustworthy than the token itself.

## Framework / hosting

- Static HTML/CSS/JS deployed via GitHub Pages from this repo's `main` branch.
- UI chrome is the published `crusher-ui-kit@0.1.6` static contract. See the workspace `CLAUDE.md` for the contract details.

## Development

- Open `index.html` directly in a browser. No build, no dependencies.
- Or serve the parent workspace via the hub's preview server: `cd ../../tools-hub && npm run preview` then visit `http://127.0.0.1:8723/utility-tools/jwt-decoder/`.

## License

MIT.
