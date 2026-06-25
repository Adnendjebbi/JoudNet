# JoudNet
By Adnen Djebbi

A modern Windows desktop app for **DNS benchmarking**, **network diagnostics**, and day-to-day connectivity troubleshooting — built with WPF and a clean light/dark UI.

> **Note:** The repository folder is `dns3` and the .NET project/executable is still named `DnsSpeedTester`. Run commands from the `DnsSpeedTester` directory below.

## Highlights

- Benchmark **UDP** and **DNS-over-HTTPS (DoH)** resolvers side by side
- Rank servers by latency with a live dashboard chart
- Built-in **network toolkit** (ping, traceroute, MTR, port check, DNS leak test, bandwidth test, and more)
- **6 languages** with RTL support for Arabic
- Light and dark themes, responsive sidebar, export to CSV/JSON

## Screenshots

<img width="2559" height="1392" alt="image" src="https://github.com/user-attachments/assets/75ec9107-78de-41b7-a386-6aa94a9bb5ad" />
<img width="2555" height="1387" alt="image" src="https://github.com/user-attachments/assets/8c1d12d7-218f-4cf3-8d1a-41e95ca229eb" />


## Features

### DNS benchmarking

- Test curated public resolvers (Google, Cloudflare, Quad9, OpenDNS, AdGuard, and others)
- Enable/disable individual **UDP** and **DoH** servers before each run
- Add **custom DNS** entries; import servers from [public-dns.info](https://public-dns.info) by country
- Ranked results table with fastest-server highlight
- Latency overview chart on the dashboard
- Optional **set system DNS** to the fastest resolver (administrator rights required)
- Export results as **CSV** or **JSON**

### Network tools

| Category | Tools |
|----------|--------|
| DNS & resolution | DNS lookup, reverse DNS, propagation check, cache flush, DoH/DoT tester, DNS leak test, WHOIS, record compare |
| Connectivity | Ping, traceroute, MTR monitor, port checker, HTTP reachability, Wake-on-LAN |
| Local network | Network adapters, public IP info, subnet scanner, hosts file editor, proxy/VPN detection |
| Diagnostics | SSL certificate check, bandwidth test (speedometer), jitter monitor, MTU discovery, network reset assistant |

### App experience

- Dashboard with one-click benchmark and public IP copy
- Collapsible sidebar for narrower windows
- Configurable query timeout
- Persistent settings and custom server list

## Requirements

| | |
|---|---|
| **OS** | Windows 10 or 11 |
| **Runtime** | [.NET 8 Desktop Runtime](https://dotnet.microsoft.com/download/dotnet/8.0) (for published builds) |
| **Development** | [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0) |

## Quick start

### Run from source

```powershell
git clone <your-repo-url>
cd dns3/DnsSpeedTester
dotnet run
```

### Build a single-file executable

```powershell
cd DnsSpeedTester
dotnet publish -c Release
```

Output:

```text
DnsSpeedTester/bin/Release/net8.0-windows/win-x64/publish/DnsSpeedTester.exe
```

The Release profile is configured for a self-contained, single-file `win-x64` publish.

## Localization

Supported UI languages:

- English
- Français
- العربية (RTL)
- Español
- Deutsch
- Русский

Change language under **Settings**. Strings live in `DnsSpeedTester/Resources/Localization/`.

## How DNS testing works

Each enabled server is queried **4 times** for an `A` record of `example.com`. The app reports the average of successful responses. Default timeout is **3000 ms** (configurable in Settings).

## Data & settings

User data is stored under:

```text
%LocalAppData%\DnsSpeedTester\
├── dns_servers.json    # Custom DNS entries
└── settings.json       # Theme, language, timeout, disabled servers
```

## Project structure

```text
dns3/
└── DnsSpeedTester/
    ├── Controls/           # Charts, gauges, logo, shared UI
    ├── Converters/         # XAML value converters
    ├── Models/             # Domain models and navigation
    ├── Resources/
    │   ├── Localization/   # en, fr, ar, es, de, ru
    │   ├── Themes/         # Light and dark resource dictionaries
    │   └── Styles.xaml
    ├── Services/           # DNS testing, tools, storage, export, i18n
    ├── ViewModels/         # MVVM (CommunityToolkit.Mvvm)
    ├── Views/              # Tool pages and dialogs
    ├── MainWindow.xaml
    └── App.xaml
```

## Tech stack

- [.NET 8](https://dotnet.microsoft.com/) + [WPF](https://learn.microsoft.com/dotnet/desktop/wpf/)
- [ModernWpfUI](https://github.com/Kinnara/ModernWpf) — Fluent-style shell and controls
- [CommunityToolkit.Mvvm](https://learn.microsoft.com/dotnet/communitytoolkit/mvvm/) — MVVM helpers
- [DnsClient](https://github.com/MichaCo/DnsClient.NET) — UDP DNS queries

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/my-change`)
3. Commit your changes with a clear message
4. Open a pull request

Bug reports and feature requests are welcome via GitHub Issues.

## Roadmap ideas

- Rename assembly/project from `DnsSpeedTester` to `JoudNet`
- App icon and README screenshots
- Automated tests for core DNS and export logic

## License

This project is licensed under the **GNU General Public License v3.0** — see [LICENSE](LICENSE) for the full text.
