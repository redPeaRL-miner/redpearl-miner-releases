# redPeaRL - help

redPeaRL is a Pearl (PRL) miner built for the AMD Radeon RX 9070 XT and RX 9060 XT (RDNA4). Nothing else: no
NVIDIA cards, no Radeon generations before RDNA4. This is a public beta for Windows and Linux; please report what you
see to support@redpearlminer.com.

## Quick start (Windows)

1. Unzip the package anywhere, for example `C:\redPeaRL\`. Keep `kernels\` next to `redpearl-miner.exe`.
2. Double-click `Start-redpearl-miner.bat`. On the first start the miner writes `redpearl.toml` next to the exe and
   stops, telling you to fill in your wallet.
3. Open `redpearl.toml` in Notepad. Remove the `#` in front of the `wallet = ` line and paste your PRL wallet address
   between the quotes. Give the machine a `worker` name if you like. Save. (The miner asks you to accept `EULA.md` on
   the next start; you can also set `accept_eula = true` in the file yourself.)
4. Double-click `Start-redpearl-miner.bat` again. The miner runs a self-test on the GPU (about 10 seconds), connects to
   the pool, and prints a status line every 10 seconds (`status_seconds` in `[log]` changes that).

If Windows Defender stops the download or the exe, see "Windows Defender" below.

## What a healthy start looks like

From our own RX 9070 XT at a 288 W power limit (Windows); your numbers depend on the card and its settings.

```
redPeaRL 0.7.0-beta.6 x86-64-v2
log: C:\redPeaRL\miner.log (10 MB x 5 files)
GPU 0: AMD Radeon RX 9070 XT
config: C:\redPeaRL\redpearl.toml, 3 setting(s)
pool: connecting to stratum+ssl://prl-us.kryptex.network:8048, worker rig1
self-test: PASS (GPU 0, gfx1201)
shape 4096 x 65536 x 8192, batch 4
mining started - status every 10 s
Stratum: share accepted (57 ms)
redPeaRL 0.7.0-beta.6 | 144.6 TH/s | 144.3 avg 15m | A 70 R 0 | 502 GH/J 288 W 2.53 GHz 750 mV | 54C hot 85C mem 82C fan 1033 rpm
```

The status line, left to right: hashrate now and the average since start (up to the last 15 minutes), shares accepted
(A) and rejected (R) - and `RC n` after the pool connection was lost and re-made n times - efficiency in GH per joule,
board power, GPU clock and voltage, edge / hotspot / memory temperatures and fan speed. The hashrate is
pool-equivalent: what the pool credits matches it within normal luck (less the 1 % fee).

## redpearl.toml

All settings live in one file next to the exe. Command-line flags override it; `RP_*` environment variables (used in
containers) sit in between.

| key | meaning |
|---|---|
| `wallet` | your PRL address (required) |
| `worker` | the name shown at the pool for this machine |
| `pool` | `kryptex`, `herominers`, `luckypool`, `pearlfortune`, `rabidmining`, or a URL such as `"stratum+ssl://host"` |
| `region` | region of the preset (`us`, `eu`, ...) or `auto` = the fastest from here (default) |
| `port`, `password` | only for a URL pool, or a pool that asks for a password |
| `device` | GPU index to mine on, only with several GPUs (one GPU per process in this beta) |
| `[log] level` | `quiet`, `normal`, `verbose`, `debug` |
| `[log] file`, `file_size_mb`, `file_count` | the log file ring (default `miner.log` next to the miner, 10 MB x 5; `file = "off"` turns it off) |
| `[log] status_seconds` | seconds between the status lines in the console, 5-600 (default 10) |
| `stats` | anonymous usage stats, `true` (default) or `false` - see below |
| `accept_eula` | `true` once you have read EULA.md and agree; the miner does not run until then |
| `[advanced] batch` | attempts per GPU batch, 4-32; the default 4 is best on power-limited cards |
| `[advanced] shape` | the matrix shape `m,n,k`; leave it unless asked (since beta.6 the miner refuses an `n` that is not a multiple of 256) |

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
The fee is written into the log as it happens. It connects to Kryptex; if Kryptex cannot be reached three times in a
row, the fee mines on your own pool as a separate developer worker and tries Kryptex again an hour later. Your mining
never waits for the fee. There is no subscription
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
Before any error text or log lines leave the machine, the wallet, worker name, password, your user name, file and
folder paths and host names are removed from them. The receiving end discards the IP address; nothing is logged with
it. We keep the records for 180 days, then they are deleted automatically; we cannot delete single records earlier,
but with `stats = false` no new records are created and the old ones expire. Deleting `redpearl-stats-id.txt` gives
your installation a new id. Privacy and data requests: admin@redpearlminer.com. The stats tell us which cards and
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

