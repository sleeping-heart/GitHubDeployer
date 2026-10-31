# 🚀 GitHub 部署助手 (GitHubDeployer)

<p align="center">
  <img src="app.png" alt="GitHubDeployer Logo" width="128" height="128" />
</p>

<p align="center">
  <strong>专为 Windows 开发者打造的轻量级、极简、高颜值的 GitHub 一键自动化部署与发布桌面工具</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows-0078D6?logo=windows&logoColor=white" alt="Platform Windows" />
  <img src="https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white" alt="Python 3.10+" />
  <img src="https://img.shields.io/badge/Architecture-x64-555555" alt="Architecture x64" />
  <img src="https://img.shields.io/badge/Security-Windows%20DPAPI-success?logo=windows-terminal&logoColor=white" alt="DPAPI Encrypted" />
  <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License MIT" />
</p>

---

## 📖 简介

**GitHub 部署助手 (GitHubDeployer)** 是一款告别繁琐 Git 终端命令、拒绝复杂臃肿配置的现代化桌面辅助工具。

无论您是正在开发一个完整的代码工程（Python / Web / C++ / Rust 等），还是刚刚编译完成了一个单文件可执行程序（`.exe`），只需**拖入窗口**，便可一键完成从本地 Git 初始化、敏感凭据扫描、远程仓库自动创建，到分支同步、Release 标签发布与资产附件上传的全流程自动化。

---

## ✨ 核心特色与亮点

### 🍃 1. 极致纯粹的呼吸感极简 UI
- **告别视觉噪音**：摒弃传统运维工具密密麻麻的生硬方框卡片，采用大面积纯白留白与现代无衬线排版（Segoe UI / 微软雅黑）。
- **渐进式交互体验**：将网络代理、Release Tag、敏感词检测、右键菜单等非高频项全部收拢至 **`⚙️ 高级设置 (点击展开 ▾)`** 抽屉中，核心操作仅保留 **选路径 ➔ 填说明 ➔ 一键推送** 三步，清新通透。
- **原生级视觉呈现**：针对 Windows 4K/2K 高分屏优化，内置通过 1024×1024 矢量超采样生成的 9 阶 Windows 原生 DPI 级别抗锯齿图标（16~256px），任务栏与标题栏清晰细腻、绝不模糊失真。

### 📦 2. 双模态部署引擎
- **📁 工程目录部署模式**：
  - 支持拖入或选择任意项目根目录，实时检测 Git 状态、当前分支、未暂存与待提交文件数量。
  - 自动检测并提示补全通用的 `.gitignore` 文件。
- **🎯 独立文件 / EXE 专属部署模式**：
  - 支持直接将桌面或下载文件夹中的 `.exe` 或独立文件拖入程序。
  - 若文件尚未归入 Git 仓库，自动唤起独立打包引导向导，智能创建专属部署工程、自动生成 `.gitignore` 与项目说明，更可一键将该文件发布为 **GitHub Release 附件**。

### 🛡️ 3. 硬件级数据安全与代码体检
- **Windows DPAPI 硬件加密**：GitHub Personal Access Token 使用 Windows 底层数据保护接口（`CryptProtectData`）进行本机硬件凭据加密，绝不将明文 Token 存入磁盘。
- **日志全链路脱敏**：实时输出的控制台与 Git 指令流中，任何 Token 均会自动被替换脱敏为 `***TOKEN***`，避免屏幕截屏或投屏时意外泄漏。
- **内置敏感密钥体检 (Secret Scanner)**：
  - 推送前毫秒级扫描待提交代码，自动识别常见的 API Key（OpenAI、Google、AWS、GitHub、Slack 等）、SSH/RSA 私钥及硬编码敏感密码；
  - 自动拦截或预警 `.env`、`credentials.json` 等高危配置文件，防范代码公开造成的安全事故。

### 🌐 4. 深度联动的 GitHub API 能力
- **零网页开仓**：无需打开浏览器，在软件内直接通过 GitHub API 一键创建全新的 **Public（公开）** 或 **Private（私有）** 仓库，并自动绑定 Remote。
- **Release 与资产附件一键发布**：一键生成指定 Tag 版本的 Release 发行版，并自动上传打包产物作为下载附件。
- **智能分支管理与智能变基 (Smart Pull & Rebase)**：支持分支新建、切换、重命名（如 `master` ➔ `main`）；推送遇远程更新时自动智能 Rebase，告别杂乱的 Merge 提交历史。
- **网络测速与多协议代理**：内置 GitHub API 连通性与毫秒级延迟测速，支持 Direct / HTTP / HTTPS / SOCKS5 代理无缝切换。

