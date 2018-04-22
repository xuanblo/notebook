# notebook

This project help you build your own blog or notebook on local server or Github.

## install

1. fork this project

```shell
git clone https://github.com/xuanblo/notebook.git
```

2. install packages

```shell
pip install mkdocs=0.17.3
pip install mkdocs-material
```

## run on local server

```shell
cd  notebook
mkdocs serve
```
See: http://127.0.0.1:8000

## put your notebook on Github for a static web page

1. build a github pages project, [how to](https://pages.github.com/)

```
git clone https://github.com/xuanblo/xuanblo.github.io.git
```

2. pull your site

```shell
cd  notebook
mkdocs build
cd ../
mv notebook/site ./
cp -r site/* xuanblo.github.io/
```
try pull `site` to your github project