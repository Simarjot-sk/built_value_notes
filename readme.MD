## built_value lib for immutalbe objects and json serialization in flutter

### Installation
```
dependencies: 
    built_value: ^8.3.3 
    built_collection: ^5.1.1
    
dev_dependencies:
    build_runner: ^2.3.2
    built_value_generator: ^8.4.2
```


### Default Serializers

```
part 'default_serializers.g.dart';

@SerializersFor([
  ResponseDto,
])
final Serializers serializers = (_$serializers.toBuilder()
      ..add(DateTimeSerializer())
      ..addPlugin(StandardJsonPlugin()))
    .build();
```

### Immutable Objects Boilerplate

```
import 'package:built_collection/built_collection.dart';
import 'package:built_value/built_value.dart';
import 'package:built_value/serializer.dart';

part 'data.g.dart';

abstract class Data implements Built<Data, DataBuilder> {

  String get title;

  TestEnum get decision;

  Data._();

  static Serializer<Data> get serializer => _$dataSerializer;

  factory Data([void Function(DataBuilder)? updates]) =
      _$Data;
}


class TestEnum extends EnumClass {
  /// Example of how to make an [EnumClass] serializable.
  ///
  /// Declare a static final [Serializers] field called `serializer`.
  /// The built_value code generator will provide the implementation. You need
  /// to do this for every type you want to serialize.
  static Serializer<TestEnum> get serializer => _$testEnumSerializer;

  static const TestEnum yes = _$yes;
  static const TestEnum no = _$no;
  static const TestEnum maybe = _$maybe;

  const TestEnum._(String name) : super(name);

  static BuiltSet<TestEnum> get values => _$values;
  static TestEnum valueOf(String name) => _$valueOf(name);
}
```