### 🖥️ 5. Windows 桌面无缝集成
- **系统级文件拖拽**：基于 `tkinterdnd2` 实现真正的原生文件/文件夹拖拽支持。
- **Windows 鼠标右键菜单**：支持一键将“使用 GitHub 部署助手打开”注册到 Windows 资源管理器文件夹和空白处右键菜单，随用随唤，亦可随时一键彻底卸载。
- **实时纯黑控制台与任务中断**：底部保留纯黑极客风格终端日志，实时输出 Git 原生流，卡顿或耗时过长时可随时点击 `⏹ 中断` 强行安全终止底层子进程。

---

## 🖥️ 界面结构概览

```
┌─────────────────────────────────────────────────────────────┐
│  🚀 GitHub 部署助手                                 —  □  × │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  📁 本地项目路径                                            │
│  [ C:\Users\YourName\Projects\my-awesome-tool       ] [浏览]│
│  状态: 🌿 分支: main | 待提交文件: 3 个                     │
│                                                             │
│  🌐 GitHub 远程仓库                                         │
│  [ https://github.com/YourName/my-awesome-tool.git  ] [➕新建]│
│                                                             │
│  📝 提交说明                                                │
│  [ feat: 完成自动化部署与界面优化                   ] [🌿分支]│
│                                                             │
│  ⚙️ 高级设置 (点击展开 ▾)                                    │
│  ├─ 🔑 GitHub 访问令牌 (Token) [验证与测速]                  │
│  ├─ 🏷️ 发布 Release 版本 (Tag: v1.0.0)                      │
│  ├─ 🌐 网络代理设置 (直连 / 自定义代理端口)                 │
│  ├─ 🔍 代码敏感信息与大文件安全扫描                          │
│  └─ 🖱️ Windows 资源管理器鼠标右键菜单集成                   │
│                                                             │
│                [  🚀 推送到 GitHub  ]                       │
│                                                             │
│  ┌───────────────────────────────────────────────────────┐  │
│  │ > git add .                                           │  │
│  │ > git commit -m "feat: 完成自动化部署与界面优化"        │  │
│  │ > git push origin main                                │  │
│  │ ✨ 推送完成！耗时: 2.1s                                │  │
│  └───────────────────────────────────────────────────────┘  │
│  [🧹 清空日志]                                 [⏹ 中断任务]│
└─────────────────────────────────────────────────────────────┘
```

---

## 🚀 快速上手

