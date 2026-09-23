---
id: snapshots
sidebar_position: 11
---

# Snapshots

**Snapshot（スナップショット）** は、インストール済みのパッケージや開発環境の設定など、インスタンスの現在の環境構成を保存するための機能です。開発環境を整えた後、その状態をバックアップするセーブポイントとして Snapshot を作成しておくと、以後インスタンスを作成する際に Snapshot を使って素早くその状態を復元でき、再度セットアップする必要がなくなります。

以下で機能と操作方法をご紹介します：

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


## Snapshot の作成

  - マシンが稼働中の状態で、マシン右側のメニューをクリックし、`Take Snapshot` をクリックすると Snapshot の作成が始まります。
    > 注意：Snapshot 作成中はインスタンスの稼働が一時停止します。

  ![](../../../../../docs/docs-images/p08/01.png)


   1. **Name**：Snapshot の名前を入力します。
   2. **The instance will be automatically released after the process is completed**：
      チェックを入れると、Snapshot 完成後にインスタンスは自動的に解放されます。
      チェックを入れない場合、Snapshot 完成後にインスタンスは自動的に Running 状態に戻り、そのまま利用を継続できます。
   3. 入力が完了したら、Take Snapshot をクリックして作成を開始します。
![](../../../../../docs/docs-images/p08/02.png)


  - 保存処理中は、インスタンスは `Running` タブから `Snapshotting` タブへ移動し、インスタンスのステータスは `Suspending` に変わります。
![](../../../../../docs/docs-images/p08/03.png)


   - Snapshot の作成が完了すると、インスタンスは以下のいずれかの状態になります：
    1. 稼働を継続する。
    2. 自動的に解放される（Take Snapshot をクリックした際に **The instance will be automatically released after the process is completed** にチェックを入れていた場合）。
  ![](../../../../../docs/docs-images/p08/04.png)

---

## Snapshot の利用

  - マシンを作成する際に Snapshot タブをクリックすると、作成済みの Snapshot が表示され、それを使ってインスタンスを作成できます。インスタンスは Snapshot 作成時点の状態に復元されます。
    > **注意事項**：Snapshot はリージョンをまたいで利用できます。例えば、`TW-03` のインスタンスから作成した Snapshot を、別のリージョン（例：`TW-04`）でインスタンスを作成する際に使用できます。注意：リージョンをまたいで Snapshot を利用する場合、初回の起動は時間がかかりますが、以降はキャッシュにより高速になります。

![](../../../../../docs/docs-images/p08/05.png)


---

## Snapshot 一覧

メイン画面で左側メニューの Snapshot をクリックすると、すべての Snapshot の一覧を確認できます。
![](../../../../../docs/docs-images/p08/06.png)

---

### Snapshot のステータス

  1. **Available** タブには利用可能なすべての Snapshot が表示され、確認・管理を行うことができます。
  2. **Restorable** タブには、削除された、または Storage Space の不足により利用できない Snapshot が表示されます。これらの Snapshot は一定期間内であれば復元可能です。
  ![](../../../../../docs/docs-images/p08/07.png)

  ### Available
    **Snapshot の情報項目**：
    - **ID**：Snapshot の一意の識別子。
    - **Name**：識別しやすい Snapshot 名。
    - **Size**：Snapshot が占有しているストレージ容量。
    - **Status**：Snapshot の現在のステータス（例：`Available`）。
    - **Create Time**：Snapshot の作成日時。
    - **Action**：実行可能な操作（`Delete` のみ）。
      > `Delete` を使用すると、Snapshot は **Restorable** タブに移動します。

    ![](../../../../../docs/docs-images/p08/08.png)
  ### Restorable
    **Snapshot の情報項目**：
    - **Action 以外は Available タブと同じ項目です**。
    - **Action**：実行可能な操作（`Restore` または `Delete`）。
      > 注意：Restorable 内の Snapshot に `Delete` を実行すると、完全に削除されます。

    ![](../../../../../docs/docs-images/p08/09.png)

    **Restorable の Snapshot を復元する**：

      復元を行うと、Snapshot は `Restorable` から `Available` へ移動し、再び利用可能な状態になります。

    1. `Restorable` タブをクリックします。
    2. `Restore` をクリックします。
    3. 復元を行うと、`Snapshot restores left` の残り回数が 1 回消費されます。
          ![](../../../../../docs/docs-images/p08/10.png)



---

## **注意事項**

- **削除と復元について**：
  Snapshot を削除すると **Restorable** タブに移動し、復元または完全削除を選択できます。

- **名前の変更について**：
  Snapshot の名前はいつでも変更でき、管理・識別がしやすくなります。

- **ストレージ管理について**：
  不要な Snapshot を定期的に整理することで、ストレージ容量を解放し、リソースを効率的に利用できます。

これらの機能により、データを簡単に管理・保護し、必要なときに特定の状態へ素早く復元することができます。
