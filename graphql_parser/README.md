# graphql_parser2
[![version](https://img.shields.io/badge/pub-v2.0.1-brightgreen)](https://pub.dartlang.org/packages/graphql_parser2)
[![Null Safety](https://img.shields.io/badge/null-safety-brightgreen)](https://dart.dev/null-safety)
[![Gitter](https://img.shields.io/gitter/room/nwjs/nw.js.svg)](https://gitter.im/angel_dart/discussion)

[![License](https://img.shields.io/github/license/dukefirehawk/graphql_dart)](https://github.com/dukefirehawk/graphql_dart/LICENSE)

Parses GraphQL queries and schemas.

*This library is merely a parser/visitor*. Any sort of actual GraphQL API functionality must be implemented by you,
or by a third-party package.

[Angel3 framework](https://github.com/dukefirehawk/angel)
users should consider 
[`package:angel3_graphql`](https://github.com/dukefirehawk/graphql_dart/tree/master/angel_graphql)
as a dead-simple way to add GraphQL functionality to their servers.

# Installation
Add `graphql_parser2` as a dependency in your `pubspec.yaml` file:

```yaml
dependencies:
  graphql_parser2: ^2.0.0
```

# Usage
The AST featured in this library was originally directly based off this ANTLR4 grammar created by Joseph T. McBride:
https://github.com/antlr/grammars-v4/blob/master/graphql/GraphQL.g4

It has since been updated to reflect upon the grammar in the official GraphQL
specification (
[June 2018](https://facebook.github.io/graphql/June2018/)).

```dart
import 'package:graphql_parser2/graphql_parser2.dart';

doSomething(String text) {
  var tokens = scan(text);
  var parser = Parser(tokens);
  
  if (parser.errors.isNotEmpty) {
    // Handle errors...
  }
  
  // Parse the GraphQL document using recursive descent
  var doc = parser.parseDocument();
  
  // Do something with the parsed GraphQL document...
}
```
