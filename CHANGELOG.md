# Changelog

All redPeaRL releases, newest first. 0.7.0-beta.1 (16 Oct 2026) had a start-up fault and was never distributed.

## 0.7.0-beta.4 (17 Oct 2026) - usage stats keep reporting

### Fixed

- **Usage stats stopped after about 45 minutes.** The heartbeat sender did one blocking HTTPS request per report with a
  deadline that only applied to asynchronous calls, so one stalled connection silenced the stats thread for the rest of
  the session while mining carried on. Seen in every session on 16-17 Oct, including the first outside tester. The
  request now runs with a hard 15-second deadline and gives up cleanly; the next report follows five minutes later.
- The log now says when a stats report is not accepted (one line per failure streak, at the normal log level), so a
  tester can tell at a glance that stats are not getting through. Mining is never affected either way.

### Documentation

- POOL-EXAMPLES.md: Kryptex custom share difficulty via the password line (d=N), with the pool's formula.

### Unchanged

Everything else is 0.7.0-beta.3 (Rabid Pool preset, start-up fix, dynamic-Huffman proofs, the efficiency change for
power-limited cards). Not code-signed yet; one GPU per process; Windows only.

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
Not code-signed yet; one GPU per process; Windows only.

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

Unchanged from 0.7.0-beta.1: not code-signed; one GPU per process; Windows only; the self-test needs the GPU to itself.
