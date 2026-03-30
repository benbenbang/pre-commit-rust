# Rust hooks for pre-commit

[Rust](https://www.rust-lang.org) tools package for [pre-commit](https://pre-commit.com).

## Hooks

| Hook ID | Description | Requires |
|---|---|---|
| `fmt` | Format files with `cargo fmt` | Rust toolchain |
| `check` | Check the package for errors | Rust toolchain |
| `clippy` | Lint with `cargo clippy` | Rust toolchain |
| `test` | Run the test suite with `cargo test` | Rust toolchain |
| `audit` | Audit `Cargo.lock` for security vulnerabilities | [`cargo-audit`](https://crates.io/crates/cargo-audit) |
| `deny` | Check licenses, bans, advisories, and sources | [`cargo-deny`](https://crates.io/crates/cargo-deny) |
| `sort` | Sort `Cargo.toml` dependency tables alphabetically | [`cargo-sort`](https://crates.io/crates/cargo-sort) |
| `machete` | Find unused dependencies in `Cargo.toml` | [`cargo-machete`](https://crates.io/crates/cargo-machete) |

## Usage

```yaml
- repo: https://github.com/benbenbang/pre-commit-rust
  rev: master
  hooks:
    - id: fmt
    - id: check
    - id: clippy
    - id: test
```

### Using all hooks

```yaml
- repo: https://github.com/benbenbang/pre-commit-rust
  rev: main
  hooks:
    - id: fmt
    - id: check
    - id: clippy
    - id: test
    - id: audit
    - id: deny
    - id: sort
    - id: machete
```

> **Note:** `audit`, `deny`, `sort`, and `machete` require their respective tools to be installed first.
> Install them with `cargo install cargo-audit cargo-deny cargo-sort cargo-machete`.

## Passing arguments

### fmt

```yaml
- repo: https://github.com/benbenbang/pre-commit-rust
  rev: main
  hooks:
    - id: fmt
      args: ['--verbose', '--edition', '2021', '--']
```

### clippy

```yaml
- repo: https://github.com/benbenbang/pre-commit-rust
  rev: main
  hooks:
    - id: clippy
      args: ['--', '-D', 'warnings', '-D', 'clippy::pedantic']
```

### test

```yaml
- repo: https://github.com/benbenbang/pre-commit-rust
  rev: master
  hooks:
    - id: test
      args: ['--', '--test-threads=4']
```

### deny

```yaml
- repo: https://github.com/benbenbang/pre-commit-rust
  rev: master
  hooks:
    - id: deny
      args: ['--all-features', 'check']
```
