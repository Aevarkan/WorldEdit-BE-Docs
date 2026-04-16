# Contributing to WorldEdit Documentation
The documentation is built with [MkDocs](https://www.mkdocs.org), and hosted by [Read the Docs](https://readthedocs.org).

## Working Locally
You will need [Python](https://www.python.org/downloads/) installed to preview your changes.

To start the live preview, in the project's root, first run
```shell
python3 -m venv .venv
```

The next command varies between operating systems. On Windows (using PowerShell), run
```powershell
. .venv\Scripts\activate.ps1
```

On Linux and macOS, run
```bash
. .venv/bin/activate
```

You should now be in the virtual environment. Install the modules required with
```shell
pip install -r requirements.txt
```

You can then enable the live preview with
```shell
mkdocs serve --livereload
```

You should get an output similar to this
```shell
$ mkdocs serve --livereload
INFO    -  Building documentation...
INFO    -  Cleaning site directory
INFO    -  Documentation built in 0.19 seconds
INFO    -  Serving on http://127.0.0.1:8000/
```

Navigate to the output address in your browser to see the live preview. Any changes you make to the documentation will be reflected live while editing.
