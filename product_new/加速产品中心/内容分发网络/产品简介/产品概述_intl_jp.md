## Content Delivery Networkとは。

Content Delivery Networkは、既存のインターネットに新しく追加されたネットワークアーキテクチャであり、全国に配置されている高性能な加速ノードで構成されています。これらの高性能なサービスノードは、特定のキャッシュポリシーに従ってユーザーのサービス内容を保存します。ユーザーが指定のサービス内容へリクエストを送信するとき、リクエストはユーザーに最も近いサービスノードにスケジューリングされ、直接にサービスノードによって迅速に応答されます。これにより、ユーザーアクセスのディレーが低下し、可用性が向上します。

CDNは、現在のインターネットサービスにおけるネットワークレベルの次の問題を効果的に解決しています。
1.ユーザーとサービスサーバー間の物理的な距離が遠く、複数回のネットワーク転送が必要であり、転送ディレーが大きく不安定です。
2.ユーザー利用のキャリアがサービスサーバーのキャリアと異なるため、リクエストはキャリア間で相互転送される必要があります。
3.サービスサーバーはネットワーク帯域幅と処理能力が限られているため、多数のユーザーリクエストを受信したとき、応答速度と可用性が共に低下します。

CDNへのアクセスは簡単です。サービス構造を調整したり、複雑な構成操作を実行したりすることなく、グローバルCDN加速サービスを利用できます。 [クイックスタート]（https://cloud.tencent.com/doc/product/228/3149）で、CDN加速サービスを簡単に起動できます。

##加速原理
サービスのオリジンサーバーのドメイン名が```www.test.com```であるとします。ドメイン名はCDNにアクセスして加速サービスの利用を開始した後、ユーザーがHTTPリクエストを送信した場合、実際の処理フローは下記図のように示します。
![](https://mc.qcloudimg.com/static/img/1bead74703061b71eeaf6bf4db27fcdb/image.png)

**詳細な説明は次の通りです。**
1.ユーザーが```www.test.com```下の画像リソース（例：1.jpg）へのリクエストを送信する場合、先にLocal DNSへドメイン名の解析リクエストを送信します。
2.Local DNSが```www.test.com```を解析しているとき、CNAME` `` www.test.com.cdn.dnsv1.com```が構成されていることが判明した場合、解析リクエストがTencent DNS（GSLB）に送信されます。GSLBはTencent Cloudが独自に開発したスケジューリングシステムであり、リクエストに最適なノードIPをアサインします。
3.Local DNS は、Tencent DNSから返された解析済みのIPを取得します。
4.ユーザーは解析されたIPを取得します。
5.ユーザーは、取得したIPにリソース1.jpgへのアクセスリクエストを送信します。
6. IPに対応するノードのキャッシュに1.jpgがある場合、データがユーザー（10）に直接返され、リクエストは終了します。ノードのキャッシュに1.jpgがない場合、ノードはサービスのオリジンサーバーに1.jpgへのリクエスト（6、7、8）を送信します。リソースを取得した後、ユーザーカスタマイズ構成のキャッシュポリシー（製品ドキュメントの [キャッシュ期限切れコンフィグレーションの構成]（https://cloud.tencent.com/doc/product/228/6290）を参照）に従って、リソースをノード（9）にキャッシュするとともに、ユーザー（10）に返します。リクエストは終了します。
