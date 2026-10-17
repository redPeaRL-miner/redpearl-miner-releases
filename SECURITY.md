# Security

## Reporting a problem

Write to **support@redpearlminer.com** with what you found, how to reproduce it and the
build you used (the version line the miner prints at start, or BUILD.txt in the zip). We answer within two working days
and tell you when a fix ships. Please do not post an unfixed vulnerability in a public issue.

## Verifying a download

Every release lists the SHA-256 of the zip and of `redpearl-miner.exe`. Check the exe before running it:

```powershell
Get-FileHash .\redpearl-miner.exe -Algorithm SHA256
```

The only download sources are the Releases page of this repository and https://redpearlminer.com. We never send
binaries by direct message, and we never ask for wallet seed phrases, keys or passwords. Anyone doing either in our
name is not us.

## What the miner does on your machine

- Connects to the pool you configured, and to Kryptex for the 1 % developer fee.
- Posts pseudonymous usage stats to redpearlminer.com every five minutes unless `stats = false` is set.
- Writes `redpearl.toml` and `miner.log` next to the executable. Nothing elsewhere; no services, no scheduled tasks,
  no changes to GPU settings or Windows settings.
- Requires no administrator rights.

## Supported versions

Only the latest release receives fixes. Beta builds are superseded by the next beta.
