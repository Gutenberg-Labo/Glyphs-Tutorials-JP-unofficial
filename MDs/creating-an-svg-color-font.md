# SVGカラーフォントの作成

[(Original page)](https://glyphsapp.com/learn/creating-an-svg-color-font)  

<br />

by Rainer Erich Scheichelbauer  

<br />

20 January 2017

********

Glyphsは何種類かあるOpenType-SVGフォントの作成方法を提供します。このチュートリアルを読めば、そのほぼ全容が分かります。

********

SVGについて調べると、[Scalable Vector Graphics](https://ja.wikipedia.org/wiki/Scalable_Vector_Graphics)の略であることが分かります。ここまでは良いのですが、フォントの分野でこの用語を使うと、実際とは異なる意味になってしまうことがあります。

### SVGフォント形式

まず第一に、SVGというWebフォントの**ファイル形式**がありました。このファイルの拡張子名は `.svg` またはzip圧縮された `.svgz` でした。これは初期iPhoneのSafariでしかサポートされなかったので、すぐに忘れ去られました。そして幸運なことに、絶滅してしまいました。それは他のフォント形式と比べるとサイズが巨大で、単なるアウトラインしか提供していませんでした。つまり、カーニングも、ヒントもなく、OpenTypeテーブルの提供するその他の良い機能は何一つありませんでした。言い換えれば、OpenTypeフォントですらありませんでした。GlyphsはOpenTypeフォントエディタですから、そんなSVGフォントは生成できません。  

このチュートリアルでは、このレガシーなSVGフォントのファイル形式については「触れません」。

### SVG OpenTypeテーブル

現在広く使われるWebフォントのファイル形式はWOFFと、ゆっくりと普及しつつある、WOFF2です。もちろん他にもありますが、簡単に言えば、WOFFとは圧縮されたOpenTypeフォントです。デスクトップフォントの兄弟姉妹である、CFF/OTFやTTFもOpenType形式ですが、どちらも独特で、WOFFほどは圧縮されていません。OpenTypeフォントをOpenTypeフォントたらしめているのは、いわゆる**OpenTypeテーブル**と呼ばれるものの集合体であるその内部構造であり、そのテーブルの1つに[SVG](https://www.w3.org/TR/SVG11/)をベースとした情報を含む[SVGテーブル](https://www.microsoft.com/typography/otspec/svg.htm)があります。こういったSVGテーブルを含むフォントは「OpenType-SVGカラーフォント」や「SVGカラーフォント」と呼ばれたりしています。  

このチュートリアルは、OpenType-SVGカラーフォントについて「です」。  

Glyphsで、フォントにSVG情報を取り込む方法は2つあります。（A）個別の `.svg` 画像ファイルから取り込む方法と、（B）既存のカラーフォントから取り込む方法です。後者は、異なるマスター上のレイヤーフォント、インデックス付きの「カラー」レイヤーを持つCPAL/COLRフォント、または「iColor」レイヤーを持つApple形式のsbixフォントのどれかからです。

### オプションA：SVG画像ファイルから取り込む

使えるSVG画像が個別のファイルで既にある場合、それをそれぞれのグリフに配置すれば、SVGテーブル付きフォントを出力できます。この方法ではベクターアニメーションのようなイカれたものも含めて、SVGファイル形式の機能がフル活用できます。  

前準備として、.glyphsファイルを好きな場所に保存し、SVGファイル用に「Images」というサブフォルダを作っておいてください。.glyphsファイルに保存されるのは画像の相対パスだけなので、画像がサブフォルダにあれば簡単にまとめておけます。  

さて例が必要です。SVG画像が手元になければ、ここに1つ用意します。大文字の `O` として赤い丸を回転させてみましょう。このSVGコードを選択してコピー（Cmd-C）してください。  

```svg
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
 width="1000" height="1000" viewBox="-400 -400 800 800">
 <title&gt;SVG animation using SMIL&lt;/title>
 <circle cx="0" cy="100" r="200" stroke="none" fill="red">
  <animateTransform
   attributeName="transform"
   attributeType="XML"
   type="rotate"
   from="0"
   to="360"
   begin="0s"
   dur="1s"
   repeatCount="indefinite"></animateTransform>
 </circle>
</svg>
```

[TextMate](https://macromates.com)、[SublimeText](https://www.sublimetext.com)、[Atom](https://atom.io)などのお好きなプレーンテキストエディタで新しいウィンドウを開き、これをペースト（Cmd-V）します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-an-svg-color-font/4e7c043556-1605628244/svgintexteditor.png">

そして、O.svgとして「Images」フォルダ内にファイルを保存します。すると、Finderで見ると、用意したファイル全体は次のようになります。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-an-svg-color-font/33935b6884-1605628243/findersetup.png">

.glyphsファイルに戻って、大文字 O を用意します。編集ビューで開き、「レイヤー」パレットで「コピー」ボタンを押下してレイヤーのコピーを追加し、それから名前を `svg`（すべて小文字）に変更します。それが終わると、次のようになります。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-an-svg-color-font/78e6453dcf-1605628244/svglayer.png">

さてここからが本題です。マスターレイヤーに置くのは何であれ黒白のフォールバック用グリフで、SVGテーブルに格納された色情報を表示できないアプリケーションではこれが表示されます。何それと思われたかもしれませんが、マスターレイヤーというのは「レイヤー」パレットで太字で表されるレイヤーのことで、今の例では「Regular」という名前です。  

でも新しい `svg` レイヤーには、.svg画像ファイルをドラッグしてドロップできます。アニメーションは動作しませんが、画像はすぐに表示されます。リンクした画像はサイズを変えたり、好きな位置に動かすことができます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-an-svg-color-font/395d4555a6-1605628244/placedsvgineditview.png">

スペーシングに関する注意：`svg` レイヤーの幅はマスターレイヤーから継承されるので、グリフの間隔を広げるにはそちらに切り戻す必要があります。この例では、配置したSVGを拡大縮小や変形させていないのであれば、幅は800に設定するのがちょうど良いでしょう。それをやるには、レイヤーパレットの「Regular」レイヤーをクリックして、灰色の情報ボックスで幅を800に変更します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-an-svg-color-font/c192bb4b7d-1605628244/setwidthto800.png">

それはさておき、フォントをWebフォントに出力します。「ファイル」＞「出力」＞「Webフォント」で、フォーマットにはWOFFとWOFF2を使います。CFFやTTFは関係ありません。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-an-svg-color-font/7587f4ca36-1605628243/exportwoff.png">

Macでは、OpenType-SVGフォントをサポートするブラウザは[Firefox](https://www.mozilla.org/en-US/firefox/new/)しかありません。Windowsでは、[Microsoft Edge](https://www.microsoft.com/en-us/windows/microsoft-edge)もサポートしています。なのでOpenType-SVGフォントをテストするにはこれらのブラウザを使う必要があります。テストのために、WOFFを表示させるためのHTMLとCSSのコードを含んだHTMLファイルを作成するか、あるいは[mekkablueのスクリプトのリポジトリ](https://github.com/mekkablue/Glyphs-Scripts)から「Test」＞「Webfont Test HTML」スクリプトを実行するかしましょう。このスクリプトは現在のフォント用のHTMLファイルを最後に使われたWebフォント出力先に生成します。  

> もしスクリプトを使うことに慣れてなければ、ちょっと時間を取ってスクリプトのreadmeのインストール手順を読み、それに従ってスクリプトをインストールしてみてください。その後、Optionキーを押しながら「スクリプト」＞「スクリプトの再読み込み」（Cmd-Opt-Shift-Y）を選択します。

スクリプトがうまく動いて出力先フォルダが開きます。あとはHTMLファイルをDockのFirefoxアイコンにドラッグ（または右クリックから「このアプリケーションで開く」＞「Firefox.app」）して、大文字の O を入力するだけです。さあどうぞ！  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-an-svg-color-font/0c481c0f5f-1605628243/animatedredcircle.gif">

ジャジャーン！ だけど、フォントでのアニメーションはプロセッサに高負荷をかけることになるのでどうか気をつけてください。コンピュータのファンは狂ったようにフル回転するでしょうし、モバイルではバッテリーが直葬になってユーザは全員あなたに微妙な感情を持つでしょう。警告しましたよ。

### オプションB：既存のカラーフォントから取り込む

Glyphsで既存のさまざまな形式のカラーフォントを取り込み、SVGとしてエクスポートできます。カラーフォントをこれらのソース形式のどれかで作成すると、そのソース形式「と」SVGとの両方にエクスポートできる利点があります。  

選択肢は3つあります。  

1. [複数レイヤーフォント](https://glyphsapp.com/tutorials/creating-a-layered-color-font)：2つ以上のマスターを重ね合わせたもの。マスターに互換性は必要ありませんが、「Master Color」を割り当てる必要があります。
2. [CPAL/COLRフォント](https://glyphsapp.com/tutorials/creating-a-microsoft-color-font)：グリフに `Color` レイヤーを持つフォントで、各レイヤーには定義済みのカラーパレットの色がリンクされます。
3. [sbixフォント](https://glyphsapp.com/tutorials/creating-an-apple-color-font)：グリフの`iColor` レイヤー上に任意の解像度のビットマップ画像が配置されているフォント。

オプションを見て、どれかの形式を選び、SVGのエクスポートを追加する方法は以下をお読みください。  

**複数レイヤーフォントの場合：** [こちらのチュートリアルの手順に従ってください。](https://glyphsapp.com/tutorials/creating-a-layered-color-font)「ファイル」＞「フォント情報」＞「マスター」の「Master Color」パラメータで色が設定されているかを確認してください。  

「ファイル」＞「フォント情報」＞「インスタンス」で、SVGテーブルを含むフォント用の新しいインスタンスを作成します。スタイル名には「レギュラー」とか「マルチカラー」、「SVG」など納得のいく名前をつけます。そしてその新しいインスタンスにカスタムパラメータ「Color Layers to SVG」を追加し、「値」をオンにしてください。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-an-svg-color-font/a268aa8cad-1605628243/colorlayerstosvg.png">

**CPAL/COLRフォントの場合：** [こちらのチュートリアルの手順に従ってください。](https://glyphsapp.com/tutorials/creating-a-microsoft-color-font)「ファイル」＞「フォント情報」＞「マスター」で最初のマスターの「カスタムパラメータ」セクションで「Color Palettes」が1つ以上設定されていることと、グリフ内の「Color」レイヤーに番号、つまり `Color 0` 、`Color 1` 、`Color 2`、……が振られていることを確認してください。  

「ファイル」＞「フォント情報」＞「インスタンス」で、SVGテーブルを含むフォント用の新しいインスタンスを作成します。これに適切なスタイル名をつけてください。そしてそのインスタンスの「カスタムパラメータ」セクションにパラメータ「Color Palette for SVG」を追加し、その値には含めたいカラーパレットのインデックスを設定します。上述の「Color Palettes」パラメータで定義したパレットが1つだけであれば、値に `0` を設定します。  

そして、カスタムパラメータ「Export SVG Table」を追加し、チェックボックスをオンにします。純粋にSVGフォントだけが欲しいなら、カスタムパラメータ「Export COLR Table」を追加してそのチェックボックスをオフにするのもありだと思います。  

「ファイル」＞「フォント情報」＞「インスタンス」で新しいインスタンスを作成し、カスタムパラメータ「SBIX to SVG」を追加して値に適切なiColorのサイズを入力します。こうすることで同じサイズのインデックスのiColorレイヤーからsbix画像が取り込まれ、SVG画像に変換されます。例えば、カスタムパラメータの値に256を指定すると、Glyphsは全ての `iColor 256` レイヤーを探し出してSVGに変換します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-an-svg-color-font/596ec67efe-1605628244/sbix2svgparameter.png">

純粋にSVGフォントだけが欲しい場合は、カスタムパラメータに「Export sbix Table」を追加してそのチェックボックスをオフにしても良いと思います。  

さあ「ファイル」＞「出力」＞「Webフォント（Cmd-E）」で出力します。もうそれだけで、それ以上のことはありません。上で説明したようにフォントをFirefoxでテストします（オプションA参照）。

### カスタムパラメータについての詳細

「ファイル」＞「フォント情報」＞「インスタンス」（Cmd-I）の、「カスタムパラメータ」では、次の3つのパラメータのどれかまたは全てを追加できます。  

* 「Export COLR Table」
* 「Export SVG Table」
* 「Export sbix Table」

これらはどのカラーテーブルを生成して実際のOpenTypeフォントに含めるか、含めないかを制御します。Webフォントのファイルサイズを抑えるためには、これらのテーブルから1つだけを出力し、他のテーブルはすべて無効にした方が良いかもしれません。例えば、オプションBで説明した方法でCPAL/COLRに基づいた設定からSVGテーブルを出力するときは、COLRテーブルの生成を抑制する方が良いでしょう。

### SVGについての詳細

私たちはまだ表面をさらっただけです。SVGとその可能性の全ての沼にハマったら、仕様やサンプルコードを追っかけてみてください。  

* 公式 [SVG 1.1 仕様書](https://www.w3.org/TR/SVG11/)（W3）
* 公式 [SVGテーブル仕様](https://www.microsoft.com/typography/otspec/svg.htm)（Microsoft Typography）
* Roel Nieskens氏のSVGテストページ [LapisLegit](https://pixelambacht.nl/lapislegit/)（ブラウザがクラッシュする可能性あり。気をつけて！）
* Adobe TypeKitの[カラーフォントコンセプトページ](https://color.typekit.com/) SVGフォントもあり
* Adobeヘルプページ [OpenType-SVGカラーフォント](https://helpx.adobe.com/typekit/using/ot-svg-color-fonts.html)

この記事を書いた時点では、SVGテーブルはFirefox、Windows 10+、そしてAdobeアプリでサポートされています。  

********

Update 2017-01-20: サポートブラウザのリストにMicrosoft Edgeを追加。  
Update 2018-03-26: sbixからSVGへの変換を追加。  
Update 2018-04-14: SVGをサポートするOSとアプリを更新。Behdadさんありがとう！  
Update 2019-02-01: 誤記を訂正し、兄弟（brothers）という単語を兄弟姉妹（siblings）に置換。Nathalieさんありがとう！  
Update 2019-11-15: 「オプションB」の導入部を更新。
