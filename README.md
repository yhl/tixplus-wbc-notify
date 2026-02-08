
## 2026/02/08 新增單一場次刊登狀態通知 tixplus-wbc-bysingle-notify.js

用法跟先前差不多，差別僅在於要指定場次編號（list_id）

list_id 每場次都有一固定數值，可參考程式碼內的對照表自行設定

## 程式有兩種版本，for Google App Script 以及 for nodejs

可依自己習慣及使用環境佈署

 - Google App Script 部份

需要至 專案設定 > ## 指令碼屬性 新增底下三組參數

> LINE Messaging API 的 Channel Access Token

CHANNEL_ACCESS_TOKEN	

> 你的 LINE User ID

LINE_USER_ID

> 刊登數量提醒，建議設 1，意即只要有刊登就會提醒

NUMBER_OF_REMINDERS

 - nodejs 部份

還須安裝相關套件
安裝依賴（第一次執行前在終端機跑一次）
npm init -y
npm install axios cheerio node-cron

也需要修改 CONFIG 中各項參數

    const CONFIG = {
    CHANNEL_ACCESS_TOKEN:  "_CHANNEL_ACCESS_TOKEN_", // LINE Messaging API 的 Channel Access Token
    USER_ID:  "_USER_ID_", // 你的 LINE User ID (U開頭)
    TARGET_URL:  "https://tradead.tixplus.jp/wbc2026", // tixplus 售票網址
    CHECK_INTERVAL:  "*/5 * * * *", // cron 格式，每 5 分鐘檢查一次（可自行調整）
    NUMBER_OF_REMINDERS:  1, // 刊登數量提醒，預設 1，意即只要有刊登就會提醒
    }

