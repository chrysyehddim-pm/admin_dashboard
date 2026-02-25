# 健康數據中心 - 管理員後台

管理員後台用於檢視與匯出「健康數據中心」專案中 Firebase Firestore 的各類活動與遊戲紀錄。

## 功能說明

- **管理員登入**：使用 Firebase Authentication 信箱／密碼登入，僅授權管理員可存取後台。
- **多資料表切換**：可選擇不同 Firestore 集合，預覽最新 10 筆資料。
- **資料匯出**：支援將所選集合的**全部資料**匯出為 **CSV** 或 **Excel (xlsx)**。

### 支援的資料表

| 集合名稱 | 說明 |
|----------|------|
| `one_day_manager_results` | 一日店長 |
| `memory_game_results` | 記憶力訓練 |
| `squat_records` | 深蹲紀錄（新版） |
| `squatRecords` | 深蹲紀錄（舊版） |
| `emotion_records` | 情緒紀錄 |
| `game_records` | 幸福柑仔店遊戲紀錄 |

## 技術與依賴

- **Firebase**（CDN）：Firestore、Authentication（compat 版 10.8.1）
- **SheetJS (xlsx)**：用於產生 CSV / Excel 檔案（CDN 0.20.1）
- 單一 HTML 頁面，無需建置流程

## 使用方式

1. 在專案目錄中，用瀏覽器直接開啟 `admin.html`，或透過本地靜態伺服器（例如 `npx serve .`）存取。
2. 輸入已於 Firebase 設定的管理員信箱與密碼後登入。
3. 在「選擇資料表」下拉選單中選擇要檢視的集合。
4. 畫面上會顯示該集合最新 10 筆預覽；點擊「下載 CSV」或「下載 Excel」可匯出該集合的**全部資料**。

## 注意事項

- **Firebase 設定**：`admin.html` 內已包含專案 `smart-squat-health` 的 Firebase 設定。若更換專案或環境，請在檔案中更新對應的 `firebaseConfig`。
- **權限**：僅已於 Firebase Authentication 建立且具 Firestore 讀取權限的帳號可登入並檢視／匯出資料。請在 Firebase Console 中正確設定 Firestore 安全規則與授權帳號。
- **匯出範圍**：匯出時會抓取所選集合的**全部文件**，資料量大時可能需要較長時間。

## 專案結構

```
admin_dashboard/
├── admin.html   # 後台單頁（登入、選表、預覽、匯出）
└── README.md    # 本說明檔
```
