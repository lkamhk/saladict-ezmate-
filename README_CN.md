<div align="center">

  <img src="assets/branding/ezmate-icon.svg" width="150" alt="saladict-ezmate- 图标"/>

  <h1>saladict-ezmate-</h1>

  <p>🖥️ Windows 桌面翻译助手：🌐 划词即译、📸 OneOCR 截图识别、✍️ AI 英文写作。</p>

  <p><strong>🖥️ Windows x64 · 📸 OneOCR · 🌐 Azure Translator · ✍️ English Helper · 🔌 Codex App Server</strong></p>

  <p><a href="README.md">繁體中文</a> | <strong>简体中文</strong></p>

</div>

基于 Saladict 改版，针对 Windows 日常使用重新整理。保留便捷的划词翻译、输入翻译和语音朗读，加入 Azure Translator、独立 English Helper 窗口，以及 Codex App Server 接入。

图标碗身的金色 **EZ** 标记，就是这个改版的标识。

## 📸 Windows OneOCR：截图翻译，一框就行

**本版 OCR 已改用 Windows OneOCR——超强、非常好用！**

遇到图片、扫描文档、视频字幕，或者屏幕上无法选中的文字，按下截图翻译快捷键，框选需要的范围，就可以识别文字并交给翻译服务。

-   **本地识别**：OneOCR 在电脑上处理截图，识别步骤无需将图片上传到 OCR 网站。
-   **框选即用**：串联截图、识别和翻译，省去逐字输入和来回复制。
-   **无需 OCR API Key**：使用 OneOCR 引擎及模型，不需要另外申请云端 OCR 账号。

在“快捷键设置 → 截图翻译（OneOCR）”中设置自己顺手的组合即可。

> 文字识别可以在本地完成；识别后的文字会由你选择的翻译服务处理。选择在线翻译时，文字仍会发送到该服务。

## 🌐 Azure Translator：接入官方翻译 API

新增 **Microsoft Azure Translator** 内置服务，可以使用自己的 Azure Translator 资源，包括 F0 资源（有每月免费额度，缓解限流困扰）。

支持自动检测源语言、繁体中文翻译，以及 global、regional 或自定义 endpoint 设置。

设置方法：

1. 准备 Azure Translator 资源的 **Subscription Key**、**Region** 和 **Endpoint**。
2. 打开“服务设置 → 翻译 → 新增内置服务”，选择 **Azure Translator**。
3. 填入 Key，按资源要求填写 Region；Endpoint 使用资源提供的地址。
4. 点击“保存”，程序会先测试翻译请求，成功后保存设置。

设置完成后，划词翻译、输入翻译和截图翻译都可以使用 Azure。F0 的可用额度及限制以你的 Azure 资源为准。

## ✍️ English Helper：不止翻译，还帮你写好英文

**看懂一句英文，和自己写得自然，是两回事。** English Helper 有独立窗口和服务设置，适合写消息、回复邮件、理解英文句子，或者检查自己写的英文。

你可以自行修改 Prompt，调整语气、难度和输出格式。

### 🤖 选择你想用的 AI

English Helper 支持 **Ollama、OpenAI、DeepSeek、Claude、OpenAI-compatible API**，以及 **Codex App Server**。支持流式显示回复。

在“服务设置 → English Helper”中选择供应商、模型及所需设置，再到“快捷键设置 → English Helper”中设置快捷键。

选中文字后按下快捷键，可以直接带入 Helper；也可以打开窗口自行输入。想用本地模型，可以选择 Ollama，预先安装及下载模型后使用。

## 🔌 Codex App Server：English Helper 也可以用 Codex

如果你已有 Codex CLI，可以将 **Codex App Server** 作为 English Helper 的 AI 供应商，沿用该 server 的登录状态，无需在 Saladict 中再次填写 Codex API Key。

### ⭐ 推荐搭配：Codex EzMate

