Watch API for Scala.js
================================
[watch](https://www.npmjs.com/package/watch) - Utilities for watching file trees.

### Description

Utilities for watching file trees.

### Build Dependencies

* [SBT v0.13.13](http://www.scala-sbt.org/download.html)

### Build/publish the SDK locally

```bash
 $ sbt clean publish-local
```

### Running the tests

Before running the tests the first time, you must ensure the npm packages are installed:

```bash
$ npm install
```

Then you can run the tests:

```bash
$ sbt test
```

### Examples

Watch the directory tree:

```scala
import io.scalajs.JSON
import io.scalajs.nodejs.fs.Stats
import io.scalajs.npm.watch._
import scalajs.js

Watch.watchTree("./node_modules", new WatchOptions(), (files: js.Dictionary[Stats], current: Stats, prev: Stats) => {
  files foreach { case (file, stat) =>
    println("file '%s' (%d bytes)".format(file, stat.size.toLong))
  }
})

// unwatch the the tree
Watch.unwatchTree("./node_modules")
```

Output:

```text
file './node_modules' (238 bytes)
file 'node_modules/.bin' (102 bytes)
file 'node_modules/exec-sh' (374 bytes)
file 'node_modules/merge' (306 bytes)
file 'node_modules/minimist' (306 bytes)
file 'node_modules/watch' (340 bytes)
file 'node_modules/.bin/watch' (1808 bytes)
file 'node_modules/exec-sh/.jshintrc' (7335 bytes)
file 'node_modules/exec-sh/.npmignore' (25 bytes)
file 'node_modules/exec-sh/.travis.yml' (1631 bytes)
file 'node_modules/exec-sh/LICENSE' (1106 bytes)
file 'node_modules/exec-sh/README.md' (3166 bytes)
file 'node_modules/exec-sh/example' (102 bytes)
file 'node_modules/exec-sh/lib' (102 bytes)
file 'node_modules/exec-sh/package.json' (2691 bytes)
file 'node_modules/exec-sh/test' (102 bytes)
file 'node_modules/merge/.npmignore' (5 bytes)
file 'node_modules/merge/LICENSE' (1116 bytes)
file 'node_modules/merge/README.md' (1135 bytes)
file 'node_modules/merge/bower.json' (503 bytes)
file 'node_modules/merge/merge.js' (2872 bytes)
file 'node_modules/merge/merge.min.js' (983 bytes)
file 'node_modules/merge/package.json' (2184 bytes)
file 'node_modules/minimist/.travis.yml' (116 bytes)
file 'node_modules/minimist/LICENSE' (1073 bytes)
file 'node_modules/minimist/example' (102 bytes)
file 'node_modules/minimist/index.js' (7189 bytes)
file 'node_modules/minimist/package.json' (2461 bytes)
file 'node_modules/minimist/readme.markdown' (2463 bytes)
file 'node_modules/minimist/test' (544 bytes)
file 'node_modules/watch/.npmignore' (45 bytes)
file 'node_modules/watch/LICENSE' (9140 bytes)
file 'node_modules/watch/cli.js' (1808 bytes)
file 'node_modules/watch/main.js' (5783 bytes)
file 'node_modules/watch/package.json' (2562 bytes)
file 'node_modules/watch/readme.mkd' (4872 bytes)
file 'node_modules/watch/scripts' (102 bytes)
file 'node_modules/watch/test' (204 bytes)
file 'node_modules/exec-sh/lib/exec-sh.js' (1896 bytes)
file 'node_modules/exec-sh/test/exec-sh.js' (4377 bytes)
file 'node_modules/minimist/example/parse.js' (69 bytes)
file 'node_modules/exec-sh/example/example.js' (443 bytes)
file 'node_modules/minimist/test/all_bool.js' (756 bytes)
file 'node_modules/minimist/test/bool.js' (3943 bytes)
file 'node_modules/minimist/test/dash.js' (980 bytes)
file 'node_modules/minimist/test/default_bool.js' (778 bytes)
file 'node_modules/minimist/test/dotted.js' (588 bytes)
file 'node_modules/minimist/test/kv_short.js' (376 bytes)
file 'node_modules/minimist/test/long.js' (779 bytes)
file 'node_modules/minimist/test/num.js' (909 bytes)
file 'node_modules/minimist/test/parse.js' (4606 bytes)
file 'node_modules/minimist/test/parse_modified.js' (238 bytes)
file 'node_modules/minimist/test/short.js' (1593 bytes)
file 'node_modules/minimist/test/stop_early.js' (328 bytes)
file 'node_modules/minimist/test/unknown.js' (2541 bytes)
file 'node_modules/minimist/test/whitespace.js' (191 bytes)
file 'node_modules/watch/scripts/release.sh' (1929 bytes)
file 'node_modules/watch/test/d' (136 bytes)
file 'node_modules/watch/test/test_monitor.js' (692 bytes)
file 'node_modules/watch/test/test_monitorRootDirectory.js' (845 bytes)
file 'node_modules/watch/test/test_watchTree.js' (697 bytes)
file 'node_modules/watch/test/d/d' (102 bytes)
file 'node_modules/watch/test/d/t' (0 bytes)
file 'node_modules/watch/test/d/d/t' (0 bytes)
```

### Artifacts and Resolvers

To add the `Watch` binding to your project, add the following to your build.sbt:  

```sbt
libraryDependencies += "io.scalajs.npm" %%% "watch" % "0.4.0-pre4"
```

Optionally, you may add the Sonatype Repository resolver:

```sbt   
resolvers += Resolver.sonatypeRepo("releases") 
```