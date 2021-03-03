# my chromebook environment

## Python

### ``conda``

まずは Anaconda 入れる。

https://www.anaconda.com/products/individual#linux

適当なところに``.sh``入れて、

``bash ***.sh``

でよしなにインストール。シェル再起動して、

``conda -V``

でインストールできているか確認。

### 環境構築 ``me``

``conda create -n default-lite python=3.8 numpy scipy pandas matplotlib seaborn bokeh scikit-learn nodejs notebook jupyterlab -c conda-forge``

あとは、

``conda install -c conda-forge umap-learn``

``jupyter labextension install @jupyterlab/toc @lckr/jupyterlab_variableinspector @kiteco/jupyterlab-kite @jupyter-widgets/jupyterlab-manager``

``pip install jupyter-kite``

``pip install ipywidgets``

``jupyter nbextension enable --py widgetsnbextension``

下は機械学習系：

``pip install jax jaxlib``

``pip install tensorflow``（numpyがダウングレードするかも）

``pip install numpyro``（jaxがダウングレードするかも）


## Julia

From https://julialang.org/downloads/platform/#linux_and_freebsd

```
wget https://julialang-s3.julialang.org/bin/linux/x64/1.5/julia-1.5.3-linux-x86_64.tar.gz
tar zxvf julia-1.5.3-linux-x86_64.tar.gz
```

そのあと、PATH通す：

``vi .bashrc``

``
PATH = "julia-1.5.3/bin:$PATH"
``