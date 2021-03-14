試験的に導入してみる jupyterlab のエクステンション


## elyra

なんなんだこれは

```
conda install -c conda-forge "elyra>=2.0.1" && jupyter lab build
```

ノートブックのパイプラインを作れるっぽい…？

## git

https://www.hiromasa.info/posts/17/

```
pip install jupyterlab_git
jupyter serverextension enable --py jupyterlab_git
jupyter labextension install @jupyterlab/git
jupyter lab build
```