# mockito

灵感来源于 [Mockito](https://github.com/mockito/mockito) 的 Dart 模拟框架

## 让我们来创建模拟

``` dart
import 'package:mockito/mockito.dart';

// 真实类
class Cat {
    String sound() => 'Meow';
    bool eatFood(String food, {bool hungry}) => true;
    Future<void> chew() async => print('Chewing...');
    int walk(List<String> places) => 7;
    void sleep() {}
    void hunt(String place, String prey) {}
    int lives = 9;
}

// 模拟类
class MockCat extends Mock implements Cat {}

// 创建模拟对象
var cat = MockCat();
```

测试中通过继承自 Mockito 的 Mock 类并实现 Cat 类，我们获得了一个支持打桩和验证的模拟类。

**使用了 Dart 的 null 安全新特性？** 阅读 [NULL_SAFETY_README][] 获取有关创建 non-nullable 类型模拟类的帮助。

[NULL_SAFETY_README]: https://github.com/dart-lang/mockito/blob/master/NULL_SAFETY_README.md

## 让我们来验证一些行为！
``` dart
// 与模拟对象交互
cat.sound();
// 验证交互
verify(cat.sound());
```

一旦被创建，模拟实例将记录所有交互。因此你可以有选择的 [`verify`] (或者 [verifyInOrder]，或者 [`verifyNever`]) 你感兴趣的交互。