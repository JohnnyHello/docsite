---
id: bind-public-ip
sidebar_position: 14
---

# Bind Public IP

**Bind Public IP** は **Glows.ai** が提供する固定 IP 管理機能です。独立した **Public IP** リソースを作成し、特定のインスタンスに紐づけることで、そのインスタンスが外部にサービスを提供したり、外部からアクセスされたりできるようになります。さらに **IP ACL** ルールを使って、この **Public IP** のインバウンド・アウトバウンドのトラフィックを細かく制御し、許可された送信元とポートのみがサービスにアクセスできるようにすることもできます。

本ガイドでは、以下の内容を順番に説明します：
1. **Public IP** の作成方法
2. **Public IP** をインスタンスに紐づける方法
3. **IP ACL** ルールを設定してアクセスを制御する方法

---

## Public IP の作成

まず左側サイドバーの `Network Endpoint` をクリックし、続けて `Create New` をクリックして **Public IP** の作成を開始します。
![](../../../../../docs/docs-images/bind-public-ip/01.png)

**Region** と **IP Bandwidth Type** を選択したら、`Create` をクリックして **Public IP** を作成します。

注意：この **Public IP** の Region は、後で紐づける予定のインスタンスの Region と一致している必要がありますので、選択前によくご確認ください。
![](../../../../../docs/docs-images/bind-public-ip/02.png)

作成が完了すると、一覧に **Public IP** が表示され、インスタンス作成時に紐づけできる準備が整ったことを示します。
注意：**Public IP** は専有リソースであるため、作成後はインスタンスに紐づけていなくても Credit を消費し続けます。作成前に必要性をよくご確認ください。

一覧に表示される各 **Public IP** には、以下の項目が含まれます：
- **ID**：各 **Public IP** の一意の識別子。
- **Address**：**Public IP** のアドレス。
- **Region**：所属するリージョン（例：TW-03）。
- **Bandwidth**：帯域幅タイプ（例：Shared、Custom）。
- **Status**：ステータス（例：Available）。
- **Cost**：この **Public IP** がこれまでに消費した Credit。
- **Action**：この **Public IP** に対して実行できる操作。
![](../../../../../docs/docs-images/bind-public-ip/03.png)

---

## Public IP の紐づけ

作成が完了すると、インスタンス作成時に紐づけることができます。
注意：インスタンスを作成する際は、紐づけたい **Public IP** と同じ Region を選択してください。
![](../../../../../docs/docs-images/bind-public-ip/04.png)

インスタンスを作成する際、メニュー下部の **Public IP Address** で `Bind` をクリックします。
![](../../../../../docs/docs-images/bind-public-ip/05.png)

ポップアップで紐づけたい **Public IP** を選択し、`Protocol` を選び、`Port` を入力したら `Bind` をクリックすると紐づけが完了します。
複数の **Public IP** を作成している場合、インスタンスと同じ Region のものがこの一覧に表示され、選択できます。
![](../../../../../docs/docs-images/bind-public-ip/06.png)

紐づけに成功すると、**Public IP** の情報が表示されます。内容を確認したら、**Public IP** が紐づけられたインスタンスを作成できます。
![](../../../../../docs/docs-images/bind-public-ip/07.png)

インスタンス作成後、インスタンス一覧で正常に紐づけられた IP アドレスを確認できます。
![](../../../../../docs/docs-images/bind-public-ip/08.png)

---

## IP ACL の設定

すべての **Public IP** には **ACL** ルールを紐づけることができ、その IP の外部アクセス権限とネットワークトラフィックの方向を制御できます。

### L3 ルールの作成

1. `Network Endpoint` をクリックし、設定したい **Public IP** を選択します。
2. `IP ACL` をクリックします。
3. `Add ACL Resource` をクリックします。
![](../../../../../docs/docs-images/bind-public-ip/09.png)

`Add ACL Resource` をクリックすると **IP ACL** が作成されます。続けて `Manage Rules` をクリックして設定を開始します。
![](../../../../../docs/docs-images/bind-public-ip/10.png)

#### L3 ルールの説明とデフォルトルール

前のステップで `Manage Rules` をクリックすると、IP `0.0.0.0/0` のデフォルト L3 ルールが表示されます。

この画面には、この **Public IP** の現在すべての **ACL** ルールの一覧が表示されます。**ACL** ルールは方向によって 2 種類に分かれます：
  > **Inbound**（インバウンド）：外部のどの送信元がこの IP にアクセスできるかを制御し、このサービスに接続できる送信元の範囲を制限します。

  > **Outbound**（アウトバウンド）：この IP が接続を許可する宛先 IP の範囲を定義し、このサービスが外部に接続できる範囲を制御します。

