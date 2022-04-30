---
title: "git checkoutの 「-b」を付けたり外したりしたくない"
emoji: "🥺"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["Git"]
published: true
---

ブランチを切り替える際、「`-b`」の付け外したりが地味に面倒だなーと思っていました。
「`-b`」を外し忘れて、`fatal: A branch named 'hoge' already exists.` に見舞われたこともしばしば...
そこで今回は、`git checkout`の「`-b`」を省略する方法をまとめます。

# 達成したいこと

下記条件を１つのコマンドで完結したい。
1. hogeブランチがない場合    → `git checkout -b hoge` の働きをする
2. hogeブランチが既にある場合 → `git checkout hoge` の働きをする

# 解決策

.gitconfigにaliasを設定する[^1]
```shell
[alias]
	ch = "!f() { git checkout $1 2>/dev/null || git checkout -b $1; }; f"
```

# まとめ

「`-b`」の付け外し忘れ防止ができるので、個人的には気に入っています！

下記を参考にしました🙏
https://stackoverflow.com/questions/26961371/switch-on-another-branch-create-if-not-exists-without-checking-if-already-exi

[^1]: もちろん、aliasが「`ch`」以外の場合や`git switch`を使用している場合でも代替できます。
