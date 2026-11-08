# IELTS Boost — Stage 36 Advanced Mastery

## Release contents

- `index.html`: full 84-day application and embedded curriculum/data.
- `audio/`: 84 original IELTS Boost practice MP3 files (synthetic practice voice; not official IELTS recordings).
- `icons/`: 192px and 512px PWA icons.
- `manifest.webmanifest`, `sw.js`, `favicon.svg`, `.nojekyll`: install/offline shell and GitHub Pages support.
- `QA_REPORT_UZ.md`, `STAGE36_FEATURES_UZ.md`, `VOCABULARY_POLICY_UZ.md`, `STAGE36_SOURCES_UZ.md` and `STAGE36_CONTENT_AUDIT.json`: implementation, source and verification notes.

## GitHub Pages deployment

1. Extract this ZIP. Upload the **contents** to the repository root (not the ZIP itself).
2. Keep the folders exactly named `audio` and `icons`, at the same level as `index.html`.
3. GitHub repository → Settings → Pages → Deploy from a branch → `main` → `/(root)` → Save.
4. Open the HTTPS GitHub Pages URL. The browser must load the app once online so the service worker can install and cache the app shell.

The complete ZIP is intended as a deployment archive/backup. For mobile browser uploads, use the smaller split upload pack supplied separately.

## Upgrade safely

The existing local-storage key (`ielts-boost-rebuilt-1.0`) is retained. Nevertheless, export a JSON backup in Settings before replacing files. Speaking audio blobs live in IndexedDB and are not included in the JSON backup; download important recordings separately from the Speaking studio.

## Install as an app on Android Chrome

Open the live HTTPS site in Chrome and let it finish loading. Interact with the page and keep it open for a while; Chrome applies install-promotion engagement heuristics, so the in-app **Install app** prompt may not appear immediately. The manifest includes an app name, 192px/512px icons, `start_url`, `scope`, `display: standalone`, and `prefer_related_applications: false`; the service worker is included and registered on HTTPS. When Chrome emits `beforeinstallprompt`, the in-app **Install app** button opens it. Otherwise open Chrome `⋮` and look for **Install app**. If the only option is **Add to Home screen**, that may create a shortcut rather than a fully installed standalone PWA. Confirm installation only when the app opens without the normal browser address bar. Actual Chrome/Samsung device installation still needs to be tested on the phone.

## Important technical boundaries

- Stage 36 uses browser `SpeechRecognition` / `webkitSpeechRecognition` for live transcript capture where supported. Recognition may require network access and browser permission. The saved audio file is not automatically transcribed offline. Manual transcript input/export is provided as fallback.
- Speaking text analytics are heuristic learning feedback. They do not assess accent, intelligibility, stress, intonation, or assign an official IELTS band. Pronunciation requires listening to the saved audio.
- All 0–10 game and criterion values are internal practice indicators, not official IELTS bands.
- Vocabulary: the searchable first 10,000 entries have US and UK IPA fields. Only the count shown in `VOCABULARY_POLICY_UZ.md` is a full bundled bilingual glossary; other definitions/translations are fetched on demand when APIs are reachable and cached locally. The translation API output is machine translation and must be checked against a learner dictionary.
- Copyright: the app links to official IELTS/Cambridge/British Council preparation resources and uses original practice tasks. It does not redistribute paid book scans, official protected tests, publisher audio or answer-key content.
