> [!WARNING]
> 由于本项目已趋于稳定甚至开始变得无聊，部分现有代码和功能已成为负担，故迁移代码到仓库 [👉sinspired/subs-check-pro](https://github.com/sinspired/subs-check-pro)，随缘更新。本仓库归档，目前功能稳定，可继续使用。

<!-- 项目logo -->
<p align="center">
  <img src="doc/logo/logo.png" alt="Project Logo" width="200"/>
</p>
<h1 align="center">Subs-Check⁺ 性能版</h1>
<p align="center" color="#6a737d">
High-performance proxy subscription checker.
</p>
<p align="center">
<a href="https://github.com/sinspired/subs-check/releases"><img src="https://img.shields.io/github/v/release/sinspired/subs-check?logo=github&include_prereleases"/></a>
<a href="https://hub.docker.com/r/sinspired/subs-check"><img src="https://img.shields.io/docker/pulls/sinspired/subs-check?logo=docker" /></a>
<a href="https://ghcr.io/sinspired/subs-check"><img src="https://img.shields.io/badge/ghcr.io-available-blue?logo=github"/></a>
<a href="https://github.com/sinspired/SubsCheck-Win-GUI"><img alt="GitHub Release" src="https://img.shields.io/github/v/release/sinspired/SubsCheck-Win-GUI?display_name=release&style=social&logo=github&label=Windows%E5%9B%BE%E5%BD%A2%E7%95%8C%E9%9D%A2"/></a>
</p>

# 🚀 高性能代理检测工具

**测活、测速、媒体解锁**，代理检测工具，支持 `100-1000` 高并发低占用运行，检测结果更准确。全新设计，适配PC和手机设备的现代 WebUI 配置管理界面，自动生成 `mihomo` 和 `singbox` 订阅，集成 `sub-store` 前端和后端，消除使用门槛，支持一键复制分享；支持自动无缝版本更新。

## ✨ 新增功能

- [x] ⚡ [**自适应流水线高并发模式**](#1-测活-测速-媒体检测分阶段流水线自适应高并发) ，减少无谓的生命浪费
- [x] 🗺️ [**增强位置标签**](#2-增强位置标签)，节点位置更准确，媒体解锁状态更清晰
- [x] 🔋 [**优化内存占用**](#3-优化内存)  
- [x] 🎲 [**智能节点乱序**](#4-智能节点乱序减少节点被测速-测死-的概率)，减少节点测死风险
- [x] 🕒 [**上次成功和历次检测可用节点保存与加载**](#5-保存并加载-历次-检测可用节点)  
- [x] 🚦 [**自动检测系统代理、GitHub 代理并设置**](#-优化系统代理和-github-代理设置可选)
- [x] 💻 支持 `Windows` `Linux` `macOS` **多平台部署**
- [x] 🐳 支持 `docker` 部署
- [x] 🪟 Windows 可搭配 [Subs-Check_GUI程序](https://github.com/sinspired/SubsCheck-Win-GUI)，包含多项优化
- [x] 🎁 [自动检查更新，无缝升级新版本](#6-自动检查更新无缝升级新版本)
- [x] 📱 全新设计的 [WebUI管理界面](#-重新设计的-webui管理界面)，优化小屏设备访问体验
- [x] 📦 [自动生成开箱即用的singbox配置](#-sing-box-订阅带分流规则)，支持 `WebUI` 一键复制订阅
- [x] ✏️ 升级配置编辑器，支持根据 `config.yaml` 自动补全。
- [x] 🧶 编辑器自动高亮设置项名称
- [x] 🔒 [优化文件分享,提升安全性](#-内置文件服务)，支持 `分享码` 分享文件
- [x] 🧩 集成 `sub-store` 前端，消除使用门槛
- [x] 🗄️ WebUI 一键管理 `sub-store`
- [x] 6️⃣ 支持 `IPv6` 代理节点
- [x] 📊 [统计订阅链接总数、可用节点数量、成功率](#7-统计订阅链接总数可用节点成功率)
- [x] 🔗 适配多种非标订阅格式，提高获取订阅成功率
- [x] 📣 增加消息通知范围：`节点状态`、`版本更新`、`Geo地理数据库更新`
- [x] ♾️ 支持检测百万-千万量级的节点库，依然保持较低的内存占用
- [x] 📡 支持检测 `isp` 类型，`原生/广播IP`，住宅/机房等，显示为 `[原生|住宅]`
- [ ] 🚧 本项目现接受 issure 反馈

### 📖 教程

- 🐳 教程：[Docker 部署](#-docker-运行)
  - [🔁 使用 WatchTowe 自动更新 docker 镜像并通知](#-使用-watchtower-自动更新-docker-镜像并通知)
- 📘 教程：[随时随地管理 subs-check 检测与订阅](#️-cloudflare-tunnel隧道映射外网访问)
  - [🔀 使用 `路径` 映射端口](#-使用路径映射端口)
  - [🌐 使用 `子域` 映射](#-使用子域映射端口)
- 📗 教程：[设置 `节点状态`、`版本更新`，`Geo地理数据库` 通知](#-通知渠道配置可选)
- 📙 教程：[订阅使用方法](#-订阅使用方法)
  - [🚀 通用订阅 (不带分流规则)](#-通用订阅-不带分流规则)
  - [🚀 Mihomo/Clash 订阅（带分流规则）](#-mihomoclash-订阅带分流规则)
  - [🚀 sing-box 订阅（带分流规则）](#-sing-box-订阅带分流规则)
- 📕 教程：[内置文件服务](#-内置文件服务)
  - [🔐 使用 `分享码` 分享)](#-使用-分享码-分享)
  - [🗂️ 无密码保护分享](#️-无密码保护分享)

### 📣 使用交流，功能讨论，issure 反馈，新版本通知

- > Telegram 群组：[subs-check性能版](https://t.me/subs_check_pro)⁠
- > Telegram 频道：[关注频道](https://t.me/sinspired_ai)⁠

> [!TIP]
>
> 功能更新频繁，请务必查看最新的 [配置文件示例](https://github.com/sinspired/subs-check/blob/main/config/config.yaml.example) 以获取最新功能支持。  

> [!NOTE]
> 查看新增功能及设置方法： [新增功能和性能优化详情](#-新增功能和性能优化详情)

## 📸 预览

![preview](./doc/images/preview.png)  
![result](./doc/images/results.png)

### ✨ 重新设计的 WebUI管理界面

![login](./doc/images/login-white.png)
![WebUI](./doc/images/WebUI.png)

### ⚡新增分享菜单项，自动生成singbox订阅，支持一键分享

|                                  |                                        |                                        |
| -------------------------------- | -------------------------------------- | -------------------------------------- |
|![sub-store](./doc/images/sub-store.png) | ![shareMenu](./doc/images/share-menu.png)  |  ![singbox](./doc/images/sing-box.png)  |

|                                  |                                        |
| -------------------------------- | -------------------------------------- |
| ![tgram](./doc/images/tgram.png) | ![dingtalk](./doc/images/dingtalk.png) |

## 🛠️ 部署与使用

> 首次运行会在当前目录生成默认配置文件。

### 📦 二进制文件运行

下载 [Releases](https://github.com/sinspired/subs-check/releases) 中适合的版本，解压后直接运行即可。

```powershell
.\subs-check.exe -f ./config/config.yaml
```

### 🖥️ 源码运行

```bash
go run . -f ./config/config.yaml
```

### 🐳 Docker 运行

> **⚠️ 注意：**  
>
> - 限制内存请使用 `--memory="500m"`。  
> - 可通过环境变量 `API_KEY` 设置 Web 控制面板的 API Key。

```bash
# 基础运行
docker run -d \
  --name subs-check \
  -p 8299:8299 \
  -p 8199:8199 \
  -v ./config:/app/config \
  -v ./output:/app/output \
  --restart always \
  ghcr.io/sinspired/subs-check:latest

# 使用代理运行
docker run -d \
  --name subs-check \
  -p 8299:8299 \
  -p 8199:8199 \
  -e HTTP_PROXY=http://192.168.1.1:7890 \
  -e HTTPS_PROXY=http://192.168.1.1:7890 \
  -v ./config:/app/config \
  -v ./output:/app/output \
  --restart always \
  ghcr.io/sinspired/subs-check:latest
```

### 📜 Docker-Compose

```yaml
version: "3"
services:
  subs-check:
    image: ghcr.io/sinspired/subs-check:latest
    container_name: subs-check
    volumes:
      - ./config:/app/config
      - ./output:/app/output
    ports:
      - "8299:8299"
      - "8199:8199"
    environment:
      - TZ=Asia/Shanghai
      # - HTTP_PROXY=http://192.168.1.1:7890
      # - HTTPS_PROXY=http://192.168.1.1:7890
      # - API_KEY=subs-check
    restart: always
    network_mode: bridge
```

### 🔁 使用 WatchTower 自动更新 docker 镜像并通知

<details>
  <summary>展开查看</summary>
#### 基础命令，每小时检查更新

```bash
docker run -d \
  --name watchtower \
  -e WATCHTOWER_POLL_INTERVAL=3600 \
  -v /var/run/docker.sock:/var/run/docker.sock \
  containrrr/watchtower subs-check

```

#### 配置`shuttr` 格式的 telegram 通知

```bash
docker run -d \
  --name watchtower \
  -e WATCHTOWER_NOTIFICATIONS=shoutrrr \
  -e WATCHTOWER_NOTIFICATION_URL=telegram://<bot_token>@telegram?channels=<chat_id> \
  -v /var/run/docker.sock:/var/run/docker.sock \
  containrrr/watchtower subs-check

```

#### 通过 `webhook` 使用 `apprise` 通知

```bash
docker run -d \
  --name watchtower \
  --restart always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -e WATCHTOWER_POLL_INTERVAL=3600 \
  -e WATCHTOWER_NOTIFICATIONS=shoutrrr \
  -e WATCHTOWER_NOTIFICATION_URL="webhook://<server-ip>:8000/notify?urls=telegram://<bot_token>@telegram?chat_id=<chat_id>,mailto://user:pass@smtp.example.com/?from=watchtower@example.com&to=you@example.com" \
  containrrr/watchtower subs-check
```

</details>

### 🪜 优化系统代理和 GitHub 代理设置（可选）

> 新增: 自动检测并设置系统代理;自动检测筛选 GitHub 代理并设置
<details>
  <summary>展开查看</summary>
  
```yaml
# 新增设置项
# 优先级 1.system-proxy;2.github-proxy;3.ghproxy-group
# 即使未设置,也会检测常见端口(v2ray\clash)的系统代理自动设置

# 系统代理设置: 适用于拉取代理、消息推送、文件上传等等。
# 写法跟环境变量一样，修改需重启生效
# system-proxy: "http://username:password@192.168.1.1:7890"
# system-proxy: "socks5://username:password@192.168.1.1:7890"
system-proxy: ""
# Github 代理：获取订阅使用
# github-proxy: "https://ghfast.top/"
github-proxy: ""
# GitHub 代理列表：程序会自动筛选可用的 GitHub 代理
ghproxy-group:
# - https://ghp.yeye.f5.si/
# - https://git.llvho.com/
# - https://hub.885666.xyz/
# - https://p.jackyu.cn/
# - https://github.cnxiaobai.com/
```

如果拉取非Github订阅速度慢，可使用通用的 HTTP_PROXY HTTPS_PROXY 环境变量加快速度；此变量不会影响节点测试速度

```bash
# HTTP 代理示例
export HTTP_PROXY=http://username:password@192.168.1.1:7890
export HTTPS_PROXY=http://username:password@192.168.1.1:7890

# SOCKS5 代理示例
export HTTP_PROXY=socks5://username:password@192.168.1.1:7890
export HTTPS_PROXY=socks5://username:password@192.168.1.1:7890

# SOCKS5H 代理示例
export HTTP_PROXY=socks5h://username:password@192.168.1.1:7890
export HTTPS_PROXY=socks5h://username:password@192.168.1.1:7890
```

如果想加速github的链接，可使用网上公开的github proxy，或者使用下方自建测速地址处的worker.js自建加速

```yaml
# Github Proxy，获取订阅使用，结尾要带的 /
# github-proxy: "https://ghfast.top/"
github-proxy: "https://custom-domain/raw/"
```

</details>

### 🌐 自建测速地址（可选）

<details>
  <summary>展开查看</summary>

> **⚠️ 注意：** 避免使用 Speedtest 或 Cloudflare 下载链接，因为部分节点会屏蔽测速网站。

1. 将 [worker.js](./doc/cloudflare/worker.js) 部署到 Cloudflare Workers。
2. 绑定自定义域名（避免被节点屏蔽）。
3. 在配置文件中设置 `speed-test-url` 为你的 Workers 地址：

```yaml
# 100MB
speed-test-url: https://custom-domain/speedtest?bytes=104857600
# 1GB
speed-test-url: https://custom-domain/speedtest?bytes=1073741824
```

</details>

## ⚙️ Cloudflare Tunnel（隧道映射）外网访问

> WebUI 经过全新设计，添加了 **logo 图标** 等资源，本地化了所有用到的依赖，因此需要比原版额外增加一个 **`static` 资源路径**。

### 🚀 简易操作步骤

1. 🔑 登录 **Cloudflare (CF)**，左侧菜单栏点击 **`Zero Trust`**  
2. 🌐 在新页面，左侧菜单栏点击 **`网络` → `Tunnels` → `创建隧道` → `选择 Cloudflared`**  
3. 🛠️ 按提示操作：  
   - `为隧道命名`  
   - `安装并运行连接器`  
   - `路由隧道`  
4. ✅ 创建完成后，在 **`Tunnels`** 页面会出现你创建的隧道  
   - 点击 **隧道名称** → **编辑**  
5. ➕ 在隧道详情页点击 **`已发布应用程序路由` → `添加已发布应用程序路由`**  
6. 🌍 配置 **主机名** 和 **服务**：  
   - 示例：`sub.你的域名.com/path`  
     - `sub` → (可选) 子域  
     - `你的域名` → 域名  
     - `path` → (可选) 路径  
   - 服务类型 → 选择 **`http`**  
   - URL → 输入 `localhost:8199` 或 `localhost:8299`  

### 📒 需添加的路由条目

> [!TIP]
> 本项目需要 `share-password` 才能访问 `./output`，可放心设置，谨慎分享。

#### 🔀 使用路径映射端口
  
| 🌐 外网访问地址                    | 🎯 本地服务地址   | 💡 用途说明    |
|-----------------------------------|------------------|-----------------|
| `sub.你的域名.com/admin`           | `localhost:8199`  | 配置管理主页    |
| `sub.你的域名.com/static`          | `localhost:8199`  | ico,js,css文件 |
| `sub.你的域名.com/api`             | `localhost:8199`  | 软件运行状态    |
| `sub_store_for_subs_check.你的域名.com/*`| `localhost:8299`| ❗必须    |
| `sub.你的域名.com/{sub-store-path}`| `localhost:8299`  | sub-store后端  |
| `sub.你的域名.com/share`           | `localhost:8299`  | sub-store分享  |
| ⚠️ 如无暴露需求，以下不建议设置 | | |
| `sub.你的域名.com/sub`             | `localhost:8199`  | 🔒分享码分享     |
| `sub.你的域名.com/more`            | `localhost:8199`  | 🔓无密码分享     |

#### 🌐 使用子域映射端口

> [!WARNING]
> `sub_store_for_subs_check` 为订阅管理保留子域，请勿修改！

| 🏷️ 外网访问地址                                    | 💻 本地服务地址      | 💡 用途说明         |
|---------------------------------------------------|----------------------|--------------------|
| `sub.你的域名.com/*`                               | `localhost:8199`     | 🔒 subs-check |
| `sub_store_for_subs_check.你的域名.com/*`          | `localhost:8299`     | 🔒 sub-store  |

### 🎉 使用方法

打开浏览器访问 👉 sub.你的域名.com/admin -> 输入 apiKey -> 🎇 Enjoy!

## 🔔 通知渠道配置（可选）

> **📦 支持 100+ 通知渠道**，通过 [Apprise](https://github.com/caronc/apprise) 发送通知。

### [📖 查看中文文档](https://sinspired.github.io/apprise_vercel/)

### 🌐 Vercel 部署

1. 点击[**此处**](https://vercel.com/new/clone?repository-url=https://github.com/sinspired/apprise_vercel)部署 Apprise。
2. 部署后获取 API 链接，如 `https://projectName.vercel.app/notify`。
3. 建议为 Vercel 项目设置自定义域名（国内访问 Vercel 可能受限）。

### 🐳 Docker 部署

> **⚠️ 注意：** 不支持 arm/v7。

```bash
# 基础运行
docker run --name apprise -p 8000:8000 --restart always -d caronc/apprise:latest

# 使用代理运行
docker run --name apprise \
  -p 8000:8000 \
  -e HTTP_PROXY=http://192.168.1.1:7890 \
  -e HTTPS_PROXY=http://192.168.1.1:7890 \
  --restart always \
  -d caronc/apprise:latest
```

<details>
  <summary>配置方法</summary>
### 📝 配置文件中配置通知

```yaml
# 配置通知渠道，将自动发送检测结果通知，新版本通知
# 复制 https://vercel.com/new/clone?repository-url=https://github.com/sinspired/apprise_vercel 到浏览器
# 按提示部署，建议为 Vercel 项目设置自定义域名（国内访问 Vercel 可能受限）。
# 填写搭建的apprise API server 地址
# https://notify.xxxx.us.kg/notify
apprise-api-server: ""
# 通知渠道
# 支持100+ 个通知渠道，详细格式请参照 https://github.com/caronc/apprise
# 格式参考：
# telegram格式：tgram://{bot_token}/{chat_id}
# 钉钉格式：dingtalk://{Secret}@{ApiKey}
# QQ邮箱：mailto://QQ号:邮箱授权码@qq.com
# 邮箱授权码：设置-账号-POP3/IMAP/SMTP/Exchange/CardDAV/CalDAV服务-开通-继续获取授权码
recipient-url:
  # - tgram://xxxxxx/-1002149239223
  # - dingtalk://xxxxxx@xxxxxxx
  # - mailto://xxxxx:xxxxxx@qq.com

# 自定义通知标题
notify-title: "🔔 节点状态更新"
```

</details>

## 💾 保存方法配置

> **⚠️ 注意：** 选择保存方法时，请更改 `save-method` 配置。

- **本地保存**：保存到 `./output` 文件夹。
- **R2**：保存到 Cloudflare R2 [配置方法](./doc/r2.md)。
- **Gist**：保存到 GitHub Gist [配置方法](./doc/gist.md)。
- **WebDAV**：保存到 WebDAV 服务器 [配置方法](./doc/webdav.md)。
- **S3**：保存到 S3 对象存储。

## 📲 订阅使用方法

> **💡 提示：** 内置 Sub-Store，可生成多种订阅格式；高级玩家可DIY很多功能

### 🚀 通用订阅 (不带分流规则)

```bash
# 通用订阅
http://127.0.0.1:8299/{sub-store-path}/download/sub

# URI 订阅
http://127.0.0.1:8299/{sub-store-path}/download/sub?target=URI

# Mihomo/ClashMeta
http://127.0.0.1:8299/{sub-store-path}/download/sub?target=ClashMeta

# Clash
http://127.0.0.1:8299/{sub-store-path}/download/sub?target=Clash

# V2Ray
http://127.0.0.1:8299/{sub-store-path}/download/sub?target=V2Ray

# ShadowRocket
http://127.0.0.1:8299/{sub-store-path}/download/sub?target=ShadowRocket

# Quantumult
http://127.0.0.1:8299/{sub-store-path}/download/sub?target=QX

# Sing-Box
http://127.0.0.1:8299/{sub-store-path}/download/sub?target=sing-box

# Surge
http://127.0.0.1:8299/{sub-store-path}/download/sub?target=Surge

# Surfboard
http://127.0.0.1:8299/{sub-store-path}/download/sub?target=Surfboard
```

### 🚀 Mihomo/Clash 订阅（带分流规则）

默认使用 `https://raw.githubusercontent.com/sinspired/override-hub/refs/heads/main/yaml/ACL4SSR_Online_Full.yaml` 覆写  

> 可在配置中更改 `mihomo-overwrite-url`。

```bash
# 如果未设置 sub-store-path
http://127.0.0.1:8299/api/file/mihomo

# 如果设置了 sub-store-path: "/path" (建议设置)
http://127.0.0.1:8299/path/api/file/mihomo
```

### 🚀 sing-box 订阅（带分流规则）

本项目默认支持 `sing-box` 最新版(`1.12`)和 `1.11(ios兼容)` 规则，可自定义规则，

✨ 在 WebUI 点击 `分享订阅` 获取订阅链接

![singbox-shareMenu](./doc/images/share-menu.png)

请查阅最新 [配置文件示例](https://github.com/sinspired/subs-check/blob/main/config/config.yaml.example)

```yaml
# singbox规则配置
# json文件为分流规则
# js脚本用来根据规则对节点进行处理
# singbox每个版本规则不兼容，须根据客户端版本选择合适的规则
# singbox 最新版
singbox-latest:
  version: 1.12
  json:
    - https://raw.githubusercontent.com/sinspired/sub-store-template/main/1.12.x/sing-box.json
  js:
    - https://raw.githubusercontent.com/sinspired/sub-store-template/main/1.12.x/sing-box.js

# singbox 1.11 版本配置（iOS 兼容）
singbox-old:
  version: 1.11
  json:
    - https://raw.githubusercontent.com/sinspired/sub-store-template/main/1.11.x/sing-box.json
  js:
    - https://raw.githubusercontent.com/sinspired/sub-store-template/main/1.11.x/sing-box.js
```

## 🌐 内置文件服务
>
> subs-check 会在测试完后保存三个文件到output目录中；output目录中的所有文件会被8199端口提供文件服务

⚠️ 为方便使用cloudflare隧道映射等方案在公网访问，本项目取消了对output文件夹的无限制访问。

### 🔐 使用 `分享码` 分享

设置 `share-password` ,使用分享码进行分享。可分享 `/output` 目录的文件，比如 `all.yaml` `mihomo.yaml`

```yaml
# 如果你要分享订阅，请设置订阅分享密码
# 订阅访问地址格式：http://127.0.0.1:8199/sub/{share-password}/filename.yaml
# 文件位置放在 output/filename.yaml
# 比如: http://127.0.0.1:8199/sub/{share-password}/all.yaml
share-password: ""
```

通过 `http://127.0.0.1:8199/sub/{share-password}/all.yaml` 访问

![share-with-password](./doc/images/share-with-password.png)

### 🗂️ 无密码保护分享

将文件放入 output/more：通过 `http://127.0.0.1:8199/more/文件名` 直接访问，适合内网或隧道映射少量文件共享

![share-for-freee](./doc/images/share-free.png)

| 服务地址                                                   | 格式说明                      | 来源说明                      |
| --------------------------------------------------------- | ----------------------------- | ---------------------------- |
| `http://127.0.0.1:8199/sub/{share-password}/all.yaml`     | Clash 格式节点                 | 由subs-check直接生成          |
| `http://127.0.0.1:8199/sub/{share-password}/mihomo.yaml`  | 带分流规则的 Mihomo/Clash 订阅  | 从上方sub-store转换下载后提供  |
| `http://127.0.0.1:8199/sub/{share-password}/base64.txt`   | Base64 格式订阅                | 从上方sub-store转换下载后提供  |
| `http://127.0.0.1:8199/sub/{share-password}/history.yaml` | Clash 格式节点                 | 历次检测可用节点               |

## **✨ 新增功能和性能优化详情**

### 1. 测活-测速-媒体检测，分阶段流水线，自适应高并发

通过将测活阶段并发数提升`100-1000`（*主要受限于设备 CPU 和路由器芯片性能，几乎不占用带宽*），同时将测速阶段并发数保持在较低水平（如 `8-32`，以减轻带宽竞争）。大幅提高性能，数倍缩短整体检测时间，并使测速结果更准确！

```yaml
# 新增设置项:
alive-concurrent: 200  # 测活并发数
speed-concurrent: 32   # 测速并发数
media-concurrent: 100  # 流媒体检测并发数
```

### 2. 增强位置标签

> 示例：🇺🇸US¹-SG⁰_3|2.5MB/s|6%|GPT⁺|TK-US|YT-US|NF|D+|X

- BadCFNode(无法访问CF网站的节点)：`HK⁻¹`
- CFNodeWithSameCountry(实际位置与cdn位置一致)：`HK¹⁺`
- CFNodeWithDifferentCountry(实际位置与cdn位置不一致)：`HK¹-US⁰`
- NodeWithoutCF(未使用CF加速的节点)：`HK²`
  
前两位字母是实际浏览网站识别的位置，`-US⁰` 为使用CF CDN服务的网站识别的位置，比如GPT， X等

```yaml
# 新增设置项:
drop-bad-cf-nodes: false  # 是否丢弃低质量的CF节点
enhanced-tag: false       # 是否开启 增强位置标签
maxmind-db-path: ""       # 指定位置数据库
```

### 3. 优化内存

`检测期下降18%，检测结束下降49%`，对内存敏感可以使用 `i386` 版本，对内存不敏感可以使用 `x64` 版本，性能略有提升，cpu占用更低。

- 去重后，释放原数据
- 结束检测，手动释放节点缓存
- 每个检测任务结束，结束空闲tcp连接占用
- pre-release 使用绿茶垃圾回收(测试中)

```powershell
# 内存监控数据:
[19:13:30] Start: PID=9040 mem=667.80 MB
[19:26:38] BigChange(>=20%) reached in 13m8.0320213s, mem=102.71 MB
[19:44:37] Down 1 step(s) of 10MB, mem=98.72 MB
[20:37:40] Down 1 step(s) of 10MB, mem=83.64 MB
[20:42:41] Down 3 step(s) of 10MB, mem=59.54 MB
```

### 4. 智能节点乱序，减少节点被测速 “测死” 的概率

```yaml
# 新增配置项:
# 相似度阈值(Threshold)大致对应网段
# 1.00 /32（完全相同 IP）
# 0.75 /24（前三段相同）
# 0.50 /16（前两段相同）
# 0.25 /8（第一段相同）
# 以下设置仅能 [减少] 节点被测速测死的概率, 无法避免被 "反代机房" 中断节点
threshold:  0.75
```

### 5. 保存并加载 `历次` 检测可用节点

可有效缓解网络环境恶劣导致的问题

```powershell
# 保存并加载 "上次检测成功的节点" 和 "历次检测成功的节点"
# keep-success-proxies: true
2025-09-25 15:52:25 INF 已获取节点数量: 15872
2025-09-25 15:52:25 INF 去重后节点数量: 11788
2025-09-25 15:52:25 INF 已加载上次检测可用节点，数量: 110
2025-09-25 15:52:25 INF 已加载历次检测可用节点，数量: 536
2025-09-25 15:52:25 INF 节点乱序, 相同 CIDR/24 范围 IP 的最小间距: 785
2025-09-25 15:52:25 INF 开始检测节点
2025-09-25 15:52:25 INF 当前参数 enable-speedtest=true media-check=true drop-bad-cf-nodes=false auto-concurrent=true concurrent=100 :alive=515 :speed=28 :media=138 timeout=5000 min-speed=512 download-timeout=10 download-mb=20
进度: [===========================================> ] 95.7% (11280/11788) 可用: 133
```

### 6. 自动检查更新，无缝升级新版本

- 软件启动时更新：重启后打开新窗口
- 定时更新任务：静默重启，如需关闭任务，直接关闭终端控制台即发送关闭信号

```yaml
# 是否开启新版本更新
# 支持启动时检查更新及定时更新任务,无缝升级新版本
# 支持apprise API通知渠道
# true: 自动更新; false: 不更新
update: false
# 启动时检查更新版本
update-on-startup: true
# 定时检查更新
# "0 0,9,21 * * *" 默认每天0点,9点,21点检查更新
cron-chek-update: "0 0,9,21 * * *"
# 使用预发布版本
prerelease: false
```

### 7. 统计订阅链接总数、可用节点、成功率

可自动生成剔除无效订阅的 `sub-urls:`, 可直观统计高质量的订阅链接。将在 `output/stats/` 文件夹生成统计文件：

```bash
output/
└── stats/
    ├── subs-valid.yaml            # 有效订阅链接
    ├── subs-stats.yaml            # 统计节点数量
    ├── subs-filtered.yaml         # 剔除无可用节点后的订阅
    └── subs-filtered-stats.yaml   # 统计成功率等数据
```

设置项：

```yaml
# 统计订阅链接有效性和成功率
# 为 true 会在 ./output/stats/ 生成订阅链接统计，每个订阅节点数量，可用节点数量，成功率
sub-urls-stats: true
```

## 🙏 鸣谢

[beck-8](https://github.com/beck-8)、[cmliu](https://github.com/cmliu)、[Sub-Store](https://github.com/sub-store-org/Sub-Store)、[bestruirui](https://github.com/bestruirui/BestSub)

## ⭐ Star History

[![Stargazers over time](https://starchart.cc/sinspired/subs-check.svg?variant=adaptive)](https://starchart.cc/sinspired/subs-check)

## ⚖️ 免责声明

本工具仅供学习和研究使用，使用者应自行承担风险并遵守相关法律法规。
