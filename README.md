# Prateek-Term Homebrew tap

Terminal emulator and SSH/serial connection manager for macOS.
<https://github.com/tripathiprateek/prateek-term>

## Install

```sh
brew tap tripathiprateek/prateek-term
brew trust tripathiprateek/prateek-term   # Homebrew 6+ requires this for third-party cask taps
brew install --cask prateek-term          # stable
brew install --cask prateek-term@rc       # release candidate
```

Without `brew trust` you get:
`Error: Refusing to load cask ... from untrusted tap`.

## Gatekeeper

Prateek-Term is ad-hoc signed but **not notarized** (no paid Apple Developer
account), so macOS may refuse the first launch. Homebrew 6 removed the old
`--no-quarantine` flag, so if that happens:

```sh
xattr -dr com.apple.quarantine /Applications/Prateek-Term.app
```

…or right-click the app → Open → Open, or allow it under
**System Settings → Privacy & Security**.

Verify what you downloaded against the `SHA256SUMS` file published with every
release: <https://github.com/tripathiprateek/prateek-term/releases>

## Channels

`prateek-term` tracks stable releases, `prateek-term@rc` tracks release
candidates. Installing an RC opts you into the RC channel — you keep getting
RCs, and the final release when it lands.

Both install the same app bundle and therefore conflict. To switch:

```sh
brew uninstall --cask prateek-term@rc
brew install --cask prateek-term
```

## Apple Silicon only

The build is arm64-only; the casks declare `depends_on arch: :arm64` so Intel
Macs fail with a clear message instead of installing an app that cannot launch.

---

Cask versions and checksums are updated automatically by CI on each release.
The canonical cask source lives in
[`packaging/homebrew/Casks`](https://github.com/tripathiprateek/prateek-term/tree/main/packaging/homebrew/Casks).
