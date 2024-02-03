A reproducer for <https://github.com/pypa/pipx/discussions/1162>.

This works as a Python package:

```
$ poetry install
$ poetry run python
>>> import pep723_pipx_poetry_experiments
>>> pep723_pipx_poetry_experiments.foo()
<Response [200]>
```

But:

```
$ ./scripts.py 
pipx version is 1.4.0
Default python interpreter is '/usr/bin/python3'
exec_app: /usr/bin/python3 -c #!/usr/bin/env -S pipx run --path

# /// script
# requires-python = ">=3.11"
# dependencies = ["pep723-pipx-poetry-experiments @ ./"]
# ///

import pep723_pipx_poetry_experiments

pep723_pipx_poetry_experiments.foo()

Traceback (most recent call last):
  File "<string>", line 8, in <module>
ModuleNotFoundError: No module named 'pep723_pipx_poetry_experiments'
```
