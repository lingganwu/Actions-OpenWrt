# Actions-OpenWrt (Redmi AX6000 Custom Build)

> 基于 OpenWrt 官方源码自动构建。
> **特色**：集成 Rclone 自动上传 OneDrive，并预置了特定的网络和安全配置。

![Build Status](https://github.com/lingganwu/Actions-OpenWrt/workflows/AX6000%20Pure%20System%20(Fix%20OneDrive%20Upload)/badge.svg)

## ⚙️ 固件硬编码配置 (重要)

本固件在编译时已通过脚本写入以下默认配置，刷机后**即刻生效**：

| 项目 | 默认值 / 状态 | 备注 |
| :--- | :--- | :--- |
| **管理 IP** | **192.168.8.1** | ⚠️ 注意不是 1.1 |
| **后台密码** | `851129` | root 账户 |
| **WAN 拨号** | PPPoE | 账号: `637143646974` / 密码: `888888` |
| **WiFi SSID** | `OpenWrt_2.4G` / `OpenWrt_5G` | 区域: AU (澳大利亚) |
| **WiFi 密码** | `19851129z` | WPA2 PSK |
| **防火墙** | Input: ACCEPT | 允许公网访问 / 流量全放行 |
| **硬件加速** | ✅ 已开启 | flow_offloading_hw |

## 🛠️ 功能特性

- **纯净底包**: 基于 `openwrt/openwrt` (可选 23.05 或 Master 分支)。
- **基本工具**: 预装 `curl`, `wget-ssl`, `openssl`, `vim` 等常用工具。
- **性能优化**: 集成 `kmod-nft-offload` 和 `irqbalance` (自动平衡多核中断)。
- **云端同步**: 编译完成后自动调用 Rclone 将固件上传至 OneDrive。

## 🚀 如何触发编译

### 方式一：定时任务
- 系统会在 **每 3 天的 18:00** 自动触发一次编译。

### 方式二：手动触发 (Workflow Dispatch)
1. 进入 Actions 页面。
2. 选择 "AX6000 Pure System (Fix OneDrive Upload)"。
3. 点击 **Run workflow**。
4. **选择分支**:
   - `openwrt-23.05` (推荐，稳定)
   - `master` (激进，最新)

## 🔐 仓库 Secrets 配置

为了让 OneDrive 上传功能正常工作，必须在仓库设置中添加以下 Secret：

| Secret Name | 说明 |
| :--- | :--- |
| `RCLONE_CONF` | **必须**。Rclone 的配置文件内容 (`rclone.conf`)，用于连接你的 OneDrive。 |

## 📂 产物下载

编译成功后，固件会通过两种方式发布：
1. **GitHub Releases**: 标签格式为 `AX6000_Build_{Run_Number}`。
2. **OneDrive**: 自动上传至 `/OpenWrt_Builds/` 目录，文件名包含日期 (如 `AX6000_Pure_23.05_20251123_...bin`)。

---
*Workflow maintained by [lingganwu](https://github.com/lingganwu)*
