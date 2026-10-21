# Security

## Reporting a problem

Write to **support@redpearlminer.com** with the subject "SECURITY", what you found, how to reproduce it and the
build you used (the version line the miner prints at start, or BUILD.txt in the package). We answer within two working days
and tell you when a fix ships. Please do not post an unfixed vulnerability in a public issue.

## Verifying a download

Every release lists the SHA-256 of each download and of the miner binary inside. Check it before running it:

```powershell
Get-FileHash .\redpearl-miner.exe -Algorithm SHA256
```

```sh
sha256sum redpearl-miner
```

The only download sources are the Releases page of this repository and https://redpearlminer.com. We never send
binaries by direct message, and we never ask for wallet seed phrases, keys or passwords. Anyone doing either in our
name is not us.

## What the miner does on your machine

- Connects to the pool you configured, and to Kryptex for the 1 % developer fee (or to your pool, as a separate
  developer worker, if Kryptex is unreachable).
- Posts pseudonymous usage stats to redpearlminer.com every five minutes unless `stats = false` is set.
- Writes `redpearl.toml`, `redpearl-stats-id.txt` and `miner.log` next to the executable,
  nothing elsewhere; no services, no scheduled tasks, no changes to GPU or system settings.
- Requires no administrator rights.

## Supported versions

Only the latest release receives fixes. Beta builds are superseded by the next beta.
