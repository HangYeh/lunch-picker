# lunch-picker

🍱 午餐選擇器：不知道中午吃什麼？按一下按鈕，從餐廳清單中隨機幫你挑一家。

整個專案只有一個 `index.html`，HTML、CSS、JavaScript 都寫在同一個檔案裡，不需要安裝或建置。

## 功能

- **隨機抽選**：按下「今天吃什麼？」，店名會快速輪流閃過並逐漸變慢，約 2.6 秒後停在結果上，同時在清單中標亮。之後可以按「再抽一次！」重抽。
- **新增餐廳**：在輸入框打店名後按「新增」或 Enter。空白或重複的店名不會加入，會顯示提示。
- **刪除餐廳**：按店名旁邊的 × 即可刪除。
- **自動儲存**：清單存在瀏覽器的 localStorage，重新整理或下次打開都還在。若瀏覽器停用 localStorage（例如某些無痕模式），頁面仍可使用，只是不會記住修改。
- **恢復預設清單**：一鍵換回預設的 10 家餐廳（會先確認）。
- **深色模式**：跟隨作業系統的淺色／深色設定自動切換，不需手動設定；系統切換時頁面會立即跟著變。
- **手機友善**：版面在手機寬度也能正常顯示。

預設清單：麥當勞、肯德基、摩斯漢堡、八方雲集、四海遊龍、吉野家、爭鮮、Subway、鼎泰豐、路邊自助餐。

## 使用方式

- **線上版**：<https://hangyeh.github.io/lunch-picker/>（需先完成下方「部署到 GitHub Pages」的設定）
- **本機**：直接用瀏覽器打開 `index.html` 即可。

## 自訂

- **預設餐廳**：修改 `index.html` 中的 `DEFAULT_RESTAURANTS` 陣列。已經存過清單的瀏覽器會繼續使用自己的清單，按「恢復預設清單」才會套用新的預設。
- **配色**：所有顏色都定義在 `<style>` 開頭的 `:root` CSS 變數中；深色模式的顏色在下方的 `@media (prefers-color-scheme: dark)` 區塊。

## 部署到 GitHub Pages

這個專案是純靜態網頁，`index.html` 就在 repo 根目錄，不需要建置或 GitHub Actions workflow，直接讓 GitHub Pages 從 `main` 分支發佈即可。

### 1. 確認 repo 可見度

GitHub 免費方案只能在 **public** repo 使用 GitHub Pages；private repo 需要 GitHub Pro、Team 或 Enterprise 方案。

若要改成 public：

1. 到 repo 的 **Settings** → **General**，捲到最下方 **Danger Zone**。
2. 按 **Change visibility** → **Change to public**，依指示輸入 repo 名稱確認。

> 改成 public 後，所有人都能看到程式碼與完整的 commit 歷史，請先確認裡面沒有不想公開的內容。

### 2. 開啟 GitHub Pages

1. 到 repo 的 **Settings** → **Pages**。
2. **Build and deployment** → **Source** 選 **Deploy from a branch**。
3. **Branch** 選 `main`，資料夾選 `/ (root)`，按 **Save**。

### 3. 等待發佈

約一到兩分鐘後，重新整理 **Settings** → **Pages** 頁面，上方會顯示網址：

<https://hangyeh.github.io/lunch-picker/>

發佈進度可以在 repo 的 **Actions** 分頁看到（名為 `pages build and deployment`）。之後每次合併到 `main`，網站都會自動更新。

> 注意：餐廳清單存在各自瀏覽器的 localStorage，每位訪客看到的都是自己的清單，彼此不會互相影響。