Defender may flag mining software (for example as "Bearfoos"). If the SHA-256 of `redpearl-miner.exe` matches the
release page, it is a false positive. To run it:

1. Windows Security > Virus & threat protection > Manage settings > Exclusions > Add an exclusion > Folder, and
   choose the folder you unzipped redPeaRL into.
2. If Defender already removed the exe, restore it from Protection history, then add the exclusion.

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
- **"GPU stall: no batch finished in 90 s"** and the miner exits with code 4 - the card stopped answering (a hung
  driver, an unstable undervolt). `Start-redpearl-miner.bat` restarts the miner after 10 seconds, up to 50 times;
  if it keeps happening, put the card at stock. `stall_seconds` in `[advanced]` changes the limit, 0 switches it off.
- **Exit codes** the launcher reacts to: 0 stopped by you, 2 a configuration message (the launcher stops so you
  can read it), 4 GPU stall, 5 no usable GPU found (the launcher retries - a driver reset looks like this),
  6 a GPU error at start (self-test or qualification failed, out of GPU memory; retried as well), 7 a GPU error
  while mining (retried), 3 forced shutdown.
- **The window closed before you could read it** - start the miner through `Start-redpearl-miner.bat`, which keeps
  the window open; the exe itself also waits for Enter when it stops with an error and was started by a double-click.
- **The taskbar shows the Windows Terminal icon, not the pearl** - the launcher opens the classic console window so
  the icon and title are redPeaRL's; a terminal you opened yourself keeps its own icon.

## Logs and reporting

`miner.log` next to the miner (the exe on Windows, the binary on Linux) holds everything the console shows (10 MB x 5
files by default). When you report a problem, attach the log or its last 200 lines, your card model, your Adrenalin power/voltage settings, and what you
expected. support@redpearlminer.com.

## Linux

The Linux package (`redpearl-miner-<version>-linux-x64.tar.gz`) holds the same files as the Windows one: the binary,
the `kernels/` folder, `start-redpearl-miner.sh`, `redpearl.toml` and these documents. It is the build our test fleet
runs.

Requirements:

- x86-64, glibc 2.38 or newer: Ubuntu 24.04, Debian 13, Fedora 40 or newer. (Ubuntu 22.04 and HiveOS are too old.)
- The AMD ROCm HIP runtime, 6.4 or newer, with the amdgpu driver: `amdgpu-install --usecase=hip` (or `rocm`) from
  AMD's instructions for your distribution. The miner loads `libamdhip64` from `/opt/rocm/lib` at start; nothing else
  from ROCm is needed, the kernels ship precompiled.
- Your user in the `render` and `video` groups (log out and in after adding them).

Run it:

```
tar xzf redpearl-miner-<version>-linux-x64.tar.gz
cd redpearl-miner-<version>-linux-x64
./start-redpearl-miner.sh
```

The first start writes `redpearl.toml` and stops; fill in your wallet as on Windows, then start again. The script
restarts the miner after an error exit the same way the Windows launcher does and stops on Ctrl+C. As on Windows, the
miner writes `miner.log` next to the binary. One difference: board power, clock and temperatures come from the amdgpu
`hwmon` interface, which a container usually does not expose (then the line shows `power n/a`).

Running it on rented machines: the same binary ships as a container image; ask us.

## Credits and licence

redPeaRL is proprietary software; see EULA.md and LICENSE. It is built on tnn-miner (MIT); see THIRD_PARTY_NOTICES.md.
AMD and Radeon are trademarks of Advanced Micro Devices, Inc.
