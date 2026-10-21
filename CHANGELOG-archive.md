# Changelog archive

The full release notes up to 0.7.0-beta.5.1, newest first; current releases are in CHANGELOG.md. 0.7.0-beta.1 (16 Oct 2026) had a start-up fault and was never distributed.

## 0.7.0-beta.5.1 (19 Oct 2026) - hotfix: no stop after 36 hours

### Fixed in beta.5.1

- **The miner no longer stops after about a day and a half.** beta.5 kept a lifetime total of the work done in a 64-bit counter and stopped when it filled up: after about 36 hours on an RX 9070 XT, about 71 hours on an RX 9060 XT. It then exited with code 0, which the launcher reads as a stop by you, so it did not restart. The counter now wraps around (hashrate is computed from differences, so nothing else changes), checked on an RX 9070 XT with the counter started just below the limit.
- **A GPU error while mining now exits with code 7** instead of 0, so the launcher restarts the miner. HELP.md lists the exit codes.

Everything else is beta.5 unchanged: status line every 10 seconds, GPU hang detection, launcher restarts after errors, Linux package, icon and title, RC counter.

## 0.7.0-beta.5 (19 Oct 2026) - GPU hang detection, 10-second status, Linux package

### New in beta.5

- **Status line every 10 seconds** (was 30). `status_seconds` under `[log]` sets it, 5 to 600.
- **GPU hang detection.** The miner no longer waits forever on a GPU that stops answering. A batch that has not finished after 15 seconds (a normal batch takes well under a second) is reported with its details and the pending driver error, and the miner exits with code 4 so the launcher can restart it. A 90-second status watchdog remains as a backstop (`stall_seconds` under `[advanced]`; 0 switches it off). Found on a test-fleet card that stopped completing work 30 seconds into every run.
- **Launcher restarts after errors.** Any exit other than a clean stop (code 0) or a configuration message (code 2) is restarted, including "no usable GPU" (code 5, what a driver reset looks like) and GPU errors at start (code 6). Config messages stay on screen.
- **Linux package** (`redpearl-miner-0.7.0-beta.5-linux-x64.tar.gz`): the build our test fleet runs. glibc 2.38 or newer (Ubuntu 24.04+) and the AMD ROCm HIP runtime 6.4 or newer; `start-redpearl-miner.sh` works like the Windows launcher. HELP.md, section Linux.
- **redPeaRL icon and title** on the console window, the taskbar and the exe itself (version block in the file properties). Under Windows Terminal the launcher opens the classic console window so the icon shows.
- **`RC n` on the status line** after the pool connection was lost and re-made n times.
- **No more coin prompt** when the exe is started directly: it mines PRL. An exe started by a double-click that stops with an error now waits for Enter instead of closing at once.

### Unchanged from beta.4

Usage-stats fix, Rabid Pool preset, dynamic-Huffman compressed proofs for Kryptex (GZIP v2), the efficiency change for power-limited cards. One GPU per process.

## 0.7.0-beta.4 (17 Oct 2026) - usage stats fixed; first public-beta build

First build of the public beta. (Internal builds made on 17 Oct while this fix was being chased were never
distributed; this is the one that shipped.)

### Fixed

- **Usage stats stopped after a few reports.** The report sender hung after each exchange when it tore down its
  connection objects on Windows; one hung report silenced stats for the rest of the session while mining carried on,
  in every session since beta.1. The connection machinery (event loop, name resolver, TLS context with the Windows
  roots) is now created once and kept for the life of the process, only the per-report stream comes and goes, each
  report runs in its own thread under a 90-second watchdog, the response is read under a 15-second deadline, GPU facts
  are queried once, and the log says when a report is refused, stuck or left a clean-up pending. Verified on the home
  card: reports every five minutes for 81 minutes with a flat thread count. Mining is never affected by stats.

### Documentation

- POOL-EXAMPLES.md: Kryptex custom share difficulty through the password line (d=N), with the pool's formula.

### Unchanged

Everything else is 0.7.0-beta.3 (Rabid Pool preset, start-up fix, dynamic-Huffman proofs, the efficiency change for
power-limited cards). One GPU per process; Windows only.

## 0.7.0-beta.3 (17 Oct 2026) - Rabid Pool preset

Same build as 0.7.0-beta.2 plus one pool preset.

### Added

- **Rabid Pool** preset: `pool = "rabidmining"` connects to prl.rabidmining.com:9933 (PPLNS, plain stratum,
  wallet.worker login). SOLO mining on that pool is a URL: `pool = "stratum+tcp://prl.rabidmining.com:9934"`.
  Checked 17 Oct 2026 from the home RX 9070 XT: login accepted, compressed proofs accepted, shares accepted.

- **POOL-EXAMPLES.md** in the package: a ready-to-paste `redpearl.toml` block for each supported pool (Kryptex, HeroMiners,
  LuckyPool, PearlFortune, Rabid Pool PPLNS and SOLO) plus the pattern for any other stratum pool.

### Unchanged

Everything else is 0.7.0-beta.2 (start-up fix, dynamic-Huffman proofs, the efficiency change for power-limited cards).
One GPU per process; Windows only.

## 0.7.0-beta.2 (17 Oct 2026) - start-up fix and smaller proofs

Replaces 0.7.0-beta.1, which never reached a tester. Same package layout and the same SHA-256 reporting in `BUILD.txt`.

### Fixed

- **The product exe did not mine.** With the coin chosen by `--prl` (which the launcher always passes), start-up ran the
  symbol lookup with an empty symbol; the product build blanks the names of every coin it does not mine, so the empty
  symbol matched 31 blank rows and the last one replaced Pearl: "Set to mine" with no name, "Unknown mining algorithm:
  140", "This coin is not supported on GPUs", reconnect loop. Every product build since the output audit had it; the
  developer builds used for all earlier testing did not (their rows carry names). Found 16 Oct 21:28 ET on the first
  run of a CI package with `redpearl.toml`. The lookup now runs only when a symbol was typed and skips blank rows.

### Changed

- **Proofs are a third smaller on the wire.** The gzip encoder gained dynamic-Huffman blocks (each block is emitted as
  the smallest of dynamic / fixed / stored). A proof for the default shape goes 301,360 -> about 3,060 bytes (98x),
  where the fixed-code encoder gave 4,670 (64x) and zlib level 6 gives 3,143. Verified against Python's gzip on 30
  cases and on 5 real proofs; the round-trip test now runs in CI (`regression/gzip`).
- **A small efficiency gain on power-limited cards**, from an internal change to how the kernel is fed; measured on
  our own card (the self-test oracle validates it on every start). Proof sizes are unchanged by it.

### Verified on this build (home RX 9070 XT, 17 Oct 2026)

Start with `redpearl.toml` (wallet, pool = "kryptex", region = "auto") through `Start-redpearl-miner.bat`: self-test
PASS, shares accepted, proof size in the log. Details in the project handoff.

### Known issues and limits

Unchanged from 0.7.0-beta.1: one GPU per process; Windows only; the self-test needs the GPU to itself.
