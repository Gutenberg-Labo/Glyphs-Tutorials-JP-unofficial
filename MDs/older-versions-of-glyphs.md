# Glyphsの過去バージョン

[(Original page)](https://glyphsapp.com/learn/older-versions-of-glyphs)  

by Rainer Erich Scheichelbauer  

3 December 2020  
Published on 31 August 2012  

********

時には、最新・最高ではないバージョンのGlyphsが必要になる場合があります。これは過去バージョンの入手方法です。

********

大抵の場合、過去のバージョンに戻すことは推奨していません。常識的に考えて、新しいバージョンが出るのは理由があるからです。しかし、最新のベータ版でトラブルが発生する時は、最新の安定版に戻した方が良いでしょう。

## 最新の安定版とベータ版

Glyphsの各メジャーバージョンの最新の安定版は、以下のリンクから入手できます。

| バージョン | リンク先 |
|------------|----------|
| Glyphs 1      | [latest.php](https://updates.glyphsapp.com/latest.php) |
| Glyphs 2      | [latest2.php](https://updates.glyphsapp.com/latest2.php) |
| Glyphs 3      | [latest3.php](https://updates.glyphsapp.com/latest3.php) |
| Glyphs Mini 1 | [latestMini.php](https://updates.glyphsapp.com/latestMini.php) |
| Glyphs Mini 2 | [latestMini2.php](https://updates.glyphsapp.com/latestMini2.php) |

最新のベータ版へは、ここからアクセスできます。「Glyphs」＞「環境設定」＞「アップデート」へ移動して、**両方の**チェックボックスを有効にし、「今チェックする」ボタンを押下します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/older-versions-of-glyphs/473923de2f-1607121762/latestbeta.png">

Glyphsが最新の状態であるか、あるいはもっと新しいバージョンをダウンロードして再起動するかどうかが提示されます。  

安定版のアップデートでは未対応のバグフィックスが、ベータ版には含まれることがあるので便利です。ベータ版のリリースはもっと頻繁に行われます。ごく最新のバージョンが十分テストされ、もうクラッシュ報告は出ないだろうと判断されたら、安定版に切り替えられます。

## 過去バージョン

一般的に、Glyphsの過去バージョンが必要になる状況は以下の3つです。

* 古いハードウェアや古いバージョンのmacOSをサポートする必要がある。
* 以前は動作していたのに最新版でうまくいかず、バグフィックスがまだ出ていない。
* Glyphsのレガシー版で作成したレガシーファイルからの出力を再作成する必要がある。

通常は、`updates.glyphsapp.com/GlyphsX.X.X-YYY.zip` スキームを使えば任意のバージョンをダウンロードできます。`X.X.X` の部分はバージョン番号、`YYY` はビルド番号を表しています。なので、例えば、バージョン2.2.2（ビルド827）をダウンロードするには、[update.glyphsapp.com/Glyphs2.2.2-827.zip](https://updates.glyphsapp.com/Glyphs2.2.2-827.zip)と入力します。

> ### Pro Tip
> Glyphs2.3から2.5のベータ版では、ハイフンの前に `b` が追加されています。そのため、バージョン2.5（ベータビルド1129）のダウンロード先は以下となります。
> [updates.glyphsapp.com/Glyphs2.5b-1129.zip](https://updates.glyphsapp.com/Glyphs2.5b-1129.zip)

Glyphs Miniの場合は、バージョン番号のすぐ前に `Mini` を追加してください。例えば、最後のGlyphs Mini 2.0.2（ビルド94）のダウンロード先は以下となります。  
[updates.glyphsapp.com/GlyphsMini2.0.2-94.zip](https://updates.glyphsapp.com/GlyphsMini2.0.2-94.zip)  

全てのビルド番号が入手できる訳ではありません。いくつかのビルドは直後に安定版のビルドと置き換えられ、中には数時間以内に削除されたものもあります。どのビルド番号が欠番かというのは、もう私たち自身でも把握していないので、どうか問い合わせはしないでください。

### Glyphs ビルド番号

ちょっと待って、どのビルド番号がどのバージョンに対応ってすぐ判別できる話でしょうか？ 簡単ではありませんよね。対応表を出しておきます。

| バージョン | 最小ビルド番号 |
|------------|----------------|
| 1.4.5 | 612  |
| 2.2.2 | 826  |
| 2.3   | 875  |
| 2.3.1 | 922  |
| 2.4b  | 923  |
| 2.4   | 937  |
| 2.4.1 | 940  |
| 2.4.2 | 986  |
| 2.4.3 | 1064 |
| 2.4.4 | 1075 |
| 2.5b  | 1027 |
| 2.5   | 1130 |
| 2.5.1 | 1133 |
| 2.5.2 | 1142 |
| 2.6   | 1192 |
| 2.6.1 | 1193 |
| 2.6.2 | 1231 |
| 2.6.3 | 1269 |
| 2.6.4 | 1272 |
| 2.6.5 | 1287 |
| 2.6.6 | 1343 |
| 3.0   | 3032 |
| 3.0.1 | 3033 |
| 3.0.2 | 3040 |

**例：** バージョン2.6.1はビルド番号1193から始まります。したがって、ビルド番号1194、1195、1196なども2.6.1のURL、例えば `updates.glyphsapp.com/Glyphs2.6.1-1196.zip` からアクセス可能です。ビルド番号を指定して404エラーが出たら、おそらくその番号のビルドは後のビルドへ統合されたのでしょう。

### Glyphs Mini ビルド番号

| バージョン | 最小ビルド番号 |
|------------|----------------|
| 2.0   | 53  |
| 2.0.1 | 71  |
| 2.0.2 | 88  |
| 2.1   | 95  |
| 2.1.1 | 97  |
| 2.1.2 | 98  |
| 2.1.3 | 99  |
| 2.1.4 | 101 |

## 更新履歴

アプリケーションには更新履歴が組み込まれていて、各バージョンで行われた変更が確認できます。「ヘルプ」＞「更新履歴」を選択すると、バージョン履歴が記されたウィンドウが開きます。  

<img alt="Accessing the change log for the current app version" src="https://glyphsapp.com/media/pages/learn/older-versions-of-glyphs/1d2887954c-1607121762/changelog.png">

## PowerPC用のGlyphs

Intel G4またはG5以前のCPUを搭載した非常に古いMacをお使いの場合、PPC対応の最新版とIntel [Universal Binary](http://en.wikipedia.org/wiki/Universal_binary)を、[updates.glyphsapp.com/latestPPC.php](https://updates.glyphsapp.com/latestPPC.php)のリンクから入手できます。この記事を書いた時点では、PPC対応の最新版はバージョン1.2.6です。

********

Update 2013-07-18: 新バージョンの更新履歴に関する注記を追加。  
Update 2016-02-16: Glyphs2に合わせた更新とベータ版ダウンロードの追加。oneweioranotherさんありがとう！  
Update 2020-12-04: 更新とリンク修正、ビルド番号を追加。
