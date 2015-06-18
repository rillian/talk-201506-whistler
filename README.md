# Rust in Gecko

In the media playback team we've been working on writing parser code in the new
rust programming language for safety. I'll talk about what this looks like, why
it's important, and how other contributors can try it too.

# Why

We don't know how to write safe, concurrent C++ code.

Media playback is cpu-intensive, must juggle many resources.

Seems ideal for thread parallelism, but we've had lots of
trouble with races, deadlocks, inefficiency.

Rewrote the stack several times over the years. Most recently
with Bobby Holly's C++ MediaPromise library.

We've been using the stagefright mp4 demuxer (from Android).
Found ~6 security vulnerabilities this year alone.

This is the problem rust was designed to solve.

# How to use rust in gecko.

Install rust compiler:

- Install button on http://www.rust-lang.org/
- Update tool https://github.com/rust-lang/rustup

- ac_add_options --enable-rust

On Mac:

- ac_add_options --enable-macos-target=10.7

FFI example.

```
if CONFIG['MOZ_RUST']:
    SOURCES += ['hello.rs',]
        UNIFIED_SOURCES += ['TestRust.cpp',]
```

Tracking bug https://bugzil.la/oxidation
