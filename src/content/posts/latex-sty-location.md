---
title: プロジェクト用の.styの置き場所
published: 2024-09-03
description: '.texと違うディレクトリに.styを置く際のVSCodeの設定'
image: ''
tags: [LaTeX]
category: 'Article'
draft: false
---

## 課題

共通した`.sty`を使用したいが、`.tex`と同じディレクトリには置きたくない場合がある。
たとえば今回はプロジェクト専用のBeamerテーマを作っており、フォルダ構造は下のようにしたい。

```
.
├── archive
│   ├── 240725
│   │   ├── en.pdf
│   │   ├── en.tex
│   │   ├── ja.pdf
│   │   └── ja.tex
│   └── 241009
│       ├── en.pdf
│       ├── en.tex
│       ├── ja.pdf
│       └── ja.tex
└── theme
    └── beamerthemexxx.sty
```

もちろん私の環境では`/usr/local/texlive/2024/texmf-dist/tex/latex/beamer`に`.sty`を入れることで対処する方法もある。
しかしプロジェクト用のファイルをグローバルに入れるのはさすがに気が進まない。

## 解決策

`latexmk`の`-e`で読み込むフォルダを追加できる。
VSCodeの場合は次のようにしてやれば簡潔になる。

```jsonc: settings.json
  "latex-workshop.latex.tools": [
    {
      "name": "latexmk",
      "command": "latexmk",
      "args": [
        "-r",
        "%WORKSPACE_FOLDER%/.latexmkrc",
        // ここ
        "-e",
        "$ENV{'TEXINPUTS'}='%WORKSPACE_FOLDER%/theme//:' . $ENV{'TEXINPUTS'};",
        "-auxdir=%WORKSPACE_FOLDER%/out",
        "%DOC%"
      ]
    }
  ]
```

ついでに`%WORKSPACE_FOLDER%`は`.latexmkrc`や`auxdir`の指定でも有用。

## 参考

https://geniusium.hatenablog.com/entry/2019/08/18/183455
