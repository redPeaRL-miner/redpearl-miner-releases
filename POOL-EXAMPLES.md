# redPeaRL - pool setup examples

Copy the block for your pool into `redpearl.toml` (next to `redpearl-miner.exe`), replace the wallet with your own
PRL address (it starts with `prl1p`), save, and start the miner. Only the `wallet`, `worker`, `pool` and `region` lines
matter here; the rest of the file keeps its defaults. The login form each pool wants (wallet/worker or wallet.worker)
is handled for you.

`redpearl-miner.exe --pool-test` times every region of every preset from your connection and exits, if you want to
pick a region by hand.

## Kryptex (PPS+, TLS, compressed proofs)

```toml
wallet = "prl1pyourwalletaddress..."
worker = "rig1"
pool   = "kryptex"
region = "auto"            # or us | eu | br | sg | hk | ru | ae
# password = "d=4194304"   # optional: a higher share difficulty for big workers (see below)
```

Kryptex share difficulty: the default is d=2097152 (one share per 9,000 TH of work; a 130 TH/s card finds one about
every 70 s), which is right for one card per worker. If one worker aggregates several PH/s (many cards behind a proxy),
raise it with the password line: d = hashrate in H/s x seconds between shares / 4,294,967,296 (Kryptex's formula).
Values below the default are ignored by the pool.

## HeroMiners (PROP, TLS)

```toml
wallet = "prl1pyourwalletaddress..."
worker = "rig1"
pool   = "herominers"
region = "auto"            # or us | us2 | us3 | ca | br | de | fr | es | fi | ru | tr | hk | kr | sg | au
```

## LuckyPool (PROP)

```toml
wallet = "prl1pyourwalletaddress..."
worker = "rig1"
pool   = "luckypool"
region = "auto"            # or us-east | us-west | us-central | us-ord | ca1 | ca2 | br | eu1 | eu2 | pl | tr | ru
                           #    | sg1 | sg2 | id | hk | in | jp | au
```

## PearlFortune

```toml
wallet = "prl1pyourwalletaddress..."
worker = "rig1"
pool   = "pearlfortune"
```

## Rabid Pool (PPLNS)

```toml
wallet = "prl1pyourwalletaddress..."
worker = "rig1"
pool   = "rabidmining"
```

Rabid Pool SOLO (the whole block to the finder) is the same pool on another port, given by address:

```toml
wallet = "prl1pyourwalletaddress..."
worker = "rig1"
pool   = "stratum+tcp://prl.rabidmining.com:9934"
```

## Any other Pearl stratum pool

```toml
wallet = "prl1pyourwalletaddress..."
worker = "rig1"
pool   = "stratum+ssl://pool.example.com"   # or stratum+tcp:// for a plain port
port   = 1234
# password = "x"                            # only if the pool asks for one
```

Tell us which pool you use (support@redpearlminer.com) and we will add it as a preset.

## Switching pools

Change the `pool` line and restart the miner. The developer fee always mines on Kryptex over its own connection; if
Kryptex cannot be reached it uses your pool briefly and goes back later (details in EULA.md, section 2).
