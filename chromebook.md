# my chromebook environment

## bash

基本所作。

```
sudo apt-get update
sudo apt-get upgrade
```

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

入れるものとしては：

- 基本
  - numpy
  - scipy
  - pandas
  - scikit-learn
- グラフ
  - matplotlib
  - seaborn
  - bokeh
- Jupyter系
  - notebook
  - jupyterlab
  - nodejs

```
conda create -n me python=3.8 numpy scipy pandas matplotlib seaborn bokeh scikit-learn nodejs notebook jupyterlab -c conda-forge
```

あとは、任意だが、UMAPのモジュール：

``conda install -c conda-forge umap-learn``


あ、notebook用のウィジェット用

```
pip install ipywidgets
jupyter nbextension enable --py widgetsnbextension
```


Jupyterのエクステンションもめぼしいものは入れておくといいかも：

``jupyter labextension install @jupyterlab/toc @lckr/jupyterlab_variableinspector @jupyter-widgets/jupyterlab-manager``


Kiteを使うなら下の２つも：

``jupyter labextension install @kiteco/jupyterlab-kite ``
``pip install jupyter-kite``



下は機械学習系：

```
pip install jax jaxlib
pip install tensorflow
pip install numpyro
```

上のインストールでnumpy（tensorflow由来）、jax（numpyro由来）がダウングレードするかも。


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

### IJulia

notebookで使えるように、これだけはまず入れておく。

``julia`` 起動して、``Pkg`` モードで

```
add IJulia
```
