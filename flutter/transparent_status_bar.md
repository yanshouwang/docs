# 在 Flutter 中设置透明状态栏

Android 平台下默认显示半透明状态栏，在 Flutter 中实现透明状态栏，只需要在 main.dart 文件中首次加载 Widget 时调用 `SystemChrome.setSystemUIOverlayStyle()` 方法：

``` dart
import 'package:flutter/material.dart';
import 'package:flutter/services.dart';

void main() {
  runApp(App());
}

class App extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    final style =
        SystemUiOverlayStyle.light.copyWith(statusBarColor: Colors.transparent);
    SystemChrome.setSystemUIOverlayStyle(style);

    return Scaffold(
      appBar: AppBar(
        title: Text('Title'),
      ),
    );
  }
}
```

注：仅适用于 Android 6.0 以上系统