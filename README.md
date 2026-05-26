# TSV 資料檔讀取程式 (TSV File Reader)

這是一個使用 C# Windows Forms 開發的桌面應用程式，主要功能為讀取以 Tab 鍵分隔的資料檔（TSV 或 TXT 格式），並將其內容（例如：單字、音標、音檔路徑及解釋）結構化地顯示於表格 (ListView) 中，方便使用者瀏覽與檢視。

## 專案簡介

本專案實作了基礎的檔案 I/O 操作與自訂物件集合管理，適合用於讀取簡易的自建字典檔或單字卡資料。

### 功能特色
* **支援多種副檔名**：可讀取 `.tsv` 以及 `.txt` 格式的純文字檔案。
* **UTF-8 編碼支援**：確保讀取包含中文或其他多國語言的資料時不會產生亂碼。
* **資料解析與顯示**：自動將每行資料依據 Tab (`\t`) 符號切割，並對應至「單字」、「音標」、「音檔路徑」與「解釋」四個欄位。若解釋欄位含有多段內容，程式會自動將其合併並換行顯示。
* **狀態列提示**：成功讀取檔案後，視窗底部狀態列會顯示成功載入的單字總數。
* **防呆機制**：關閉程式時會彈出確認視窗，避免使用者誤觸導致未預期的關閉。

## 專案架構

本專案包含以下核心類別：

* **`Program.cs`**：程式的進入點 (Main Method)。
* **`frmTSVFile.cs`**：應用程式主視窗，包含功能表 (MenuStrip)、清單檢視 (ListView) 以及狀態列 (StatusStrip)，處理所有的 UI 互動與檔案讀取事件。
* **`frmAbout.cs`**：「關於」視窗，透過反射 (Reflection) 讀取並顯示專案的組件資訊（版本、版權、產品名稱等）。
* **`WordItem.cs`**：資料模型類別，代表單一單字項目。內建字串處理邏輯，能在建構時將傳入的單行字串解析為對應屬性。
* **`WordCollection.cs`**：繼承自 `Collection<WordItem>` 的自訂集合類別，負責批次處理字串陣列並轉換為 `WordItem` 物件清單。

## 執行說明

### 系統需求
* Windows 作業系統
* .NET Framework (支援 Windows Forms)
* Visual Studio (建議 2019 或更新版本)

### 操作步驟
1. 使用 Visual Studio 開啟本專案的方案檔 (`.sln`)。
2. 按下 `F5` 或點選「開始」建置並執行應用程式。
3. **載入資料**：
   * 在程式主畫面左上角點選 **「檔案(F)」** > **「開啟(O)」**。
   * 選擇一個以 Tab 鍵分隔內容的 `.tsv` 或 `.txt` 檔案（檔案編碼需為 UTF-8）。
   * 載入成功後，資料會顯示於主畫面的表格中。
4. **檢視關於**：
   * 點選 **「幫助(H)」** > **「關於(A)」** 可查看程式的版本與版權資訊。
5. **離開程式**：
   * 點選 **「檔案(F)」** > **「離開(X)」** 或直接點選視窗右上角的關閉按鈕，系統會跳出確認視窗，點選「是」即可關閉程式。

## 📸 系統畫面截圖

### 1. 程式主畫面
資料讀取前的主視窗介面，包含清晰的資料欄位標題。
<img width="747" height="485" alt="image" src="https://github.com/user-attachments/assets/5af86541-3c5b-4655-ac0c-fd8c1629cd46" />


### 2. 檔案選單
提供開啟檔案 (`OpenFileDialog`) 與離開程式的功能。
<img width="749" height="486" alt="image" src="https://github.com/user-attachments/assets/bdcf50c2-6263-4550-8cf8-f90b090a3d2a" />
<img width="932" height="587" alt="image" src="https://github.com/user-attachments/assets/dd029155-9c3e-4081-ae8b-3603d1e06058" />
<img width="750" height="486" alt="image" src="https://github.com/user-attachments/assets/f17ccf66-f83b-4ca2-8e2b-8fee38d100a1" />


### 3. 幫助選單
可呼叫出「關於」視窗檢視程式版本資訊。
<img width="750" height="485" alt="image" src="https://github.com/user-attachments/assets/941c8e5a-a05d-4987-858d-3d191b823de4" />
<img width="749" height="484" alt="image" src="https://github.com/user-attachments/assets/931f39fe-a9ad-4136-b9a2-27f607b1c80c" />

