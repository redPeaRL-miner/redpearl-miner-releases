# redPeaRL End User Licence Agreement

Version 1.1 (beta), effective 16 October 2026

This agreement is between you and **Red PeaRL Miner**, a sole proprietorship operating under an assumed business
name registered in North Carolina, United States ("we", "us"). "redPeaRL" is the name of our product. The agreement
covers the redPeaRL software, including the program redpearl-miner.exe, its GPU kernel files, launcher scripts,
configuration templates, documentation and any updates we provide (together, the "Software").

You accept this agreement by typing "I agree" when the Software asks you on its first start, by setting
`accept_eula = true` in its configuration file, or by installing, copying or running the Software. If you do not accept
it, do not install or run the Software.

You must be at least 18 years old, or the age of majority where you live if that is higher, to use the Software.

## 1. Licence

We grant you a personal, non-exclusive, non-transferable, revocable licence to install and run the Software on
computers you own or control, to mine the Pearl (PRL) cryptocurrency for your own account, for personal or commercial
purposes, for as long as you comply with this agreement.

The Software is licensed, not sold. We and our licensors keep all rights not expressly granted here.

## 2. Development fee

The Software is provided free of charge. In return, while it mines, it spends about **1 % of its mining time** mining
for our wallet (the "development fee"): about one GPU batch in every hundred is mined with our wallet address and a
worker name that begins with "fee" (for example "fee-kryptex"). The fee normally mines on the Kryptex pool over its own
connection. If Kryptex cannot be reached, the fee uses your pool connection and mines on the pool you configured, where
it appears as a separate worker under our wallet, not yours; it tries Kryptex again later. The rest of the mining time
is yours, and your own mining never waits for the fee connection.

The development fee runs on your hardware and uses your electricity; you accept that cost as the price of the
Software. You agree not to remove, disable, reduce or redirect the development fee, and not to use any tool, patch or
network method to do so.

## 3. Restrictions

You may not, and may not help anyone else to:

1. copy, distribute, sell, rent, lend, sublicense or publish the Software, except to make backup copies for your own
   use or as section 4 allows;
2. modify the Software or create works based on it;
3. reverse engineer, decompile or disassemble the Software, or extract its GPU kernels, except to the extent the law
   where you live allows this despite this restriction;
4. remove or change copyright, trademark or licence notices in the Software;
5. use the Software on computers you do not own or have no permission to use, or in any way that breaks the law.

## 4. Free download and sharing

The Software is offered as a free download, worldwide. You may share links to the official download page at
redpearlminer.com. Redistributing the Software files themselves (for example in mining OS images or rental
marketplaces) needs our written permission.

## 5. Third-party components and trademarks

The Software contains open-source components that are licensed to you under their own licences, listed in
THIRD_PARTY_NOTICES.md, which is part of the Software. Nothing in this agreement limits your rights under those licences
for those components.

Pearl and PRL are marks of their respective owners; we are not affiliated with or endorsed by Pearl Research Labs or
any mining pool. AMD and Radeon are trademarks of Advanced Micro Devices, Inc.

## 6. Use at your own risk

**You use the Software entirely at your own risk.**

Mining runs your graphics card at high load for long periods. You are responsible for:

1. your hardware: cooling, power supply, clock and voltage settings, and wear;
2. your electricity costs, including the share used by the development fee;
3. checking that mining, owning and receiving cryptocurrency is legal where you live, and for any taxes;
4. your wallet address, pool account and their security;
5. antivirus exclusions you choose to add for the Software.

Mining income depends on the network, the coin's price, the pool and luck. We make no promise that you will earn
anything or more than you spend.

## 7. Indemnity

If you use the Software on computers you do not own or are not permitted to use, or otherwise in breach of section 3 or
of the law, you will defend us and hold us harmless from any claim, loss or cost (including reasonable legal fees)
that arises from that use.

## 8. Data and network use

**Mining connections.** The Software connects to the mining pool you configure and, for the development fee, to the
pool described in section 2, and sends what mining needs: your wallet address, worker name, the Software's name and
version, and mining results. It opens a local statistics port (8989) only if you start it with the `--broadcast` or
`--mmpos` option.

**Usage statistics.** Unless you switch them off, the Software sends us pseudonymous usage statistics every five
minutes while it runs, and one error record after a fatal error. They are pseudonymous, not anonymous: the records
carry a random installation identifier that is created on the first run and stored next to the program, so records
from the same installation can be grouped. Each record contains the Software version, operating system version,
graphics card model, architecture and memory size, the settings in use (pool preset, batch, shape, log level, which
pool the development fee is using, whether this agreement has been accepted), hashrate, share counts, power, clock,
voltage and temperature readings, uptime, the self-test result, error counts and the last error message; an error
record adds the error text and the last lines of the log. Before anything is sent, the Software removes your wallet
address, worker name, pool password, Windows user name, file and folder paths and host names from all text. The
statistics never include your computer name, files or anything you typed. We do not record your IP address: the
receiving service discards it, and our hosting provider (Cloudflare) processes it only to deliver the request and keeps
no request logs on our behalf.

