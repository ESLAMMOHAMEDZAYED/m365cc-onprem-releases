# M365 Command Center: on-premise releases

This repository publishes M365 Command Center for on-premise installation on your own Windows server. It holds only the release files. The release history is in [RELEASES.md](RELEASES.md).

## Download

Get the setup program from [Releases](https://github.com/ESLAMMOHAMEDZAYED/m365cc-onprem-releases/releases). Each release has three files:

| File | What it is |
|---|---|
| `M365CommandCenter_OnPremise_64bit.exe` | The setup program. Run it as an administrator; running it again on an installed server upgrades it. |
| `SHA256SUMS.txt` | The SHA-256 of the setup program and of the main files inside it. |
| `latest.json` | The release file that installations read to show an update notice. |

## Check the download before running it

```powershell
(Get-FileHash .\M365CommandCenter_OnPremise_64bit.exe -Algorithm SHA256).Hash
```

The result must match the setup program's line in that release's `SHA256SUMS.txt` and in [RELEASES.md](RELEASES.md). If it doesn't, don't run it; download it again.

## Update notices

In **Platform Admin > Settings > Updates**, set the update address to:

```
https://m365cc.nexentrasolution.com/download/onprem/latest.json
```

Use this address, not GitHub's own `latest.json` link: GitHub sends its downloads on to another server, and the installation would then show a setup address that doesn't work.

The installation then says when a newer version is out. It never downloads or installs anything by itself: you download the new setup, check its SHA-256 and run it. An upgrade keeps your data.

The address follows the newest full release, so pre-releases don't show as update notices.