### 方式一：下载即用（推荐）
如果你只需要直接使用工具，可直接下载打包好的绿色单文件：
- **可执行文件**：`GitHubDeployer.exe`
- **系统要求**：Windows 10 / 11（64位）
- **外部依赖**：本机已安装 [Git 命令行工具](https://git-scm.com/) 并已配置在系统 `PATH` 环境变量中。

#### 初次使用 3 步走：
1. **获取 GitHub Token**：
   - 登录 GitHub，访问 `Settings` ➔ `Developer Settings` ➔ `Personal access tokens (classic)`；
   - 生成一个新 Token，勾选 **`repo`**（代码与 Release 读写权限）以及 **`workflow`**（可选）；
   - 打开本软件，展开 `⚙️ 高级设置` 粘贴 Token，点击 **验证**。Token 将自动进行 Windows DPAPI 硬件加密保存。
2. **选择或拖入项目**：
   - 将任意代码文件夹（或需要发布的 `.exe` 单文件）直接拖入软件窗口。
3. **一键推送**：
   - 点击 **`[➕ 新建仓库]`** 或填入已有的仓库地址；
   - 输入本次提交说明，点击 **`🚀 推送到 GitHub`**，静待完成！

---

### 方式二：从源码运行与二次开发

#### 1. 克隆代码仓库
```bash
git clone https://github.com/YourName/GitHubDeployer.git
cd GitHubDeployer
```

#### 2. 配置 Python 运行环境
推荐使用 Python 3.10 及以上版本：
```bash
# 创建虚拟环境（可选）
python -m venv venv
venv\Scripts\activate

# 安装必要依赖
pip install pillow tkinterdnd2
```

#### 3. 启动程序
```bash
python main_gui.py
```

---

## 🛠️ 打包构建单文件 EXE

本项目经过针对 PyInstaller 深度定制与资源整合，可一键编译为无需任何外部 DLL 的独立单文件 EXE。

### 1. 安装打包工具
```bash
pip install pyinstaller pillow tkinterdnd2 pefile
```

### 2. 生成原生高保真图标
```bash
python create_icon.py
```

### 3. 执行 PyInstaller 编译命令
```powershell
pyinstaller --onefile --windowed `
  --name "GitHubDeployer" `
  --icon "app.ico" `
  --add-data "app.ico;." `
  --add-data "app.png;." `
  --collect-data tkinterdnd2 `
  --clean `
  main_gui.py
```
编译产物位于 `dist/GitHubDeployer.exe`。

---

## 📂 项目代码结构

```
quirky-oppenheimer/
├── main_gui.py            # GUI 主界面与交互编排（Tkinter + 极简视觉样式 + 拖拽响应）
├── git_manager.py         # Git 底层核心驱动（分支管理、智能 Rebase、命令异步封装、进程熔断）
├── github_api.py          # GitHub REST API 封装（连通测速、远程建仓、Release 创建与资产上传）
├── secret_scanner.py      # 代码敏感信息与凭据扫描引擎（正则匹配各类 API Key、私钥、高危文件）
├── security.py            # Windows DPAPI 安全加密套件（Token 硬件绑定与动态加解密）
├── config_manager.py      # 配置持久化中心与多项目路径历史记忆
├── context_menu.py        # Windows 资源管理器右键上下文菜单注册表管理器
├── create_icon.py         # 1024x1024 矢量高保真 9 阶 Windows DPI 图标生成脚本
├── app.ico / app.png      # 应用程序图标（已完成系统抗锯齿适配）
├── GitHubDeployer.exe     # 编译生成好的 Windows 单文件可执行程序
└── README.md              # 项目技术与使用文档
```

---

## 🛡️ 安全机制说明

| 维度 | 防护策略 |
| :--- | :--- |
| **Token 本地存储** | 采用 Windows 专有硬件级凭据加密技术 **DPAPI**（`CryptProtectData`），仅当前登录用户有权解密，杜绝因拷贝配置文件导致的凭据泄露。 |
| **日志流脱敏** | 所有控制台输出、Git 命令参数均经过动态脱敏过滤器，任何 Token 均强制替换为 `***TOKEN***`，无明文暴露。 |
| **代码泄露防御** | 内置代码静态体检，在 `git add` 之前主动扫描高危密钥格式，发现潜在风险自动弹窗预警并中止推送。 |
| **大文件拦截** | 预警超过 50MB / 100MB 的大体积二进制文件，提供一键写入 `.gitignore` 功能，避免 Git 仓库异常膨胀及 GitHub 拒收。 |

---

## ❓ 常见问题 (FAQ)

#### Q1: 点击推送时提示网络超时或无法连接 GitHub？
> **A:** 国内网络环境下直连 GitHub 可能会出现 DNS 污染或波动。请展开 `⚙️ 高级设置` ➔ `网络代理设置`，选择 `自定义代理` 并填入您本地的科学代理客户端端口（例如 Clash 默认为 `http://127.0.0.1:7890` 或 v2ray 默认为 `http://127.0.0.1:10809`），点击 **测速** 确认连通后再执行推送。

#### Q2: GitHub Token 应该勾选哪些权限？
> **A:** 建议使用 Classic Token 并勾选 **`repo`** 全套权限（用于读写私有/公有代码仓及 Release 附件发布）。如果不需要创建仓库或发布 Release，仅勾选 `public_repo` 即可。

#### Q3: 为什么把单个 .exe 拖进去会提示“部署独立可执行程序”？
> **A:** 这是专为独立软件开发者设计的特性。如果该 `.exe` 位于桌面或下载等非 Git 目录中，软件会自动为您在安全目录下创建专属部署工程，并提供自动生成说明文档和直发 GitHub Release 的快捷操作。

#### Q4: 如何开启或移除 Windows 鼠标右键菜单？
> **A:** 展开界面的 `⚙️ 高级设置` ➔ `Windows 右键菜单集成`，点击 **`添加至系统右键菜单`** 即可在任意文件夹右键直接调用本软件；点击 **`清理右键菜单`** 即可完全干净卸载，不留任何残留注册表垃圾。

---

## 📄 开源协议

本项目采用 [MIT License](LICENSE) 开源授权。欢迎提交 Issue 与 Pull Request！
