---
title: 複数のGitHubアカウントを使い分ける
published: 2024-09-03
description: 'GitHubアカウントの切り替え方を忘れがちなのでメモ'
image: ''
tags: [Git, Setup]
category: 'Note'
draft: false
---

## Remote

```
git@github-xxx:<アカウント名>/<リポジトリ名>.git
```

## Local

```bash
git config --local user.name "xxx"
git config --local user.email "yyy@mail.com"
```

将来的に`includeIf`での切り替えに移行するかな

## あんさんSSHまだですの

```bash
mkdir ~/.ssh/xxx
ssh-keygen -t ed25519 -C "yyy@mail.com" -f ~/.ssh/xxx/id_ed25519
```

```:~/.ssh/config
Host github.com-xxx
  HostName github.com
  IdentityFile ~/.ssh/xxx/id_ed25519
  User git
  UseKeychain yes
  AddKeysToAgent yes
```

` ~/.ssh/xxx/id_ed25519.pub`はGitHubへ

## 参考

https://zenn.dev/taichifukumoto/articles/how-to-use-multiple-github-accounts
