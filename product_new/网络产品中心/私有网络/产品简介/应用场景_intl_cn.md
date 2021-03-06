##  托管简单网站
您可以使用私有网络部署简单的 Web 应用，如博客、网站和日志系统等；通过 [安全组](https://intl.cloud.tencent.com/document/product/215/31889) 和 [网络 ACL](https://intl.cloud.tencent.com/document/product/215/5132) 等防火墙，可以使 Web 应用响应 HTTP 等请求，但拒绝 Web 应用访问 Internet，从而保证 Web 应用的安全；在流量突增时，可以在 VPC 中启用 [负载均衡](http://intl.cloud.tencent.com/document/product/214/524) 。
![](//mccdn.qcloud.com/static/img/23729e8b1f865148f8851e82db3cfff5/image.png)
相关产品：[云服务器（CVM）](http://intl.cloud.tencent.com/document/product/213/495)、[云数据库](https://intl.cloud.tencent.com/doc/product/236)、[负载均衡](http://intl.cloud.tencent.com/document/product/214/524)。

## 托管多层 Web 应用
私有网络可以在为应用提供 Internet 服务的同时，又保障数据库服务器的安全。您可以安全灵活地在私有网络中托管多层 Web 应用程序：在私有网络中创建不同的子网，将整个 Web 层放在一个子网，通过 [弹性 IP](https://intl.cloud.tencent.com/document/product/215/4958) / [公网网关](https://intl.cloud.tencent.com/document/product/215/4972) / NAT 网关与 Internet 通信；将逻辑层单独放在一个子网，只能和 Web 层及数据层通信；将数据层放在另外一个子网，只和逻辑层通信。子网和子网之间的流量通过 [网络 ACL](https://intl.cloud.tencent.com/document/product/215/5132) 控制。
![](//mccdn.qcloud.com/static/img/64ac36b8359811995205cba91f788c85/image.png)
相关产品：[云服务器（CVM）](http://intl.cloud.tencent.com/document/product/213/495)、[云数据库](https://cloud.tencent.com/doc/product/236)、[弹性 IP](https://intl.cloud.tencent.com/doc/product/213)、[NAT 网关](http://intl.cloud.tencent.com/document/product/215/4975)、[公网网关](https://intl.cloud.tencent.com/document/product/215/4972)。

##  部署弹性混合云
您可以在私有网络内，部署应用程序；在企业数据中心，部署数据库服务器。私有网络提供稳定安全的VPN 连接 / [专线接入](https://intl.cloud.tencent.com/document/product/216) 服务，帮您打通企业数据中心与云端资源。您可使用 [弹性伸缩](http://intl.cloud.tencent.com/document/product/377/3154) 服务，以根据业务量扩展应用程序的资源（云服务器等），既降低了企业 IT 运维成本，又无需担心企业核心数据外泄，轻松实现弹性混合云部署。
![](//mccdn.qcloud.com/static/img/23ac09921e7876e6d33d75704dc7f6db/image.png)
相关产品：[云服务器（CVM）](http://intl.cloud.tencent.com/document/product/213/495)、[云硬盘（CBS）](http://intl.cloud.tencent.com/document/product/362/2345)、[弹性伸缩（AS）](http://intl.cloud.tencent.com/document/product/377/3154)、[专线接入](https://intl.cloud.tencent.com/document/product/216)、VPN 连接。

