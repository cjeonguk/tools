# Tools

A collection of small, useful tools that run entirely in the browser.

This repository follows the single-file HTML tool approach described in Simon
Willison's [Useful patterns for building HTML tools](https://simonwillison.net/2025/Dec/10/html-tools/).
Each tool is deliberately easy to read, copy, host, and change.

The intended public address for the collection is `https://tools.cjeong.uk/`.
GitHub Pages currently deploys the site until that custom domain is configured.

## Principles

- One focused tool per self-contained HTML file.
- Inline CSS and JavaScript. No required build step, framework, or package
  manager.
- Prefer browser-local processing for files, clipboard data, and transformations.
- Use URL parameters or fragments for small, shareable state.
- Use `localStorage` for larger local state or user-provided API keys. Never put
  secrets in source code or URLs.
- Add CDN dependencies only when they substantially help, and pin their versions.

## Repository layout

```text
.
├── AGENTS.md       # Instructions for coding agents
├── index.html      # Tool collection homepage
├── {tool-name}.html
├── README.md
└── LICENSE
```

Tool files use lowercase `kebab-case` names at the repository root, for example
`json-to-yaml.html`. Each file must work on its own when served as a static
page.

## Local development

Run a static server from the repository root:

```sh
python3 -m http.server 8000
```

Open [http://localhost:8000/](http://localhost:8000/) in a browser. Test through
HTTP instead of opening files with `file://`, because browser APIs and CORS
behavior differ.

## Adding a tool

1. Create a focused `{tool-name}.html` file at the repository root.
2. Keep its HTML, CSS, and JavaScript in that file unless a version-pinned CDN
   dependency is clearly warranted.
3. Include an accessible title, labelled controls, visible keyboard focus, useful
   error states, and a link back to `index.html`.
4. Add a card for the tool in the `Tool catalog` section of `index.html`.
5. Serve the site locally and test the normal, empty, and invalid-input paths.

See [AGENTS.md](AGENTS.md) for the complete implementation and verification
guidance.

## Deployment

GitHub Pages deploys the root of the `main` branch. No build process is required.
The deployment will use `tools.cjeong.uk` once the custom domain is configured.

## License

[MIT](LICENSE)
