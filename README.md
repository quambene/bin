<!-- markdownlint-disable MD024 MD031 -->

# bin

Utility bash scripts for `cargo`, `git`, etc.

- [cargo-clean](#cargo-clean)
  - [Usage](#usage)
  - [Examples](#examples)
- [cargo-regression](#cargo-regression)
  - [Usage](#usage)
- [git-checkout](#git-checkout)
  - [Usage](#usage)
  - [Examples](#examples)

## cargo-clean

`cargo-clean` searches for `target` folders and `Cargo.toml` files in a given
directory. For all found sub directories, `cargo clean` is executed.

### Usage

``` bash
cargo-clean <directory>
cargo-clean <directory> --dry-run
```

### Examples

``` bash
cargo-clean ~/my_rust_projects
```

A dry run of `cargo-clean` is accomplished via parameter `--dry-run`:

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

## cargo-regression

`cargo-regression` runs all integration tests which are behind feature flag
"integration-test" on two branches. Some of these tests may fail. It then compares
the test results and determines if any regression did occur.

### Usage

1. Copy script to `~/bin`
1. Add `~/bin` to PATH:
    ``` bash
    export PATH="$HOME/.cargo/bin:$PATH"
    ```
1. Make script executable:
    ``` bash
    chmod u+x cargo-regression
    ```
1. Run the script in your local Rust project:
    ``` bash
    cargo-regression
    ```

## git-checkout

`git-checkout` searches all local branches for keywords and checks out the matched
branch. If the branch couldn't be found locally, all remote branches are
searched. The matched branch is checked out locally and set up to track the
remote branch.

### Usage

``` bash
git-checkout <keyword1> <keyword2> <keyword3> ... <keywordn>
git-checkout <keyword1> <keyword2> <keyword3> ... <keywordn> --dry-run
```

### Examples

#### Search and check out local branch

``` bash
git-checkout fix bug
```

``` console
> Searching for pattern: *fix*bug*
> Switched to branch 'bug-386729-fix-terrible-bug'
> Your branch is up to date with 'origin/bug-386729-fix-terrible-bug'.
```

#### Search and check out remote branch

``` bash
git-checkout fix bug
```

``` console
> Searching for pattern: *fix*bug*
> Branch 'bug-386729-fix-terrible-bug' set up to track remote branch 'bug-386729-fix-terrible-bug' from 'origin'.
> Switched to a new branch 'bug-386729-fix-terrible-bug'
```
