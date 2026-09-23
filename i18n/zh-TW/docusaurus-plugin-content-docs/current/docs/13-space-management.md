---
id: space-management
sidebar_position: 13
---

# 儲存管理

在 **儲存管理** 頁面，您可以全面掌控您的存儲資源，透過靈活的計畫調整與空間分配，確保資源的最佳利用。以下是功能介紹與操作指南：

---

## **Snapshot 與 Image 計費方式調整通知**

為提供更彈性且便利的環境與資料管理體驗，平台將於 **2026 年 12 月 1 日 00:00（UTC+8）** 起調整 Snapshot 與 Image 的配額及計費機制。
調整後，Storage 套餐配額將僅適用於 Datadrive 儲存空間；Snapshot 與 Image 將不再佔用 Storage 配額，並改採依實際使用容量進行按時計費。
新的計費規則如下：
- 計費單價：0.0001 credits / 小時 / GB
- 當 Snapshot 或 Image 建立成功後，系統將開始計費
- 當 Snapshot 或 Image 被刪除後，系統將停止計費

此調整旨在讓用戶能更靈活地管理儲存資源，並依實際使用情況進行成本管理。

如有任何疑問，請透過以下方式聯繫我們：
[點擊這裡聯繫我們](/docs/contact-us)

## **Space Storage**

頁面最上方顯示 **Space Storage** 的比例條，清楚展示當前的使用情況，**Storage Space** 總空間可以讓你分配至三種用途，分別是 **Snapshot**, **Datadrive** 以及**Image**。

例如：

- **Using 17.1GB of 50GB**
- **Expires on 2026-09-28**

圖示說明了您的 **Snapshot**, **Datadrive** 以及 **Image** 三者加總後，佔用了17.1GB。
  ![Space storage](../../../../../docs/docs-images/p10/01.png)

## **Quota**

在主頁下方，您可以看到 **Snapshot**, **Datadrive** 以及 **Image** 的各別存儲使用情況。

例如：

- **Image** 區塊：**Using 3.79 GB of 20 GB**。
- **Snapshot** 區塊：**Using 13.30 GB of 18 GB**。
- **Datadrive** 區塊：**Using 0 GB of 4 GB**。
![Space storage](../../../../../docs/docs-images/p10/02.png)


### **訂閱儲存方案**

點擊 `Upgrade` 按鈕進入 **Select Storage Plan** 頁面。
 ![Space storage](../../../../../docs/docs-images/p10/03.png)

您可以選擇不同容量方案，方案將對應需要扣除的 **Credit**，所有方案的有效期均為 **30 Days**。選擇方案後，下方會顯示一個 **Summary**，包括：
- **Storage**：選擇的存儲方案大小。
- **Expire**：方案的到期日。
- **Total Price**：總價格。
![Space storage](../../../../../docs/docs-images/p10/04.png)

## **更改訂閱方案**

例如，當前已訂閱的方案為 `50GB`，您可以在訂閱期間內變更方案，例如： `訂閱小於 50GB 的方案`、`再次訂閱 50GB 方案`、`訂閱大於 50GB 的方案`。
1. **降級方案**：到期日不變，不會退還價格差額。請注意，在降級以前，您的 **Storage Space** 已使用的空間，必須小於您的降級選項的方案空間大小，否則將無法點選。降級前請先清除您不再使用的資料。
2. **選擇相同大小方案**：將使相同方案再延長 **30 Days**。將再次收取完整訂閱費用。
3. **升級方案**：升級方案後到期日不變。計費方式：以當前方案和新方案價格的價差，乘上方案的剩餘天數。
![Space storage](../../../../../docs/docs-images/p10/05.png)

## **Modify**

點擊 `Modify` 按鈕，您可以自由調整 **Snapshot**, **DataDrive** 和 **Image** 可使用的存儲空間。
![Modify](../../../../../docs/docs-images/p10/06.png)

點擊 `Modify` 按鈕後，您將在頁面上看到 **Snapshot**, **DataDrive** 和 **Image** 的各別存儲使用情況。
- 您可以自由分配 **Snapshot**, **Datadrive** 和 **Image** 各自能使用的空間。
- **Datadrive** 需進一步安排其不同區域的空間，例如 **TW-03**, **TW-04** ..等區域各別可使用的空間。
- 未被 **Snapshot** 及 **Datadrive** 使用而剩餘的空間，將會分配給 **Image**。
![Quota list](../../../../../docs/docs-images/p10/07.png)
