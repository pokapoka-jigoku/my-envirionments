# my chromebook environment

## bash

基本所作。

```
sudo apt-get update
sudo apt-get upgrade
```

日本語入力できるようにするなら、以下参考？：

https://qiita.com/suzuki_sh/items/adead0fd9adefec112af

### IPAフォントのインストール

```
sudo apt install fonts-ipafont fonts-ipaexfont
```

### Myricaフォントのインストール。 ``~/.fonts``に移動させる。

```
mkdir /tmp/fonts; cd $_
wget https://github.com/tomokuni/Myrica/raw/master/product/Myrica.zip
unzip Myrica.zip
mv ./Myrica.TTC ~/.fonts/
fc-cache --force --verbose
```

### セットアップ

``fcitx-mozc``を使う。

```
$ sudo apt install fcitx-mozc
```

…あとはさっきの記事を見て設定！：

https://qiita.com/suzuki_sh/items/adead0fd9adefec112af#%E6%97%A5%E6%9C%AC%E8%AA%9E%E5%85%A5%E5%8A%9B%E3%81%AE%E3%82%BB%E3%83%83%E3%83%88%E3%82%A2%E3%83%83%E3%83%97


## git

```
sudo apt-get install git

git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

## Docker

このQiita参考にする：

https://qiita.com/pyama2000/items/90b189964f71def53b19#docker%E9%96%A2%E9%80%A3%E3%83%84%E3%83%BC%E3%83%AB%E3%82%92%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB

あるいは公式の説明（多分一緒）

https://docs.docker.com/engine/install/ubuntu/

## VSCode

普通に入れましょう

https://qiita.com/s1r/items/c0977bd3c5d6244ba829

## Python

### ``conda``

まずは Anaconda 入れる。

https://www.anaconda.com/products/individual#linux

適当なところに``.sh``ダウンロードする。

あるいは``wget``で、

```
wget https://repo.anaconda.com/archive/Anaconda3-2020.11-Linux-x86_64.sh
```

```
bash ***.sh
```

でよしなにインストール。シェル再起動して、

```
conda -V
```

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
export PATH="/home/$USER/julia-1.5.3/bin:$PATH"
``

juliaは基本的にREPLでパッケージ管理もできるし、逐一必要なやつ入れていけばOK

### IJulia

notebookで使えるように、これだけはまず入れておく。

``julia`` 起動して、``Pkg`` モードで

```
add IJulia
```

### プロジェクト系

```
add PkgTemplates
add Revise
```

See: https://qiita.com/mametank/items/43330a9452f0039ca22d
