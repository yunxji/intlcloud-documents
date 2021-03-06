## 概要
指定されたバケットを削除する必要があるが、**削除失敗、バケット内の有効データを先に削除してください**というプロンプトが表示される時、**アップロード未完了**管理項目に入ってアップロードされていない断片化したファイルを確認して、それを削除することができます。バケット内のアップロードされていないファイルとアップロードされたファイルがすべて削除されたことを確認した後、バケットを削除できます。

>!オブジェクトのアップロード中に、アップロードが一時停止またはキャンセルされたファイルはいずれも【アップロード未完了】管理項目に表示されます。アップロードが完了したファイルのみが【ファイルリスト】で確認できます。

## 操作手順

1. Tencent Cloudアカウントを使用して[COSコンソール](https://console.cloud.tencent.com/cos5)にログインし、【バケットリスト】ナビゲーションバーをクリックした後、削除する必要があるバケットををクリックし、バケット詳細画面に入ります。
![](https://main.qcloudimg.com/raw/b90ad17947a0ec530db87210f4b9027d.png)
2. バケット詳細画面で、【アップロード未完了】管理項目をクリックして、アップロードされていない断片化したファイルを確認でき、右側の【削除】ボタンをクリックして、アップロードされていない断片化ファイルを削除でき、または上方の【断片のクリア】ボタンをクリックして、アップロードされていない断片化したファイルをすべて削除できます。
![](https://main.qcloudimg.com/raw/af458d9b1c70edce7dc256c5ea85ccfc.png)
3. 「断片のクリア」または「削除」操作を実行した後、【アップロード未完了】管理項目にリストが空として表示されます。
![](https://main.qcloudimg.com/raw/def3369810e97035187854a6651cb627.png)
