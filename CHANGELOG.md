# Block YouTube Ads Shortcut Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- README instructions for running the userscript automatically on every
  YouTube page load via the Userscripts Safari extension.

### Changed

- Userscript now matches only YouTube domains instead of every website.

### Deprecated

### Removed

### Fixed

- No sound on the next video in Safari after a video ad was auto-skipped:
  ads are now muted and seeked slightly before their end, and the audio is
  re-synced once the video starts.
- Video ads not skipped while the video plays in Picture-in-Picture or in the
  background: ad skipping is now also triggered by video playback events.
- Sound restored on the wrong video when the page has several players.
- A failing page task (e.g. logo insertion) preventing ad skipping.
- `Response.prototype.json` override always throwing because of a wrong
  `Reflect.apply` call.
- Userscript failing at `document-start` when `document.head` does not exist
  yet.

### Security

## [0.0.4] - 2026-07-17
