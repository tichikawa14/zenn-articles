---
title: "Github ActionsでResource not accessible by integrationが出た際の対処法"
emoji: "📑"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [GithubActions]
published: true
---

[こちらの記事](https://zenn.dev/ryo_kawamata/articles/schedule-publish-on-zenn-article)を参考にZennの予約投稿を試していたところ、
Github Actionsの`${{ secrets.GITHUB_TOKEN }}`の部分で下記のエラーが出てしまったので、解決策をメモしておきます。

![](https://i.gyazo.com/7426d8b968a2a16522f9a6d190610043.png)

:::details 実際のワークフロー用のyamlコード
https://github.com/tichikawa14/zenn-articles/blob/main/.github/workflows/merge-schedule.yml
:::

# 解決方法
該当するリポジトリの`Settings > Actions > General > Workflow permissions`を
`Read repository contents permission` から `Read and write permissions` に変更すると解決できました

![](https://i.gyazo.com/f0a5477217b16cc2c04144ee1adb6614.png)
