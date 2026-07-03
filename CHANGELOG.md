# Changelog

All notable changes to Quirio are recorded here, newest first. Version numbers
follow [semantic versioning](https://semver.org): `MAJOR.MINOR.PATCH` — bump the
last number for fixes, the middle for new features, the first for big milestones.

## [0.5.1] — 2026-07-03

A download-and-casting release: the installer now opens the way the install
steps promise, and sending a book to a speaker got a lot steadier.

### Fixed

- **First launch no longer claims “Quirio is damaged.”** Earlier downloads
  shipped with a broken code signature, so macOS refused them outright — with
  no way forward but a Terminal command. The app is now properly signed at
  build time: first launch shows the standard one-time “could not verify”
  warning instead, and **System Settings → Privacy & Security → Open Anyway**
  clears it, exactly as the install steps describe.
- **Casting holds up for big books and Apple Lossless.** Apple Lossless books
  now cast (Quirio quietly converts them first; your original file is never
  touched), and a speaker that needs a while to read a long book is given that
  while — no more silent give-ups or retry loops mid-handoff. A finished book
  now ends its cast cleanly, and one press starts a re-listen.

### Improved

- **Better company while a speaker gets ready.** Casting a long book shows a
  calm waiting state with a soft estimate, instead of leaving you to wonder
  whether anything is happening.
- **Long books are served to Cast speakers index-first** when the file keeps
  its index at the tail, so the speaker never needs a second pass through a
  large file. Nothing about your files changes.
- **Security hardening under the hood**, from a top-to-bottom audit of how the
  app’s windows and processes talk to each other.

## [0.5.0] — 2026-06-27

The biggest update yet: a new way to look at a book before you play it, and a real
backup system for your whole library.

### Added

- **A book-detail inspector.** Click any book and a floating glass panel slides into
  your shelf — cover, length, narrator, description, chapters, and **Play** — so you
  can have a proper look before you commit. Clicking a book no longer hijacks
  playback; choose whether a click opens details or plays straight away in
  **Settings → Playback** (and the other is always a right-click away).
- **Jump to any chapter.** The inspector's **Chapters** pill opens a slide-up list —
  tap a chapter to jump right there, your exact place always kept.
- **Back up your whole library — and keep it backed up.** Export your covers, edits,
  finished and favorite marks, and listening progress to a single file; **Restore**
  brings it back with a preview (merge, replace, or progress-only). Turn on a
  **daily auto-backup** that rotates older copies and can write to iCloud or an
  external folder, and your books reconnect to their audio on their own.
- **Inline speed & volume in the mini player.** Adjust both right in the docked bar,
  without opening the full window.
- **A friendlier, searchable Help.** The in-app FAQ is warmer and bigger, with live
  search to jump straight to an answer.
- **Smarter window sizing.** Quirio opens at a size that fits your display, and
  remembers where you left it between launches.

### Changed

- **A calmer launch** — the splash holds until your library is ready instead of
  flashing an empty shelf.
- **A refreshed Now Playing** — a bigger cover, cleaner single-row metadata, a length
  footer, and a frosted scroll edge so the summary passes under the chrome rather
  than clipping under it.
- **More accurate chapters** — upgraded the metadata engine (music-metadata 11) for
  correct chapter timing on more files.
- **Richer book descriptions** — embedded formatting and HTML entities now render
  cleanly instead of showing as raw markup.
- **Cover picker** — clearer source labels and a one-click **Revert to original**.
- **Tidier Settings** — the Library pane is reorganized by how often you touch each
  thing, with a hidden-book count in the stored-locally summary.
- **Sharper buttons and typography**, plus honest macOS info: the app and README now
  name what Quirio is tested on (Apple Silicon, macOS Tahoe) rather than overpromising.

### Fixed

- Light-mode contrast sweeps — the Import Summary modal and alert colors now hold up
  in both themes.
- Nav-tab sliding-pill color flash, and marquee jitter when switching views.
- The in-app version number now shows correctly.
- Slimmed the packaged app by dropping leftover development files from the build.

## [0.3.1] — 2026-06-19

A polish release: light mode is warmer and easier to read across the board, and the
player bar got a readability fix plus a more refined, textured look.

### Changed

- **Warmer, calmer light mode.** Dialogs, the Filters / Sort / ⋯ and Alerts
  popovers, the metadata-quality badge, the welcome screens, and the "Edit details"
  and "Review tracks" windows now all sit on the same warm cream as the rest of the
  app — no more cool or muddy panels standing out against the page.
- **A richer player bar.** The playback controls and the "Add your library now"
  button picked up a soft grainy-gradient texture (with the original flat gradient
  kept as a fallback).

### Fixed

- **The player bar stays readable.** Its title and controls no longer fade out when
  you scroll over very light or very dark covers — contrast now holds in both light
  and dark mode.
- **A more natural player-bar shadow,** so the bar reads as a real floating control
  in both themes.

## [0.3.0] — 2026-06-18

Quirio got a lot smarter about duplicates — both the ones you're about to import
and the ones already on your shelf — and the Hidden & skipped screen grew into a
real management tool.

### Added

- **Duplicate-aware importing.** When you add a book Quirio already has, it tells
  you up front instead of quietly making a second copy — and it recognizes the
  *same book in a different format* (say, an M4B and a folder of MP3s) as one
  title rather than two. You get a plain-language heads-up, a "Same book · other
  format" badge, and a sensible default, so your shelf stays tidy.
- **Find & merge duplicates already in your library.** A new audit in
  **Settings → Library** spots audiobooks that slipped in twice and merges them
  back into one — carefully keeping your progress, your finished marks, and which
  book you had open last.
- **A grown-up Hidden & skipped screen.** **Settings → Library → Hidden &
  skipped** was rebuilt with bulk **Forget all** / **Replace all**, a per-row
  **Show in Finder**, the full path on hover, a short guide to what each action
  does, and a calm "all caught up" state when there's nothing left to tidy.

### Fixed

- **True duplicates can no longer sneak in.** A safety check could be fooled when
  a book listed its author as the narrator, letting a genuine duplicate slip past
  the edition match. It now holds.

### Changed

- The skipped-duplicates comparison keeps its details aligned on one line, and
  languages are now matched by their base (so `en-US` and `en` count as the same),
  which helps Quirio recognize editions of the same book.

## [0.2.0] — 2026-06-17

Your library settings now live where they belong — a durable file that survives
every app update — and the app opens on a branded loading screen instead of a
blank flash.

### Fixed

- **Your settings survive updates now.** Watched folders, sort order, grid/list
  view, theme, playback preferences, and dismissed tips are kept in a durable
  app-data file instead of fragile in-window storage, so updating Quirio can no
  longer reset them. (Previously, watched folders could quietly disappear
  between versions.)
- The metadata-badge tip no longer reappears on every launch — dismissing it
  now sticks.

### Added

- **Automatic folder recovery.** If an earlier version lost your watched
  folders, this update rebuilds them from the books already in your library —
  external drives included; they reconnect on their own when you plug them back
  in.
- **Launch screen.** A branded loading screen on cold start replaces the brief
  empty/transparent window, and the navigation icons, fonts, and animations are
  ready the moment the app appears — so first impressions feel smooth. Light and
  dark, honoring Reduce Motion.

## [0.1.0] — 2026-06-16

First packaged build — an internal test release to exercise the end-to-end
release pipeline (build → versioned folder → notices + checksum). Unsigned beta.

### Added

- Local, offline audiobook library: import books, chapter navigation, playback
  with resume of your last-played book.
- "Listen on" output / Google Cast picker.
- Metadata quality chips and a coalescing alert center.
- Automated DMG packaging: the installer ships with the designed background and
  fixed icon layout (app + Applications drop zones), no manual dragging.

### Notes

- **Unsigned beta.** On first launch macOS will warn about an unidentified
  developer; open **System Settings → Privacy & Security → Open Anyway**. This
  goes away once the app is signed + notarized (a later step).
