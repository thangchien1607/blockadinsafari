# Block YouTube Ads in Safari on iPhone/iPad

> An iOS Shortcut that blocks YouTube ads in Safari on iPhone and iPad — for users who want an ad-free YouTube experience in their mobile browser.

<p align="center">
  <img src="https://cdn.adguard.com/public/Adguard/Blog/safari-problems/shortcut-in-safari-en.jpeg" alt="Block YouTube Ads shortcut in Safari" width="600">
</p>

## Description

Safari's Content Blocking capabilities are [no longer enough](https://adguard.com/en/blog/youtube-ads-in-safari-explained.html) to handle YouTube ads. This project ships a JavaScript userscript, distributed as an iOS Shortcut, that blocks YouTube ads for end users on iPhone and iPad.

**Target audience**: iPhone and iPad owners who watch YouTube in Safari and want ads blocked without switching to a different browser or app.

**The problem**: Standard content blockers cannot keep up with YouTube's ad delivery, leaving Safari users with unskippable video ads and banner overlays. This shortcut injects logic into the YouTube page that hides ad elements, strips ad metadata from responses, auto-skips video ads, and adds an AdGuard logo to the interface.

## Table of Contents

- [Getting Started](#getting-started)
- [Usage](#usage)
- [Automatic Mode](#automatic-mode)
- [Remote Version](#remote-version)
- [Supported Languages](#supported-languages)
- [FAQ / Troubleshooting](#faq--troubleshooting)
- [Development](#development)
- [Documentation](#documentation)

---

## Getting Started

You need an iPhone or iPad running iOS 13 or later with the Shortcuts app, and you must [allow untrusted shortcuts](https://www.macworld.com/article/233447/how-to-allow-untrusted-shortcuts-in-ios-13.html) before installing.

### Install the shortcut

Choose the version that fits your needs:

- **Standard version**: [agrd.io/ios_youtube_shortcut](https://agrd.io/ios_youtube_shortcut) — the code is bundled into the shortcut. You get a fixed snapshot that only changes when you reinstall.
- **Remote version**: [agrd.io/ios_youtube_shortcut_remote](https://agrd.io/ios_youtube_shortcut_remote) — the shortcut downloads the latest code from GitHub on every run, so you get updates automatically without reinstalling.

Tap a link above on your iPhone or iPad and the Shortcuts app opens with an **Add Shortcut** prompt. Confirm to add it to your shortcuts.

---

## Usage

1. Open [youtube.com](https://youtube.com) in **Safari** (the shortcut only works in Safari, not other browsers or the YouTube app).
2. Tap the **Share** button in Safari.
3. Choose **Block YouTube Ads (by AdGuard)** from the action list.
4. The shortcut runs and reloads YouTube with ads blocked — video ads are auto-skipped, banner ads are hidden, and the AdGuard logo appears in the interface.

To make the shortcut easier to reach, tap **Edit actions...** in the Share sheet and add it to your **Favorites** with the **Plus** icon.

> **Note**: You need to run the shortcut again every time you reload or navigate to a new YouTube page. To block ads automatically without tapping anything, see [Automatic Mode](#automatic-mode).

---

## Automatic Mode

iOS Shortcuts cannot run JavaScript on a page by themselves — the **Run JavaScript on Web Page** action only works when you launch it from the Share sheet, and Shortcuts automations cannot trigger it. To block ads automatically every time you open YouTube, use the userscript build with a userscript manager instead.

1. Install the free [Userscripts](https://apps.apple.com/app/userscripts/id1463298887) app from the App Store.
2. Open the app and choose a folder where your userscripts will be stored.
3. Enable the extension: **Settings → Apps → Safari → Extensions → Userscripts**, turn it on, and allow it on `youtube.com` (or **All Websites**).
4. Download `block-youtube-ads.user.js` from the [latest GitHub Release](https://github.com/AdguardTeam/BlockYouTubeAdsShortcut/releases/latest) (or build it yourself, see [Development](#development)) and save it into the Userscripts folder.
5. Open [youtube.com](https://youtube.com) in Safari. The script runs automatically on every page load and reload — the AdGuard logo in the YouTube header confirms that it is active.

The userscript only runs on `www.youtube.com`, `m.youtube.com`, `music.youtube.com`, and `www.youtube-nocookie.com`.

---

## Remote Version

The standard version bundles a fixed copy of the code, so you must reinstall the shortcut to pick up new improvements. If you want updates without reinstalling, use the remote version instead — it fetches the latest `index.js` from the [latest GitHub Release](https://github.com/AdguardTeam/BlockYouTubeAdsShortcut/releases/latest) on every launch.

[Get the remote version](https://agrd.io/ios_youtube_shortcut_remote).

---

## Supported Languages

The shortcut interface and injected text support the following 11 languages:

English, Russian, Spanish, German, French, Italian, Simplified Chinese, Traditional Chinese, Korean, Japanese, and Ukrainian.

---

## FAQ / Troubleshooting

**The shortcut isn't in the Share sheet.**
Tap **Edit actions...** in the Share sheet, find **Block YouTube Ads (by AdGuard)**, and add it to Favorites with the **Plus** icon.

**I reloaded the page and ads came back.**
The shortcut must be re-run each time you reload YouTube. This is expected — the injected script does not persist across page navigation. Use [Automatic Mode](#automatic-mode) if you want ads blocked on every load without re-running anything.

**It doesn't work in Chrome / Firefox / the YouTube app.**
The shortcut uses the Safari Share sheet and only runs in Safari on iPhone and iPad.

**I can't install the shortcut.**
Make sure you have [allowed untrusted shortcuts](https://www.macworld.com/article/233447/how-to-allow-untrusted-shortcuts-in-ios-13.html) in Settings → Shortcuts.

**How do I get updates?**
With the standard version, reinstall the shortcut from [agrd.io/ios_youtube_shortcut](https://agrd.io/ios_youtube_shortcut). With the remote version, updates are automatic — the latest code is fetched on every run.

For other issues, please [open an issue](https://github.com/AdguardTeam/BlockYouTubeAdsShortcut/issues) on the public mirror.

---

## Development

To build the shortcut from source you need [Yarn](https://yarnpkg.com/).

Install dependencies:

```sh
yarn install
```

Build all outputs to the `dist/` directory:

```sh
yarn build
```

The build produces four self-contained files in `dist/`: a userscript (`.user.js`), a browser-extension variant (`extension.js`), an iOS Shortcut variant (`index.js`), and a remote loader (`remote.js`).

Run the linter before submitting changes:

```sh
yarn lint
```

---

## Documentation

- [LLM agent rules](AGENTS.md) — AI-assisted development guidelines and project architecture
- [Deployment and configuration](DEPLOYMENT.md) — CI/CD pipelines, release process, and distribution channels
- [Changelog](CHANGELOG.md) — version history
