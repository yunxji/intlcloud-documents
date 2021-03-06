## 1. API Description

API request domain name: batch.tencentcloudapi.com.

This API is used to submit a job.

Default API request frequency limit: 2 times/second.


## 2. Input Parameters

The following list of request parameters lists only the API request parameters and some common parameters. For the complete list of common parameters, see [Common Request Parameters](/document/api/599/30473).

| Parameter name | Required | Type | Description |
|---------|---------|---------|---------|
| Action | Yes | String | Common parameter; the value for this API: SubmitJob |
| Version | Yes | String | Common parameter; the value for this API: 2017-03-12 |
| Region | Yes | String | Common parameters; for details, see the [Region List](/document/api/599/30473#.E5.9C.B0.E5.9F.9F.E5.88.97.E8.A1.A8) supported by the product. |
| Placement | Yes | [Placement](/document/api/599/30482#Placement) | Location information of the submitted job. This parameter allows you to specify information such as the availability zone of the CVM instance with which the job is associated. |
| Job | Yes | [Job](/document/api/599/30482#Job) | Job information |
| ClientToken | No | String | A string used to guarantee the idempotency of the request. This string is generated by the user and must be unique for different requests. The maximum length is 64 ASCII characters. If this parameter is not specified, the idempotency of the request cannot be guaranteed. |

## 3. Output Parameters

| Parameter name | Type | Description |
|---------|---------|---------|
| JobId | String | When a job is submitted through this API, this parameter is returned and indicates the job ID. Returning the job ID list does not mean that the job is parsed/executed successfully. The job state can be queried using the DescribeJob API. |
| RequestId | String | The unique request ID which is returned for each request. The RequestId for the current request needs to be provided when troubleshooting. |

## 4. Examples

### Example 1. Submitting a Job

#### Input

```
https://batch.tencentcloudapi.com/?Action=SubmitJob
&Placement.Zone=ap-guangzhou-2
&Job.JobName=test
&Job.JobDescription=test&Job.Priority=1
&Job.Tasks.0.TaskName=hello2
&Job.Tasks.0.TaskInstanceNum=1
&Job.Tasks.0.Application.DeliveryForm=LOCAL
&Job.Tasks.0.Application.Command=python -c "fib=lambda n:1 if n<=2 else fib(n-1)+fib(n-2); print(fib(20))"
&Job.Tasks.0.ComputeEnv.EnvType=MANAGED
&Job.Tasks.0.ComputeEnv.EnvData.InstanceType=S1.SMALL1
&Job.Tasks.0.ComputeEnv.EnvData.ImageId=img-bd78fy2t
&Job.Tasks.0.RedirectInfo.StdoutRedirectPath=cos://dondonbatch-1251783334.cosgz.myqcloud.com/hello2/logs/
&Job.Tasks.0.RedirectInfo.StderrRedirectPath=cos://dondonbatch-1251783334.cosgz.myqcloud.com/hello2/logs/
&<Common request parameter>
```

#### Output

```
{
  "Response": {
    "JobId": "job-4yn0we13",
    "RequestId": "bf2a9734-e485-423f-9d73-a93f5e6c6a0c"
  }
}
```

## 5. Developer Resources

**It is recommended to use [`API 3.0 Explorer`](https://console.cloud.tencent.com/api/explorer). This tool provides various capabilities such as online debugging, signature verification, SDK code generation and quick API retrieval that significantly reduce the difficulty of using cloud APIs.**

Cloud API 3.0 comes with a set of complementary development tools that make it easier to call the API.

* [Tencent Cloud SDK 3.0 for Python](https://github.com/TencentCloud/tencentcloud-sdk-python)
* [Tencent Cloud SDK 3.0 for Java](https://github.com/TencentCloud/tencentcloud-sdk-java)
* [Tencent Cloud SDK 3.0 for PHP](https://github.com/TencentCloud/tencentcloud-sdk-php)
* [Tencent Cloud SDK 3.0 for Go](https://github.com/TencentCloud/tencentcloud-sdk-go)
* [Tencent Cloud SDK 3.0 for NodeJS](https://github.com/TencentCloud/tencentcloud-sdk-nodejs)
* [Tencent Cloud SDK 3.0 for .NET](https://github.com/TencentCloud/tencentcloud-sdk-dotnet)
* [Tencent Cloud CLI 3.0](https://cloud.tencent.com/document/product/440/6176)

## 6. Error Codes

Only the error codes related to this API are listed below. For other error codes, see [Common Error Codes](/document/api/599/30479#.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81).

| Error Code | Description |
|---------|---------|
| AllowedOneAttributeInEnvIdAndComputeEnv | One (and only one) parameter must be specified for ComputeEnv and EnvId. |
| InternalError | Internal error |
| InvalidParameter.CvmParameters | Invalid CVM parameter. |
| InvalidParameter.JobDescriptionTooLong | The job description is too long. |
| InvalidParameter.JobNameTooLong | The job name is too long. |
| InvalidParameter.NotificationEventNameDuplicate | Duplicate message notification event name. |
| InvalidParameter.NotificationTopicName | Invalid topic name. |
| InvalidParameter.NotificationTopicNameTooLong | The topic name is too long. |
| InvalidParameter.TaskName | Invalid task name. |
| InvalidParameter.TaskNameTooLong | The task name is too long. |
| InvalidParameterValue.ComputeEnv | Compute environment parameter validation failed. |
| InvalidParameterValue.DependenceNotFoundTaskName | The dependent task definition could not be found. |
| InvalidParameterValue.DependenceUnfeasible | Loop task dependency is prohibited. |
| InvalidParameterValue.LocalPath | Invalid local storage path. |
| InvalidParameterValue.MaxRetryCount | The number of retries is too large. |
| InvalidParameterValue.Negative | Invalid negative parameter. |
| InvalidParameterValue.RemoteStoragePath | Invalid storage path format. |
| InvalidParameterValue.RemoteStorageSchemeType | Invalid storage type. |
| LimitExceeded.JobQuota | Insufficient job quota. |
| UnauthorizedOperation.UserNotAllowedToUseBatch | It is prohibited to use Batch service. |

