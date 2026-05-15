# CLIProxyAPI Tray

> 本仓库是 [kitephp/CLIProxyAPI-Tray](https://github.com/kitephp/CLIProxyAPI-Tray) 的 **Ai-Data-Man** 维护分支。

Windows 系统托盘管理工具，用于启动和管理 [CLIProxyAPI](https://github.com/Ai-Data-Man/CLIProxyAPI)。

托盘版本：`2.0.0`

## 功能

- 托盘常驻，单实例运行
- 启动、停止、重启 CLIProxyAPI
- 自动检测并下载最新可用版本
- 版本隔离
- 一键打开管理页面（WebUI）
- 托盘个性化设置

## 与上游差异

- **下载源**：CLIProxyAPI 二进制默认从 Ai-Data-Man fork 获取
- **自动打开 WebUI**：新增 `Auto Open WebUI` 开关，控制启动/重启/更新后是否自动打开管理页面
- **安装路径**：默认安装目录 `~/.cli-proxy-api-tray`

## 环境要求

- Windows 10 / Windows 11
- Windows PowerShell 5.1 或 PowerShell 7
- 能访问 GitHub Releases

## 快速开始

### 方式 A：克隆仓库使用

克隆后在仓库目录双击 `create-shortcut.bat`，安装目录即为仓库目录。

### 方式 B：一行命令安装

```powershell
irm https://raw.githubusercontent.com/Ai-Data-Man/CLIProxyAPI-Tray/main/install.ps1 | iex
```

安装器不会覆盖已有的 `config.yaml`、`settings.json`、`versions/`、`logs/`。

## 使用说明

### 托盘菜单

- `Running (vX.Y.Z)` / `Not Running`：当前服务状态，只读显示
- `Start`：启动 CLIProxyAPI
- `Restart`：重启当前服务
- `Stop`：停止 CLIProxyAPI 进程
- `Open` → `WebUI` / `Folder` / `Config`
- `Settings` → `Auto Open WebUI` / `Auto Update` / `Reset Password`
- `Update`：检查并安装最新版本
- `About`：打开项目 GitHub 页面
- `Exit`：退出托盘并停止进程

### 托盘双击行为

- 服务运行中：直接打开 WebUI
- 服务未运行：启动服务

## 设置项说明

### Auto Open WebUI

影响范围：
- 通过 `Start` / `Restart` / `Update` 后是否自动打开 WebUI
- 脚本启动时（检测到已运行）是否自动打开 WebUI

不影响：
- 手动点击 `Open` → `WebUI`
- 双击托盘（服务已运行时）

### Auto Update

- 默认关闭
- 开启后每次托盘启动时自动检查最新 CLIProxyAPI 版本
- 发现新版本自动下载安装，不弹确认框
- 更新失败时恢复到之前记录的版本信息
- 不会后台定时检查；手动 `Update` 仍可随时检查

## 状态文件

`settings.json` 字段：`version`、`arch`、`autoOpenWebUI`、`autoUpdate`、`updatedAt`

- 主状态文件：`<脚本目录>\settings.json`
- 回退路径：`%LOCALAPPDATA%\CLIProxyAPI_Tray\settings.json`（脚本目录不可写时自动降级）
- 版本目录：`<脚本目录>\versions\<version>\`

## 相关 Fork

- [Ai-Data-Man/CLIProxyAPI](https://github.com/Ai-Data-Man/CLIProxyAPI) — CLIProxyAPI 本体 fork
- [Ai-Data-Man/Cli-Proxy-API-Management-Center](https://github.com/Ai-Data-Man/Cli-Proxy-API-Management-Center) — Web 管理面板 fork

## 许可证

MIT
