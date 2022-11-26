# bin

Utility bash scripts for `cargo`, `git`, etc.

- [cargo-clean](#cargo-clean)

## cargo-clean

`cargo-clean` searches for `target` folders and `Cargo.toml` files in a given
directory. For all found sub directories, `cargo clean` is executed.

### Usage

``` bash
cargo-clean ~/my_rust_projects
```

A dry run of this script is accomplished via parameter `--dry-run`:

``` bash
cargo-clean ~/my_rust_projects --dry-run
```

``` console
> Checking ~/my_rust_projects for Rust targets
> cargo clean ~/my_rust_projects/serde (dry run)
> cargo clean ~/my_rust_projects/tokio (dry run)
> cargo clean ~/my_rust_projects/rayon (dry run)
> 3 targets removed (dry run)
```
