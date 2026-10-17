# redPeaRL - help

redPeaRL is a Pearl (PRL) miner built for the AMD Radeon RX 9070 XT and RX 9060 XT (RDNA4). Nothing else: no
NVIDIA cards, no Radeon generations before RDNA4. This is a closed-beta build; please report what you see to
support@redpearlminer.com.

## Quick start (Windows)

1. Unzip the package anywhere, for example `C:\redPeaRL\`. Keep `kernels\` next to `redpearl-miner.exe`.
2. Double-click `Start-redpearl-miner.bat`. On the first start the miner writes `redpearl.toml` next to the exe and
   stops, telling you to fill in your wallet.
3. Open `redpearl.toml` in Notepad. Remove the `#` in front of the `wallet = ` line and paste your PRL wallet address
   between the quotes. Give the machine a `worker` name if you like. Save. (The miner asks you to accept `EULA.md` on
   the next start; you can also set `accept_eula = true` in the file yourself.)
4. Double-click `Start-redpearl-miner.bat` again. The miner runs a self-test on the GPU (about 10 seconds), connects to
   the pool, and prints a status line every 30 seconds.

If Windows Defender stops the download or the exe, see "Windows Defender" below.

## What a healthy start looks like

```
redPeaRL 0.7.0-beta.4 x86-64-v2
log: C:\redPeaRL\miner.log (10 MB x 5 files)
GPU 0: AMD Radeon RX 9070 XT
config: C:\redPeaRL\redpearl.toml, 3 setting(s)
pool: connecting to stratum+ssl://prl-us.kryptex.network:8048, worker rig1
self-test: PASS (GPU 0, gfx1201)
shape 4096 x 65536 x 8192, batch 4
mining started - status every 30 s
Stratum: share accepted (57 ms)
redPeaRL 0.7.0-beta.4 | 140.7 TH/s | 140.7 avg 1m | A 1 R 0 | 488 GH/J 288 W 2.50 GHz 751 mV | 48C hot 75C mem 74C fan 1747 rpm
```

The status line, left to right: hashrate now and the 1-minute (later 15-minute) average, shares accepted (A) and
rejected (R), efficiency in GH per joule, board power, GPU clock and voltage, edge / hotspot / memory temperatures and
fan speed. The hashrate is pool-equivalent: what the pool credits per worker matches this figure.

## redpearl.toml

All settings live in one file next to the exe. Command-line flags override it; `RP_*` environment variables (used in
containers) sit in between.

| key | meaning |
|---|---|
| `wallet` | your PRL address (required) |
| `worker` | the name shown at the pool for this machine |
| `pool` | `kryptex`, `herominers`, `luckypool`, `pearlfortune`, or a URL such as `"stratum+ssl://host"` |
| `region` | region of the preset (`us`, `eu`, ...) or `auto` = the fastest from here (default) |
| `port`, `password` | only for a URL pool, or a pool that asks for a password |
| `device` | GPU index to mine on, only with several GPUs (one GPU per process in this beta) |
| `[log] level` | `quiet`, `normal`, `verbose`, `debug` |
| `[log] file`, `file_size_mb`, `file_count` | the log file ring (default `miner.log` next to the exe, 10 MB x 5) |
| `stats` | anonymous usage stats, `true` (default) or `false` - see below |
| `accept_eula` | `true` once you have read EULA.md and agree; the miner does not run until then |
| `[advanced] batch` | attempts per GPU batch, 4-32; the default 4 is best on power-limited cards |
| `[advanced] shape` | the matrix shape; leave it unless asked |

A wrong key or value stops the miner at start with a message naming the key and the allowed values.

## Pools

- **Kryptex** - fully supported: TLS, every region, worker names, and Kryptex's compressed-proof protocol.
- **HeroMiners**, **LuckyPool**, **PearlFortune**, **Rabid Pool** (`pool = "rabidmining"`, PPLNS; SOLO via
  `pool = "stratum+tcp://prl.rabidmining.com:9934"`) - presets; the login form each pool wants is handled for you.
- Ready-to-paste config blocks for every pool are in `POOL-EXAMPLES.md` in this folder.
- Any other Pearl stratum pool: `pool = "stratum+ssl://host"` (or `stratum+tcp://`) and `port = ...`. Tell us which
  one, and we will add it as a preset.

`redpearl-miner.exe --pool-test` times every region of every preset from your connection and exits.

## The fee

redPeaRL charges a 1 % developer fee: about 14 minutes in every 24 hours, your GPU mines to the developer's wallet.
The fee is written into the log as it happens. It connects to Kryptex; if Kryptex cannot be reached, your own mining
is not affected and the fee connection retries later. Your mining never waits for the fee. There is no subscription
and no hidden switching; the anonymous usage stats are described in the next section and switched off with one line.

## Usage stats (pseudonymous)

