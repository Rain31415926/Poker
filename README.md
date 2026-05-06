# C# WinForm Poker Game

這是一個使用 C# Windows Forms 開發的簡易撲克牌遊戲 (Video Poker)。玩家可以進行下注、發牌、選擇換牌，最終由系統自動判定牌型並給予對應賠率的獎金。

## 🎮 遊戲功能

- **下注系統**：包含加註 (+500)、減注 (-500) 以及 梭哈 (All-in) 功能。
- **洗牌機制**：模擬真實 52 張牌隨機洗牌，確保遊戲公平性。
- **換牌邏輯**：玩家可點擊牌面選擇要留下的牌或要換掉的牌（翻至背面代表換牌）。
- **自動牌型判定**：支持以下牌型判定：
  - 同花大順 (Royal Flush) - 250倍
  - 同花順 (Straight Flush)
  - 鐵支 (Four of a Kind) - 25倍
  - 葫蘆 (Full House) - 9倍
  - 同花 (Flush) - 6倍
  - 順子 (Straight) - 4倍
  - 三條 (Three of a Kind) - 3倍
  - 兩對 (Two Pair) - 2倍
  - 一對 (One Pair) - 1倍

## 🛠️ 技術實作細節

### 1. 牌值計算公式
程式碼將 52 張牌簡化為 0-51 的整數，透過數學運算快速分離花色與點數：
- **花色 (Suit)**: `cardIndex % 4` (0:梅花, 1:方塊, 2:愛心, 3:黑桃)
- **點數 (Point)**: `cardIndex / 4` (0:A, 1:2, ..., 12:K)

### 2. 牌型判定演算法
利用 `Array.Sort` 對點數出現頻率進行降冪排序：
- 若 `pointCount[0] == 4` ➔ **鐵支**。
- 若 `pointCount[0] == 3 && pointCount[1] == 2` ➔ **葫蘆**。
- 利用 `Max()` 與 `Min()` 差值判斷 **順子**。

### 3. 開發者測試後門 (Debug Mode)
在遊戲過程中（發牌後），可以透過鍵盤快捷鍵快速變更手牌進行判定測試：
- `Q`: 同花大順
- `W`: 同花順
- `E`: 同花
- `R`: 鐵支
- `T`: 葫蘆
- `Y`: 三條

## 🚀 如何執行

1. 使用 Visual Studio 打開專案。
2. 確保 `Resources` 內已加入對應的撲克牌圖片。
3. 編譯並執行專案即可開始遊戲。

## 📸 使用畫面展示 (UI Showcase)

### 1. 初始狀態與下注
開啟程式後，預設資金為 **1,000,000**。玩家可以透過 `+` / `-` 按鈕或手動輸入金額，最後按下 **[押注]** 或 **[梭哈]** 啟動遊戲。
> *註：下注後，「發牌」按鈕才會啟用，確保遊戲流程正確。*

### 2. 發牌與選擇換牌
點擊 **[發牌]** 後，系統會從 52 張牌中隨機抽出 5 張。
- **操作方式**：點擊牌面圖片，牌會翻至「背面」，代表你想**換掉**這張牌。
- **保留策略**：留在「正面」的牌代表你想要保留。

### 3. 換牌與判定
按下 **[換牌]** 後，系統會將翻至背面的牌替換成新牌。接著點擊 **[判斷牌型]**，系統將自動：
- 檢查是否符合特殊牌型。
- 計算對應賠率。
- 將贏得的金幣匯入總資金。
- 顯示結果於標籤（例如：`梅花 一對，贏得 500 元`）。


## 🎞️ 操作示範 (Giphy / Image Placeholder)

### 遊戲主畫面

<img width="744" height="471" alt="image" src="https://github.com/user-attachments/assets/95693585-5ec1-4617-9698-7a60c0198d1c" />

### 換牌展示
<img width="741" height="476" alt="image" src="https://github.com/user-attachments/assets/a5ea910a-72f3-461a-84d7-3f240440ca47" />
<br>
<img width="742" height="476" alt="image" src="https://github.com/user-attachments/assets/e1281877-a4b6-4a04-a690-67f1d902a65a" />
<br>
<img width="742" height="479" alt="image" src="https://github.com/user-attachments/assets/ad9edae0-a022-42c5-b30b-65ca6d9d8777" />
  
### 牌型判定結果

<img width="742" height="473" alt="image" src="https://github.com/user-attachments/assets/f20eef27-d492-413d-acbe-a4c65849e84d" />

