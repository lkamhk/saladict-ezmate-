<div align="center">

  <img src="assets/branding/ezmate-icon.svg" width="150" alt="saladict-ezmate- 圖示"/>

  <h1>saladict-ezmate-</h1>

  <p>🖥️ Windows 桌面翻譯小幫手：🌐 選取即譯、📸 OneOCR 截圖辨識、✍️ AI 英文寫作。</p>

  <p><strong>🖥️ Windows x64 · 📸 OneOCR · 🌐 Azure Translator · ✍️ English Helper · 🔌 Codex App Server</strong></p>

  <p><strong>繁體中文</strong> | <a href="README_CN.md">简体中文</a></p>

</div>

由 Saladict 改版而來，針對 Windows 日常使用重新整理。保留方便嘅選取翻譯、輸入翻譯同語音朗讀，加入 Azure Translator、獨立 English Helper 視窗，以及 Codex App Server 接入。

圖示碗身嘅金色 **EZ** 標記，就係呢個改版嘅識別。

## 📸 Windows OneOCR：截圖翻譯，一框就得

**本版 OCR 已改用 Windows OneOCR——超強、無敵好用！**

遇到圖片、掃描文件、影片字幕，或者畫面上揀唔到嘅文字，按截圖翻譯快捷鍵，框住需要嘅範圍，就可以辨識文字並交畀翻譯服務。

-   **本機辨識**：OneOCR 喺電腦上處理截圖，辨識步驟毋須上傳圖片到 OCR 網站。
-   **框選即用**：由擷取畫面、辨識到翻譯接起來，省去逐字輸入同來回複製。
-   **毋須 OCR API Key**：使用 OneOCR 引擎及模型，唔使另外申請雲端 OCR 帳戶。

喺「快捷鍵設定 → 截圖翻譯（OneOCR）」設定自己順手嘅組合即可。

> 文字辨識可以本機完成；辨識後嘅文字會按你選用嘅翻譯服務處理。選擇線上翻譯時，文字仍會傳送到該服務。

## 🌐 Azure Translator：接入官方翻譯 API

新增 **Microsoft Azure Translator** 內建服務，可以使用自己嘅 Azure Translator 資源，包括 F0 資源(有每月免費額度,解決限流煩惱)。

支援自動偵測來源語言、繁體中文翻譯，以及 global、regional 或自訂 endpoint 設定。

設定方法：

1. 準備 Azure Translator 資源嘅 **Subscription Key**、**Region** 同 **Endpoint**。
2. 開啟「服務設定 → 翻譯 → 新增內建服務」，選擇 **Azure Translator**。
3. 填入 Key，按資源要求填寫 Region；Endpoint 使用資源提供嘅地址。
4. 按「儲存」，程式會先測試翻譯請求，成功後保存設定。

設定完成後，選取翻譯、輸入翻譯同截圖翻譯都可以使用 Azure。F0 嘅可用額度及限制以你嘅 Azure 資源為準。

## ✍️ English Helper：唔止翻譯，仲幫你寫好英文

**睇得明一句英文，同自己寫得自然，係兩回事。** English Helper 有獨立視窗同服務設定，適合寫訊息、回覆電郵、理解英文句子，或者檢查自己寫嘅英文。

你可以自行修改 Prompt，調整語氣、程度同輸出格式。

### 🤖 選擇你想用嘅 AI

English Helper 支援 **Ollama、OpenAI、DeepSeek、Claude、OpenAI-compatible API**，以及 **Codex App Server**。支援串流顯示回覆。

喺「服務設定 → English Helper」選擇供應商、模型及所需設定，再到「快捷鍵設定 → English Helper」設定快捷鍵。

選取文字後按快捷鍵，可以直接帶入 Helper；亦可以打開視窗自行輸入。想用本機模型，可以選擇 Ollama，預先安裝及下載模型後使用。

## 🔌 Codex App Server：English Helper 亦可以用 Codex

如果你已有 Codex CLI，可以將 **Codex App Server** 作為 English Helper 嘅 AI 供應商，沿用該 server 嘅登入狀態，毋須喺 Saladict 再填 Codex API Key。

### ⭐ 推薦搭配：Codex EzMate