On by default; `stats = false` in `redpearl.toml` (or `RP_STATS=false`) turns them off, and the start-up line says
which it is. They are pseudonymous, not anonymous: a random install id lets records from one installation be grouped,
but nothing in them identifies you. Every 5 minutes while mining, one small HTTPS record goes to
`https://redpearlminer.com/api/stats` with:

- a random install id (`redpearl-stats-id.txt` next to the exe; delete it to get a new one),
- miner version, operating system version,
- GPU model, architecture, VRAM size,
- your settings: pool preset, batch, shape, log level, which pool the fee is on, whether the EULA is accepted,
- the status-line numbers: hashrate, 15-minute average, accepted and rejected shares, GH/J, power, clock, voltage,
  temperatures, fan speed, uptime,
- health: self-test result, number of error lines since start, the last error message, pool reconnect count,
- on a fatal error: one crash record with the error and the last log lines.

Never sent: your wallet address, worker name, pool password, computer name, user name, files, or anything you typed.
Before any error text or log lines leave the machine, the wallet, worker name, password, Windows user name, file and
folder paths and host names are removed from them. The receiving end discards the IP address; nothing is logged with
it. We keep the records for 180 days, then they are deleted automatically; we cannot delete single records earlier,
but with `stats = false` no new records are created and the old ones expire. Deleting `redpearl-stats-id.txt` gives
your installation a new id. Questions about this data: admin@redpearlminer.com. The stats tell us which cards and
settings work and where it breaks, which is what a beta is for.

## Licence

redPeaRL is proprietary software licensed under the agreement in `EULA.md` (in this folder). On the first start in a
console the miner shows where the agreement is and asks you to type `I agree`; that writes `accept_eula = true` into
`redpearl.toml`. Headless starts set the line (or `RP_ACCEPT_EULA=true`) themselves. The miner does not mine until it
is accepted.

## Your GPU settings

redPeaRL never changes power limit, clocks, voltage, fan curve or memory timing. Set the card up in AMD Software
(Adrenalin) exactly as you want it and the miner works with that. The miner only reads the sensors it shows.

A note from our own testing: on an RX 9070 XT a power limit around -15 % with a modest undervolt gave us the best
efficiency; stock power gave a few percent more hashrate for much more heat. Your card will differ. Change one thing
at a time and watch the status line for a few minutes.

## Windows Defender

The beta build is not yet code-signed, and Defender tends to flag unsigned mining software (it may name a generic
family such as "Bearfoos"). It is a false positive for this file; check the SHA-256 in `BUILD.txt` against the
download page if you want to be sure. To run it:

1. Windows Security > Virus & threat protection > Manage settings > Exclusions > Add an exclusion > Folder, and
   choose the folder you unzipped redPeaRL into.
2. If Defender already removed the exe, restore it from Protection history, then add the exclusion.

A signed build is planned for the release.

## Benchmark without a pool

`redpearl-miner.exe --benchmark 60` runs the self-test and then mines for 60 seconds with no wallet or pool, printing
the same status line. Good for comparing settings.

## Troubleshooting

- **"self-test: FAIL"** or **"Pearl device qualification failed"** - the GPU did not reproduce the reference result.
  Usually another program is using the GPU heavily (close other miners and benchmarks), or an unstable overclock or
  undervolt. Put the card at stock in Adrenalin and try again; if it still fails, send us `miner.log`.
- **"GPU 0: ..." names a card that is not an RX 9070 XT / 9060 XT** - redPeaRL will not run on it.
- **No shares after several minutes** - check the pool and region in `redpearl.toml`; `--pool-test` shows what is
  reachable from your connection. A share arrives on average every minute or two on a 9070 XT.
- **Rate is well below what you expect** - look at the board power and clock in the status line. A card running far
  under its power limit or at a low clock is usually an Adrenalin profile that did not apply; open Adrenalin and
  re-apply your profile.
- **Hotspot above 100 C** - the fan curve is yours to set in Adrenalin; the miner does not touch it.
- **"CONFIG ERROR"** at start - the message names the key and the allowed values; fix the line it points to.
- **"Licence not accepted yet"** - set `accept_eula = true` in `redpearl.toml` after reading EULA.md.

## Logs and reporting

`miner.log` next to the exe holds everything the console shows (10 MB x 5 files by default). When you report a
problem, attach the log or its last 200 lines, your card model, your Adrenalin power/voltage settings, and what you
expected. support@redpearlminer.com.

## Linux

A Linux build, including a container image for rented GPUs, is in development. Beta testers hear first.

## Credits and licence

redPeaRL is proprietary software; see EULA.md and LICENSE. It is built on tnn-miner (MIT); see THIRD_PARTY_NOTICES.md.
AMD and Radeon are trademarks of Advanced Micro Devices, Inc.
