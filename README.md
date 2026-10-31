# GitHub 部署助手 (GitHubDeployer)



<p align="center">
  <strong>面向 Windows 平台的轻量级自动化 GitHub 部署与 Release 发行桌面工具</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows-0078D6?logo=windows&logoColor=white" alt="Platform Windows" />
  <img src="https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white" alt="Python 3.10+" />
  <img src="https://img.shields.io/badge/Architecture-x64-555555" alt="Architecture x64" />
  <img src="https://img.shields.io/badge/Security-Windows%20DPAPI-success?logo=windows-terminal&logoColor=white" alt="DPAPI Encrypted" />
  <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License MIT" />
</p>

---

## 一、软件介绍与功能概述

GitHub 部署助手 (GitHubDeployer) 是一款专为 Windows 用户设计的绿色桌面工具。软件旨在简化本地工程目录及单个可执行文件部署到 GitHub 仓库的操作流程，替代繁琐的底层终端命令。

### 核心功能

- **极简界面与低干扰交互**：主界面仅保留路径选择、仓库绑定、提交说明与一键推送四个必要环节；网络代理、Release 标签与高级检测等选项收纳于折叠抽屉中，按需展开。
- **双模态部署支持**：
  - **项目目录部署**：支持将任意项目根目录直接拖入，自动识别当前 Git 分支、文件变动状态与待提交文件统计；
  - **独立程序部署**：支持将桌面或下载目录中的单个可执行程序（.exe）直接拖入，自动建立隔离发布项目，并可一键上传为 GitHub Release 附件下载直链。
- **硬件级凭据安全保护**：GitHub 访问令牌（Token）采用 Windows 专有硬件级凭据加密技术 DPAPI（CryptProtectData）存储，禁止明文落盘，仅限当前设备登录用户可解密；终端日志输出自动对 Token 实施强制动态脱敏。
- **提交前代码安全体检 (Secret Scanner)**：内置静态密钥特征扫描器，在提交前主动扫描识别常见的 API 密钥（OpenAI、Google、AWS、GitHub、Slack 等）、SSH/RSA 私钥以及 .env、credentials.json 等高危配置文件，避免代码意外公开造成的安全事故。
- **免网页在线建仓**：深度集成 GitHub REST API，在软件内即可一键在线创建全新的公开（Public）或私有（Private）远程仓库，并自动绑定本地 Remote。
- **智能同步与变基 (Smart Pull & Rebase)**：遇远端代码更新或分支分叉时，提供自动暂存、变基拉取与冲突回滚保护，确保本地提交历史整洁。
- **系统级桌面交互集成**：支持窗口全局文件拖放，提供 Windows 资源管理器鼠标右键菜单（“使用 GitHub 部署助手打开”）一键添加与干净卸载。

---

## 二、安装与运行环境

### 软件形态

- **单文件免安装运行**：本软件为完全独立的单文件绿色可执行程序 `GitHubDeployer.exe`（体积约 33MB），零外部运行依赖，下载后直接双击即可运行，不产生多余运行残留。

### 运行环境要求

