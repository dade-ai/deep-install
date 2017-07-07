server
===

- ref: `https://github.com/nteract/hydrogen`

`~/.jupyter/jupyter_notebook_config.py`가 없으면

```
$ jupyter notebook --generate-config
$ nano .jupyter/jupyter_notebook_config.py
NotebookApp.allow_origin="127.0.0.1"
# jupyter notebook



```
