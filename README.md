# Actions-lede - OpenWrt固件自动构建系统

![GitHub](https://img.shields.io/github/license/yourusername/Actions-lede)
![GitHub Workflow Status](https://img.shields.io/github/workflow/status/yourusername/Actions-lede/build%20lede%20os)

## 项目简介

本项目基于 GitHub Actions 实现了 OpenWrt 固件的自动化构建和发布系统。它能够自动拉取 [Lean's lede](https://github.com/coolsnowwolf/lede) 源码，根据预设的配置文件编译适用于不同设备的 OpenWrt 固件，并自动发布到 GitHub Releases。

本项目源于 [P3TERX/Actions-OpenWrt](https://github.com/P3TERX/Actions-OpenWrt)

[![LICENSE](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square&label=LICENSE)](https://github.com/P3TERX/Actions-OpenWrt/blob/master/LICENSE)
![GitHub Stars](https://img.shields.io/github/stars/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Stars&logo=github)
![GitHub Forks](https://img.shields.io/github/forks/P3TERX/Actions-OpenWrt.svg?style=flat-square&label=Forks&logo=github)

## 功能特性

- 🔄 **自动化构建**：通过 GitHub Actions 实现固件的全自动构建
- ⏰ **定时构建**：每周五自动执行构建任务
- 📦 **多设备支持**：通过不同的配置文件支持多种设备
- 🗃️ **自动发布**：构建成功的固件自动发布到 GitHub Releases
- 🧹 **自动清理**：自动清理旧的构建记录和发行版本
- ⚙️ **高度可配置**：可通过环境变量灵活调整构建参数

## 支持的设备配置

项目中已包含以下设备的配置文件：

- `nx30pro.config` - NX30 Pro 路由器配置
- `newifiD2.config` - Newifi D2 路由器配置
- `m28k.config` - M28K 路由器配置

## 使用方法

### 方法一：使用此模板创建自己的仓库

1. 点击 [Use this template](https://github.com/wang46495255/Actions-lede/generate) 按钮创建一个新仓库。

### 方法二：生成设备配置文件

通过 Lean's OpenWrt 源代码生成 `.config` 文件：
1. 克隆 [coolsnowwolf/lede](https://github.com/coolsnowwolf/lede) 项目
2. 运行 `./scripts/feeds update -a` 和 `./scripts/feeds install -a`
3. 运行 `make menuconfig` 配置固件
4. 保存配置文件为 `.config`

### 方法三：推送配置文件到仓库

将生成的机型配置文件推送到 GitHub 仓库：
- 如果只使用单一配置，可以将文件命名为 `.config`，并在工作流中的环境变量设置 `CONFIG_FILE: .config`
- 如果需要支持多机型，可以将配置文件重命名为 `机型.config`，在工作流中改为相同的名称

### 方法四：触发构建

1. 在 Actions 页面选择 "Build OpenWrt" 选项
2. 点击 "Run workflow" 按钮
3. 构建完成后，点击 Actions 页面右上角的 "Artifacts" 按钮，即可下载二进制文件

### 方法五：更改构建机型

需要构建不同机型时，只需在工作流中将配置文件改为需要编译的机型配置文件（同名即可）。

## 配置说明

在 `.github/workflows/BUILD-LEDE.yml` 文件中可以修改以下环境变量来定制构建过程：

| 变量名 | 默认值 | 说明 |
|--------|--------|------|
| `REPO_URL` | https://github.com/coolsnowwolf/lede | 源码仓库地址 |
| `REPO_BRANCH` | master | 源码分支 |
| `FEEDS_CONF` | feeds.conf.default | feeds 配置文件 |
| `CONFIG_FILE` | nx30pro.config | 设备配置文件 |
| `UPLOAD_BIN_DIR` | false | 是否上传完整的 bin 目录 |
| `UPLOAD_FIRMWARE` | true | 是否上传固件目录 |
| `UPLOAD_RELEASE` | true | 是否发布到 GitHub Releases |

## 构建流程

1. 初始化 Ubuntu 环境并安装编译依赖
2. 克隆 LEDE 源码
3. 更新和安装 feeds
4. 加载指定的设备配置文件
5. 下载编译所需的软件包
6. 并行编译固件
7. 整理编译产物
8. 上传到 GitHub Artifacts
9. 发布到 GitHub Releases

## 自定义配置

### 添加新的设备支持

1. 获取目标设备的配置：
   ```bash
   # 在本地编译环境中运行
   make menuconfig
   # 配置完成后保存配置
   make defconfig
   cat .config > your_device.config
   ```

2. 将生成的配置文件添加到本项目中

3. 修改工作流中的 `CONFIG_FILE` 变量或在手动触发时选择对应的配置文件

### 修改发布策略

默认情况下，系统会：
- 保留最近的5个发行版本
- 每周五自动构建并使用"Weekly_"前缀标记
- 其他时间构建使用"YYYY.MM.DD-HHMM"格式标记

可以通过修改 `.github/workflows/BUILD-LEDE.yml` 中的相关部分来自定义这些策略。

## 鸣谢

- [Microsoft Azure](https://azure.microsoft.com)
- [GitHub Actions](https://github.com/features/actions)
- [OpenWrt](https://github.com/openwrt/openwrt)
- [coolsnowwolf/lede](https://github.com/coolsnowwolf/lede)
- [Mikubill/transfer](https://github.com/Mikubill/transfer)
- [softprops/action-gh-release](https://github.com/softprops/action-gh-release)
- [Mattraks/delete-workflow-runs](https://github.com/Mattraks/delete-workflow-runs)
- [dev-drprasad/delete-older-releases](https://github.com/dev-drprasad/delete-older-releases)
- [peter-evans/repository-dispatch](https://github.com/peter-evans/repository-dispatch)

## 许可证

[麻省理工学院](https://github.com/P3TERX/Actions-OpenWrt/blob/main/LICENSE) © [**P3TERX**](https://p3terx.com)
