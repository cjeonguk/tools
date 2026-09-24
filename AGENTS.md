# Agent Instructions

## Purpose

This is a static collection of small browser tools. The primary deliverable is a
focused, independently usable HTML page, not an application framework.

Read `README.md` and inspect related existing tools before making changes. Reuse
an established pattern when it fits; otherwise prefer the smallest clear
implementation.

## Repository rules

- Put each browser tool in the repository root as `{kebab-case-name}.html`.
- Keep each tool self-contained: inline its CSS and JavaScript so it can be
  copied, served, or hosted alone.
- Do not introduce React, a build step, a package manager, generated bundles, or
  a shared application runtime for a single tool.
- Update the `Tool catalog` in `index.html` whenever adding, renaming, or
  removing a tool.
- Give every tool a descriptive `<title>`, a visible `<h1>`, and a link back to
  `index.html`.
- Use relative URLs for repository pages so tools work at the GitHub Pages
  project path (`/tools/`) and on local servers.

## Implementation guidance

- Use semantic HTML, explicit `<label>` elements, native controls, and visible
  `:focus-visible` styles.
- Make layouts usable on narrow screens without horizontal scrolling.
- Describe loading, success, and error states in the UI. Use an appropriate live
  region when a result changes asynchronously.
- Prefer browser APIs for clipboard access, local file processing, downloads,
  URL state, and persistent local state.
- Store only non-sensitive, local user state in `localStorage`. Never put API
  keys, tokens, or credentials in source code, commits, or shareable URLs.
- Make network requests only for functionality the user has requested. Explain
  external API limitations and handle CORS or fetch failures clearly.
- Treat all user-provided text, HTML, URLs, files, and API responses as untrusted.
  Do not inject untrusted strings with `innerHTML`; use DOM APIs or text content.
- Use a CDN only when a well-known library materially reduces complexity. Pin the
  exact version and keep the dependency count low.
- Do not add analytics, trackers, or implicit third-party requests.

## Catalog cards

Add future cards as ordinary HTML in `index.html`, inside the `#tool-catalog`
element. Each card should contain:

- A link to the tool.
- A concise one-sentence description.
- Optional plain-text capability tags.

Do not add placeholder cards, a generator, or a metadata format until the
collection has a concrete need for one.

## Verification

Before considering a change complete:

1. Serve the repository with `python3 -m http.server 8000`.
2. When available, use `playwright-cli` against `http://localhost:8000/`, not `file://`.
3. Check the primary workflow plus empty and invalid-input paths where relevant.
4. Inspect the browser console and requests for errors or unexpected requests.
5. Check a desktop viewport and a narrow mobile viewport for overflow, clipping,
   layout breaks, and keyboard access.
6. Use reduced-motion emulation when adding motion.
7. If GitHub Pages is configured, verify the deployed project URL as well.

Do not commit screenshots, recordings, local browser profiles, or other
verification artifacts unless they are explicitly requested.
