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

- Userscript failing at `document-start` when `document.head` does not exist
  yet.

### Security

## [0.0.4] - 2026-07-17
