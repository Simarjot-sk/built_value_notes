## built_value lib for immutalbe objects and json serialization in flutter

### Installation

dependencies: 
    built_value: ^8.3.3 
    built_collection: ^5.1.1
    
dev_dependencies:
    build_runner: ^2.3.2
    built_value_generator: ^8.4.2



### Default Serializers

part 'default_serializers.g.dart';

@SerializersFor([
  ResponseDto,
])
final Serializers serializers = (_$serializers.toBuilder()
      ..add(DateTimeSerializer())
      ..addPlugin(StandardJsonPlugin()))
    .build();
