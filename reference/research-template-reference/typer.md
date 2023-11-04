---
description: https://typer.tiangolo.com/
---

# Typer

## Simplest CLI

```
import typer


def main(name: str):
    print(f"Hello {name}")


if __name__ == "__main__":
    typer.run(main)
```

## Hierarchical CLI (multiple entrypoints)

Please look through https://github.com/ezhang7423/language-control-diffusion/blob/main/src/lcd\_\_main\_\_.py

{% @github-files/github-code-block url="https://github.com/ezhang7423/language-control-diffusion/blob/main/src/lcd/__main__.py" %}

## Add configuration saving
