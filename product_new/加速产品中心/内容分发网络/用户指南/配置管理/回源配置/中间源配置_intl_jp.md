中間ソースは、サービスサーバー（即ち、オリジンサーバー）とCDNノード（海外ユーザーの場合、海外CDNノードとなる）の中間層に位置するオリジンプルサーバーです。ユーザーがリクエストを発送する時、リクエストは先にCDNエッジサーバーに到着しますが、ノードに必要なリソースがない場合、中間ソースへリソースリクエストを発送します。中間ソースで命中していない場合、中間ソースはオリジンサーバーにリクエストを発送します。
加速サービスの効果を向上させるために、2018年10月15日より、ドメイン名にアクセスする時に中間ソースがデフォルトで有効になり、手動で無効にすることがサポートされません。中間ソース構成がデフォルトで有効になった後、対応する構成項目はコンソールに表示されません。

## 構成ガイド
[CDNコンソール](https://console.cloud.tencent.com/cdn)にログインし、左側のメニューの【ドメイン名管理】をクリックして編集するドメイン名の右側の【管理】をクリックします。
![](https://mc.qcloudimg.com/static/img/1f2cb594cd614b62b589cb20a20ed362/basic-config-1.png)
【オリジンプル構成】をクリックすると、「中間ソース構成」モジュールが表示されない場合、ドメイン名は**中間ソース構成がデフォルトで有効になっている**ことを示します。ユーザーのオリジンプルリクエスト動作は中間ソースで収束され、中間ソースによって統一的にオリジンプルしてデータを取得するため、CDN加速効果が向上し、オリジンプル後のオリジンサーバーのアクセス圧力が効果的に軽減されます。
>**注意事項：**
>既に追加されているドメイン名において、「オリジンプル構成」で確認すると、中間ソース構成が無効になっていることである場合、手動で有効にして加速効果を向上させることをお勧めします。この構成アイテムは有効にすると、遮蔽されますので、クローズ操作はサポートしません。


## 構成ケース
- 次の通りに構成されている場合、
![](https://mc.qcloudimg.com/static/img/09edbb5616e6a110c5c5ff7cc62efe53/middle-config-1.png)
CDNの構造は次の通りです、
![](https://mc.qcloudimg.com/static/img/d51c746c04251579e09995adfea0b669/middle-config-2.png)
ユーザーリクエストが各エッジサーバーに到着すると、エッジサーバーでリソースに命中していない場合、親ノードにオリジンプルしますが、親ノードでまだ命中していない場合は、ユーザーのオリジンサーバーにオリジンプルします。
- 次の通りに構成されている場合、
![](https://mc.qcloudimg.com/static/img/798c46d5624b29526d78372ccd3c1a78/middle-config-4.png)
CDNの構造は次の通りです。
![](https://mc.qcloudimg.com/static/img/7d91b1ba3394b1b900af2d3ac810648e/middle-config-3.png)
ユーザーリクエストが各エッジサーバーに到着すると、エッジサーバーでリソースに命中していない場合、直接にユーザーのオリジンサーバーにオリジンプルして取得します。
