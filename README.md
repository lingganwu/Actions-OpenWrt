# 🔴 Redmi AX6000 OpenWrt 自动编译项目

> **特性**：纯净精简、集成 Passwall、自动配置拨号与 WiFi、OneDrive 同步。

本项目基于 GitHub Actions，每隔 3 天自动编译适配 **Redmi AX6000 (MT7986)** 的 OpenWrt 固件。源码基于 [hanwckf/immortalwrt-mt7986](https://github.com/hanwckf/immortalwrt-mt7986)，以稳定著称。

## 🚀 固件默认配置信息 (重要)

刷入固件后，系统会自动应用以下设置，无需手动配置：

| 项目 | 详细信息 |
| :--- | :--- |
| **管理地址 (LAN IP)** | `192.168.8.1` |
| **后台默认密码** | `851129` |
| **默认用户名** | `root` |
| **2.4G WiFi 名称** | `OpenWrt_2.4G` |
| **5G WiFi 名称** | `OpenWrt_5G` |
| **WiFi 密码** | `19851129z` |
| **宽带拨号账号** | `637143646974` |
| **宽带拨号密码** | `888888` |

## 🧩 集成插件

本固件主打精简稳定，仅包含核心科学上网插件：

* **LuCI-App-Passwall** (最新版)
    * 包含 Xray 核心
    * 包含 SingBox 核心
    * 包含 ChinaDNS-NG

## 🔄 自动化策略

* **源码更新**：使用 hanwckf 的 master 分支。
* **编译频率**：每 3 天自动运行一次 (北京时间 02:00)。
* **固件存储**：
    1.  **OneDrive**: 自动上传至 `OpenWrt_Builds` 文件夹 (需配置 Rclone)。
    2.  **GitHub Releases**: 作为备份，永久保留历史版本。

## 🛠️ 使用说明

### 1. 下载固件
点击本仓库右上角的 [Releases](../../releases) 页面下载最新的 `.bin` 文件（文件名包含 `sysupgrade`）。

### 2. 刷入方法
* **如果你已经是 OpenWrt 系统**：进入后台 -> 系统 -> 备份/升级 -> 刷写新的固件 (sysupgrade)。
* **如果你是官方系统**：请先解锁 SSH 并刷入 uboot，再在 uboot 控制台刷入固件。

## ⚠️ 免责声明

* 本项目仅供学习交流使用，请勿用于非法用途。
* **注意**：由于固件内预置了个人宽带账号密码，请务必将本仓库设置为 **Private (私有)**，防止隐私泄露。

---
*Auto-built by GitHub Actions*
