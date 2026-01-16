<div align="center">

  # 🔮 Self-Configuration

  ### Personal Proxy Tool Configuration Collection
  **个人代理工具配置文件集合**

  [![Clash](https://img.shields.io/badge/Clash-Meta-blue?style=flat-square&logo=clash)](Clash.yaml) [![Surge](https://img.shields.io/badge/Surge-5-orange?style=flat-square)](Surge.conf) [![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

  [**Features**](#-features) • [**Clash**](#-clash-configuration) • [**Surge**](#-surge-configuration) • [**Providers**](#-multiple-proxy-providers) • [**Sources**](#-rule-sources)

  [🇨🇳 简体中文](README_CN.md) | 🇺🇸 English

</div>

---

## ✨ Features

- 🚀 **High Performance** - Optimized configurations for maximum speed
- 🎯 **Smart Routing** - Intelligent traffic splitting and regional selection
- 🛡️ **Privacy Protection** - Built-in ad blocking and tracker prevention
- 🌍 **Global Streaming** - Netflix, Disney+, YouTube, TikTok unlock support
- 🤖 **AI Services** - Dedicated routing for ChatGPT, Claude, Gemini
- 📱 **Cross-Platform** - Support for Clash, Surge, Stash, and more
- ⚡ **Auto Failover** - Automatic URL testing for optimal node selection
- 🔄 **Easy Updates** - Integrated subscription management

---

## 📁 File Structure

```
Self-Configuration/
├── Clash.yaml      # Clash / Clash Meta configuration
├── Surge.conf      # Surge configuration
├── README.md       # English documentation
└── README_CN.md    # 中文文档
```

---

## 🔷 Clash Configuration

> **Compatible Clients**: `Clash` · `Clash for Windows` · `Clash Meta` · `Stash` · `FlClash`

### ⚙️ Basic Settings

| Setting | Value | Description |
|:-------:|:-----:|:-----------:|
| **Mixed Port** | `7890` | Shared HTTP/SOCKS5 port |
| **Controller** | `9090` | Web dashboard port |
| **Mode** | `Rule` | Rule-based routing mode |
| **Allow LAN** | `true` | Allow LAN connections |
| **IPv6** | `true` | IPv6 support enabled |
| **Enhanced Mode** | `Fake-IP` | Enhanced performance mode |

### 🌐 DNS Configuration

| Type | Server | Provider |
|:----:|:------:|:--------:|
| **DoT** | `tls://223.5.5.5:853` | Alibaba DNS |
| **DoT** | `tls://223.6.6.6:853` | Alibaba DNS |
| **DoH** | `https://doh.pub/dns-query` | DNSPod |
| **DoH** | `https://dns.alidns.com/dns-query` | Alibaba DNS |

### 🎯 Proxy Groups

#### 🚀 Main Selection Groups

| Group | Type | Description |
|:-----:|:----:|:-----------:|
| **节点选择** | `select` | Main entry point for policy selection |
| **手动切换** | `select` | Manual node selection |
| **自动选择** | `url-test` | Auto-select lowest latency node |

#### 🌍 Regional Groups

| Group | Filter Pattern | Region |
|:-----:|:--------------:|:------:|
| 🇭🇰 **Hong Kong** | `港\|HK\|Hong Kong` | Hong Kong SAR |
| 🇯🇵 **Japan** | `日\|JP\|Japan` | Japan |
| 🇺🇸 **United States** | `美\|US\|United States` | USA |
| 🇸🇬 **Singapore** | `新\|SG\|Singapore` | Singapore |
| 🇹🇼 **Taiwan** | `台\|TW\|Taiwan` | Taiwan |
| 🇰🇷 **Korea** | `韩\|KR\|Korea` | South Korea |
| 🇬🇧 **United Kingdom** | `英\|UK\|United Kingdom` | UK |
| 🇩🇪 **Germany** | `德\|DE\|Germany` | Germany |
| 🇫🇷 **France** | `法\|FR\|France` | France |
| 🌍 **Other Regions** | *Exclude above* | Other regions |

#### 📦 Service-Specific Groups

| Group | Default | Purpose |
|:-----:|:-------:|:-------:|
| 🤖 **AI服务** | Proxy | ChatGPT, Claude, Gemini |
| 📹 **YouTube** | Proxy | YouTube videos |
| 🔍 **谷歌服务** | Proxy | Google Search, Maps |
| 📧 **Google FCM** | Proxy | Push notifications |
| ✈️ **Telegram** | Proxy | Messaging service |
| 🍎 **Apple服务** | DIRECT | Apple services |
| Ⓜ️ **微软服务** | DIRECT | Microsoft services |
| 🌍 **国外媒体** | Proxy | Netflix, Disney+, etc. |
| 🎯 **国内流量** | DIRECT | Mainland China sites |
| 🫧 **WeChat** | DIRECT | WeChat messaging |
| 🚫 **广告拦截** | REJECT | Ad blocking |

### 📋 Rule Priority

```
 1. 🚫 Ad Blocking      → REJECT
 2. ⚡ Special Rules    → DIRECT
 3. 🤖 AI Services      → Proxy
 4. 🎬 Streaming        → Proxy
 5. 📺 CN Media         → DIRECT
 6. 💬 Messaging        → Proxy
 7. 🔧 Tech Services    → Auto
 8. 💰 Cryptocurrency   → Proxy
 9. 🎮 Gaming           → Auto
10. 🇨🇳 CN Rules        → DIRECT
11. 🌏 GeoIP CN         → DIRECT
12. 🌐 Final Rule       → Proxy
```

### 🚀 Quick Start

#### 1. Import Configuration

Download [Clash.yaml](Clash.yaml) and import it to your client.

#### 2. Update Subscription URL

Replace the subscription URL in the configuration:

```yaml
proxy-providers:
  all-proxies:
    type: http
    url: "https://your-subscription-url"
    interval: 3600
    path: ./providers/all-proxies.yaml
    health-check:
      enable: true
      interval: 600
      url: http://www.gstatic.com/generate_204
```

#### 3. Enable and Select Nodes

Enable the configuration and select your preferred nodes.

---

## 🔗 Multiple Proxy Providers

When you have multiple subscription sources, you can integrate them as follows:

### 1. Configure Multiple Providers

```yaml
proxy-providers:
  provider-1:
    type: http
    url: "https://subscription-1.com"
    interval: 3600
    path: ./providers/provider-1.yaml
    health-check:
      enable: true
      interval: 600
      url: http://www.gstatic.com/generate_204

  provider-2:
    type: http
    url: "https://subscription-2.com"
    interval: 3600
    path: ./providers/provider-2.yaml
    health-check:
      enable: true
      interval: 600
      url: http://www.gstatic.com/generate_204
```

### 2. Integration Methods

#### Method A: Proxy Groups

```yaml
proxy-groups:
  # Auto-select fastest node from all providers
  - name: "Auto"
    type: url-test
    use:
      - provider-1
      - provider-2
    url: http://www.gstatic.com/generate_204
    interval: 300

  # Manual selection from all providers
  - name: "Manual"
    type: select
    use:
      - provider-1
      - provider-2

  # Regional groups with filter
  - name: "Hong Kong"
    type: url-test
    use:
      - provider-1
      - provider-2
    filter: "港|HK|Hong Kong"
    url: http://www.gstatic.com/generate_204
    interval: 300
```

#### Method B: Load Balancing

```yaml
proxy-groups:
  - name: "Load-Balance"
    type: load-balance
    use:
      - provider-1
      - provider-2
    strategy: consistent-hashing  # or round-robin
    url: http://www.gstatic.com/generate_204
```

### 3. Key Parameters

| Parameter | Description |
|:---------:|:-----------:|
| **`use`** | Specify which proxy providers to use |
| **`filter`** | Filter nodes by name (supports regex) |
| **`url-test`** | Auto-test latency and select fastest |
| **`load-balance`** | Distribute traffic across nodes |
| **`select`** | Manual selection mode |

### 4. Best Practices

> **💡 Tip**: Follow these practices for optimal performance

- **Regional Grouping** - Use `filter` to group nodes by region
- **Smart Selection** - Use `url-test` for automatic optimal node selection
- **Regular Updates** - Set appropriate `interval` for subscription updates
- **Health Check** - Enable `health-check` to filter unavailable nodes
- **Backup Sources** - Configure multiple subscriptions for higher availability

---

## 🔶 Surge Configuration

> **Compatible Clients**: `Surge for iOS` · `Surge for macOS`

### ⚙️ Basic Settings

| Setting | Value | Description |
|:-------:|:-----:|:-----------:|
| **HTTP Port** | `6152` | Wi-Fi sharing port |
| **SOCKS5 Port** | `6153` | Wi-Fi sharing port |
| **Controller** | `6160` | API control port |
| **Dashboard** | `6166` | Web dashboard port |
| **IPv6** | `false` | Disabled by default |

### 🌐 DNS Configuration

| Type | Server | Provider |
|:----:|:------:|:--------:|
| **System DNS** | `223.5.5.5`, `223.6.6.6`, `119.29.29.29` | China DNS |
| **DoH** | `https://doh.pub/dns-query` | DNSPod |
| **DoH** | `https://dns.alidns.com/dns-query` | Alibaba DNS |
| **Hijack** | `8.8.8.8:53`, `8.8.4.4:53` | Google DNS |

### 🎯 Proxy Groups

#### 🚀 Core Groups

| Group | Type | Description |
|:-----:|:----:|:-----------:|
| **NoAuto** | `select` | Main entry point |
| **Automatic** | `select` | Regional selection |
| **AllServer** | `select` | All subscription nodes |
| **Proxy** | `select` | Proxy policy |

#### 🌍 Regional Groups (Auto URL-Test)

| Group | Filter Pattern | Interval |
|:-----:|:--------------:|:--------:|
| **Hong Kong** | `港\|🇭🇰\|香港\|HK\|Hong` | 300s |
| **Taiwan** | `台\|🇹🇼\|台湾\|TW\|Tai` | 300s |
| **Japan** | `日\|🇯🇵\|日本\|JP\|Japan` | 300s |
| **Singapore** | `坡\|🇸🇬\|新加坡\|狮城\|SG` | 300s |
| **United States** | `美\|🇺🇸\|美国\|US\|States` | 300s |
| **United Kingdom** | `🇬🇧\|英国\|UK` | 300s |
| **Korea** | `韩\|韩国\|Korea\|KR\|🇰🇷` | 300s |
| **Other** | *Exclude above* | 300s |

#### 📦 Service-Specific Groups

| Group | Default | Purpose |
|:-----:|:-------:|:-------:|
| **AI** | Automatic | ChatGPT, Claude, Gemini, Bing |
| **YouTube** | Automatic | YouTube videos |
| **Netflix** | Hong Kong | Netflix streaming |
| **Disney+** | Hong Kong | Disney+ streaming |
| **TikTok** | Taiwan | TikTok unlock |
| **Telegram** | Automatic | Messaging |
| **X** | Automatic | Twitter/X |
| **Microsoft** | Mainland | Microsoft services |
| **OneDrive** | Mainland | Cloud storage |
| **Apple** | Mainland | Apple services |
| **WeChat** | Mainland | WeChat |
| **Bilibili** | Mainland | Bilibili (HK/TW unlock) |
| **Speedtest** | Mainland | Speed test |

### 📋 Rule Priority

```
 1. 🔧 Unbreak Rules    → DIRECT
 2. ✏️ Manual Rules     → Custom
 3. 🚫 Ad Blocking      → REJECT
 4. 🔒 Privacy          → REJECT
 5. 📱 CN Apps          → DIRECT
 6. 🍎 Apple Services   → DIRECT
 7. 🤖 AI Services      → Automatic
 8. 🎬 Streaming        → Regional
 9. 🌏 Regional Unlock  → Regional
10. 💬 Social Media     → Automatic
11. 🔧 Other Global     → Auto
12. 🇨🇳 CN Rules        → DIRECT
13. 🌐 Global Rules     → Auto
14. 🏠 LAN              → DIRECT
15. 🎯 Final Rule       → NoAuto
```

### ✨ Special Features

#### 🔄 URL Rewrite

| Original | Target | Type |
|:--------:|:------:|:----:|
| `google.cn` | `google.com` | 302 Redirect |
| `maps.google.cn` | `maps.google.com` | 302 Redirect |
| `taobao.com` | HTTPS | Force upgrade |
| `jd.com` | HTTPS | Force upgrade |

#### 🏠 Host Mapping

| Service | DNS Server | Description |
|:-------:|:----------:|:-----------:|
| **Taobao/Tmall/Alipay** | `223.5.5.5` | Alibaba services |
| **JD/QQ/WeChat** | `119.28.28.28` | Tencent services |
| **Bilibili/NetEase** | `119.29.29.29` | Entertainment |
| **Router Admin** | System DNS | Local devices |

### 🚀 Quick Start

#### 1. Import Configuration

Download [Surge.conf](Surge.conf) and import it to Surge.

#### 2. Update Subscription URL

```
AllServer = select, ..., policy-path=https://your-subscription-url
```

#### 3. Configure MITM Certificate

Install and trust the MITM certificate for URL rewrite functionality.

#### 4. Enable Configuration

Enable the configuration in Surge.

---

## 📚 Rule Sources

| Source | Description | Provider |
|:------:|:-----------:|:--------:|
| **[dler-io/Rules]** | Main Clash ruleset | @dler-io |
| **[blackmatrix7]** | Cross-platform rules | @blackmatrix7 |
| **[SukkaW/Surge]** | SKK ruleset | @SukkaW |
| **[VirgilClyne]** | ASN rules | @VirgilClyne |
| **[Semporia]** | TikTok unlock | @Semporia |

---

## ⚠️ Important Notes

| Item | Description |
|:----:|:-----------:|
| 🔗 **Subscription** | Must replace with your own subscription URL |
| 🔄 **Rule Update** | Rules auto-update every 7 days |
| ⏱️ **Speed Test** | 300s interval, 3s timeout |
| 🔐 **MITM Certificate** | Required for Surge URL rewrite |
| 🔍 **Node Filter** | Auto-filter nodes with "traffic/reset/expire" keywords |

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

<div align="center">

  **Made with ❤️ for a better internet experience**

  [⬆ Back to Top](#-self-configuration)

</div>
