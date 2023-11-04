---
description: >-
  Poetry @ https://python-poetry.org/ basically replaces pip, and gives you a
  maintainable way to track packages. It also makes it trivial to publish to
  PyPI.
---

# Poetry

The relevant files are `pyproject.toml` and `poetry.lock`

## Reinstalling dependencies

To do a full install, you should run `make install`. For just reinstalling python dependencies, you can use the following:

```
poetry lock -n && poetry export --without-hashes > requirements.txt
poetry install -n
```

## Publishing

First bump the version on line 14. Then run the below command: This is also setup in CI/CD in `.github/workflows/build_and_publish.yml`. Just add PYPI\_PASSWORD as a secret under the github repo's Settings -> Secretes and variables -> Actions.

```
poetry publish --build --username <USERNAME> --password <PASSWORD>
```

For me personally it would be

```
poetry publish --build --username ezipe --password R...
```

### Other useful commands

`poetry shell`- Enter the projectry virtual environment

`poetry add` - Add a new dependency

`poetry add --group dev` - Add a new dev dependency

