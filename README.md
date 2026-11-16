# LyfeDesk approved apps

Apps that are **not part of the base LyfeDesk install**, approved for the +phone App Store. (Today: phone apps. Later: other toys and apps.)

- One folder per app: `manifest.pdl`, `icon/`, `screens/`, `ops/*.c` and an `ops/build_<id>.sh`. **Source only** (no binaries).
- `catalog.pdl` lists every approved app with the SHA-256 tree hash of its folder.
- The App Store installs from **one pinned commit** (a full 40-character id written in the phone prefs, never a branch):
  `STORE_SOURCE | git | https://github.com/<owner>/lyfedesk-approved-apps | <40-hex commit>`.
  It fetches exactly that commit, checks each folder against `catalog.pdl`, refuses anything that does not match (or holds a binary, a symlink or an `ops/+x` folder), re-hashes at install time, then builds the app locally.
- Approving an app = merging it here **and** moving the pin on the machine that installs it.

Design: `16.game/PLUS-PHONE-APP-STORE-AND-APPROVED-REPO-DESIGN-2026-11-16.md` in the LyfeDesk HQ-IQ-BOOK.

## Status
Published set: `stock-x`, `true-swords-clash` and its separate data dependency `bible-verses` (the Bible text; installed by the store into `deps/bible-verses/`, never inside the app package).
