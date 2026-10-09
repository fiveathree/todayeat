# 今日吃甚麼 — 命運大輪盤

食飯時間唔知食咩、又唔想叫外賣？撳一下，輪盤幫你喺附近揀一間。

## 點用

開 `index.html`（要 HTTPS 或者 localhost，瀏覽器先肯俾定位）→ 撳「幫我揀今餐食咩」→ 允許定位 → 輪盤自動轉 → 出結果。

- **就食呢間，帶我去**：開 Google 地圖步行導航，同時記低，之後 2 日唔會再抽到同一間
- **唔想食呢間，再轉**：剔走呢間再抽
- 偏好（最遠行幾遠、只要素食）同紀錄都儲喺瀏覽器 localStorage

## 資料來源

餐廳資料嚟自 [OpenStreetMap](https://www.openstreetmap.org/)，經 Overpass API 查詢，**唔使 API key、冇收費**。

限制：

- 餐廳齊唔齊視乎該區有冇人喺 OSM 標記
- 好多餐廳冇填營業時間。確定閂咗嘅會剔走；冇資料嘅照抽，結果頁會提「營業時間未確認」
- 冇評分、冇價位（OSM 冇呢啲資料），所以結果頁俾條連結去 Google 地圖睇

## 部署

純靜態單檔。GitHub repo → Settings → Pages → 揀 `main` branch 就得。

## 可以改嘅設定

`index.html` 嘅 `<script>` 頂部：`WHEEL_MAX`（輪盤幾多間）、`AVOID_REPEAT_DAYS`（幾多日唔重複）、`DIST_STEPS`（距離選項）。
