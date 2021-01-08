# dd_gql

A new Flutter package.

## Getting Started

This project is a starting point for a Dart
[package](https://flutter.dev/developing-packages/),
a library module containing code that can be shared easily across
multiple Flutter or Dart projects.

For help getting started with Flutter, view our 
[online documentation](https://flutter.dev/docs), which offers tutorials, 
samples, guidance on mobile development, and a full API reference.


1. get-graphql-schema http://XXXXXXXXXXXXXX/ > sdl.gql 导出文件到根目录下
2. 项目根目录下创建 build.yaml 文件
3. 在lib目录下创建 gqls 文件夹, 用来存放 .graphql 文件
4. 在lib目录下创建 Models 文件夹, 用来存放自动生成的文件

``` build.yaml
targets:
  $default:
    sources:
      - lib/**
      - sdl.gql
    builders:
      artemis:
        options:
          schema_mapping:
            - schema: sdl.gql
              queries_glob: lib//gqls/**.graphql
              output: lib/Models/models.dart
          scalar_mapping:
            - graphql_type: GenericScalar
              dart_type: Object
              use_custom_parser: true
```

``` pubspec.ymal
.
.
.
dev_dependencies:
  flutter_test:
    sdk: flutter
  json_serializable: ^3.0.0
  build_runner: ^1.5.0
.
.
.
```


5. flutter pub run build_runner build --delete-conflicting-outputs