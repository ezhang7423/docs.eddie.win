---
description: https://github.com/ezhang7423/research_project
---

# Research Template Reference

Primary Development Features/Dependencies:

* [Poetry](poetry.md)
* [Typer](typer.md)
* [eztils](../eztils-reference/)
* [Dockerfile](dockerfile.md)
* [CI/CD for building and publishing](ci-cd.md)

Dive into the specifics of each feature by checking out the complete documentation for each.

### Optional Features

Google Drive Remote Filesystem

Option 1 (mounts google drive onto local file system): [https://github.com/astrada/google-drive-ocamlfuse](https://github.com/astrada/google-drive-ocamlfuse)

Option 2 (makes gdrive act like a local folder with fsspec api):

[https://github.com/fsspec/gdrivefs](https://github.com/fsspec/gdrivefs)





## 🏗️ Development

1. Install and initialize poetry and install `pre-commit` hooks:

```bash
make install
make pre-commit-install
```

2. Run the codestyle:

```bash
make codestyle
```

### Makefile usage

[`Makefile`](https://github.com/ezhang7423/%7B%7Bresearch\_project%7D%7D/blob/master/Makefile) contains a lot of functions for faster development.

<details>

<summary>1. Download and remove Poetry</summary>

To download and install Poetry run:

```bash
make poetry-download
```

To uninstall

```bash
make poetry-remove
```

</details>

<details>

<summary>2. Install all dependencies and pre-commit hooks</summary>

Install requirements:

```bash
make install
```

Pre-commit hooks coulb be installed after `git init` via

```bash
make pre-commit-install
```

</details>

<details>

<summary>3. Codestyle</summary>

Automatic formatting uses `pyupgrade`, `isort` and `black`.

```bash
make codestyle

# or use synonym
make formatting
```

Codestyle checks only, without rewriting files:

```bash
make check-codestyle
```

Note: `check-codestyle` uses `isort`, `black` and `darglint` library

Update all dev libraries to the latest version using one comand

```bash
make update-dev-deps
```

</details>

<details>

<summary>5. Type checks</summary>

Run `mypy` static type checker

```bash
make mypy
```

</details>

<details>

<summary>6. Tests with coverage badges</summary>

Run `pytest`

```bash
make test
```

</details>

<details>

<summary>7. All linters</summary>

Of course there is a command to ~~rule~~ run all linters in one:

```bash
make lint
```

the same as:

```bash
make test && make check-codestyle && make mypy && make check-safety
```

</details>

<details>

<summary>8. Docker</summary>

```bash
make docker-build
```

which is equivalent to:

```bash
make docker-build VERSION=latest
```

Remove docker image with

```bash
make docker-remove
```

More information [about docker](https://github.com/ezhang7423/%7B%7Bresearch\_project%7D%7D/tree/master/docker).

</details>

<details>

<summary>9. Cleanup</summary>

Delete pycache files

```bash
make pycache-remove
```

Remove package build

```bash
make build-remove
```

Delete .DS\_STORE files

```bash
make dsstore-remove
```

Remove .mypycache

```bash
make mypycache-remove
```

Or to remove all above run:

```bash
make cleanup
```

</details>
