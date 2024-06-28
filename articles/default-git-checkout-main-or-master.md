---
title: "デフォルトブランチがmainかmasterかを意識せずcheckoutしたい"
emoji: "🐥"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["Git"]
published: true
---

案件によって、デフォルトブランチがまだ master のままになっていることがあります。
そのため master ブランチがデフォルトブランチなのに誤って main ブランチに切り替えてしまい、`error: pathspec 'main' did not match any file(s) known to git` で怒られることも。(その逆も然り)

そこで今回は、エイリアスを使用してデフォルトブランチが main か master かを意識せず checkout する方法をまとめます。

# 解決策

~/.zshrc に alias を設定する
```shell
[alias]
  alias gm='git checkout $(git symbolic-ref refs/remotes/origin/HEAD | sed "s@^refs/remotes/origin/@@")'
```

これで `git checkout master` や `git checkout main` の代わりに、`gm` を実行することで、デフォルトブランチが main か master かを意識せずに切り替えることができます。
