# DRACOTALON

[![latest release](https://img.shields.io/github/v/release/DRACOCODEX/dracotalon-releases?label=stable&color=2a6)](https://github.com/DRACOCODEX/dracotalon-releases/releases/latest)

**DRACOTALON is a standalone, autonomous coding agent for the terminal.** It runs against **your
own sovereign models** — a DRACONEX CAPT endpoint on your network, or an external provider you
supply a key for. It operates in your current working directory and writes to your real filesystem.
One self-contained binary: no runtime to install, no daemon, nothing to configure before the first
launch.

This repository holds **release binaries only**. The source is private.

## Install

macOS and Linux:

```bash
curl -fsSL https://github.com/DRACOCODEX/dracotalon-releases/releases/latest/download/install.sh | bash
```

Windows (PowerShell):

```powershell
irm https://github.com/DRACOCODEX/dracotalon-releases/releases/latest/download/install.ps1 | iex
```

The installer picks the artifact for your machine, verifies its SHA256 against the published
sidecar, refuses to install anything it cannot verify, and puts `dracotalon` on your PATH. Then:

```bash
cd ~/Development/my-app    # any project directory
dracotalon                 # the agent operates HERE, in your CWD
```

Nothing is configured on a fresh install, so the setup screen opens by itself. Pick a provider,
paste its key, press Enter — the binary probes it live and tells you straight away whether that
credential works. One provider is enough to start.

Update in place with `dracotalon update`. Background update checks are off unless you turn them on.

## Stable and pre-release

Releases here come in two kinds.

| | Stable | Pre-release |
|---|---|---|
| Marked | normal release | **Pre-release** badge |
| What the install command gives you | ✅ this | never |
| `/releases/latest` resolves to | ✅ this | skipped |
| Who it is for | everyone | trying something new early |

**Stable is the default and you get it by doing nothing.** The install command above and
[`/releases/latest`](https://github.com/DRACOCODEX/dracotalon-releases/releases/latest) both
resolve to the newest stable release, and GitHub skips pre-releases when resolving them — so a
pre-release can never reach you by accident.

A **pre-release** is newer than stable and less proven. It exists so a change can be exercised
before it is handed to everyone. To run one, pick it from
[all releases](https://github.com/DRACOCODEX/dracotalon-releases/releases) and install that version
explicitly:

```bash
DRACOTALON_VERSION=v0.6.0-alpha.1 \
  bash <(curl -fsSL https://github.com/DRACOCODEX/dracotalon-releases/releases/latest/download/install.sh)
```

Going back is the plain install command again, which returns you to stable.

## Verifying a download

Every binary ships a `.sha256` sidecar, and each release carries a combined `SHA256SUMS.txt`:

```bash
sha256sum -c dracotalon-<version>-linux-x86_64.sha256     # or: shasum -a 256 -c
```

The installer does this for you and refuses to proceed if it cannot. Checking against
`SHA256SUMS.txt` instead reports the artifacts you did not download as missing, so add
`--ignore-missing`.

The binaries are not code-signed or notarized yet. `install.sh` clears the macOS quarantine flag
and `install.ps1` clears the Windows mark-of-the-web; Windows may still show "unknown publisher"
once on first run. Until signing is in place, the checksum is the thing to check.

## What each release contains

Six platforms — macOS and Linux on arm64 and x86_64, Windows on arm64 and x86_64 — each with a
`.sha256` sidecar, plus `SHA256SUMS.txt`, both installers, and a `README.md` covering the offline
install case.

Linux builds are static, so they run on any distribution.

## Links

- [Latest stable release](https://github.com/DRACOCODEX/dracotalon-releases/releases/latest)
- [All releases, including pre-releases](https://github.com/DRACOCODEX/dracotalon-releases/releases)

Issues and questions go to the DRACOFORCE team.
