---
id: space-management
sidebar_position: 13
---

# Space Management

**Space Management** ページでは、ストレージリソースを一元管理でき、柔軟なプラン変更とスペース配分によって、リソースを最適に活用できます。以下で機能と操作方法をご紹介します：

---

## **Snapshot および Image の課金方式変更に関するお知らせ**

より柔軟かつ便利な環境・データ管理を実現するため、プラットフォームは **2026 年 12 月 1 日 00:00（UTC+8）** より、Snapshot と Image サービスのクォータおよび課金方式を変更いたします。
変更後、Storage パッケージのクォータは Datadrive のストレージにのみ適用されます。Snapshot と Image は Storage クォータを消費しなくなり、実際の使用容量に応じた時間課金方式に変わります。
新しい課金ルールは以下のとおりです：
- 課金単価：0.0001 credits／時間／GB
- Snapshot または Image が作成完了した時点で課金が開始されます
- 対応する Snapshot または Image が削除された時点で課金が停止されます

この変更は、ユーザーがストレージリソースをより柔軟に管理し、実際の利用状況に応じてコストを最適化できるようにすることを目的としています。

ご不明な点がございましたら、以下の方法でお問い合わせください：
[お問い合わせはこちら](/docs/contact-us)

## **Space Storage**

画面上部の **Space Storage** バーには、現在の使用状況がわかりやすく表示されます。**Storage Space** の総容量は、**Snapshot**、**Datadrive**、**Image** の 3 つの用途に配分できます。

例：

- **Using 17.1GB of 50GB**
- **Expires on 2026-09-28**

このバーは、**Snapshot**、**Datadrive**、**Image** の使用量を合計した容量を表示しています（この例では 17.1GB）。
  ![Space storage](../../../../../docs/docs-images/p10/01.png)

## **Quota**

メインダッシュボードの下部では、**Snapshot**、**Datadrive**、**Image** それぞれのストレージ使用状況を確認できます。

例：

- **Image**：**Using 3.79 GB of 20 GB**。
- **Snapshot**：**Using 13.30 GB of 18 GB**。
- **Datadrive**：**Using 0 GB of 4 GB**。
![Space storage](../../../../../docs/docs-images/p10/02.png)


### **Storage プランの購入**

`Upgrade` ボタンをクリックすると **Select Storage Plan** 画面に移動します。
 ![Space storage](../../../../../docs/docs-images/p10/03.png)

異なる容量のプランから選択できます。それぞれ必要な **Credit** 量が対応しており、すべてのプランの有効期間は **30 日間** です。プランを選択すると、下部に以下を含む **Summary** が表示されます：
- **Storage**：選択したストレージプランの容量。
- **Expire**：プランの有効期限。
- **Total Price**：合計金額。
![Space storage](../../../../../docs/docs-images/p10/04.png)

## **サブスクリプションプランの変更**

例えば、現在契約中のプランが `50GB` の場合、契約期間中にプランを変更できます。例：`50GB より小さいプランへの変更`、`50GB プランの再契約`、`50GB より大きいプランへの変更`。
1. **プランのダウングレード**：有効期限は変わらず、差額の返金は行われません。ダウングレードする前に、現在使用中の **Storage Space** がダウングレード先のプラン容量より小さいことが必要です。そうでない場合は選択できません。ダウングレード前に不要なデータを削除しておいてください。
2. **同じ容量のプランを選択**：同じプランがさらに **30 日間** 延長されます。この場合、サブスクリプション料金が全額再度請求されます。
3. **プランのアップグレード**：アップグレード後も有効期限は変わりません。課金方法：現在のプランと新プランの差額に、プランの残り日数を乗じた金額となります。
![Space storage](../../../../../docs/docs-images/p10/05.png)

## **Modify**

`Modify` ボタンをクリックすると、**Snapshot**、**Datadrive**、**Image** に利用できるストレージ容量を自由に調整できます。
![Modify](../../../../../docs/docs-images/p10/06.png)

`Modify` をクリックすると、画面上で **Snapshot**、**Datadrive**、**Image** それぞれのストレージ使用状況を確認できます。
- **Snapshot**、**Datadrive**、**Image** それぞれが利用できる容量を自由に配分できます。
- **Datadrive** はさらにリージョンごとの配分が必要です。例えば **TW-03**、**TW-04** など、各リージョンで利用可能な容量を設定します。
- **Snapshot** と **Datadrive** に使用されず残った容量は、**Image** に割り当てられます。
![Quota list](../../../../../docs/docs-images/p10/07.png)
