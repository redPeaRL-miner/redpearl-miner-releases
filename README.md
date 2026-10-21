# redPeaRL

**A Pearl (PRL) miner built for the AMD Radeon RX 9070 XT and RX 9060 XT.**

redPeaRL mines one coin on one GPU family and does it well: the kernels are hand-built for RDNA4 (gfx1201 / gfx1200)
and ship precompiled, so the miner starts hashing in seconds with no tuning sweep. It never changes your card's power,
clocks or fans; your Adrenalin profile is what it runs with.

**Public beta.** Windows 10/11 and Linux (x86-64). No NVIDIA or pre-RDNA4 support, by design.

Website: https://redpearlminer.com · Support: support@redpearlminer.com

## Download

The current build is on the [Releases](../../releases) page: a Windows zip and a Linux tar.gz, each with its SHA-256
next to it. Compare the hash with the one on the Releases page before you run the file:

```powershell
Get-FileHash .\redpearl-miner.exe -Algorithm SHA256
```

```sh
sha256sum redpearl-miner
```

## Quick start (Windows)

1. Unzip anywhere; keep the `kernels` folder next to `redpearl-miner.exe`.
2. Run `Start-redpearl-miner.bat` once. It writes `redpearl.toml` and stops.
3. Put your PRL wallet address into `redpearl.toml` and pick a pool (`pool = "kryptex"` is the default; HeroMiners,
   LuckyPool, PearlFortune and Rabid Pool are built in). `POOL-EXAMPLES.md` has a ready block for each.
4. Run it again. Type `I agree` when the licence is shown. It mines.

Linux: see `HELP.md`, section Linux. `HELP.md` in the package covers every setting.

## Pools

| Pool | Preset | Notes |
|---|---|---|
| Kryptex | `kryptex` | Default. TLS, regional endpoints, compressed proofs (GZIP v2), custom share difficulty via `password = "d=N"` |
| HeroMiners | `herominers` | TLS, regional endpoints |
| LuckyPool | `luckypool` | Regional endpoints |
| PearlFortune | `pearlfortune` | Plain TCP |
| Rabid Pool | `rabidmining` | PPLNS; SOLO via `stratum+tcp://prl.rabidmining.com:9934` |

Any other Pearl stratum pool works with a `stratum+ssl://` or `stratum+tcp://` URL.

## Fee and stats

- **Developer fee: 1 %**, mined to our own wallet on Kryptex over its own connection (on your pool as a separate worker
  if Kryptex is unreachable) and logged as it happens.
- **Usage stats** are on by default and pseudonymous: a random install id, card model, settings, hashrate, power,
  temperatures, share counts and error messages (paths, names and wallet removed). No IP is stored. `stats = false` in
  `redpearl.toml` turns them off. Full list: HELP.md and https://redpearlminer.com/privacy.

## Reporting problems

Open an [issue](../../issues) or write to support@redpearlminer.com. For a crash, attach the last 200 lines of
`miner.log` (next to the miner); it contains no wallet or personal data at the default log level.

## Licence and credits

redPeaRL is proprietary software of Red PeaRL Miner (Lincoln County, North Carolina, USA); see `EULA.md` and `LICENSE`
in the package. It is built from [tnn-miner](https://github.com/Tritonn204/tnn-miner) by Tritonn204 (MIT licence); the
copyright and permission notice are reproduced in `THIRD_PARTY_NOTICES.md`, with the other third-party licences.

Older release history: [CHANGELOG-archive.md](CHANGELOG-archive.md).
