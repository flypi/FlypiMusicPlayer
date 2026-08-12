# Flypi Music

Flypi Music is a Material You Android music app based on OpenTune. It focuses on a clean music experience with search, playback, library features, lyrics, downloads, and a modern Jetpack Compose interface.

<p align="center">
  <a href="https://github.com/flypi/FlypiMusicPlayer/releases/latest">
    <img alt="Latest release" src="https://img.shields.io/github/v/release/flypi/FlypiMusicPlayer?style=flat-square&label=release">
  </a>
  <a href="LICENSE">
    <img alt="License" src="https://img.shields.io/github/license/flypi/FlypiMusicPlayer?style=flat-square">
  </a>
  <img alt="Android" src="https://img.shields.io/badge/platform-Android%206.0%2B-3DDC84?style=flat-square&logo=android&logoColor=white">
  <img alt="Kotlin" src="https://img.shields.io/badge/Kotlin-Jetpack%20Compose-7F52FF?style=flat-square&logo=kotlin&logoColor=white">
</p>

## Download

Get the latest APK from the GitHub Releases page:

[Download Flypi Music APK](https://github.com/flypi/FlypiMusicPlayer/releases/latest)

Verified release APK:

- Signed release build, not debug.
- Package name: `com.flypimusic.music`
- Verified with APK Signature Scheme v1, v2, v3, and v4 (kept for compatibility with older/OEM installers, e.g. Android Go, MIUI).

## What's new (v1.5)

- **Fixed a crash on the "Cached" library shortcut** — tapping it threw
  `IllegalArgumentException: Navigation destination that matches route
  cache_playlist/cached cannot be found`. The screen and view model were
  already built, they just weren't wired into the navigation graph.
- **Fixed the same crash on the "Top" library shortcut** (`top_playlist/...`
  route was missing too).
- **Fixed a latent route mismatch** in the Explore / Mood & Genres screens
  (`youtube_browse/...` vs the registered `browse/...`) before it could ever
  cause a crash.
- **Added Spotify-style screen transitions** — slide/fade when navigating
  forward, fade/slide when going back, replacing the previous instant cuts
  between screens.
- **Animated the like (heart) button in the song menu** — smooth color
  transition + spring bounce, matching the behavior already present in the
  expanded player.

Full history: see [CHANGELOG.md](CHANGELOG.md).

## Features

- Search songs, videos, albums, and playlists.
- Stream music with background playback.
- Manage library items and playlists.
- Download music for offline listening.
- View lyrics when available.
- Use a modern Material You interface.
- Supports Android Auto and Android media controls.
- Desktop app for Windows, macOS, and Linux.

## Build From Source

Requirements:

- Android Studio
- Android SDK
- JDK 21

Before building, set up local config (never commit the real files):

```bash
cp local.properties.example local.properties        # fill in your Last.fm keys + sdk.dir
cp app/google-services.json.example app/google-services.json  # or your own Firebase project's file
```

Build the universal release APK:

```powershell
.\gradlew.bat :app:packageUniversalRelease
```

The generated APK is created under:

```text
app/build/outputs/apk/universal/release/
```

Alternatively, push to GitHub and let CI build it for you — see
`.github/workflows/build-apk.yml`, which produces a debug APK on every push
and a signed release APK + GitHub Release whenever a `v*` tag is pushed.

## Modules / Data Providers

Flypi Music is split into small Kotlin/JVM modules, most of which are plain
API clients with no Android dependency (useful for the desktop port, see
`docs/DESKTOP_ROADMAP.md`):

| Module          | Purpose                                        |
| --------------- | ----------------------------------------------- |
| `innertube`     | YouTube Music search, browsing, and streaming   |
| `lrclib`        | Synced lyrics                                   |
| `betterlyrics`  | Additional lyrics source                        |
| `kugou`         | Lyrics fallback source                          |
| `lastfm`        | Scrobbling and artist/track metadata            |
| `applepodcasts` | Podcast search and episode metadata             |
| `simpmusic`     | Additional music metadata source                |
| `shazamkit`     | On-device song recognition                      |
| `canvas`        | Spotify-style canvas/video backgrounds          |
| `kizzy`         | Discord Rich Presence                           |

## Repository Links

- Releases: https://github.com/flypi/FlypiMusicPlayer/releases
- Issues: https://github.com/flypi/FlypiMusicPlayer/issues
- Source: https://github.com/flypi/FlypiMusicPlayer

## Credits

Flypi Music is based on the open-source OpenTune project by Arturo254.

Original project: https://github.com/Arturo254/OpenTune

## License

This project is licensed under the GPL-3.0 license. See [LICENSE](LICENSE) for details.
