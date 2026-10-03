# CSL Interactives

靜態中文學習互動入口網站。根目錄的 `index.html` 是入口頁；每個活動皆位於 `games/<activity-name>/`，並保有自己的程式碼與媒體檔案。

目前活動：

- `games/csl2-rolling/`：CSL2 中文轉球抽題
- `games/misc-falling_gifts/`：中文禮物大作戰（語音版）
- `games/misc-writing-gifts/`：中文寫字禮物大作戰（打字／實驗性手寫辨認）

寫字禮物遊戲每回合 2 分鐘，同時最多 2 個禮物，漏接不扣命；結束顯示總分、三色收藏數與成功答對字數。打字支援中文輸入法組字；iPhone/iPad 可在打字模式切換系統中文手寫鍵盤。網頁內 Canvas 辨認依賴瀏覽器的 Handwriting Recognition API 與繁體中文模型，沒有 API 時會停用該選項；有 API 也不保證支援繁體中文，尚未完成真實 iOS 裝置驗證。

新增活動時，請建立獨立資料夾、在入口首頁加入 tile，並確認活動內有清楚的「返回入口」連結。所有路徑都必須使用相對路徑，以支援 GitHub Pages 等靜態網站部署。
