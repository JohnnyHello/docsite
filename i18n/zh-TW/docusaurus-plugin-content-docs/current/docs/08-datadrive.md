---
id: datadrive
sidebar_position: 8
---

# Datadrive

Datadrive 是 Glows.ai 提供的雲端儲存空間，可在您建立實例時，掛載至您的虛擬機器或容器中使用，也能讓您在不同實例之間存取與共用資料。

---

## **Datadrive主頁面**

點擊側邊欄的 **Data Drive** 進入頁面，此頁面中會直接顯示您存放的資料，並提供多種操作功能。您可以透過直觀的介面管理您的數據文件。
  ![](../../../../../docs/docs-images/p06/01.png)


該頁面顯示不同區域的標籤頁，不同區域的 Datadrive 資料彼此獨立，例如：
  1. **JP-01**
  2. **TW-03**
  3. **TW-04**
  ![](../../../../../docs/docs-images/p06/02.png)

---

## **主畫面按鈕功能**

![](../../../../../docs/docs-images/p06/03.png)


### **1. Refresh**

- **功能**：重新整理列表，顯示最新的檔案與資料夾狀態。

### **2. New Folder**

- **功能**：新增一個新的資料夾。
- **操作流程**：
  1. 點擊 **New Folder** 按鈕。
  2. 在彈出的對話框中輸入資料夾名稱。
  3. 點擊確認後，新的資料夾將顯示於列表中。

### **3. Upload**

- **功能**：上傳檔案到當前的區域（例如：`JP-01`、`TW-04`等）位置。
  >請注意：Datadrive 網頁版不支援上傳資料夾檔案功能，若需要上傳資料夾檔案，請使用 Datadrive 桌面版。
- **操作流程**：
  1. 點擊 **Upload** 按鈕。
  ![](../../../../../docs/docs-images/p06/04.png)

  2. 選擇要上傳的檔案。
  ![](../../../../../docs/docs-images/p06/05.png)

  3. 上傳完成後，檔案將顯示於列表中。


---

## **檔案與資料夾列表**

在 Datadrive 主頁面中，您將看到一個列出所有檔案與資料夾的清單，包含以下欄位：

- **Name**：檔案或資料夾的名稱。
- **Size**：檔案或資料夾的大小。
- **Last Modified**：檔案或資料夾的最後修改時間。
![](../../../../../docs/docs-images/p06/06.png)


### **檔案操作按鈕（Actions）**

任何一列檔案，被點擊或者鼠標 hover 時，提供以下操作選項：

- **Download**：下載指定的檔案。
  > **注意**：此功能僅適用於檔案，資料夾無法直接下載。
- **Move**：將檔案或資料夾移動到其他位置。
- **Rename**：對名稱進行重新命名。
- **Delete**：刪除指定的檔案或資料夾。
![](../../../../../docs/docs-images/p06/07.png)


---
## **掛載/使用 Datadrive**

### 建立實例時掛載 Datadrive

 **操作流程**：
  1. 點擊 `Create New` 開始建立實例，在細項設定中的 **Mount Datadrive** 欄位點擊 `Mount`。
    ![](../../../../../docs/docs-images/p06/08.png)

  2. **Mount Datadrive 彈窗的資訊**：
    - **Region**：選擇要掛載的 Datadrive 所在區域（例如：`TW-03`等）。
      > 請注意，實例僅能掛載與其相同區域的 Datadrive。
    - **Usage**：該區域 Datadrive 目前已使用容量／總容量。
    - **Mount Path**：Datadrive 掛載至實例後對應的路徑，預設為`/datadrive`。
    - **Permissions**：掛載後的讀寫權限，可選 `Read only` 或 `Read & write`。
    - 點擊`Mount`後，建立實例，即可成功掛載。
      ![](../../../../../docs/docs-images/p06/09.png)

  3. **建立實例**：

      掛載成功後會顯示該 Datadrive 資訊，確認無誤後點擊 `Complete Checkout`，即可建立掛載了 Datadrive 的實例。
      ![](../../../../../docs/docs-images/p06/10.png)

### 實例中使用 Datadrive
 
 **操作流程**：
  1. 建立掛載了 Datadrive 的實例後，在實例列表中，點擊該實例的 Datadrive 標籤，即可看到 Datadrive 資訊。
  ![](../../../../../docs/docs-images/p06/11.png)


  2. 使用 SSH 進入實例後，透過預設路徑 `/datadrive`，即可成功存取 Datadrive 中的資料。
   ![](../../../../../docs/docs-images/p06/12.png)

---

## **注意事項**

1. **檔案與資料夾操作**：
   - 請注意資料夾無法直接使用下載功能。
   - 所有刪除或移動操作均需先選取目標項目。

2. **命名規則**：
   - 編輯名稱時，請避免使用特殊字符或重複名稱。

3. **檔案大小限制**：
   - 上傳檔案時，請確認檔案大小是否符合系統允許的上限。

以上是 **Datadrive** 頁面的完整功能說明，若需要進一步協助，請參考相關操作指南。
