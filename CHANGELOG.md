# redPeaRL changelog

## 0.7.0-beta.7 (22 Oct 2026) · [release](https://github.com/redPeaRL-miner/redpearl-miner-releases/releases/tag/v0.7.0-beta.7)
- Shares found right after a pool job refresh (about every 40 s) are now sent instead of dropped: about 0.1 % more credited work
- If a pool refuses such a share, the miner stops doing this on that connection (one log line)

## 0.7.0-beta.6.1 (21 Oct 2026) · [release](https://github.com/redPeaRL-miner/redpearl-miner-releases/releases/tag/v0.7.0-beta.6.1)
- Fixed the Windows exe failing to start on Windows 10 ("Entry Point Not Found: SHGetPropertyStoreForWindow", since beta.5)
- Windows only; Linux stays on beta.6

## 0.7.0-beta.6 (21 Oct 2026) · [release](https://github.com/redPeaRL-miner/redpearl-miner-releases/releases/tag/v0.7.0-beta.6)
- ~2 % higher hashrate and efficiency on RX 9070 XT and RX 9060 XT
- Invalid custom `shape` values (n not a multiple of 256) are now refused at start instead of mining nothing

## 0.7.0-beta.5.1 (19 Oct 2026) · [release](https://github.com/redPeaRL-miner/redpearl-miner-releases/releases/tag/v0.7.0-beta.5.1)
- Fixed the miner stopping after ~36 hours on RX 9070 XT (~71 hours on RX 9060 XT)
- A GPU error while mining now exits with code 7, so the launcher restarts the miner

## 0.7.0-beta.5 (19 Oct 2026) · [release](https://github.com/redPeaRL-miner/redpearl-miner-releases/releases/tag/v0.7.0-beta.5)
- GPU hang detection: a stuck batch exits with code 4 and the launcher restarts the miner
- Status line every 10 seconds (`status_seconds` under `[log]`)
- Launcher restarts the miner after any error exit
- Linux package (Ubuntu 24.04+, ROCm HIP runtime 6.4+)
- redPeaRL icon and window title
- `RC n` on the status line counts pool reconnects
- No coin prompt when the exe is started directly

## 0.7.0-beta.4 (17 Oct 2026) · [release](https://github.com/redPeaRL-miner/redpearl-miner-releases/releases/tag/v0.7.0-beta.4)
- Fixed usage stats stopping after a few reports
- Kryptex custom share difficulty documented in POOL-EXAMPLES.md

## 0.7.0-beta.3 (17 Oct 2026)
- Added Rabid Pool preset (PPLNS and SOLO)
- Added POOL-EXAMPLES.md with a ready config for every supported pool

## 0.7.0-beta.2 (17 Oct 2026)
- Fixed the miner not mining at start
- Smaller proofs on the wire (~98x compression)
- Slight efficiency gain on power-limited cards

Older detail: [CHANGELOG-archive.md](CHANGELOG-archive.md)
