# NOTICE

## Origin

This repository is a modified fork of **Limusic**:

- Upstream: <https://github.com/SimoHypers/limusic>
- Upstream license: GNU General Public License v3.0
- Fork point: `v1.3.0`, commit `9fb803b` (`chore: bump to 1.3.0`)
- Fork name: **Wrath**

Limusic is itself a desktop rebuild of the playback engine behind
[Metrolist](https://github.com/mostafaalagamy/Metrolist). Limusic's README, source
comments and Git history carry the detailed provenance of that work; they are
retained in this repository's history.

## Copyright

The upstream code is Copyright (C) the Limusic contributors, licensed under
GPL-3.0. Those notices are retained. Modifications made for this fork are
Copyright (C) 2026 the Wrath contributors, also licensed under GPL-3.0.

Nothing in this fork relicenses upstream code. Every file originating upstream
remains under GPL-3.0.

## Modifications

This fork changes:

1. Product and package identity: product name, bundle identifier, binary and
   crate names, window titles, URI schemes, environment variable prefixes,
   database/log/config file names, desktop and MPRIS identities.
2. Update delivery: the updater endpoint and signing public key are removed, so
   this build does not trust or contact upstream's release channel.
3. Integrations that require the upstream maintainer's accounts: Discord
   application ID, release-metadata repository paths, translation portal and
   donation links.
4. Documentation: this README, NOTICE, and the translation contribution notes.
5. Removed: upstream's marketing website, website deployment workflow, stream
   health monitoring workflow, and funding configuration.

No attempt is made to represent these changes as upstream's work, and no upstream
maintainer endorses this fork.

## Third-party components

This project depends on third-party crates and system libraries (Tauri, mpv,
WebKitGTK/WebView2, and others), each under its own license. Run
`cargo tree` / see `Cargo.lock` and `ui/package.json` for the exact set. Their
licenses are unaffected by this fork's GPL-3.0 licensing.

## Reporting

Issues caused by this fork's modifications belong here. Issues in the shared code
base are usually better reported upstream, unless the fork changed them.
