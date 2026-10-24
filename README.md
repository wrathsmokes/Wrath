# Wrath

**A native desktop YouTube Music client. Rust + Tauri, ad-free, no Electron.**

Wrath is a **fork of [Limusic](https://github.com/SimoHypers/limusic)** by
[SimoHypers](https://github.com/SimoHypers), rebranded and maintained separately.
It is not affiliated with upstream, with YouTube, or with Google.

> **Status:** source-only. There are no Wrath releases yet — build from source.
> Upstream's releases are *Limusic* and are not this project.

---

## About this fork

Changes in Wrath relative to upstream `limusic` v1.3.0:

- Renamed product, binary, bundle identifier (`com.wrath.desktop`), window titles,
  log/database/config filenames, MPRIS name, notification name, URI schemes,
  environment variables and package/crate names.
- **Auto-update removed.** `tauri.conf.json` carries no endpoints and no signing
  public key, `createUpdaterArtifacts` is off, and the UI's update check returns
  early. A Wrath build cannot be silently updated by upstream's releases. To
  re-enable, generate your own Tauri keypair and restore the `plugins.updater`
  block with your own endpoint and key.
- **Discord Rich Presence disabled** until you register your own Discord
  application (`APP_ID` in `src-tauri/src/discord.rs`). Upstream's application
  ID and badge URL are not reused.
- **No repository links ship in the app.** The bug-report button and the GitHub
  changelog feed are removed, and the release feed constant (`RELEASES_REPO` in
  `src-tauri/src/commands.rs`) is empty, so What's new reports "no releases".
  `scripts/release.sh` takes the publishing repository from `REPO=owner/name` when
  you run it. Upstream attribution links in this file and `NOTICE.md` stay, because
  GPL-3.0 requires crediting the original project.
- Upstream's marketing site and donation/translation-portal links are removed.

Everything else — the player, YouTube InnerTube transport, lyrics pipeline, local
library, scrobbling, Listen Together, theming — is upstream code, under the same
license.

---

## Features

- **Ad-free playback**: streams come straight from YouTube's API, ads never do
- **Search & browse**: songs, albums, artists, playlists and the YTM home feed
- **Sign in** with your YouTube Music account: in-app Google login or cookie-paste,
  several accounts with switching
- **Your library**: playlists, liked songs, saved albums and artists, uploads, and
  write actions (like, add to playlist, create/edit/delete playlists, subscribe)
- **History** in YouTube Music's own day buckets
- **Gapless playback** with loudness normalization, powered by libmpv
- **Queue** with radio/automix continuation, drag to reorder, restored across restarts
- **Synced lyrics**: side panel with auto-scroll, word-by-word where the source has
  timings, translations under each line
- **Music videos** where the artwork sits, with the same gapless audio behind it
- **Mini Player and theater mode**
- **Local Music** with metadata intact
- **Last.fm** and **ListenBrainz** scrobbling
- **OS media keys** and now-playing integration (MPRIS, SMTC, taskbar preview)
- **System tray**, start-on-login, global hotkeys
- **Listen Together**: synced listening rooms over a self-hosted relay
- **Eighteen languages**, accent palettes, custom colors, fonts, corner roundness,
  custom app icon, adaptive theme from the playing cover

Discord Rich Presence exists in the code but is off in this fork until a Discord
application is configured.

---

## Building from source

Prerequisites are the same as upstream; see
[docs/BUILD-PLATFORMS.md](docs/BUILD-PLATFORMS.md) for the full per-platform list.

**Windows (x64)** — the primary target for this fork:

```powershell
# Rust (MSVC toolchain), Node 22/24, pnpm, and the VS C++ build tools are required.
cd ui; pnpm install; cd ..
cargo tauri build
```

Windows builds dynamically link **libmpv**, so `libmpv-2.dll` must sit beside the
binary. Upstream publishes a prepared archive at
`https://github.com/SimoHypers/limusic/releases/download/deps/`; the release
workflow (`.github/workflows/windows-release.yml`) shows which one and where it is
copied. Linux and macOS builds are unchanged from upstream's instructions.

Output lands in `target/release/bundle/`.

---

## License and attribution

Wrath is distributed under **GPL-3.0**, the same license as upstream. See
[LICENSE](LICENSE) and [NOTICE.md](NOTICE.md).

```
Wrath — a rebranded fork of Limusic
Copyright (C) 2025-2026 the Limusic contributors
Copyright (C) 2026 the Wrath contributors

This program is free software: you can redistribute it and/or modify it under the
terms of the GNU General Public License as published by the Free Software
Foundation, either version 3 of the License, or (at your option) any later version.
```

If you distribute a modified Wrath, GPL-3.0 requires that you keep these notices,
keep the license, mark your changes, and make the complete corresponding source
available under the same license.

---

## Upstream

- Project: <https://github.com/SimoHypers/limusic>
- License: GPL-3.0
- Upstream docs: [CONTRIBUTING.md](CONTRIBUTING.md), [docs/](docs/)

Bug reports about the shared code base are usually better upstream; report
Wrath-only changes (branding, disabled updater, this fork's packaging) here.

## Disclaimer

Wrath is not affiliated with, funded, authorized, endorsed by, or in any way
associated with YouTube, Google LLC, or their affiliates and subsidiaries. All
trademarks, service marks, and intellectual property rights referenced in this
project belong to their respective owners.

This project exists for lawful use: analyzing and modifying software you are
authorized to use, under the terms of its license and the terms of the services it
interoperates with.
