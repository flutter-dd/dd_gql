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


1. get-graphql-schema http://XXXXXXXXXXXXXX/ > schema.graphql 导出文件到根目录下
2. 项目根目录下创建 build.yaml 文件
3. 在lib目录下创建 graphql 文件夹, 用来存放 .graphql 文件
``` build.yaml
targets:
  $default:
    sources:
      - lib/**
      - schema.graphql
    builders:
      artemis:
        options:
          schema_mapping:
            - schema: schema.graphql
              queries_glob: lib/**.graphql
              output: lib/graphql/models.dart
          scalar_mapping:
            - graphql_type: GenericScalar
              dart_type: Object
              use_custom_parser: true
```
4. flutter pub run build_runner build --delete-conflicting-outputs