1. **操作系统**：Windows 10 / Windows 11（64位系统）。
2. **基础依赖**：计算机需安装 [Git 命令行工具](https://git-scm.com/) 并确保其已添加到系统环境变量 PATH 中。
3. **网络条件**：能够正常连接 GitHub 服务；网络受限环境下可通过内置代理功能配合本地网络工具使用。

### 启动方法

直接双击运行桌面或本地目录中的 `GitHubDeployer.exe` 即可启动。

---

## 三、详细操作指南

### 1. 首次配置与凭据设置

1. 打开程序，点击“高级设置 (点击展开 ▾)”。
2. 在 Token 输入框中粘贴具有 `repo` 权限的 GitHub Personal Access Token。
3. 点击“验证与测速”按钮；验证成功后，程序将通过 Windows DPAPI 将凭据加密保存在本地配置中，后续启动无需再次输入。

### 2. 部署本地代码项目（文件夹）

1. **选择目录**：将代码文件夹直接拖入软件窗口，或点击“浏览目录”选中目标文件夹。
2. **确认状态**：观察路径下方状态栏；若提示“未初始化 Git 仓库”，可点击右侧出现的“初始化 Git”完成本地仓库初始化。
3. **绑定仓库**：在仓库地址栏输入远程 Git 仓库地址；若尚未建仓，点击“新建仓库”直接在线创建并自动填入。
4. **提交与推送**：输入本次提交说明，点击“推送到 GitHub”，等待下方控制台显示操作完成。

### 3. 部署独立可执行程序 (.exe) 并发布 Release

1. **拖入文件**：将桌面或任意目录下的 .exe 文件直接拖入软件窗口。
2. **确认发布方案**：程序自动检测并弹出独立文件处理向导，点击“创建独立部署项目 (推荐)”，系统将自动建立专属隔离目录并生成工程配置。
3. **启用 Release 发布**：展开高级设置，勾选“Release Tag”并确认版本标签号（如 `v1.0.0`）。
4. **一键同步**：点击“推送到 GitHub”，程序将自动推送版本代码，并将该 .exe 文件作为官方 Release 附件上传，任务完成后提供直接下载直链。

### 4. 配置网络代理

1. 展开“高级设置”，勾选“代理”复选框。
2. 输入本地代理客户端地址及端口（例如 `http://127.0.0.1:7890`）。
3. 再次点击验证或执行推送，网络数据流将全自动经由代理通道传输。

### 5. 注册与卸载 Windows 鼠标右键菜单

1. 展开“高级设置”，勾选“右键菜单集成”。
2. 系统弹出注册成功提示后，在任意文件夹或目录空白处点击鼠标右键，即可看到“使用 GitHub 部署助手打开”选项。
3. 若需清理，取消勾选即可彻底移除相关注册表键值。

---

## 四、常见问题解答 (FAQ)

### Q1: 提示找不到 git 命令或系统找不到指定文件？

本软件底层依赖系统安装的 Git 客户端执行传输。请前往 [Git 官网](https://git-scm.com/) 下载安装 Git for Windows，并在安装选项中勾选“Git from the command line and also from 3rd-party software”（将其加入环境变量 PATH）。

### Q2: GitHub Token 需要勾选哪些权限？存储是否安全？

- **权限建议**：使用 Classic Token 时，勾选 `repo` 作用域即可覆盖代码读写、分支管理及 Release 资产上传等全部功能。
- **安全保障**：Token 仅在本地使用 Windows DPAPI 硬件隔离加密技术保存，密钥仅限当前登录系统的用户账户解密。日志输出流实时动态脱敏，杜绝截屏或投屏时明文外泄。

### Q3: 为什么把桌面上的 .exe 文件拖入时会提示创建独立项目？

这是内置的文件防误防丢保护机制。桌面和下载目录通常包含大量个人敏感文件与快捷方式，若直接在桌面根目录执行 Git 初始化，可能导致无关文件被批量提交到公开仓库。创建专属隔离目录可确保仅部署目标文件本身。

### Q4: 推送时提示网络连接超时或连接重置？

国内访问 GitHub 服务器可能出现路由波动。建议展开“高级设置”，勾选“代理”并配置本地端口（如 Clash 或 v2ray 本地监听端口），测速正常后再行提交。

### Q5: 提示远端分支存在冲突，无法直接推送？

当远端仓库存在本地没有的新提交记录（例如在 GitHub 网页端手动修改过 README.md）时，Git 会触发保护机制。软件会自动弹出提示，选择“自动合并并推送”即可自动执行智能变基（Smart Pull & Rebase），在保留本地代码的同时平滑同步远端修改。

---

## 五、开源协议

本项目采用 [MIT License](LICENSE) 开源授权。
