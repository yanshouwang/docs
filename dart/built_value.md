Flutter 中通过 shake trees 技术删除无用代码，减少 APP 体积，导致 Flutter 中不支持反射，在序列化和反序列化时无法自动生成指定类型的对象，相关代码需要手动实现
built_value 和 json_serializer 可以帮助开发者自动生成相关代码，减少工作量和错误率

``` yaml
dependencies:
    built_value: ^7.1.0
dev_dependencies:
    build_runner: ^1.10.2
    built_value_generator: ^7.1.0
```

- VSCode 插件: Built Value Snippets

## 枚举类

## 序列化

### 使用方法
### 默认值（_initializeBuilder）
### JSON 格式 (JsonObject or Object）
### BuiltList<JsonObject> 处理日期
### 集合（BuiltCollection）
### 使用 implements 而不是 extends

## 使用注解
- @nullable
- @BuiltValueField
- @BuiltValueEnumConst