想更方便地管理 App Server，推荐搭配我开发的 **[Codex EzMate](https://github.com/lkamhk/CodexEzMate)**——Windows 上的 Codex 常驻助手。它可以在后台启动或复用本地 App Server，提供登录、连接状态、重启和意外退出后恢复，方便 English Helper 随时连接使用。

除了 Server 托管，还可以查看 Codex 剩余用量、搜索及管理本地会话，以及监控指定的 Goal，在额度恢复后继续因额度耗尽而暂停的工作。

Codex EzMate 的默认 App Server 地址同样是 `ws://127.0.0.1:4500`。托管 Server 启动后，在 English Helper 中填入相同地址，再点击“测试连接／读取模型”即可。

> 🎉 **Codex EzMate 已正式发布！** 欢迎前往 [下载最新版本](https://github.com/lkamhk/CodexEzMate/releases/latest) 获取 Windows x64 安装版或免安装版，搭配 English Helper 使用；功能介绍和使用方法请参阅 [GitHub 项目](https://github.com/lkamhk/CodexEzMate)。

### ⚙️ 首次设置

先完成 Codex CLI 登录：

```powershell
codex login
```

然后启动本地 App Server：

```powershell
codex app-server --listen ws://127.0.0.1:4500
```

打开“服务设置 → English Helper”：

1. 供应商选择 **Codex App Server**。
2. 请求路径填入 `ws://127.0.0.1:4500`。
3. 点击“测试连接／读取模型”。
4. 模型留空则使用 server 默认值，或填入读取到的 model ID。
5. 保存后即可使用。

登录状态有效时，不需要每次重新执行 `codex login`。App Server 需要保持运行，也可以交由常驻程序在后台管理。仅打开 Codex 桌面 App，并不代表上述 WebSocket 端口已启动。

每次 Helper 查询会创建独立的 **ephemeral thread**，不沿用上一句对话。Saladict 本地翻译历史是另一项设置；如不想保留，请开启“翻译设置 → 停用历史记录”。

## 🧰 其他日常功能

| 功能         | 用法                             |
| ------------ | -------------------------------- |
| 划词翻译     | 选中文字，再使用快捷键或翻译图标 |
| 输入翻译     | 打开输入窗口，直接粘贴或输入文字 |
| 多服务翻译   | 按需添加服务，对照不同译文       |
| 剪贴板监听   | 从系统托盘启用，复制文字后触发翻译 |
| TTS 语音朗读 | 使用 Google／百度 TTS 朗读文字   |
| 生词收藏     | 支持 Anki、欧路词典等收藏服务    |
| 自动更新     | “About／关于 → 检查更新”        |

目前默认翻译服务为 **Yandex、DeepL Web、腾讯交互翻译**；需要自己的 API 或 AI 服务时，可再添加 Azure、OpenAI 等供应商。Google TTS 为默认朗读服务，百度 TTS 也支持中文朗读。

免费公共翻译服务可能限流；如果遇到 429，可稍后重试或切换服务。

## 🚀 开始使用

本版以 **Windows 11 x64** 为使用环境，图形界面使用 WebView2。

1. 使用本项目的 `saladict-ezmate-` Windows x64 安装包完成安装。
2. 启动后，从右下角系统托盘图标打开设置。
3. 选择翻译服务，设置划词翻译、截图翻译及 English Helper 快捷键。
4. 已安装版本可从“关于 → 检查更新”获取更新。

OneOCR 需要完整的引擎及模型资源，请勿仅单独移动主程序 EXE。如果出现资源缺失提示，请重新安装完整程序。

## 🛠️ 从源代码开发

准备 Node.js、pnpm、Rust、Windows C++ Build Tools 及 WebView2，再在项目目录执行：

```powershell
pnpm install
pnpm tauri dev
```

测试 OneOCR 时，需要在 `src-tauri/resources/oneocr/` 中准备 `oneocr.dll`、`oneocr.onemodel` 和 `onnxruntime.dll`。

## 💬 问题反馈与致谢

遇到问题或有功能建议，欢迎到 [GitHub Issues](https://github.com/lkamhk/saladict-ezmate-/issues) 留言。反馈时请附上程序版本、Windows 版本、使用的服务和复现步骤，请勿公开 API Key。

本项目衍生自 [Saladict](https://github.com/allentown521/saladict)，并继承 [Pot](https://github.com/pot-app/pot-desktop) 的开源基础，感谢原作者及贡献者。

项目源代码依 [GPL-3.0](LICENSE) 授权；第三方组件依各自许可证授权。
