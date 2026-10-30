# Neurosynth 心理資訊學作業

公開網站：**[https://neurosynth-homework-2026.onrender.com](https://neurosynth-homework-2026.onrender.com)**

完整後端下載：[neurosynth_backend.zip](https://github.com/samueltiong209-stack/neurosynth-homework-2026/raw/refs/heads/main/neurosynth_backend.zip)

使用 Flask + PostgreSQL，查詢原始 TF-IDF 分數與 MNI 座標；每篇論文只計一次。公開 HTTPS 的 39 項交叉驗證全部通過，核對每頁的完整研究 ID 與論文資訊。ZIP 包含原始碼、套件、匯入工具、可攜資料、部署設定、中文 README 與測試報告，不含密碼、虛擬環境或舊模型。

|API|公開範例|結果|
|---|---|---:|
|詞彙研究|[memory](https://neurosynth-homework-2026.onrender.com/terms/memory/studies)|2,744 篇|
|座標研究|[-22, 0, -20](https://neurosynth-homework-2026.onrender.com/locations/-22_0_-20/studies)|547 篇|
|暫定詞彙比較|[memory − fear](https://neurosynth-homework-2026.onrender.com/dissociate/terms/memory/fear)|2,702 篇|
|暫定座標比較|[左側位置 − 右側位置](https://neurosynth-homework-2026.onrender.com/dissociate/locations/-22_0_-20/22_0_-20)|344 篇|

**實作假設**：詞彙分數 > 0，座標半徑 6 mm；可用 threshold/radius 調整。dissociate 暫定為 A − B，尚未經老師確認，不是統計雙重分離檢定。老師提供的參考 repo 回傳 404。

網站與資料庫均為 Render Free／$0。網站閒置 15 分鐘會休眠；PostgreSQL 在 **2026/11/29 22:42:19 台北時間**到期，到期後無法查詢。[官方限制](https://render.com/docs/free)。

## 重建部署

ZIP 解壓到 backend/。本 repository 使用 ZIP 來源，Render 的 Root Directory 留空。

Build Command:
```sh
python -m zipfile -e neurosynth_backend.zip . && python -m pip install -r backend/requirements.txt
```

Start Command:
```sh
sh backend/start.sh
```

Python 3.14.0；Health Check /health；環境變數 DATABASE_URL 使用同區域 Free PostgreSQL 的內部 URL。serve.py 先監聽 HTTP，再背景原子匯入；資料提交前 health 不成功。完整設定見 ZIP 內 DEPLOYMENT.md。

最後 ZIP 更新補充公開驗證與交付說明，程式與套件與已部署 commit 3998e6e 完全一致，見 ZIP 的 reports/deployed_code_match.json。
