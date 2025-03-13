## Prerequires

* Python3 and pip

## Installation

1. Download the project to your local device,

    ```
    git clone git@github.com:hari-robotics/polimi-msc-control-notes.git
    ```

2. Go to project directory, open a terminal here, type:

    ```
    pip install -r requirements.txt
    ```

## Creating new posts

1. Create a new markdown file under `docs/` folder, subfolder is allowed.

2. Add your document path to `mkdocs.yml`, it should follow the rules below:

```yaml
nav:
- 'Title': 'path/to/your/file'
```

Then, you can edit your documents

## Debugging

To preview the documents, type:

```
mkdocs serve
```

If it runs successfully, it will show a prompt like below:

```
INFO    -  [17:36:46] Serving on http://127.0.0.1:8000/
```

Go to the link and you can preview the page.

## Help

For more information, please go to the [mkdocs-material](https://squidfunk.github.io/mkdocs-material/) official website and see the user manual.