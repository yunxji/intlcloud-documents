当您不再需要该子机时，可随时销毁专用子机。销毁专用子机实例后，挂载在实例上的本地盘和非弹性云硬盘都将一并销毁，保存在这些存储上的数据将丢失。但挂载在该实例上的弹性云盘会继续保留，数据不受影响。

## 通过宿主机控制台销毁实例
1. 登录 [专用宿主机控制台](https://console.cloud.tencent.com/cvm/cdh)。
2. 单击相应宿主机 ID/名称，进入宿主机详情页。
3. 单击【云主机列表】进入宿主机下主机列表详情。
4. 选择需要销毁的专用子机，单击【销毁】进行销毁实例操作。
![](https://main.qcloudimg.com/raw/1d42bf78f07ab5af287763162af1f3a6.png)

## 通过云主机控制台销毁实例
1. 登录 [云主机控制台](https://console.cloud.tencent.com/cvm)。
2. 找到所要销毁的专用子机实例。单击右侧操作栏中【更多】>【云主机状态】>【销毁】。
![](https://main.qcloudimg.com/raw/27ce25d4b9a4d4d095a64eb856ab2871.png)

## 通过 API 销毁子机
使用 TerminateInstances 接口销毁子机，具体用法详见[ 退还实例 API](https://intl.cloud.tencent.com/document/api/213/15723)。

