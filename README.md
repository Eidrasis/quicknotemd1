# Quick Note MD

Capture a thought in one tap and append it to your Obsidian daily note. No account, no sync service, no network.

Tap the widget, type, hit send. The note lands at the end of today's daily note and the app closes instantly.

![Screenshot](docs/screenshot.png)

## Features

- Home screen widgets in two sizes (1x1 and 2x1)
- Floating note card that opens with the keyboard already up
- Voice notes through the system speech recognizer
- Writes straight to a folder you choose, such as your Obsidian daily notes folder
- Configurable file name format, compatible with Obsidian's Daily Notes syntax
- Light and dark themes
- English and Turkish interface

## How it works

On first launch you pick your daily notes folder once. The app keeps access to it with Android's Storage Access Framework, so it never needs broad storage permissions. Then you set the file name format, which defaults to `YYYY-MM-DD`. A live preview shows today's file name as you type.

Every note is appended as a new line to today's file, which is created if it doesn't exist yet:

```
- 14:32 Call the dentist about Tuesday
- 14:35 Idea: widget colors based on time of day
```

### File name format

The format uses the same Moment.js syntax as Obsidian's Daily Notes plugin, so you can copy it straight from the plugin settings. `.md` is added automatically.

| Token | Meaning | Example |
| --- | --- | --- |
| `YYYY` / `YY` | Year | 2026 / 26 |
| `MMMM` / `MMM` | Month name | November / Nov |
| `MM` / `M` | Month number | 11 / 11 |
| `DD` / `D` | Day of month | 05 / 5 |
| `dddd` / `ddd` | Weekday name | Thursday / Thu |
| `[text]` | Literal text | `[Daily] YYYY-MM-DD` → Daily 2026-11-05 |

A `/` in the format creates subfolders inside the folder you picked, for example `YYYY/MM/YYYY-MM-DD`. Month and weekday names follow your device language.

## Known limitations

- If today's note doesn't exist yet, the app creates an empty file. Obsidian templates are not applied.
- The `Do` token (1st, 2nd, 3rd) is not supported.
- Voice input relies on the system speech recognizer, which may be missing on devices without Google services.

## Privacy

- No internet permission
- No microphone permission (voice input uses the system speech recognizer)
- No analytics, no tracking, no ads
- Backups are disabled
- Your notes never leave your device unless your own sync (Obsidian Sync, Syncthing, etc.) moves them

## Install

Requires Android 8.0 or newer.

Download the latest APK from the [Releases](https://github.com/Eidrasis/quicknotemd/releases) page and install it on your device. You may need to allow installs from your browser or file manager.

## Build from source

Requirements: Android Studio or the Android SDK command-line tools, and JDK 17.

```bash
git clone https://github.com/Eidrasis/quicknotemd.git
cd quicknotemd
./gradlew assembleDebug
```

The APK is written to `app/build/outputs/apk/debug/`.

## Usage

1. Open the app, choose your daily notes folder, and set the file name format.
2. Long-press your home screen, open Widgets, and add Quick Note MD.
3. Tap the pencil to type a note, or the microphone to dictate one.

## Contributing

Issues and pull requests are welcome. Please keep the app small and single-purpose: fast capture, nothing else.

## License

MIT. See [LICENSE](LICENSE).
