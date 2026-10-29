# redPeaRL changelog

## 0.7.0-beta.8.5 (28 Oct 2026) · [release](https://github.com/redPeaRL-miner/redpearl-miner-releases/releases/tag/v0.7.0-beta.8.5)
- **Alpha Pool** preset: `pool = "alphapool"`, also in the app
- **Update notice**: the log and a green **Update** badge in the app say when a newer release is out (hourly check; nothing is downloaded; `RP_UPDATE_CHECK=0` turns it off)
- **Share difficulty** in the log and the app
- **Hot-card warning** at 100 C hotspot
- **Linux**: GPU temperatures, clock, voltage and fan, also under WSL2
- Windows: greatly reduced CPU usage while mining (about 7 % of one core)
- The start-up self-test waits and retries when another program is busy on the GPU
- Windows: GPU sensors on older AMD drivers
- Clearer "no GPU" message
- A network outage counts as one reconnect

## 0.7.0-beta.8.3 (27 Oct 2026) · [release](https://github.com/redPeaRL-miner/redpearl-miner-releases/releases/tag/v0.7.0-beta.8.3)
- The wallet field accepts your Kryptex account: the Mining Username from your Kryptex profile (krx...) or the account email. The earnings then go into your Kryptex account, which can auto-exchange them to BTC. Setup no longer refuses a login just because it isn't a prl1 address, and the pool panel shows "paid via your Kryptex account"
- An email login keeps its worker name (you@example.com/rig1)

## 0.7.0-beta.8.2 (27 Oct 2026) · [release](https://github.com/redPeaRL-miner/redpearl-miner-releases/releases/tag/v0.7.0-beta.8.2)
- **redpearl-app.exe** (Windows): double-click it instead of the batch file. First start opens Setup (wallet, worker, pool, EULA) and writes `redpearl.toml`; then tap the coin to mine
- Live view: hashrate, efficiency, power, temperatures, shares, uptime, a 60-minute chart with the pool's figure, your wallet's pool stats, an earnings estimate
- Log with All / Shares / Warnings / Errors filters, "Copy for bug report", "Open log folder"
- Plain messages for the usual problems: miner not responding, pool reconnecting, no supported GPU, GPU busy at the self-test, rejected shares, high temperatures
- Minimal view: a fixed 400 x 400 window. The window remembers its size; the dashboard fits it without scrolling
- Setup re-checks the file's values each time it opens and shows each step as done or not
- Miner: read-only status API on 127.0.0.1 for the app (off unless the app sets it)
- Small increase in mining performance: a faster GPU kernel, about +0.4 % hashrate (measured on an RX 9070 XT at a 288 W power limit)
- The miner's own EULA prompt wrote `accept_eula` inside `[advanced]` and dropped the file's line endings
- A pool reply in a shape the miner did not expect dropped the connection ("Invalid error response", then a 10-second reconnect); such replies are now logged and ignored
- The fee connection's routine closes no longer show in the log or count as errors
- The old stats server (`--broadcast`) is gone
- PCs with integrated graphics (most Ryzen CPUs): the miner chose the RX 9070 / 9060 card but loaded its GPU code onto the integrated graphics ("no kernel image is available for execution on the device"), so the self-test failed and nothing mined
- A pool address on PearlHash, which redPeaRL does not support yet, now stops at start and says so, instead of failing with a TLS certificate error
- Windows: the log no longer shows "The token does not have the specified privilege." at start (a harmless Windows message that looked like an error)

## 0.7.0-beta.7.1 (23 Oct 2026) · [release](https://github.com/redPeaRL-miner/redpearl-miner-releases/releases/tag/v0.7.0-beta.7.1)
- PCs with integrated graphics (most Ryzen CPUs) no longer stop with "requires exactly one selected GPU": the miner picks the RX 9070 / 9060 card and says which GPU it skipped
- Closing the miner during the start-up self-test is a normal stop, not a "qualification failed" error
- A second copy of redPeaRL on a GPU that is already mining now stops at once with "another redPeaRL is already mining on this GPU" instead of failing the self-test
- When the self-test fails, the log says what to do: close another miner or game using the GPU, or reset an unstable overclock / undervolt in AMD Software

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