ACL ルールの各項目は以下のとおりです：
- **Remote CIDR**：送信元または宛先の IP 範囲を **CIDR** 形式で表します（例：`0.0.0.0/0` はすべての IP を表します）。
- **Direction**：このルールの方向。`Inbound` または `Outbound`。
- **Default Policy**：**Remote CIDR** に適用されるアクション。`Deny`（拒否）または `Allow`（許可）。
- **Status**：ルールが有効かどうか（例：`Pending` は未適用、`Applied` は適用済み）。
- **Description**：ユーザーがこの **ACL** に記入した説明。
- **Created Time**：この **ACL** ルールが作成された日時。
- **Action**：この **ACL** に対して実行できる操作。
![](../../../../../docs/docs-images/bind-public-ip/11.png)

デフォルトでシステムは 1 つの `Inbound` ルールを作成します：**Remote CIDR** は `0.0.0.0/0`（すべての送信元 IP を表す）、**Default Policy** は `Deny` で、これはデフォルトでこの IP へのすべての外部アクセスが拒否されることを意味します。

#### L3 ルールの追加

デフォルトの `0.0.0.0/0` ルール以外に、L3 ルールへ別の IP を追加することもできます。
`Add Rule` をクリックすると追加を開始できます。
![](../../../../../docs/docs-images/bind-public-ip/12.png)

- **Rule Direction**：このルールの方向。`Inbound` または `Outbound`。
- **Action**：`Allow` はこの IP を許可、`Deny` はこの IP を拒否します。
- **Source IP Address**：このルールを適用する IP アドレス。
- **Description**：このルールの説明。
- 設定が完了したら `Create L3 Rule` をクリックしてルールを追加します。
![](../../../../../docs/docs-images/bind-public-ip/13.png)

作成が完了すると、新しい L3 ルールが確認できます。
![](../../../../../docs/docs-images/bind-public-ip/14.png)

### L4 ルールの作成

特定の送信元からのアクセスを許可するため、`New L4 Rule` をクリックして例外ルールを追加します。
![](../../../../../docs/docs-images/bind-public-ip/15.png)

**L4 Rule** の設定：
1. 設定中の **L4** ルールは L3 ルール `0.0.0.0/0` に属するため、**L4 Policy** は `Allow` にのみ設定できるとシステムに表示されます。この場合、`Default Policy` が `Deny` であるため、IP アドレス `0.0.0.0/0` はすべての IP からのアクセスを拒否している状態です。そのため、許可したい接続をホワイトリストに登録するために L4 ルールが必要になります。
2. **Destination Port**：開放したい宛先ポート範囲を入力します（例：8000 から 8888）。単一のポートのみ開放する場合は、両方のフィールドに同じ値を入力してください（例：`8000` から `8000`）。
3. ポート範囲が正しいことを確認したら、`Add` をクリックしてこの設定をルール一覧に追加します。
4. `Create L4 Rule` をクリックしてルール作成を完了します。
![](../../../../../docs/docs-images/bind-public-ip/16.png)

**L4 Rule** の作成が完了すると、L3 ルール `0.0.0.0/0` の下に例外ルールとして表示されます。このルールの Policy は `Allow` となり、デフォルトでは全ての接続が拒否されている（L3 の Deny ルール）状態のなかで、ポート 8000 から 8888 への接続のみが許可されることを意味します。

L4 Rule 一覧に表示される情報：
- **Policy**：この **L4** ルールのアクション。`Deny` の L3 ルールに属するため、`Allow` のみ設定可能です。
- **Protocol**：このルールが適用されるプロトコル（例：Custom TCP）。
- **Port Range**：このルールが開放する宛先ポート範囲（例：8000-8888）。
- **Description**：ユーザーがこの **L4** ルールに記入した説明。
- **Created Time**：この **L4** ルールが作成された日時。
- **Action**：このルールに対して実行できる操作（例：Edit）。
![](../../../../../docs/docs-images/bind-public-ip/17.png)

---

## 同一の Public IP に複数のインスタンスを紐づける

作成時にこの **Public IP** に紐づけられた各インスタンスは、以下の一覧に表示されます。
![](../../../../../docs/docs-images/bind-public-ip/18.png)

---

## お問い合わせ

**Glows.ai** のご利用中にご不明な点やご提案がございましたら、メール、Discord、または Line からお気軽にお問い合わせください。

**Email:** [support@glows.ai](mailto:support@glows.ai)

**Discord:** [https://discord.com/invite/glowsai](https://discord.com/invite/glowsai)

**Line:** [https://lin.ee/fHcoDgG](https://lin.ee/fHcoDgG)
