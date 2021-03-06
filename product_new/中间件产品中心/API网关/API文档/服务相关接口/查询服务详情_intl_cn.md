## 接口描述

本接口（DescribeService）用于查询一个服务的详细信息、包括服务的描述、域名、协议、创建时间、发布情况等信息。

## 输入参数

以下请求参数列表仅列出了接口请求参数，其它参数可参考 [公共请求参数]((https://intl.cloud.tencent.com/document/api/213/6976)。

| 参数名称      | 是否必选 | 类型     | 描述          |
| --------- | ---- | ------ | ----------- |
| serviceId | 是    | String | 待查询的服务唯一 ID |

## 输出参数

| 参数名称              | 类型           | 描述                                                         |
| --------------------- | -------------- | ------------------------------------------------------------ |
| code                  | Int            | 公共错误码，0表示成功，其他值表示失败。详见错误码页面的 <a href="https://cloud.tencent.com/doc/api/372/%E9%94%99%E8%AF%AF%E7%A0%81#1.E3.80.81.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81" title="公共错误码">公共错误码</a> |
| codeDesc              | String         | 业务侧错误码。成功时返回 Success，错误时返回具体业务错误原因 |
| message               | String         | 模块错误信息描述，与接口相关                                 |
| serviceId             | String         | 服务唯一 ID                                                  |
| serviceName           | String         | 用户自定义的服务名称                                         |
| serviceDesc           | String         | 服务描述                                                     |
| subDomain             | String         | 系统给该服务自动分配的域名                                   |
| protocol              | String         | 服务的前端请求类型。如 HTTP 和 HTTPS                         |
| createdTime           | Timestamp      | 创建时间。按照 ISO8601 标准表示，并且使用 UTC 时间。格式为：YYYY-MM-DDThh:mm:ssZ |
| modifiedTime          | Timestamp      | 最后修改时间。按照 ISO8601 标准表示，并且使用 UTC 时间。格式为：YYYY-MM-DDThh:mm:ssZ |
| availableEnvironments | List Of String | 已经发布的环境列表，如 Test、Pre、release                    |

## 示例 
```
https://apigateway.api.qcloud.com/v2/index.php?
&<公共请求参数>
&Action=DescribeService
&serviceId=service-XX
```
返回示例如下：
```
{
	"code": "0",
	"message": "",
	"codeDesc": "Success",
	"serviceId": "service-XX",
	"serviceName": "test1",
	"serviceDesc": "test1",
	"subDomain": "523e8dc7bbe04613b5b1d726c2a7889d-apigateway.ap-guangzhou.qcloud.com",
	"protocol": "http",
	"createdTime": "2017-08-07T00:00:00Z",
	"modifiedTime": "2017-08-07T00:00:00Z",
	"availableEnvironments": [
		"Pre",
		"release"
	]
}
```