想更方便管理 App Server，推薦搭配我開發嘅 **[Codex EzMate](https://github.com/lkamhk/CodexEzMate)**——Windows 上嘅 Codex 常駐助手。佢可以喺背景啟動或重用本機 App Server，提供登入、連線狀態、重新啟動同意外退出後恢復，方便 English Helper 隨時連線使用。

除咗 Server 代管，仲可以查看 Codex 剩餘用量、搜尋及管理本機會話，以及監控指定嘅 Goal，喺額度恢復後繼續因額度耗盡而暫停嘅工作。

Codex EzMate 嘅預設 App Server 地址同樣係 `ws://127.0.0.1:4500`。代管 Server 啟動後，喺 English Helper 填入相同地址，再按「測試連線／讀取模型」即可。

> 🎉 **Codex EzMate 已正式發佈！** 歡迎到 [下載最新版本](https://github.com/lkamhk/CodexEzMate/releases/latest) 取得 Windows x64 安裝版或免安裝版，搭配 English Helper 使用；功能介紹同使用方法請睇 [GitHub 專案](https://github.com/lkamhk/CodexEzMate)。

### ⚙️ 首次設定

先完成 Codex CLI 登入：

```powershell
codex login
```

然後啟動本機 App Server：

```powershell
codex app-server --listen ws://127.0.0.1:4500
```

到「服務設定 → English Helper」：

1. 供應商選擇 **Codex App Server**。
2. 請求路徑填入 `ws://127.0.0.1:4500`。
3. 按「測試連線／讀取模型」。
4. 模型留空使用 server 預設，或填入讀取到嘅 model ID。
5. 儲存後即可使用。

登入狀態有效時，唔需要每次重新 `codex login`。App Server 需要保持運行，亦可以交由你嘅常駐程式喺背景管理。只開啟 Codex 桌面 App，唔代表上述 WebSocket 端口已啟動。

每次 Helper 查詢會建立獨立 **ephemeral thread**，唔沿用上一句對話。Saladict 本機翻譯歷史係另一項設定；如不想保留，請開啟「翻譯設定 → 停用歷史記錄」。

## 🧰 其他日常功能

| 功能         | 用法                             |
| ------------ | -------------------------------- |
| 選取翻譯     | 選取文字，再使用快捷鍵或翻譯圖示 |
| 輸入翻譯     | 開啟輸入視窗，直接貼上或輸入文字 |
| 多服務翻譯   | 按需要加入服務，對照不同譯文     |
| 剪貼簿監聽   | 從系統匣啟用，複製文字後觸發翻譯 |
| TTS 語音朗讀 | 使用 Google／百度 TTS 朗讀文字   |
| 生詞收藏     | 支援 Anki、歐路詞典等收藏服務    |
| 自動更新     | 「About／關於 → 檢查更新」       |

目前預設翻譯服務為 **Yandex、DeepL Web、騰訊交互翻譯**；需要自己嘅 API 或 AI 服務時，可再加入 Azure、OpenAI 等供應商。Google TTS 為預設朗讀服務，百度 TTS 亦支援中文朗讀。

免費公共翻譯服務可能限流；如果遇到 429，可稍後重試或切換服務。

## 🚀 開始使用

本版以 **Windows 11 x64** 為使用環境，圖形介面使用 WebView2。

1. 使用本專案嘅 `saladict-ezmate-` Windows x64 安裝包完成安裝。
2. 啟動後，從右下角系統匣圖示開啟設定。
3. 選擇翻譯服務，設定選取翻譯、截圖翻譯及 English Helper 快捷鍵。
4. 已安裝版本可從「關於 → 檢查更新」取得更新。

OneOCR 需要完整嘅引擎及模型資源，請勿只單獨搬走主程式 EXE。若出現資源缺失訊息，請重新安裝完整程式。

## 🛠️ 從原始碼開發

準備 Node.js、pnpm、Rust、Windows C++ Build Tools 及 WebView2，再喺專案目錄執行：

```powershell
pnpm install
pnpm tauri dev
```

測試 OneOCR 時，需要喺 `src-tauri/resources/oneocr/` 準備 `oneocr.dll`、`oneocr.onemodel` 同 `onnxruntime.dll`。

## 💬 回報問題與致謝

遇到問題或有功能建議，歡迎到 [GitHub Issues](https://github.com/lkamhk/saladict-ezmate-/issues) 留言。回報時附上程式版本、Windows 版本、使用嘅服務同重現步驟，請勿貼出 API Key。

本專案衍生自 [Saladict](https://github.com/allentown521/saladict)，並承襲 [Pot](https://github.com/pot-app/pot-desktop) 嘅開源基礎，感謝原作者及貢獻者。

專案原始碼依 [GPL-3.0](LICENSE) 授權；第三方元件依各自授權。
