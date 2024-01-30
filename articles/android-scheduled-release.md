---
title: "Androidアプリの初回リリースを指定日に公開する方法"
emoji: "⏰"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [Android, Flutter]
published: true
---

## はじめに

今回は、Android アプリの初回リリースを指定日に公開する方法をご紹介します。
Apple では日付を指定して公開できるのですが、Android では指定日公開の機能が用意されていないため少し工夫が必要でした。

## アップデートの場合は時間指定公開が簡単にできる

まず最初に、Android でもアップデートにおいては指定日公開が可能です。
ただ、初回リリースでは「公開の概要」部分が表示されておらず、一度アプリを公開しないと「公開の概要」の設定が編集できないようです。

参考) [【Android】google play consoleで手動公開する【時間指定公開】](https://howto-gadget.com/android/google-play-console-update-manual/)

## 初回リリースを指定日に公開する方法

ここからが本題です。
結論から言うと指定日に公開する方法は、**「内部(クローズド)テストから製品版にプロモートする」** です。

具体的な手順を実際の画面を交えて説明します。

1. Google Play Console にアプリ情報を登録する。
2. 内部(クローズド)テストでリリース(トラック)を作成する。
3. 内部(クローズド)テストの審査が通ったら、「製品版」にプロモートする。
   ![製品版にプロモート](https://tandems-corporate-site-images.s3.ap-northeast-1.amazonaws.com/blog/202212/2480772172/001.png)
4. 製品版の審査が通ったら、「公開の概要」より公開する。
   ![公開の概要より公開](https://tandems-corporate-site-images.s3.ap-northeast-1.amazonaws.com/blog/202212/2480772172/002.png)

## 質問コーナー

### 内部(クローズド)テストと製品版にプロモート後の審査どちらも必要か

どちらも必要です。製品版の審査の方がよりしっかり見ている印象です。(提出していたログイン情報の誤りをこの段階で初めて指摘されました)

### 内部テストとクローズドテストの違いは何か

**内部テスト**： 最大 100 人のテスターにアプリを迅速に配信できるので、少人数かつスピーディにテストを実施したい際にオススメ。
**クローズドテスト**： 内部テストよりも多くの人数に試すことができ、トラックも複数作成できるため、より幅広いユーザーや様々な機能を並行してテストしてもらいたい時などにオススメ。
参考) [オープンテスト版、クローズド テスト版、内部テスト版をセットアップする](https://support.google.com/googleplay/android-developer/answer/9845334?hl=ja)

### 審査にはどのくらい時間がかかるか

[公式](https://support.google.com/googleplay/android-developer/answer/9859751?hl=ja&visit_id=637556819934441326-3233823909&rd=1)によると、審査には最大７日かかるとのことなので、余裕を持って審査に提出できると良さそうです。

### 公開したらすぐ Google Play に反映されるか

どうやら検索に引っかかるまで少し時間がかかるようです。(今回だと１時間ほどで反映されました。)

#### 参考

- [Google公式 アプリを公開する](https://support.google.com/googleplay/android-developer/answer/9859751?hl=ja&visit_id=637556819934441326-3233823909&rd=1)
- [Androidアプリの初回リリースを手動で公開する方法に関するメモ](https://develop.hateblo.jp/entry/google-play-manual-release)
- [【画像で解説】Androidアプリをプロモートして製品版を公開する方法](https://pursue.fun/tech/how-to-android-google-play-console-promote-release/)
