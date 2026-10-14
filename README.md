# 快打旋風 6 好友對戰排行榜

純前端網頁（單一 `index.html`），可直接部署到 GitHub Pages。
戰績存在 Firebase Firestore，所有朋友開同一個網址就看到同一份排行榜，即時同步。

沒設定 Firebase 時會自動變成「單機模式」（資料只存在各自瀏覽器）。

## 1. 建立 Firebase（免費）

1. 到 https://console.firebase.google.com → 新增專案
2. 左側 **Build → Firestore Database** → 建立資料庫（選離你近的地區，例如 `asia-east1`，模式選「正式版」）
3. Firestore 的 **規則** 分頁：貼上 `firestore.rules` 的內容 → 發布
4. **專案設定（齒輪）→ 一般 → 你的應用程式 → 新增 Web 應用程式 (`</>`)**，複製畫面上的 `firebaseConfig`
5. 打開 `index.html`，把 `FIREBASE_CONFIG` 的 `apiKey / authDomain / projectId / appId` 換成你的

> Web 的 `apiKey` 不是密碼，放在公開 repo 沒問題；安全性靠第 3 步的 Firestore 規則。

## 2. 上傳到 GitHub 並開啟 Pages

1. 在 GitHub 建立新 repo（例如 `sf6-leaderboard`），把 `index.html`、`README.md`、`firestore.rules` 放進去
2. repo 的 **Settings → Pages**
3. **Source** 選 *Deploy from a branch*，Branch 選 `main`、資料夾 `/ (root)` → Save
4. 等 1～2 分鐘，網址會是 `https://你的帳號.github.io/sf6-leaderboard/`

## 房間

網址後面加 `?room=名字` 可以開不同的排行榜，例如 `.../?room=dorm`。
房間名稱就像一個不公開的暗號：知道網址的人都能看、能寫，所以不要把連結公開貼出去。

## 注意

- 目前沒有登入機制：知道網址的人都能新增或刪除戰績。只給朋友群用就夠；想更嚴格可以再加 Firebase Authentication。
- Firebase 免費額度（Spark）對朋友對戰紀錄綽綽有餘。
