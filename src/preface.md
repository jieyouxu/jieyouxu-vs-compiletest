# Preface

This little book records my adventure in ~~fighting~~ reworking [`compiletest`].

```admonish success title="Kudos to people who have contributed to compiletest"
This little book will likely have many rants and complaints. But these are not directed to any
particular contributor. [`compiletest`] mostly organically grew over the years and it's long past
due for some tidy ups and reworks. I hope the reworks will make [`compiletest`] easier to
maintain, less painful to debug, and easier to add new test modes and test suites if deemed
desirable.

[`compiletest`] has done exceptionally well in helping the development of [`rustc`] and friends.
Thanks to everyone who contributed to [`compiletest`] to help the development of [`rustc`] and
friends.
```

```admonish warning title="Content Warning: Here Be Dragons"
This little book will contain my rants, which may include vulgar language. It's not intended to be
a professional piece of technical writing.
```

## Context

[`compiletest`] is the main test harness of the Rust compiler (see the [Compiletest chapter] in the
dev-guide). Over the years, it has seen many additions and modifications that is mostly organically
grown, which makes it a pain to debug and maintain.

[compiler-team MCP 536][mcp-536] was accepted to rewrite compiletest out of tree as [`ui_test`]. But
there's still tons of work to be done, and there isn't a clear picture of how to completely replace
[`compiletest`] with [`ui_test`] -- even the MVP goal of using [`ui_test`] to run the ["ui" test
suite][ui-test-suite] is highly non-trivial.

I expect the rewrite to take multiple years. In the meantime, [`rustc`] and friends still need to
rely on [`compiletest`] to have some guardrails for making changes and minimizing regressions. We
better make sure the test harness is reliable, otherwise the compiler and friends are like a big
jenga tower that will collapse if you pull out the "compiletest" piece.

<div align="center">
  <img src="./preface/compiletest.png" width="30%" />

  Image edited from <https://xkcd.com/2347/>
</div>

[`compiletest`]: https://github.com/rust-lang/rust/tree/master/src/tools/compiletest
[Compiletest chapter]: https://rustc-dev-guide.rust-lang.org/tests/compiletest.html
[mcp-536]: https://github.com/rust-lang/compiler-team/issues/536
[`ui_test`]: https://github.com/oli-obk/ui_test
[ui-test-suite]: https://github.com/rust-lang/rust/tree/master/tests/ui
[`rustc`]: https://github.com/rust-lang/rust
