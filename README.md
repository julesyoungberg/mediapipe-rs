# ux-mediapipe

Rust and mediapipe.

Mediapipe is a framework for building AI-powered computer vision and augmented reality applications. It provides high level libraries exposing some of its solutions for common problems. This package makes some of these solutions available in Rust. In order to use it we must build a custom mediapipe C++ library.

## requirements

- [bazel](https://bazel.build/install)

## setup

Clone the modified Mediapipe repo:

```shell
git clone https://github.com/julesyoungberg/mediapipe.git
cd mediapipe
```

Build & install the mediagraph library.

### mac os

```shell
bazel build --define MEDIAPIPE_DISABLE_GPU=1 mediapipe:libmediagraph.dylib
sudo cp bazel-bin/mediapipe/libmediagraph.dylib /usr/local/lib/libmediagraph.dylib
cp mediapipe/mediagraph.h /usr/local/include/mediagraph.h
```

### linux (untested)

```shell
bazel build --define MEDIAPIPE_DISABLE_GPU=1 mediapipe:mediagraph
cp bazel-bin/mediapipe/libmediagraph.so /usr/local/lib/libmediagraph.so
cp mediapipe/mediagraph.h /usr/local/include/mediagraph.h
```

## examples

Examples are located in the `./examples` directory. Run them with

```shell
cargo run --release --example hello
```

## usage

Add the following to your dependencies list in `Cargo.toml`:

```toml
ux-mediapipe = { git = "https://github.com/julesyoungberg/ux-mediapipe" }
```
