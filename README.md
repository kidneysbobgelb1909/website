# 晉英精密工業 官方網站 · JIIN Tech Website

網址：**https://www.jiin-tech.com**

本文件說明網站的結構，以及如何修改網站內容。不需要寫程式的經驗，照著步驟做即可。

---

## 1. 網站是怎麼運作的

- 網站放在 GitHub，透過 **GitHub Pages** 免費上線。
- 上線的內容來自 **`website` 分支** 裡的 **`docs/` 資料夾**。
- 只要 `docs/` 裡的檔案一被更新（commit / push），**約 1 分鐘後**網站就會自動更新。
- 網站是純 HTML 檔案，沒有後台、沒有資料庫。

> ⚠️ 修改 `website` 分支 = 直接修改正式網站。修改前請先確認內容正確。

---

## 2. 檔案在哪裡

```
docs/
├── index.html         中文 首頁
├── about.html         中文 關於我們
├── contact.html       中文 聯絡我們
├── en/                英文版（index / about / contact）
├── de/                德文版（index / about / contact）
├── css/site.css       全站樣式（顏色、字型、版面）
├── assets/
│   ├── img/factory.jpg      首頁大圖（工廠照片）
│   └── logo/                Logo 檔案
│       ├── jiin-logo.svg        頁首用（淺色底）
│       ├── jiin-logo-dark.svg   頁尾用（深色底）
│       └── jiin-symbol.svg      瀏覽器分頁小圖示
└── CNAME              網域設定 —— ⛔ 請勿刪除或修改
```

網站共 **9 個頁面**：3 種語言（中文、English、Deutsch）× 3 頁（首頁、關於我們、聯絡我們）。

> 專案根目錄的 `src/`、`dist/`、`scripts/`、`package.json` 是舊版樣板留下的檔案，**目前沒有使用**，修改它們不會影響網站。

---

## 3. 如何修改文字（最常用）

### 方法 A：直接在 GitHub 網頁上修改（推薦，不需安裝任何軟體）

1. 登入 GitHub，打開 https://github.com/kidneysbobgelb1909/website
2. 確認左上角分支選的是 **`website`**
3. 進入 `docs/`，點選要修改的檔案（例如 `about.html`）
4. 點右上角的 **鉛筆圖示 ✏️（Edit this file）**
5. 用 `Ctrl+F` / `Cmd+F` 找到要改的文字，直接修改
   - 只改 `>` 和 `<` 之間的文字，**不要動到 `<...>` 標籤本身**
   - 例如：`<p>這段文字可以改</p>`
6. 點右上角 **Commit changes…**，寫一句說明（例如「更新公司簡介」），按 **Commit changes**
7. 約 1 分鐘後到網站確認（若看到舊內容，按 `Ctrl+Shift+R` / `Cmd+Shift+R` 強制重新整理）

### 方法 B：在自己電腦上修改並預覽

適合一次改很多地方。需要安裝 Git 與 Python（Mac 已內建 Python）。

```bash
git clone git@github.com:kidneysbobgelb1909/website.git
cd website
git checkout website

# 開啟本機預覽
cd docs
python3 -m http.server 8000
# 用瀏覽器打開 http://localhost:8000
```

修改檔案後重新整理瀏覽器即可看到結果（尚未上線）。確認沒問題後：

```bash
git add docs
git commit -m "說明這次改了什麼"
git push origin website
```

---

## 4. 修改時的重要規則

### ✅ 三種語言要一起改
同一段內容在中文、英文、德文頁面各有一份。改了中文版，請記得也修改：
- `docs/xxx.html`（中文）
- `docs/en/xxx.html`（英文）
- `docs/de/xxx.html`（德文）

如果不確定英文或德文怎麼寫，可以先改中文，再請人協助翻譯；但不要讓三個版本的事實資料（例如設備數量、電話）不一致。

### ✅ 頁首與頁尾在每一頁都有一份
選單、Logo、頁尾的公司資訊，**9 個頁面各有一份**。要修改時，9 個檔案都要改。

### ✅ 聯絡資訊出現在多個地方
更改 **電話、Email、地址** 時，請在全部 9 個檔案中搜尋舊的內容並全部替換：

| 資訊 | 搜尋這段文字 |
|---|---|
| 電話（中文頁） | `03-5534528` |
| 電話（英/德文頁） | `+886-3-553-4528` |
| 電話（撥號連結，所有頁） | `tel:+88635534528` |
| Email | `info@jiin-tech.com` |
| 地址（中文） | `新竹縣竹北市中和街52號` |
| 地址（英/德文） | `No. 52, Zhonghe St.` |

