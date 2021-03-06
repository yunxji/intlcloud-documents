### JNI 方式使用 API 出现下面的问题？

```
Exception in thread "main" java.lang.UnsatisfiedLinkError:
com.tls.tls_sigcheck.tls_gen_signature_ex2(Ljava/lang/String;Ljava/lang/String;Ljava/lang/String;)I
        at com.tls.tls_sigcheck.tls_gen_signature_ex2(Native Method)
        at Demo.main(Demo.java:31)
```

排除动态库路径不正确的因素后，请确认代码中 package 路径是否正确，因为 JNI 动态库在编译时，接口的名称都是通过 package 路径生成的，所以不要尝试修改 tls_sigcheck.java 中的 package 路径自行编译，如此会导致上述问题。

### JNI 方式使用 API 出现下面问题？

```
Exception in thread "main" java.lang.UnsatisfiedLinkError: *** Can't load IA 32-bit *** on a AMD 64-bit platform
```

典型的 JVM 与动态库不匹配，请32位 JVM 使用32位动态库进行加载。

### UserSig 有效期是多久？

UserSig 作为云通信 IM 登录鉴权的重要凭证，默认有效期为180天，只能通过原生接口修改有效期，其他接口与工具不能修改有效期。UserSig 有效期最长可以设置为50年，为了您的帐号安全建议将 UserSig 有效期设置为两个月。详情可参阅 [生成 UserSig](https://intl.cloud.tencent.com/document/product/1027/31308)。

### 帐号是否可以删除？

云通信 IM 的帐号是不允许删除的，如果您不希望继续使用这个帐号，您可以通过 Rest  API 调用 [帐号登录态失效接口](https://intl.cloud.tencent.com/document/product/1027/31316) 使该帐号的所有者的登录状态失效。

### 登录报错70009？

请检查公私钥是否匹配，请不要使用云通信 IM Demo 的私钥来生成 UserSig。
