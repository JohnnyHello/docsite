---
id: auto-deploy
sidebar_position: 6
---

# 自動部署

在 **Auto Deploy** 頁面，您可以配置並自動化部署流程，使您的應用程式能夠高效、安全地運行。

使用 GPU 部署服務時，通常需要手動創建實例，使用完畢後也得手動釋放；當服務的使用頻率較不固定或請求較為零散時，這樣的操作方式就顯得繁瑣。

Glows.ai 提供 Auto Deploy 服務來解決這個問題。完成配置後，系統會提供一個固定的服務連結；當有請求發送至此連結 URL，Glows.ai 會根據配置處理請求，自動創建實例、執行指令。若連續 n 分鐘內都沒有新的請求進來，Glows.ai 便會自動釋放該實例。

換句話說，Auto Deploy 讓「創建實例 → 處理請求 → 釋放實例」形成一個自動化的循環，使用者只需維護單一固定的服務連結，並可直接將此連結整合進程式碼或自動化流程中，無需再手動管理實例的生命週期，也不必擔心因忘記釋放而持續產生費用，進而達到節省成本的效果。

以下是詳細功能介紹：

---
## **建立 Auto Deploy**

### **設定Auto Deploy**
進入 Auto Deploy 界面，點擊右上角的 `New Deploy`，新建一個配置項，即可開始建立。

---
![](../../../../../docs/docs-images/autodeploy/01.png)

- **Deploy Name**：此次自動部署的名稱。
- **Deploy Description**：此次自動部署的說明文字。
- **Access Method**：存取方式，可選 `Public` 或 `Private`。
- **Instance & Image**：欲透過自動部署啟動的機器類型和鏡像。可以選自己配置好的 Snapshot，也可以選系統預置的鏡像。
![](../../../../../docs/docs-images/autodeploy/02.png)

---
- **Port (HTTP/HTTPS)**：對外服務所使用的埠號。
- **Start Command**：實例啟動時自動執行的指令。
- **Instance Idle Retention Period**：透過自動部署的啟動實例閒置多久後會自動釋放。
- **Maximum Number of Instances**：此自動部署最多可開啟的實例數量。
- 設定完成後點擊 `Confirm`。
![](../../../../../docs/docs-images/autodeploy/03.png)

### **確認部署**

1. 完成表單填寫後，點擊 `Confirm`。
2. 系統將開始部署您的 Auto Deploy 設定。部署成功後，應用程式狀態將顯示於 **Activated** 列表中，代表您的自動部署設置已經待命，等候您調用。
4. **Instance Status**： 顯示 `Standby` 代表此自動部署正等待您調用，顯示`Running` 表示當前已透過此自動部署開啟了實例。
![](../../../../../docs/docs-images/autodeploy/04.png)
![](../../../../../docs/docs-images/autodeploy/05.png)



---

## **Auto Deploy 狀態**

### **Auto Deploy 基本資訊**

在 **Auto Deploy** 頁面中，您可以看到兩種部署狀態：

1. **Activated**：自動部署已經啟用，隨時待命。
2. **Suspended**：自動部署服務已暫停，未在運行中。
![](../../../../../docs/docs-images/autodeploy/06.png)

**每個部署任務列表包含以下欄位**：

- **ID**：每個部署任務的唯一標識符。
- **Name**：部署任務名稱。
- **Status**：當前部署狀態（Activated、Suspended）。
- **Instance Status**：實例的當前運行狀態（如 Standby、Running）。
- **Cost**：此部署消耗的資源費用。
- **Last Running Time**：最近一次運行的時間。
- **Action**：可對部署進行的操作（詳見下方操作介紹）。
![](../../../../../docs/docs-images/autodeploy/07.png)
---

### **Auto Deploy 詳細內容**

**點擊右側箭頭後，顯示詳細資訊**：

1. **ID／Auto Deploy Name／Auto Deploy Description**：此部署的基本資訊，建立時所填寫的名稱與說明。
2. **Instance Preview**：此部署所配置的機器類型與映像檔預覽，包含 Image、GPU/CPU 規格、RAM、Storage 等，內容同建立時的設定。
3. **Service & Start Command**：
    - **Access Method**：自動部署的存取方式。
    - **URL**：對外存取此服務的網址，是實際連線／呼叫服務時使用的位置。
    - **Port**：URL 對應的服務埠號。
    - **Start Command**：自動部署的實例啟動時自動執行的指令（若有設定）。
4. **Deployment Control**：閒置釋放時間與最大實例數量等部署管控設定，內容同建立時的設定。
![](../../../../../docs/docs-images/autodeploy/08.png)


---

## **Auto Deploy 可執行的操作**

在 **Action** 欄位提供以下操作：

### **1. Edit**

- **功能**：編輯部署配置。
- **使用情境**：當需要修改部署名稱、環境變數或其他設定時在此進行操作。

### **2. Suspend**

- **功能**：暫停部署，停止應用程式的運行。
- **使用情境**：當不再需要運行應用程式時，可暫停部署節省資源成本。

### **3. Deploy**

- **功能**：啟動或重新部署應用程式。
- **使用情境**：透過設定好的 AutoDeploy 啟動實例，此功能相當於使用 AutoDeploy 提供的 URL（URL 詳情可見使用者教學中的`Glows.ai Auto Deploy 使用案例`篇章）。
![](../../../../../docs/docs-images/autodeploy/09.png)


### **4. Delete**

- **功能**：刪除部署任務。
- **使用情境**：當不再需要此自動部署時，可刪除部署任務，**刪除後無法恢復**。

### **5. Resume**

- **功能**：恢復已暫停的自動部署設置。
- **使用情境**：當自動部署設置處於 Suspended 狀態且需要重新啟動時，可使用此操作使其回到 Activated 狀態，之後可點擊 `Deploy` 來部署實例。
![](../../../../../docs/docs-images/autodeploy/10.png)


### **6. Release**

- **功能**：將透過自動部署開啟的實例釋放，將實例轉為 Released 狀態。
- **使用情境**：當不需要使用已部署的實例時，可點擊 `Release` 來釋放資源並停止費用計算。
![](../../../../../docs/docs-images/autodeploy/11.png)


---

## **Auto Deploy 基本使用方式**

1. 於 Auto Deploy 頁面，複製您要使用的 Auto Deploy 的服務網址，這串 URL 就是觸發此服務的固定入口。
![](../../../../../docs/docs-images/autodeploy/12.png)

2. 透過瀏覽器開啟該網址，或用 curl 對此網址發送請求。
![](../../../../../docs/docs-images/autodeploy/13.png)

3. 請求處理完成後，回到 My Instances 頁面查看，已成功透過 Auto Deploy 觸發並啟動機器。
![](../../../../../docs/docs-images/autodeploy/14.png)

4. 若您在建立此 Auto Deploy 時已設定 Instance Idle Retention Period，實例在連續閒置超過該時間未收到請求後，會自動為您釋放，無需手動操作。
![](../../../../../docs/docs-images/autodeploy/15.png)

---

## **注意事項**

- **應用刪除不可逆**：刪除應用後，無法恢復。

- **暫停可節省資源**：想暫時停用一個自動部署的設置，可選擇 `Suspend`。

- **確認設定後再部署**：確保設定正確，以避免部署錯誤。

---

**以上是關於 Auto Deploy 的完整指南，如需更詳細的操作步驟與案例，請參考 [**Glows.ai Auto Deploy 使用說明**](https://docs.glows.ai/docs/auto-deploy-usage)。**