You can switch the statistics off at any time by setting `stats = false` in the configuration file (or the
`RP_STATS=false` environment variable); the Software states at every start whether they are on. Deleting the file
`redpearl-stats-id.txt` next to the program gives your installation a new identifier. We keep the statistics for
180 days and then delete them automatically; we cannot delete individual records earlier, but once you switch the
statistics off no new records are created and the existing ones expire. We use the statistics to see which hardware
and settings work and where the Software fails, and we may publish aggregated figures that cannot identify any
installation. The complete list of fields is in HELP.md. Questions about this data: admin@redpearlminer.com.

The Software sends no other data to us.

## 9. Updates and support

We may release updates but are not required to. An update may change or remove features. Updates are covered by this
agreement unless they come with a new one. We do not have to provide support.

## 10. No warranty

THE SOFTWARE IS PROVIDED "AS IS" AND "AS AVAILABLE", WITHOUT ANY WARRANTY OF ANY KIND, WHETHER EXPRESS OR IMPLIED,
INCLUDING WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, TITLE AND NON-INFRINGEMENT. WE DO NOT WARRANT
THAT THE SOFTWARE WILL BE ERROR-FREE, RUN WITHOUT INTERRUPTION, FIND ANY SHARES OR BLOCKS, OR WORK WITH ANY PARTICULAR
HARDWARE, DRIVER, POOL OR FUTURE VERSION OF THE PEARL PROTOCOL. SOME JURISDICTIONS DO NOT ALLOW THESE EXCLUSIONS, SO
SOME OF THEM MAY NOT APPLY TO YOU.

## 11. Limitation of liability

TO THE MAXIMUM EXTENT THE LAW THAT APPLIES TO YOU ALLOWS, WE, OUR AFFILIATES, LICENSORS AND CONTRIBUTORS ARE NOT LIABLE
TO YOU OR ANYONE ELSE FOR ANY INDIRECT, INCIDENTAL, SPECIAL, CONSEQUENTIAL, EXEMPLARY OR PUNITIVE DAMAGES OR LOSSES
ARISING FROM OR RELATED TO THE SOFTWARE OR THIS AGREEMENT, WHETHER BASED ON CONTRACT, TORT (INCLUDING NEGLIGENCE),
STRICT LIABILITY OR ANY OTHER THEORY, INCLUDING LOST PROFITS, LOST OR STOLEN CRYPTOCURRENCY, MISSED SHARES OR BLOCKS,
LOST DATA, DAMAGE TO HARDWARE, ELECTRICITY COSTS AND BUSINESS INTERRUPTION, EVEN IF WE WERE TOLD THEY WERE POSSIBLE.

TO THE SAME EXTENT, OUR TOTAL LIABILITY FOR ALL CLAIMS ARISING FROM OR RELATED TO THE SOFTWARE OR THIS AGREEMENT IS
LIMITED TO THE GREATER OF US$50 OR THE VALUE OF THE DEVELOPMENT FEE MINED FROM YOUR INSTALLATION IN THE 12 MONTHS
BEFORE THE CLAIM.

## 12. Rights the law does not let us take away

Nothing in this agreement excludes or limits our liability for death or personal injury caused by our negligence, for
fraud or fraudulent misrepresentation, or for anything else that cannot be excluded or limited under the law that
applies to you. If you are a consumer, you may have statutory rights that this agreement cannot change; those rights
are not affected.

## 13. Export and sanctions

The Software is subject to US export-control and sanctions laws, including the Export Administration Regulations and
the sanctions administered by the US Treasury's Office of Foreign Assets Control (OFAC). You may not download, use,
export or re-export the Software into a country or region under a comprehensive US embargo, or if you are on a US
government restricted-party list, or where any other export-control or sanctions law that applies to you prohibits it.
By downloading the Software you confirm that none of this applies to you.

## 14. Termination

This licence ends automatically if you break this agreement. You may end it at any time by deleting the Software. When
it ends you must stop using the Software and delete all copies. The last paragraph of section 2 and sections 3, 5, 7,
10, 11, 12, 13, 15 and 16 continue after it ends.

## 15. Governing law

This agreement is governed by the laws of the State of North Carolina and the federal laws of the United States,
without regard to conflict-of-law rules. The United Nations Convention on Contracts for the International Sale of Goods
does not apply. The state and federal courts located in North Carolina have exclusive jurisdiction, except that if you
are a consumer, mandatory consumer-protection law where you live still applies and you may bring a claim in your local
courts where that law gives you the right to.

## 16. General

This agreement is the whole agreement between you and us about the Software. If any part of it is found unenforceable,
the rest stays in force. If we do not enforce a right, we have not given it up. You may not transfer this agreement; we
may transfer it, including to a company we form to own and publish the Software, or to a successor of the Software. We
may update this agreement for future versions; the version that came with your copy applies to it.

## 17. Contact

Red PeaRL Miner, admin@redpearlminer.com (also for questions about the usage statistics).
