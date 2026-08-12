# rss-translator-lzcapp

This repository packages RSSBox as a LazyCat LPK v2 application.

## Runtime

- Package ID: `cloud.lazycat.app.rss-translator`
- Version: `2025.9.18`
- Upstream app image source: `docker.io/versun/rssbox:2025.9.18`
- Manifest runtime app image: `registry.lazycat.cloud/czyt/versun/rssbox:0651b2ed8e7b5f9c`
- HTTP entrypoint: `/` -> `http://rsstranslator:8000/`
- Persistent data:
  - `/lzcapp/var/data` -> `/app/data`
  - `/lzcapp/var/redis` -> `/data`

The migration keeps LazyCat Registry delivery and preserves the current package version and upstream tag family.

## Build

The project now uses split LPK v2 metadata with `package.yml`, `manifest.yml`, and `lzc-build.yml`, and sets `min_os_version: 1.5.0`.

## Automation

`.github/lazycat-action.yml` tracks the upstream `docker.io/versun/rssbox` image, keeps `delivery: lazycat`, and enables both official and MiaoMiao private publication.

`.github/workflows/lazycat.yml` supports:

- `push` on `main`
- `workflow_dispatch`
- reusable `workflow_call`

It also enables `versioned-release-asset: true`, so release assets are named like `cloud.lazycat.app.rss-translator-v2025.9.18.lpk`.

Required GitHub Secrets:

- `LZC_API_TOKEN`
- `APPSTORE_URL`
- `APPSTORE_TOKEN`
- `APP_ID` (optional)
- `PRIVATE_STORE_GROUP_CODES` (optional)
