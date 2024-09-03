---
title: Gitのコミットメッセージ
published: 2024-09-03
description: 'コミットメッセージの方針をメモ'
image: ''
tags: [Git]
category: 'Note'
draft: false
---

ひとまずこれでいきたい。
参考の記事そのままコピペですみません。

`<Type>: <Emoji> #<Issue Number> <Title>`  
例）feat: ✨ #123 ログイン機能の実装をする

- `chore` タスクファイルなどプロダクションに影響のない修正
- `docs` ドキュメントの更新
- `feat` ユーザー向けの機能の追加や変更
- `fix` ユーザー向けの不具合の修正
- `refactor` リファクタリングを目的とした修正
- `style` フォーマットなどのスタイルに関する修正
- `test` テストコードの追加や修正

`feat`が基本で、`feat`ぽくないならその他、で良いかな

## 参考

https://zenn.dev/itosho/articles/git-commit-message-2023
