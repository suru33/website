# Rust tools setup

[Original installation instructions for all operating systems](https://www.rust-lang.org/tools/install)

## MacOS Homebrew

```shell
brew install rustup-init

# run `rustup-init`
# It will install rustc and cargo
```

### Rust documentation

```shell
rustup doc
```

### To update tool chain

```shell
rustup update
```

### To create a new project

```shell
# For binary project
cargo new --bin <project_name>

# For library project
cargo new --lib <library_name>
```

### To compile

```shell
# To compile and run at the same time
cargo run

# For development/debug build
cargo build

# For release build
cargo build --release
```

### Idiomatic rust check

```shell
cargo clippy
```
