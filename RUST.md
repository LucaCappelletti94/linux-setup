# Rust

To install Rust, follow the instructions on the [Rust website](https://www.rust-lang.org/tools/install). The easiest way is to run the following command in your terminal:

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

## SSCACHE

[SCCACHE](https://github.com/mozilla/sccache) is a ccache-like tool. It is used as a compiler wrapper and avoids compilation when possible. Sccache has the capability to utilize caching in remote storage environments, including various cloud storage options, or alternatively, in local storage. 

```bash
cargo install sccache --locked
```

## Setting up the Cargo config.toml

Create a file named `config.toml` in the `~/.cargo` directory with the following content:

```toml
[target.x86_64-unknown-linux-gnu]
linker = "/usr/bin/clang"
rustflags = [
  "-Clink-arg=-fuse-ld=mold",
  "-Ctarget-cpu=native"
]

[build]
rustc-wrapper = "sccache"
```