地圖連結與地圖（聯絡我們頁）使用的是網址編碼後的中文地址，若地址變更，請一併更新 `contact.html` 中的 `maps.google.com` 連結。

### ⛔ 不要做的事
- 不要刪除或修改 `docs/CNAME`（會讓 www.jiin-tech.com 失效）
- 不要改檔名或資料夾名稱（會造成連結失效）
- 不要上傳未壓縮的大圖（見下方）
- 不要在網站上公開客戶名稱，除非客戶已同意

---

## 5. 常見修改對照表

| 想修改的內容 | 檔案 | 搜尋關鍵字 |
|---|---|---|
| 首頁大標題 | `index.html` | `<h1>` |
| 首頁四個數字（1994、ISO 9001…） | `index.html` | `fact-value` |
| 技術能力三張卡片 | `index.html` | `card-num` |
| 設備說明（沖床噸數範圍） | `index.html` | `80 至 160 噸` |
| 公司簡介文字 | `about.html` | `class="prose"` |
| 公司概要（成立、認證…） | `about.html` | `rule-list` |
| 藍色「有新的專案嗎？」區塊 | `index.html`、`about.html` | `class="cta"` |
| 搜尋引擎顯示的網站描述 | 每一頁 | `name="description"` |
| 瀏覽器分頁標題 | 每一頁 | `<title>` |

**範例：新增一台 200 噸沖床（噸數範圍變成 80–200 噸）**
1. `index.html`：首頁上方數字區的「80–160 噸」，以及設備說明「涵蓋 80 至 160 噸」
2. `about.html`：公司概要中的「設備」一行
3. 英文版、德文版搜尋 `80–160 t` 並重複以上步驟

> 網站上只寫噸數範圍，**不寫沖床台數**。

---

## 6. 圖片與 Logo

### 更換或新增照片
1. 先把照片縮小：寬度約 **2000 像素以內**、檔案大小 **500 KB 以內**、格式 **JPG**
   - Mac：在「預覽程式」→ 工具 → 調整大小；輸出時選 JPEG、品質調低
   - 也可使用 https://squoosh.app 線上壓縮
2. 檔名只用 **英文小寫、數字、連字號**，例如 `press-160t.jpg`（不要有空白或中文）
3. 放到 `docs/assets/img/`
4. 首頁大圖目前是 `factory.jpg`，設定在 `docs/css/site.css` 中搜尋 `factory.jpg`；若用同一個檔名直接覆蓋，就不必改程式碼

### Logo
Logo 檔案在 `docs/assets/logo/`。若要更換，請用相同檔名覆蓋：
- `jiin-logo.svg`：頁首（白底，黑字 + 品牌藍點）
- `jiin-logo-dark.svg`：頁尾（深色底，白字 + 亮藍點）
- `jiin-symbol.svg`：瀏覽器分頁小圖示

---

## 7. 品牌顏色與字型

顏色統一設定在 `docs/css/site.css` 最上方的 `:root` 區塊。

| 用途 | 色碼 |
|---|---|
| 品牌藍（按鈕、重點） | `#0a5aa8` |
| 深色底上的亮藍（頁尾 Logo） | `#3d8fe0` |
| 主要文字 | `#16191d` |
| 深色背景（頁尾、頁首區塊） | `#1c2026` |

字型：英文使用 **Inter**，中文使用 **Noto Sans TC**（由 Google Fonts 載入）。

---

## 8. 改壞了怎麼辦

每一次修改都有紀錄，可以還原。

- **GitHub 網頁**：打開該檔案 → 點 **History** → 找到改壞之前的版本 → 點 `...` → **View file** → 複製內容，回到檔案編輯並貼上覆蓋 → Commit
- **指令列**：
  ```bash
  git log --oneline          # 找到要撤銷的那次修改
  git revert <修改編號>
  git push origin website
  ```

---

## 9. 其他說明

- **聯絡表單**：網站目前沒有線上表單（GitHub Pages 無法接收表單資料），客戶透過 Email 與電話聯絡。若日後需要表單，可使用 Formspree 等服務。
- **新增頁面**：複製一個相近的頁面（例如 `about.html`）並改名，修改內容後，記得在 9 個頁面的選單（`<nav class="nav"`）與頁尾中加上連結，三種語言都要新增。
- **網域**：`www.jiin-tech.com` 的 DNS 指向 GitHub Pages（`kidneysbobgelb1909.github.io`），設定在網域註冊商處，一般不需要更動。

---

© 晉英精密工業有限公司 JIIN TECH INDUSTRIAL CO., LTD.
