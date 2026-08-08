# Flypi Music

Flypi Music is a Material You Android music app based on OpenTune. It focuses on a clean music experience with search, playback, library features, lyrics, downloads, and a modern Jetpack Compose interface.

<p align="center">
  <a href="https://github.com/flypimusic/flypi-music/releases/latest">
    <img alt="Latest release" src="https://img.shields.io/github/v/release/flypimusic/flypi-music?style=flat-square&label=release">
  </a>
  <a href="LICENSE">
    <img alt="License" src="https://img.shields.io/github/license/flypimusic/flypi-music?style=flat-square">
  </a>
  <img alt="Android" src="https://img.shields.io/badge/platform-Android%206.0%2B-3DDC84?style=flat-square&logo=android&logoColor=white">
  <img alt="Kotlin" src="https://img.shields.io/badge/Kotlin-Jetpack%20Compose-7F52FF?style=flat-square&logo=kotlin&logoColor=white">
</p>

## Download

Get the latest APK from the GitHub Releases page:

[Download Flypi Music APK](https://github.com/flypimusic/flypi-music/releases/latest)

Current release asset:

[Flypi-Music.apk](https://github.com/flypimusic/flypi-music/releases/download/v1.0/Flypi-Music.apk)

Verified release APK:

- Signed release build, not debug.
- Package name: `com.flypimusic.music`
- Verified with APK Signature Scheme v2 and v3.

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

- Releases: https://github.com/flypimusic/flypi-music/releases
- Issues: https://github.com/flypimusic/flypi-music/issues
- Source: https://github.com/flypimusic/flypi-music

## Credits

Flypi Music is based on the open-source OpenTune project by Arturo254.

Original project: https://github.com/Arturo254/OpenTune

## License

This project is licensed under the GPL-3.0 license. See [LICENSE](LICENSE) for details.
