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
$ rm -rf ~/.cache/pipx/ ~/.local/state/pipx/
$ pipx --version
1.4.3
$ ./scripts.py 
Fatal error from pip prevented installation. Full pip output in file:
    /home/alex/.local/state/pipx/log/cmd_2024-02-03_12.33.57_pip_errors.log

Some possibly relevant errors from pip install:
    ERROR: Invalid requirement: 'pep723-pipx-poetry-experiments@ ./'
Error installing pep723-pipx-poetry-experiments@ ./.
[alex@molly pep723-pipx-poetry-experiments]$ cat /home/alex/.local/state/pipx/log/cmd_2024-02-03_12.33.57_pip_errors.log
PIP STDOUT
----------

PIP STDERR
----------
ERROR: Invalid requirement: 'pep723-pipx-poetry-experiments@ ./'
Hint: It looks like a path. File 'pep723-pipx-poetry-experiments@ ./' does not exist.
```
