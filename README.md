# NetCP downloads

NetCP is a Windows desktop tool that captures Outlook, Office and Teams traffic and explains what went wrong: the likely root cause, who owns it (client, network, tenant admin or Microsoft) and what to do next. It opens HAR files and Fiddler `.saz` archives, and can hand redacted findings to GitHub Copilot through an MCP server.

## Download

Get the newest version from the **[latest release](../../releases/latest)**.

| File | What it is |
|---|---|
| `NetCP-Setup-<version>.exe` | The installer. Recommended. Installs for your user only (no administrator rights, no .NET install needed) and adds a Start-menu shortcut. Run it again later to upgrade or repair. |
| `netcp-app-<version>-win-x64.zip` | The desktop app, for people who prefer to unzip. |
| `netcp-cli-<version>-win-x64.zip` | The `netcp` command-line analyser. |
| `netcp-mcp-<version>-win-x64.zip` | The MCP server for GitHub Copilot. |
| `SHA256SUMS.txt` | Checksums for all of the above. |

Requires 64-bit Windows 10 or 11. Packet capture additionally needs [Npcap](https://npcap.com) and running NetCP as administrator; everything else works without.

## Check your download

```powershell
Get-FileHash .\NetCP-Setup-<version>.exe -Algorithm SHA256
```

The hash must match the line for that file in `SHA256SUMS.txt`.

## Windows SmartScreen

The files are not code-signed yet, so Windows SmartScreen says it protected your PC. Choose **More info**, then **Run anyway**. For a zip, right-click the file, choose Properties and tick **Unblock** before extracting. If your organisation blocks unsigned apps outright, ask your administrator to allow it.

## Privacy

NetCP runs on your machine and has no telemetry. The only request it makes by itself is an update check: when the app starts it asks GitHub whether a newer release exists, which shows GitHub your IP address and that you use NetCP. Untick **Check for updates** in the app to turn it off. Nothing is downloaded or installed automatically. Captures can contain passwords and tokens: use **Export HAR** and choose the shareable (redacted) option before sharing one. In shared output, passwords are always masked and user names keep only their first half.

## Support and feedback

NetCP is written and maintained by **abtyagi**. Write to **abtyagi@microsoft.com** with your NetCP version (the About button in the app, or `netcp about`), what you were doing, and the finding titles or session ids involved. Please do not attach a raw HAR or `.saz`.

## Licence

NetCP is released under the MIT licence; the text is shown in the installer.
