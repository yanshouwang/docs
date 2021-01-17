# 样式指南

[原文链接](https://developers.google.cn/protocol-buffers/docs/style)

本文档提供 .proto 文件的样式指南。通过遵循这些约定，将会使你的 protocol buffer 消息的定义和相应的类型一致且易于阅读。

请注意，protocol buffer 的样式随着时间的推移而变化，因此很有可能会看到以不同约定或样式编写的 .proto 文件。在修改这些文件时，请遵循现有的样式。保持一致性是关键。然而，当创建新的 .proto 文件时，最好使用当前的最佳样式。

## 标准文件格式

- 每行的字符长度不超过 80 个
- 使用 2 个空格进行缩进
- 推荐使用双引号声明字符串

## 文件结构

文件使用小写蛇形命名法：lower_snake_case.proto

使用以下方式对文件进行排序：

- 许可证标头（如果适用）
- 文件概述
- 语法
- 包
- 导入（排序过的）
- 文件选项
- 其他

## 包

包名使用小写，并且对应目录结构。例如，如果文件位于 my/package/，对于的包名应为 my.package。

## 消息和字段名称

消息使用帕斯卡命名法，如 SongServerRequest。字段（包括字段名和扩展名）使用小写蛇形命名法，如 song_name。

``` protobuf
message SongServerRequest {
    required string song_name = 1;
}
```

对字段使用此命名约定可提供如下访问器：

``` c++
C++:
const string& song_name() { ... }
void set_song_name(const string& x) { ... }
```

``` java
Java:
public String getSongName() { ... }
public Builder setSongName(String v) { ... }
```

如果字段名中包含数字，数字的位置应该在字母之后而不是下划线之后。例如，使用 song_name1 而不是 song_name_1。

## 重复字段

对重复字段（数组）使用复数名称。

``` protobuf
repeated string keys = 1;
...
repeated MyMessage accounts = 17;
```

## 枚举

枚举类型名使用帕斯卡命名法，枚举值的名称使用大写蛇形命名法：

``` protobuf
enum FooBar {
    FOO_BAR_UNSPECIFIED = 0;
    FOO_BAR_FIRST_VALUE - 1;
    FOO_BAR_SECOND_VALUE = 2;
}
```

每个枚举值以分号结束，而不是逗号。枚举的 0 值应该具有 UNSPECIFIED 后缀。

## 服务

如果 .proto 文件中定义了 RPC 服务，服务名和 RPC 方法名都使用帕斯卡命名法：

``` protobuf
service FooService {
    rpc GetSomething(FooRequest) returns (FooResponse);
}
```

## 避免使用

- 必须字段（仅适用于 proto2）
- 组（仅适用于 proto2）