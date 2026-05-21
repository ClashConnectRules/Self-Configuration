<div align="center">

  # 🔮 Self-Configuration

  ### 个人代理工具配置文件集合
  **Personal Proxy Tool Configuration Collection**


  [![Clash](https://img.shields.io/badge/Clash-Meta-blue?style=flat-square&logo=clash)](Clash.yaml) [![Surge](https://img.shields.io/badge/Surge-5-orange?style=flat-square)](https://github.com/ClashConnectRules/Surge) [![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

  [**功能特性**](#-功能特性) · [**Clash**](#-clash-配置) · [**Surge**](#-surge-配置) · [**多订阅源**](#-多订阅源整合) · [**规则来源**](#-规则来源)

  🇨🇳 简体中文 | [🇺🇸 English](README.md)

</div>

---

> **订阅推荐**：[点击注册](https://hizrj.xyz/#/register?code=qpdHySHz) 获取订阅链接。

## ✨ 功能特性

- 🚀 **高性能** - 优化配置，速度至上的设计
- 🎯 **智能分流** - 智能流量拆分和地区选择
- 🛡️ **隐私保护** - 内置广告拦截和追踪防护
- 🌍 **全球流媒体** - Netflix、Disney+、YouTube、TikTok 解锁支持
- 🤖 **AI 服务** - ChatGPT、Claude、Gemini 专用路由
- 📱 **跨平台支持** - 支持 Clash、Surge、Stash 等客户端
- ⚡ **自动故障转移** - 自动 URL 测试选择最优节点
- 🔄 **便捷更新** - 集成订阅管理，轻松维护

---

## 📁 文件结构

```
Self-Configuration/
├── Clash.yaml      # Clash / Clash Meta 配置文件
└── README.md       # 文档

 🔶 Surge 配置 → https://github.com/ClashConnectRules/Surge
```

---

## 🔷 Clash 配置

> **适用客户端**: `Clash` · `Clash for Windows` · `Clash Meta` · `Stash` · `FlClash`

### ⚙️ 基础设置

| 配置项 | 值 | 说明 |
|:------:|:-----:|:-----------:|
| **混合端口** | `7890` | HTTP/SOCKS5 共用端口 |
| **控制端口** | `9090` | Web 面板控制端口 |
| **运行模式** | `Rule` | 规则路由模式 |
| **允许局域网** | `true` | 允许局域网连接 |
| **IPv6** | `true` | IPv6 支持已启用 |
| **增强模式** | `Fake-IP` | 性能增强模式 |

### 🌐 DNS 配置

| 类型 | 服务器 | 提供商 |
|:----:|:------:|:------:|
| **DoT** | `tls://223.5.5.5:853` | 阿里云 DNS |
| **DoT** | `tls://223.6.6.6:853` | 阿里云 DNS |
| **DoH** | `https://doh.pub/dns-query` | DNSPod |
| **DoH** | `https://dns.alidns.com/dns-query` | 阿里云 DNS |

### 🎯 策略组

#### 🚀 主选择组

| 策略组 | 类型 | 说明 |
|:------:|:----:|:-----------:|
| **节点选择** | `select` | 主入口，手动选择策略 |
| **手动切换** | `select` | 手动选择具体节点 |
| **自动选择** | `url-test` | 自动选择延迟最低节点 |

#### 🌍 地区节点组

| 策略组 | 筛选规则 | 地区 |
|:------:|:--------:|:------:|
| 🇭🇰 **Hong Kong** | `港\|HK\|Hong Kong` | 中国香港 |
| 🇯🇵 **Japan** | `日\|JP\|Japan` | 日本 |
| 🇺🇸 **United States** | `美\|US\|United States` | 美国 |
| 🇸🇬 **Singapore** | `新\|SG\|Singapore` | 新加坡 |
| 🇹🇼 **Taiwan** | `台\|TW\|Taiwan` | 中国台湾 |
| 🇰🇷 **Korea** | `韩\|KR\|Korea` | 韩国 |
| 🇬🇧 **United Kingdom** | `英\|UK\|United Kingdom` | 英国 |
| 🇩🇪 **Germany** | `德\|DE\|Germany` | 德国 |
| 🇫🇷 **France** | `法\|FR\|France` | 法国 |
| 🌍 **Other Regions** | *排除以上* | 其他地区 |

#### 📦 服务分流组

| 策略组 | 默认策略 | 用途 |
|:------:|:--------:|:-------:|
| 🤖 **AI服务** | 代理 | ChatGPT、Claude、Gemini |
| 📹 **YouTube** | 代理 | YouTube 视频 |
| 🔍 **谷歌服务** | 代理 | Google 搜索、地图 |
| 📧 **Google FCM** | 代理 | 推送通知 |
| ✈️ **Telegram** | 代理 | 即时通讯 |
| 🍎 **Apple服务** | 直连 | Apple 服务 |
| Ⓜ️ **微软服务** | 直连 | Microsoft 服务 |
| 🌍 **国外媒体** | 代理 | Netflix、Disney+ 等 |
| 🎯 **国内流量** | 直连 | 国内网站 |
| 🫧 **WeChat** | 直连 | 微信 |
| 🚫 **广告拦截** | 拒绝 | 广告过滤 |

### 📋 分流规则优先级

```
 1. 🚫 广告拦截      → 拒绝
 2. ⚡ 特殊规则      → 直连
 3. 🤖 AI 服务       → 代理
 4. 🎬 国际流媒体    → 代理
 5. 📺 国内媒体      → 直连
 6. 💬 通讯工具      → 代理
 7. 🔧 科技服务      → 自动
 8. 💰 加密货币      → 代理
 9. 🎮 游戏服务      → 自动
10. 🇨🇳 国内规则     → 直连
11. 🌏 GeoIP CN     → 直连
12. 🌐 兜底规则      → 代理
```

### 🚀 快速开始

#### 1. 导入配置

下载 [Clash.yaml](Clash.yaml) 并导入到客户端。

#### 2. 修改订阅地址

替换配置中的订阅地址：

```yaml
proxy-providers:
  all-proxies:
    type: http
    url: "https://你的订阅地址"
    interval: 3600
    path: ./providers/all-proxies.yaml
    health-check:
      enable: true
      interval: 600
      url: http://www.gstatic.com/generate_204
```

#### 3. 启用并选择节点

启用配置并选择你喜欢的节点。

---

## 🔶 Surge 配置

> **👉 Surge 配置已迁移至: [ClashConnectRules/Surge](https://github.com/ClashConnectRules/Surge)**

<div align="center">

### 🔶 [点击前往 Surge 仓库 →](https://github.com/ClashConnectRules/Surge)

[![Surge](https://img.shields.io/badge/Surge-5-orange?style=for-the-badge&logo=surge)](https://github.com/ClashConnectRules/Surge)

| 功能 | 描述 |
|:----:|:----:|
| 🚀 **智能分流** | 智能流量分流 |
| 🛡️ **广告拦截** | 多源广告规则 |
| 🌍 **流媒体解锁** | Netflix、Disney+、YouTube、TikTok |
| 🤖 **AI 服务** | ChatGPT、Claude、Gemini 专用路由 |
| 📱 **跨平台** | iOS & macOS 支持 |

</div>

---

## 🔗 多订阅源整合

当你有多个订阅源时，可以按以下方式整合：

### 1. 配置多个代理提供者

```yaml
proxy-providers:
  provider-1:
    type: http
    url: "https://订阅源1.com"
    interval: 3600
    path: ./providers/provider-1.yaml
    health-check:
      enable: true
      interval: 600
      url: http://www.gstatic.com/generate_204

  provider-2:
    type: http
    url: "https://订阅源2.com"
    interval: 3600
    path: ./providers/provider-2.yaml
    health-check:
      enable: true
      interval: 600
      url: http://www.gstatic.com/generate_204
```

### 2. 整合方式

#### 方式 A：策略组整合

```yaml
proxy-groups:
  # 从所有提供者中自动选择最快节点
  - name: "自动选择"
    type: url-test
    use:
      - provider-1
      - provider-2
    url: http://www.gstatic.com/generate_204
    interval: 300

  # 从所有提供者中手动选择
  - name: "手动选择"
    type: select
    use:
      - provider-1
      - provider-2

  # 地区分组（带过滤）
  - name: "香港节点"
    type: url-test
    use:
      - provider-1
      - provider-2
    filter: "港|HK|Hong Kong"
    url: http://www.gstatic.com/generate_204
    interval: 300
```

#### 方式 B：负载均衡

```yaml
proxy-groups:
  - name: "负载均衡"
    type: load-balance
    use:
      - provider-1
      - provider-2
    strategy: consistent-hashing  # 或 round-robin
    url: http://www.gstatic.com/generate_204
```

### 3. 关键参数说明

| 参数 | 说明 |
|:----:|:----:|
| **`use`** | 指定使用哪些代理提供者 |
| **`filter`** | 按节点名称过滤（支持正则表达式）|
| **`url-test`** | 自动测试延迟并选择最快节点 |
| **`load-balance`** | 负载均衡，分散流量到多个节点 |
| **`select`** | 手动选择模式 |

### 4. 最佳实践

> **💡 提示**: 遵循以下实践以获得最佳性能

- **按地区分组** - 使用 `filter` 将不同地区的节点分组
- **智能选择** - 使用 `url-test` 自动选择最快节点
- **定期更新** - 设置合适的 `interval` 更新订阅
- **健康检查** - 启用 `health-check` 过滤不可用节点
- **备份方案** - 配置多个订阅源提高可用性

---

## 📚 规则来源

| 来源 | 说明 | 作者 |
|:----:|:-----------:|:----:|
| **[dler-io/Rules]** | Clash 主要规则集 | @dler-io |
| **[blackmatrix7]** | 全平台规则集 | @blackmatrix7 |
| **[SukkaW/Surge]** | SKK 规则集 | @SukkaW |
| **[VirgilClyne]** | ASN 规则 | @VirgilClyne |
| **[Semporia]** | TikTok 解锁规则 | @Semporia |

---

## ⚠️ 重要提示

| 项目 | 说明 |
|:----:|:----:|
| 🔗 **订阅地址** | 使用前必须替换为自己的订阅地址 |
| 🔄 **规则更新** | 规则集自动更新周期为 7 天 |
| ⏱️ **节点测速** | 自动测速间隔 300 秒，超时 3 秒 |
| 🔐 **MITM 证书** | Surge 的 URL 重写功能需要安装证书 |
| 🔍 **节点过滤** | 自动过滤包含"流量/重置/到期"等关键词 |

---

## 📄 开源协议

本项目基于 [MIT License](LICENSE) 开源。

---

<div align="center">

  **Made with ❤️ for a better internet experience**

  [⬆ 返回顶部](#-self-configuration)

</div>
