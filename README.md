# 課堂加分管理系統

此專案提供一個簡易的「課堂加分管理」網頁系統，包含以下功能：

1. **日曆**  
   - 支援「上一個月」與「下一個月」切換。  
   - 點擊任意日期，即可進入加扣分畫面。

2. **加扣分**  
   - 依照選定日期，對指定班級、學生進行加分或扣分。  
   - 若當日尚無分數紀錄，系統會自動使用「前一日」的分數做為基礎。  
   - 當加扣分後，後續日期也會同步累計調整。

3. **違規紀錄**  
   - 可記錄學生違規行為，並在日後查看或刪除單筆違規紀錄。

4. **每月統計圖表**  
   - 使用 [Chart.js](https://www.chartjs.org/) 呈現當月各學生分數總和的長條圖。

5. **分組管理**  
   - 可設定分組數量、選擇組員，並對分組進行加扣分。  
   - 當對分組進行加扣分，該組內所有學生的分數也會一併更新。

6. **隨機選擇學生**  
   - 在加扣分畫面可隨機抽出一位學生作答。

7. **獎品兌換**  
   - 可新增、編輯、刪除獎品，設定「尚餘數量」及「所需分數」。  
   - 當學生要兌換獎品時，若分數足夠，系統會扣除學生分數並減少獎品庫存，同時記錄兌換紀錄。

8. **新增 / 刪除學生**  
   - 在加扣分畫面中，可針對目前班級新增或刪除學生。

9. **刪除班別**  
   - 針對選定的班別進行刪除（含班級下所有學生）。

10. **匯入 / 匯出 JSON**  
    - 可將所有資料（包含班級、學生、分數、違規紀錄、分組資料、獎品清單、兌換紀錄）匯出為 JSON 檔案。  
    - 也可匯入 JSON 檔案，載入先前的所有資料。

---

## 使用方式

1. **下載 / 複製** 本專案：  
   - 將本專案 Clone 或下載 ZIP 後解壓縮到本地。

2. **打開 `index.html`**：  
   - 直接使用瀏覽器開啟 `index.html` 檔案，或使用任意靜態伺服器（如 `live-server`）執行。  
   - 預設顯示 2025/2 的月曆，點選任意日期即可進入加扣分畫面。

3. **操作流程**：  
   1. 如需管理多個班級與學生，可在「新增班級與學生」中輸入班級名稱以及學生清單（每行一位學生，格式如 `15陳小明`）。  
   2. 在日曆中點選日期，進入加扣分畫面，於上方班級下拉選單選取班級後即可進行加扣分或違規紀錄。  
   3. 如需顯示每月統計圖表，可點選「每月統計」按鈕。  
   4. 如需分組管理，可點選「設定分組」，輸入分組數量，然後對組別加扣分。  
   5. 隨機選擇學生：於加扣分畫面中可點選「隨機選擇學生」。  
   6. 獎品兌換：於「獎品兌換」畫面中可新增獎品，並為學生進行兌換。  
   7. 若要新增 / 刪除學生，或刪除班別，則在加扣分畫面進行操作。  
   8. 可於「匯入 / 匯出 JSON」中儲存或載入先前的資料。

4. **注意事項**：  
   - 若匯入 JSON 後想立即看到新資料，請確認是否已在加扣分畫面。系統會自動刷新目前顯示的日期與班級。  
   - 如果日曆仍無法顯示，請在瀏覽器 Console 檢查是否有 JavaScript 錯誤，並確保已完整複製 `index.html` 內所有程式碼。

---

## 資料結構

- `allData`  
  - `classes`: `[ { className, students: [ { code, name, scores, infractions, redemptions } ] }, ... ]`
- `prizeList`: `[ { id, name, quantity, requiredPoints }, ... ]`
- `groupData`: 依照日期 & 班級記錄分組情況 `{ '20250213': { 0: { groups: [...] } }, ... }`
- `currentScoreDate`: 當前選取的日期，如 `"20250213"`

---

## 授權

此專案僅供學習與教學示範用途。若有任何問題或建議，歡迎於 Issue 區提出或進行 PR。

---

歡迎在使用本專案時提供回饋或貢獻程式碼，共同使此「課堂加分管理系統」更加完善！
