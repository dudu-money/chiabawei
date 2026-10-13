# 呷飽未

高雄早餐到宵夜的店家清單，名字取自台語的「吃飽了沒」。可以放在 GitHub Pages，加到手機主畫面當 App 用，接上 Firebase 之後家人朋友可以共用同一份清單。

沒有設定 Firebase 也能用，這時清單只存在那一個瀏覽器裡（單機模式）。

## 檔案

- `index.html`：整個網站
- `firebase-config.js`：貼 Firebase 設定的地方
- `firestore.rules`：Firestore 安全規則
- `manifest.webmanifest`，`sw.js`，`icon-*.png`，`apple-touch-icon.png`：讓它能加到主畫面

## 步驟 1：建立 Firebase 專案

1. 到 Firebase 主控台，新增專案（免費的 Spark 方案就夠）。
2. 專案首頁按「</>」新增網頁應用程式，名稱隨意，不用勾 Firebase Hosting。
3. 畫面會出現一段 `firebaseConfig`，把裡面的內容複製到 `firebase-config.js`，格式照檔案裡的範例，把 `null` 換成那一段。

## 步驟 2：打開 Email 登入

Authentication，開始使用，登入方式，電子郵件/密碼，啟用，儲存。

## 步驟 3：建立 Firestore 並貼上規則

1. Firestore Database，建立資料庫，選正式版模式，位置選台灣（asia-east1）或附近的。
2. 進入「規則」分頁，把 `firestore.rules` 的內容整段貼上，按發布。

## 步驟 4：放到 GitHub Pages

1. 在 GitHub 新增一個 repository，例如 `kaohsiung-food`。
2. 把這個資料夾裡的所有檔案上傳到 repository 最上層。
3. Settings，Pages，Source 選 `Deploy from branch`，Branch 選 `main`，資料夾選 `/ (root)`，儲存。
4. 等一兩分鐘，網址會是 `https://你的帳號.github.io/kaohsiung-food/`。

## 步驟 5：加到手機主畫面

- iPhone：用 Safari 開網址，按分享，選「加入主畫面」。
- Android：用 Chrome 開網址，按選單，選「安裝應用程式」或「加到主畫面」。

主畫面上會有自己的圖示，開起來是全螢幕。

## 怎麼共用

1. 自己先註冊登入。第一次登入會自動建立「我的清單」，這支手機原本存的店家會一起搬上去。
2. 在清單區按「分享連結」，把連結傳給家人朋友。
3. 對方打開連結，註冊或登入後就會加入同一份清單。成員都能新增和刪除店家。
4. 想分成不同群組，可以按「新增清單」，例如「我和老公」，「朋友聚餐」，各自分享不同連結。

## 更新網站後手機沒變

把 `sw.js` 最上面的 `kh-food-v4` 改成 `kh-food-v5`，再上傳，手機就會重新下載。

## 想放其他縣市的店

推薦店家目前只有高雄，但「我的清單」可以放全台灣的店。按「新增店家」，縣市填例如「台南市」，行政區填例如「安平區」。清單裡有兩個以上的縣市時，篩選列會自動出現「所有縣市」的下拉選單。Google 地圖連結會用那家店自己的縣市去搜尋，不會跑到高雄。

如果想把其他縣市的推薦也放進內建清單，打開 `index.html`，找到 `BASE` 這一段，照現有格式再加幾行，並把 `BASE.forEach` 那一行改成依各家店自己的縣市設定。

## 想換顏色

`index.html` 開頭 `:root` 裡的變數就是配色，目前是青綠底加燕麥米色的單色系，不分淺色深色。改完再依上一段更新版本號。
