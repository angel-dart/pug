# pug
[![version 1.0.0](https://img.shields.io/badge/pub-1.0.0-brightgreen.svg)](https://pub.dartlang.org/packages/angel_pug)

Pug (nee Jade) view generator for Angel.

# Installation
In your `pubspec.yaml`:

```yaml
dependencies:
  angel_pug: ^1.0.0
```

# Usage
This package exports a simple
[Angel plugin](https://github.com/angel-dart/angel/wiki/Using-Plug-ins)
that configures your application to render views out of a given directory.

```dart
import 'dart:io';
import 'package:angel_framework/angel_framework.dart';
import 'package:angel_pug/angel_pug.dart';

main() async {
  // ...
  await app.configure(pug(new Directory('views')));
}
```

The `pug` function accepts an optional `Iterable<String> extensions` parameter,
which defaults to `['.pug', '.jade']`. These extensions will be suffixed to template names
when calling `res.render` (i.e. `res.render('foo')` searches for `['foo.pug', 'foo.jade']`)
to find the corresponding view file. 

If you set it to `null` or an empty iterable, then extensions
will not be added. This is a rare case, and only is necessary if your template files have no extensions.
