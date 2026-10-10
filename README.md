# 今日吃甚麼 — 命運大輪盤

吃飯時間不知道吃什麼、又不想叫外送？按一下，輪盤幫你在附近挑一間。

## 使用方式

打開 `index.html`（需要 HTTPS 或 localhost，瀏覽器才會允許定位）→ 按「幫我選這餐吃什麼」→ 允許定位 → 輪盤自動轉 → 顯示結果。

- **就吃這間，帶我去**：開啟 Google 地圖步行導航，同時記錄下來，之後 2 天不會再抽到同一間
- **不想吃這間，再轉**：剔除這間再抽一次
- 偏好（最遠走多遠、只要素食）和紀錄都存在瀏覽器的 localStorage

## 資料來源

餐廳資料來自 [OpenStreetMap](https://www.openstreetmap.org/)，透過 Overpass API 查詢，**不需要 API key、不收費**。

公共 Overpass 伺服器是免費服務，有時很慢甚至沒有回應，所以：

- 同時詢問幾個伺服器，採用最快回應的那個，最多等 20 秒，載入中可以取消
- 找到的餐廳清單會在瀏覽器保留 7 天。在同一個地方（例如公司）第二次打開不用再等網路
- 伺服器全部無法連線但有舊清單時，會先用舊清單

限制：

- 餐廳是否齊全，取決於該區有沒有人在 OSM 上標記
- 很多餐廳沒有填營業時間。確定已打烊的會剔除；沒有資料的照樣會抽到，結果頁會提示「營業時間未確認」
- 沒有評分和價位（OSM 沒有這些資料），所以結果頁提供連結到 Google 地圖查看

## 部署

純靜態，沒有 build step：`index.html` 加三個圖示檔（`favicon.svg`、`favicon.ico`、`apple-touch-icon.png`）。GitHub repo → Settings → Pages → 選擇 `main` branch 即可。

## 可調整的設定

`index.html` 的 `<script>` 開頭：`WHEEL_MAX`（輪盤放幾間）、`AVOID_REPEAT_DAYS`（幾天內不重複）、`DIST_STEPS`（距離選項）、`OVERPASS_ENDPOINTS`（地圖伺服器清單）。
