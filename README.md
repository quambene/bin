<!-- markdownlint-disable MD024 -->

# bin

Utility bash scripts for `cargo`, `git`, etc.

- [cargo-clean](#cargo-clean)
  - [Usage](#usage)
  - [Examples](#examples)
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
