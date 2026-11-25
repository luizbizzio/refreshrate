# Contributing to Refresh Rate Test

Serve the repository with `python -m http.server 8000` and open `http://localhost:8000`. The measurement and animation live in [`index.html`](index.html).

## Review a change

- Compare the displayed result against a known display refresh setting. Test at least two refresh rates when available and distinguish the display setting from the browser's measured frame rate in your report.
- Verify that the ghost count and animation match the displayed result. Try leaving the tab in the background and returning, and moving the window between displays if you have a mixed-refresh setup.
- If you change [`sw.js`](sw.js) or the manifest, test a fresh visit and an update from an existing cache.

Include the browser, OS, refresh setting, displayed result, and any frame-rate limit relevant to the test.
