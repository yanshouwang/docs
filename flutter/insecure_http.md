# 允许不安全明文请求

Android 和 iOS 中默认禁止使用不安全的 HTTP 请求，如果请求不支持 HTTPS，需要在项目中允许 HTTP 请求。

修改 `android/app/src/main/AndroidManifest.xml` 文件，在 `application` 节点属性中添加 `android:usesCleartextTraffic="true"`：

``` XML
...
<application
    ...
    android:usesCleartextTraffic="true">
...
```

修改 `ios/Runner/info.plist` 增加 `NSAppTransportSecurity` 配置如下：

``` plist
...
<dict>
    ...	
    <key>NSAppTransportSecurity</key>
	<dict>
		<key>NSAllowsArbitraryLoads</key>
        <true/>
	</dict>
</dict>
...
```