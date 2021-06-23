---
layout: post
title: 横田研で推奨しているPython環境構築
---

横田研鯖缶です。  
横田研の人はTSUBAMEやABCI、富岳、Summitなど、多くのスパコンを使います。  
ここではどのスパコンでもだいたい使えるPythonの環境構築の仕方を書いていきます。

## 思考停止でできるpyenv & Pythonインストール
### 1. pyenvのインストール

```bash
curl https://pyenv.run | bash
```
（ https://github.com/pyenv/pyenv-installer ）

これによって以下のリポジトリがインストールされます：
- https://github.com/pyenv/pyenv.git
- https://github.com/pyenv/pyenv-doctor.git
- https://github.com/pyenv/pyenv-installer.git
- https://github.com/pyenv/pyenv-update.git
- https://github.com/pyenv/pyenv-virtualenv.git
- https://github.com/pyenv/pyenv-which-ext.git

### 2. 環境変数の設定  

以下を`.zshrc`とか`.bashrc`に追記
```bash
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
```

### 3. pyenvの環境変数等の反映  

```bash
. ~/.zshrc
```
とか
```bash
. ~/.bashrc
```
とか一度exitしてsshし直すとか。

### 4. Pythonのインストール  

pyenvコマンドで好きなバージョンのPythonをインストール
```bash
pyenv install 3.8.5
```

どんなバージョンがインストール可能かを見たければ以下のコマンドを実行。
```bash
pyenv install --list
```

### 5. インストールしたPythonがデフォルトで使われるようにする

```
pyenv global 3.8.5
```

## 原則
- ホームディレクトリ下など、自分で全てをコントロールできる場所にインストールする
- システムのPythonは使わない
- スパコンセンターが用意したPythonは使わない
  - 僕も[ひなどりクラスタ](https://rioyokotalab.github.io/Lab-Servers-2020/)のパッケージ管理をしていますが、大体管理者が入れるパッケージはけしからんので、信じられるのは自分のみという気持ちでPythonに限らず全て自分で入れるのがいいでしょう。

## 補足
またに`$HOME`は計算ノードから見られないスパコンがあります。  
こういう場合はpyenvを計算ノードから見られるストレージに置く必要があります。  
たとえばこれを`/path/to/work`とすれば、
```
mv $HOME/.pyenv /path/to/work
```
とし、`PYENV_ROOT`を
```
export PYENV_ROOT="/path/to/work/.pyenv"
```
と設定します。

## 遭遇したことがあるエラー・不具合

### pyenv実行時にlocaleのエラーが出る。
```
/home/XXXX/.pyenv/libexec/pyenv-help: 行 29: 警告: setlocale: LC_CTYPE: ロケールを変更できません (UTF-8): No such file or directory
   doctor      Verify pyenv installation and development tools to build pythons.
/home/XXXX/.pyenv/libexec/pyenv-help: 行 29: 警告: setlocale: LC_CTYPE: ロケールを変更できません (UTF-8): No such file or directory
   exec        Run an executable with the selected Python version
```

なにか環境変数が足りない場合があります。  
今回は
```
export LANG=ja_JP.UTF-8
```
を`.bashrc`等に追記し反映することで解決しました。

### Pythonのインストールが刺さる

loadしているmoduleが悪さをしている可能性があります。
```
moduler purge
```
してみましょう。
