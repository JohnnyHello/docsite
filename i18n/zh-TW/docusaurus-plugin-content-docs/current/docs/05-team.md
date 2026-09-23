---
id: team
sidebar_position: 5
---

# Glows.ai團隊版使用教程

Glows.ai 的團隊版功能，將構建團隊協作體系，實現資源集中管理、靈活配額分配、安全共享機制，滿足企業級用戶雲資源共享使用需求。

本教程分為三部分：

- [創建者使用教程](#創建者使用教程)
- [管理員使用教程](#管理員使用教程)
- [普通成員使用教程](#普通成員使用教程)

------

## 創建者使用教程

### 創建團隊

登錄 Glows.ai 平台後，點擊右上角個人信息，在彈框中點擊 `Teams`，然後點擊 `Create Teams` 進入團隊創建流程。

![Create Team Menu](../../../../../docs/docs-images/p05team/01.png)

目前有 Free 、 Basic 和 Premium 三個版本，您可以根據團隊項目需要選擇合適版本，如果有更進階需求，可以點擊`Contact us`聯繫我們客製化開發。

![Select Team Plan](../../../../../docs/docs-images/p05team/02.png)

選擇好團隊套餐類型後，可以繼續設置團隊名稱和簡介信息。

![Set Team Name](../../../../../docs/docs-images/p05team/03.png)

選擇套餐購買時長，後續可以手動續費，然後點擊 `Next`。

![Choose Plan Duration](../../../../../docs/docs-images/p05team/04.png)


確認信息無誤，點擊`Create Team`即可完成團隊創建。

![Confirm Team Creation](../../../../../docs/docs-images/p05team/05.png)


創建成功後，您會看見團隊基本信息，您已成為該團隊的 **創建者**(**Owner**)，此身份會自動綁定到您個人帳號，未來可透過個人帳號進入團隊頁面。

點擊 `Enter Team` 可直接進入團隊頁面。

![Team Created](../../../../../docs/docs-images/p05team/06.png)


### 切換到團隊介面

您可以從 Glows.ai 個人帳號頁面直接切換到團隊版本。按圖示點擊右上角個人信息，在彈框中點擊 `Teams`，然後點擊要進入的團隊。

![Switch To Team](../../../../../docs/docs-images/p05team/07.png)


### 成員管理

創建者或者管理員帳號登錄後，可以點擊左側功能欄的 `Member` tab，進行成員管理，目前支持：**新增成員**、**派發 Credits**、**收回成員 Credits**、**資源可見性控制**、**修改成員基本信息**、**成員實例管理**等功能。

#### 添加成員

點擊 `Member` 介面中的 `Add Members` 按鈕進入添加成員流程。

![Add Team Member](../../../../../docs/docs-images/p05team/08.png)


可以設置新成員的：**帳號(Login Account)**、**密碼(Login Password)**、**角色(Role)**、**初始 Credit 額度(Assign Credit)**、**別名(Alias)**、**描述說明(Note)**。設置完成後點擊介面中的 `Add Member` 按鈕完成成員創建。

角色(Role) 目前支援設置為 **Admin(管理員)**或者**Member(普通成員)**。

分配額度(Assign Credits)是設定成員在加入團隊當下能獲得的初始點數，可以用於租用機器或者購買 **Storage Space 方案**，也可以創建後再分配。

![New Member Form](../../../../../docs/docs-images/p05team/09.png)


創建成功後，可以點擊 `Copy Login Details` 獲取到新成員信息，然後將信息發送給對應成員。新成員登錄使用方法參考[普通成員登入方法](#加入團隊)

![Copy Login Details](../../../../../docs/docs-images/p05team/10.png)


#### 儲值 Credits

團隊中所有成員使用的任何 Credits 都需要先經由 **創建者**（**Owner**） 儲值到團隊中，再派發給成員使用。
在團隊版頁面中，**創建者**（**Owner**）首先點擊右上方的 **Credits 信息**，再點擊 `Recharge` 開始進行儲值。

![Recharge Credits](../../../../../docs/docs-images/p05team/11.png)

除了支持與個人版相同的 Credits 儲值方式之外，在團隊版中，**創建者**（**Owner**）可以使用個人帳號中的 Credits 儲值到團隊版帳戶中使用。

選擇或填寫 **Credits 數量** 並選擇 `USD` 後，選擇 `Glows.ai Balance` ，點擊 `Recharge`，即可完成儲值。
![Recharge From Balance](../../../../../docs/docs-images/p05team/12.png)


#### 派發 Credits

在 `Member` 介面中點擊對應成員後的 Action 按鈕，選擇 `Assign Credits`，進入派發 Credits 介面。

![Assign Credits](../../../../../docs/docs-images/p05team/13.png)


輸入派發金額後點擊 `Assign` 完成派發。

![Confirm Assign Credits](../../../../../docs/docs-images/p05team/14.png)

#### 收回 Credits

在相同頁面中，選擇 `Reclaim Credits` 後，即可收回成員的 Credits。操作方式與派發 Credits 相同。

![Reclaim Credits](../../../../../docs/docs-images/p05team/15.png)


#### 資源可見性控制

在 `Permissions & Quota` 中可以設置團隊成員可以看見哪些顯卡、鏡像、可用實例總數和存儲總空間。

點擊 `Permissions & Quota` 進入權限設置介面，首先可以控制團隊成員可見機器資源，可以控制：**機器區域**（**Region**）、**機器類型**(**Type**)
、**機器型號**(**Accelerator**)。

圖示中顯示的權限設置為：團隊成員只能使用 **TW-03**、**TW-04**區域的 **GPU** 類型機器，並只能選擇 **NVIDIA GeForce RTX 4090** 規格。

![Machine Permissions](../../../../../docs/docs-images/p05team/16.png)


頁面下滑，繼續設置成員可以使用哪些官方基礎鏡像。圖示中顯示的權限設置為：團隊成員只能使用 **Gemma4 31B Q8** 及 **Qwen3.5-27B-Claude-4.6-Opus-Q8** 兩種鏡像創建實例。

![Image Permissions](../../../../../docs/docs-images/p05team/17.png)


最後還可以設置團隊成員實例資料、**Snapshots** 數量、**Storage Space** 可用空間等。

![Resource Quota Settings](../../../../../docs/docs-images/p05team/18.png)


設置完成後，點擊右上角的 `Save` 按鈕即可保存設置。將來團隊成員在創建實例時點擊 `Create New` 所能挑選的機器，將會限定於 `Permissions & Quota` 所設置的機器類型和環境。

![Save Permissions](../../../../../docs/docs-images/p05team/19.png)



#### 修改成員基本信息

在 `Member` 介面中點擊對應成員後的 `Details` 按鈕可以進入成員詳細面板介面。

![Member Details Panel](../../../../../docs/docs-images/p05team/20.png)


目前支持修改成員的 **Name**、**Role**（例如：**Admin** 或 **Member**）、**Account Balance**、**Note**、**Login Password**。在詳細面板介面還可以看到該成員其他使用信息，比如：剩餘Credits、總花費、實例數量、存儲使用情況等。

![Edit Member Info](../../../../../docs/docs-images/p05team/21.png)


點擊該介面右上角的 `Edit Permission` 按鈕，可以設置單個成員的資源可見性，可以實現讓不同成員看到不同的機器資源和鏡像資源。

![Edit Permission](../../../../../docs/docs-images/p05team/22.png)

將 **Use Team Default Permission** 從 `On` 改為 `Off` 即可進行設置。

![Individual Permission](../../../../../docs/docs-images/p05team/23.png)


#### 成員實例管理

在 `Instances` 介面中點擊 `Admin View`，可以看到所有成員的實例紀錄和運行情況。

![Admin View Instances](../../../../../docs/docs-images/p05team/24.png)



點擊想要關閉的成員實例數據條中的 `Action`，再點擊 `Release` 即可直接釋放該成員實例。

![Release Instance](../../../../../docs/docs-images/p05team/25.png)


### Storage Space 管理

#### 訂閱團隊版共享 Storage Space 方案

在`Storage Space`介面選擇`Admin View`，然後點擊`Upgrade`按鈕選擇需要的套餐，再點擊`Recharge`即可完成 Storage Space 購買。

**請注意**：訂閱團隊共享 Storage Space 方案時，請按圖示步驟先點擊 `Admin View`，如果於 `Member View` 下則是訂閱團隊版之中的個人 Storage Space 方案。

![Upgrade Storage Plan](../../../../../docs/docs-images/p05team/26.png)


#### 分配團隊共享 Storage Space

在`Storage Space`介面選擇`Admin View`，可以看到團隊共享 Storage Space 的使用情況，以及每個成員在團隊版中的個人 Storage Space 的使用情況。

![Storage Usage Overview](../../../../../docs/docs-images/p05team/27.png)


在`Storage Space`介面選擇`Admin View`後，點擊 **Team Storage Space** 的 `Manage` 按鈕，

![Manage Team Storage](../../../../../docs/docs-images/p05team/28.png)

進入團隊共享 Storage Space 分配介面後，點擊 `Modify`，即可設置 **Datadrive** 和 **Snapshot** 空間額度，最後點擊 `Update` 完成分配。分配方式與個人版相同。

![Allocate Storage Quota](../../../../../docs/docs-images/p05team/29.png)


### 共享 Datadrive 管理

點擊側邊欄的 `Datadrive` 後於介面選擇 `Admin View` ，可以看到團隊共享 Datadrive 的使用情況，還有每個團隊成員個人 Datadrive 的使用情況。

![Datadrive Usage Overview](../../../../../docs/docs-images/p05team/30.png)


點擊 `Team Datadrive` 的 `Manage` 按鈕，進入團隊 Datadrive 管理介面。

![Manage Team Datadrive](../../../../../docs/docs-images/p05team/31.png)

在此介面中可以看見不同**區域**（**Region**）的共享 Datadrive 的檔案總覽，只有團隊**創建者**（**Owner**）和管理員有權限在團隊共享 Datadrive 上傳和刪除檔案，所有成員均可以 下載（**Download**）檔案。

![Datadrive File List](../../../../../docs/docs-images/p05team/32.png)



其他成員在創建實例時可以選擇掛載團隊共享Datadrive，實例中的路徑為`/team_data`，普通成員只有可讀權限，團隊創建者和管理員有讀寫權限。

![Mount Team Datadrive](../../../../../docs/docs-images/p05team/33.png)


### Snapshots 管理

在 `Snapshots` 介面選擇 `Admin View`，可以看到團隊和每個團隊成員個人創建的 Snapshot。

![Snapshots Overview](../../../../../docs/docs-images/p05team/34.png)


#### 設置團隊共享 Snapshot

只需要點擊想要轉變到團隊共享的 Snapshot 後的 `Details`，然後再選擇 `Share to team` 即可將成員創建的 Snapshot 變成團隊共享 Snapshot。

![Share Snapshot](../../../../../docs/docs-images/p05team/35.png)


#### 使用團隊共享 Snapshot

其他成員創建實例的時候，選擇 Snapshot，就可以看到團隊共享的 Snapshot 了，團隊共享的 Snapshot 右上角也會有一個 **Team** 標記。

![Use Shared Snapshot](../../../../../docs/docs-images/p05team/36.png)


#### 管理團隊 Snapshot

在 `Snapshots` 介面選擇 `Admin View` 後，點擊 `Team Shared Snapshots` 模塊右上角的 `Manage` 按鈕，即可進入管理團隊 Snapshot 介面。

![Manage Shared Snapshots](../../../../../docs/docs-images/p05team/37.png)


在這個介面可以看到所有團隊 Snapshot，目前只支持刪除操作，選擇不需要的 Snapshot 點擊 `Action` 中的 `Delete` 按鈕即可刪除。

**注意**： 團隊Snapshot執行刪除操作後，會徹底刪除，無法找回，請謹慎操作。

![Delete Snapshot](../../../../../docs/docs-images/p05team/38.png)


### Billing 管理

在 `Billing` 介面選擇 `Admin View`，可以看到團隊所有成員的帳單數據。

![Team Billing Overview](../../../../../docs/docs-images/p05team/39.png)

帳單查詢支援依成員與帳單類型進行篩選。

![Filter By Member](../../../../../docs/docs-images/p05team/40.png)
![Filter By Type](../../../../../docs/docs-images/p05team/41.png)






### 團隊資訊編輯

在`Team Setting`介面點擊右上角的`Edit`按鈕，可以編輯團隊的名稱和描述信息。

![Edit Team Info](../../../../../docs/docs-images/p05team/42.png)
![Team Info Saved](../../../../../docs/docs-images/p05team/43.png)


## 管理員使用教程

管理員除了不能創建團隊和儲值外，其他權限和團隊創建者一樣，請參考[團隊創建者使用教程內容](#創建者使用教程)。

## 普通成員使用教程

普通成員僅支持以下功能：創建實例（Create New）、實例管理(Instances)、Datadrive管理(Datadrive)、Snapshot管理(Snapshots)、Storage管理(Storage Space)、帳單查詢(Billing)、個人信息修改(Profile)，和Glows.ai主網操作一致，具體請看[Glows.ai使用手冊](https://docs.glows.ai/docs/create-new)。

![Member Feature List](../../../../../docs/docs-images/p05team/44.png)

### 加入團隊

普通成員拿到團隊創建者或管理員創建的成員帳號後可以從兩個入口加入團隊。

#### 1> 團隊版本連結登入

瀏覽器訪問下面團隊登錄介面，輸入團隊帳號密碼。

```bash
https://platform.glows.ai/team/login
```

![Team Login Page](../../../../../docs/docs-images/p05team/45.png)



#### 2>  Glows.ai 個人版頁面進入

登入 Glows.ai 主網後，點擊右上角個人頭像，選擇 **`Teams`->`Join Team`**。

![Join Team Menu](../../../../../docs/docs-images/p05team/46.png)

在 Join Team 介面輸入團隊帳號密碼，即可將 Glows.ai 個人帳號和團隊綁定，往後就可以直接在個人頁面中切換至團隊頁面了，無需再次使用團隊版帳號密碼登入。

![Join Team Form](../../../../../docs/docs-images/p05team/47.png)



不論用哪一種方式登入，首次登錄後會需要重置密碼。

![Reset Password](../../../../../docs/docs-images/p05team/48.png)

### 獲取Credits

團隊成員如果需要 Credits，請向團隊創建者或者管理員申請。

### 創建實例

點擊 `Create New`，選擇自己需要租用的顯卡和環境。

![Create Instance](../../../../../docs/docs-images/p05team/49.png)

下滑可以看到實例相關配置，團隊版中除了 **Mount Team Datadrive** 之外，其餘設置與個人版相同。設置完畢後點擊 `Complete Checkout` 即可完成實例創建。

- **Unit Qty**：租用顯卡數量，如果設置為2，則表示租用2張顯卡。
- **Mount Personal Datadrive**：可以選是否掛載個人 Datadrive。
- **Mount Team Datadrive**：可選擇掛載團隊共享 Datadrive 到實例中的 `/team_data` 目錄下，團隊**創建者**（**Owner**）和**管理員**（**Admin**）有寫入和讀取權限，普通成員只有讀取權限。
- **Bind Public IP Address**：綁定固定 IP。

![Instance Configuration](../../../../../docs/docs-images/p05team/50.png)

團隊一般成員掛載 Team Datadrive 只有**可讀權限**（**Read only**），而團隊**創建者**（**Owner**）和**管理員**（**Admin**）有**寫入和讀取權限**（**Read & Write**）。

![Datadrive Read Only](../../../../../docs/docs-images/p05team/51.png)


### 實例管理

實例啟動成功後，可以在 Instances 介面看到新啟動的實例，點擊實例可以看到實例更詳細的信息和更多操作。

- **Access:** 實例的訪問信息，比較常用的是 SSH(Port 22) 和 Jupyterlab(Port 8888)
- **Monitor:** 實例CPU、GPU資源監控
- **Billing:** 實例費用明細
- **Config:** 實例配置說明（實例啟動鏡像軟體說明）
- **Hardware:** 實例硬件配置說明

使用完成後，可以在 `Action` 中可以選擇 `Release` 釋放實例，或者 `Take Snapshot` 創建一個快照。

![Release Or Snapshot](../../../../../docs/docs-images/p05team/52.png)

### 其他功能

團隊版之中的個人 **Storage Space** 及其之下的 **Datadrive** 管理(Datadrive)、**Snapshots** 管理(Snapshots)，以及帳單查詢(Billing)、個人信息修改(Profile)均與個人版頁面操作一致，請參考教程內容：[Glows.ai使用手冊](https://docs.glows.ai/docs/create-new)

## 聯繫我們

如果您在使用 Glows.ai 的過程中有任何疑問或者建議，歡迎通過郵件、Discord或者Line聯繫我們。

**Email:** [support@glows.ai](mailto:support@glows.ai)

**Discord:** [https://discord.com/invite/glowsai](https://discord.com/invite/glowsai)

**Line:** [https://lin.ee/fHcoDgG](https://lin.ee/fHcoDgG)
