# baseline-environment

Generated: 2026-03-16T16:05:27.139888+00:00

## Fresh checkout

- Path: `<local WiFi checkout>`
- Baseline branch: `master`
- Baseline SHA: `c2813c5a72214fb465d42e5c3e2e757931274a85`
- Upstream remote: `https://github.com/openwisp/openwisp-wifi-login-pages.git`

## Planned baseline validation

- `yarn install`
- `./run-qa-checks`
- `yarn coverage`
- `yarn build-dev`
- `yarn browser-test` after Docker-backed browser prerequisites are available

## Current browser-test prerequisites

- Firefox: present as macOS app bundle, not on PATH (`/Applications/Firefox.app/Contents/MacOS/firefox`)
- Geckodriver: present (`/opt/homebrew/bin/geckodriver`)
- Docker daemon: reachable - daemon reachable
- openwisp-radius checkout: present - <local Radius checkout>

## Current blockers observed before full validation

- `openwisp-radius` Python environment and test database still need setup before browser validation
- Firefox is currently available as an app bundle rather than a plain `firefox` binary on `PATH`
