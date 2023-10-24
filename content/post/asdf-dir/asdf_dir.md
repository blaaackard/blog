---
title: "brew で asdf のバージョン上げたら使えなくなった"
description: $ASDF_DIRに悩まされた話🤢
slug: asdf_dir
date: 2023-10-25T00:30:26+09:00
math:
license:
hidden: false
comments: true
draft: false
categories:
    - ツール
tags:
    - ツール
    - asdf
---

# 問題

brewで asdf のバージョンを 0.11.1 から 0.13.1 に上げたときに asdf コマンドが効かなくなりました。

```bash
❯ asdf
Unknown command: `asdf `
/opt/homebrew/opt/asdf/libexec/bin/asdf: line 117: /opt/homebrew/Cellar/asdf/0.11.1/libexec/lib/commands/command-help.bash: No such file or directory
```

# 原因

環境変数 `$ASDF_DIR` で古いバージョンを指定していた。

```bash
vi ~/.zshrc

# 以下の記述が...
export ASDF_DIR=/opt/homebrew/Cellar/asdf/0.11.1/libexec
```

`/opt/homebrew/Cellar/asdf/0.13.1/libexec`に書き換えようと思ったけどそもそもこれ指定しなくてよいのでは？と思いコメントアウトして再読み込みすると、、、

```bash
❯ asdf
version: v0.13.1

MANAGE PLUGINS
```

普通に使えました。  
過去の自分はなぜこの環境変数を使ったのか謎。



