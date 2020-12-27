# マルチプルマスター・1：マスターの設定

[(Original page)](https://glyphsapp.com/learn/multiple-masters-part-1-setting-up-masters)  

<br />

by Rainer Erich Scheichelbauer  

<br />

16 December 2020  
Published on 9 November 2013  


********

大規模なフォントファミリーの制作を考えていますか？ それには複数のマスターを作成して補間生成を理解しなくてはなりません。ここではその始め方を説明します。  

********

補間生成に関するAdobe社の技術を「マルチプルマスター」と呼びます。マスター間で段階的に計算するために複数の（multiple）、つまり少なくとも2つのマスターを必要とするからです。正確に言えば、マルチプルマスターというのは「ユーザ」が所有するフォントで補間生成を行えるという[過去のフォント形式でした](http://en.wikipedia.org/wiki/Multiple_master_fonts)。おそらくは複雑だったために、全く支持を得られることがなく、1990年代後半に打ち切られました。  

とは言うものの、大規模なフォントファミリーの作成においては、マルチプルマスターの補間技術は現在の書体デザインでも重要な役割を果たしています。言うまでもなく、それはGlyphsにも組み込まれています。しかしマルチプルマスターを扱う前に、「マスター」と「インスタンス」の違いを理解しておかなくてはなりません。  

## マスター対インスタンス

**マスター**とは「自分自身で作図するもの」です。これらは補間生成のための「入力」です。マスターはフォント情報の「マスター」タブで管理されます。マスターは各グリフでレイヤー別に作図します。あるファミリーでの作業中でも、補間生成がうまく働くかを確認するためにマスター間を常に行ったり来たりすることになるでしょう。マスターは「ファイル」＞「フォント情報」＞「マスター」で設定します。  

**インスタンス**またはスタイルとは「コンピュータが計算するもの」です。これらは「出力」であり、補間生成の出力「結果」です。インスタンスはフォント情報の「インスタンス」タブで管理されます。Glyphsでは、インスタンスは今すぐに即刻使えるOpenTypeフォントとして出力されます。適切に設定され全てその通りに動作すれば、補間生成されたインスタンスのポイントやパスをいじる必要はありません。インスタンスは「ファイル」＞「フォント情報」＞「出力スタイル」で設定します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/multiple-masters-part-1-setting-up-masters/b2ad83b060-1606865185/interpolation-1.png">

## マスターの設定

それでは、パーティーを始めましょう。Glyphsで新規ファイルを作成したら、「ファイル」＞「フォント情報」を選択して「マスター」タブへ移動します。すでにマスターが1つあります。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/multiple-masters-part-1-setting-up-masters/bcc1a5a237-1608562153/fontinfo-masters.png">

ご覧のとおり、「Regular」マスターという名前になっています。注意：この名前はマスターのデザインに対して意味を持つものではありません。マスターはすごく細字だったりあるいは逆に太字だったりするかもしれません。実際のところ、マスターの名前と、指定できる「アイコン」は、完全に任意です。  

そんな訳で、マスターには「どんな」名前をつけても構わないので、自分が納得できる名前を選ぶと良いでしょう。デザイナーの中には、インスタンスと区別するために、「Lightest」や「Boldest」という名前にする人たちもいます。「アイコン」も同様です。自分にとってわかるものを選んでください。  

補間生成を行うためには、少なくとも1つの補間軸に合わせて作成されたマスターが、2つ以上必要です。  

## 補間軸の追加

「補間軸とは何ですか？」聞かれると思いました。簡単です。補間軸とは補間生成の次元のことです。Glyphsでは「フォント情報」＞「フォント」で定義した補間軸に合わせて補間を生成できます。補間軸とは「Weight」軸、「Width」軸、「Optical Size」軸といった定義済みの「古典的な」軸のどれかということになりますが、その他あなたにとって軸にできると思えるものならなんでも補間軸になり得ます。補間軸を作成するには、「フォント情報」＞「フォント」を開き、「補間軸」見出しの横にある＋アイコンを押下すると、補間軸が現れます。  

> ###Legacy Tip
> **Glyphs 2**では、暗黙の了解で「Weight」軸が最初の補間軸として使われました。これを変えるには、「ファイル」＞「フォント情報」＞「フォント」でカスタムパラメータに「Axes」を追加する必要があります。Glyphs 2では補間軸は最大で6つまで扱えます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/multiple-masters-part-1-setting-up-masters/57b1db4882-1608562153/fontinfo-font-axes.png">

メニューにリストアップされた補間軸からどれかを選ぶか、またはオリジナルの補間軸（「カスタム補間軸」）を設定できますが、今のところは「Weight」軸にこだわることにしましょう。全ての軸には「補間軸名」と4文字の「補間軸タグ」があり、今の場合は「Weight」と `wght` になります。さて、マスターを補間軸上では異なる位置に配置しなくてはなりません。  

> ###Pro Tip
> **カスタム補間軸**にも4文字のタグが必要です。将来の仕様拡張との衝突を避けるために、カスタム補間軸のタグは**全て大文字**にすべきとされています。例えば、「Serif」軸なら、小文字の `serf` は将来仕様に追加されるかもしれないので避け、全て大文字である `SERF` を選びます。  

「マスター」タブに戻ると、新たに「Weight」軸用の補間軸上の座標欄が表示されています。ここには何か意味のある値を入力できます。Weight軸ではデザイナーの多くはおおよそのストローク幅を選んでいます。今の場合は100としましょう。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/multiple-masters-part-1-setting-up-masters/c8767a7d02-1608562153/master-coordinate.png">

さて2つ目のマスターを追加する必要があります。そうでないと補間生成ができません。左下の＋アイコンを押下すると、オプションから次のどれかを選択できます。  

* 「空のマスターを追加」： 新しい空のマスターを追加します。
* 「他のフォントから追加」： 2番目の.glyphsファイルの内容を新しいマスターとして挿入します。
* 「選択中のマスターを複製」： 現在選択中のマスターをコピーして新しいマスターとして追加します。

あるいは、サイドバーにあるマスターの名前をドラッグして、長押ししても良いです。  

## マスター間の切り替え

さて、作図は簡単です。実際のところGlyphsで何かを描くのと同じです。唯一の違いは、設定した2つのマスターに対応する2つのレイヤーに作図しなければならないことです。マスターレイヤーを切り替えるには、単純にCmd-1とCmd-2、つまりコマンドキーとマスターの番号に対応する数字を押すだけです。あるいはフォントに2つ以上のマスターがあるとすぐに下のボタンが表示され、これもマスターレイヤーの切り替えに使えます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/multiple-masters-part-1-setting-up-masters/f7db763979-1606865185/interpolation-8.gif">

## マスターの作図

さて、「Regular」マスターに切り替えて文字を作図しましょう。個人的に、他の多くの文字で図形を再利用できるのでnから作るのが好きです。そこでこれがnです。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/multiple-masters-part-1-setting-up-masters/87c3de83d9-1606865185/interpolation-7.png">

忘れないでください。「Regular」という単語は、補間軸上での位置を意味しているだけで、文字のデザインには全く関係ありません。なので、作図しているnが実社会でレギュラーと呼ばれる書体に比べるとだいぶ細いように見えても気にしないでください。  

nが作図できたら、全選択してクリップボードにコピーします。そして、Cmd-2を押して「Bold」マスターに切り替え、nをそこにペーストします。それから、ノードを動かしてnを超ぶっとくします。通常では、余白を減らしたければ、文字が暗く見えるようにします。最終的に、太いウェイトほどページの中で暗く見えるようになります。という訳で、懐を小さくすることはサイドベアリングを少し減らすのと同じくらい重要です。  

Pro Tip： ノードやセグメントを動かすとき、CtrlとOptを同時に押しながらドラッグしたりカーソルを動かしたりすると、周囲のハンドルの位置の比率が保たれるので便利です。これを「ナッジ移動」と呼びます。  

Cmd-1とCmd-2で切り替えはいつでもできます。しかし太字のnが出来上がったら、2つを横に並べて見てみると良いでしょう。これは「編集」＞「すべてのマスターを表示」で行えます。マスターにアクセスするショートカットの表示を加えていますが、nの2つのマスターはこのように表示されます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/multiple-masters-part-1-setting-up-masters/86b54f3566-1606865185/interpolation-9.png">

### マスターの値の設定

今がステムの太さを確認する絶好のチャンスです。ステム幅はタイプデザインのウェイト決定で役に立つキーとなる値です。なのでステム幅をウェイト軸のマスターの値に使うことをお勧めします。  

ステム幅を手早く調べるには、Ctrl、Cmd、Optを同時に長押しします。すると「ものさしツール」（L）が一時的に表示されます。もし指がまだ空いているなら、Shiftキーを追加して、水平線をドラッグするとステム幅を確認できます。これを両方のマスターで行います。今の場合では、ステム幅は90と300になっています。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/multiple-masters-part-1-setting-up-masters/72880cce00-1606865185/interpolation-10.png">

これで「ファイル」＞「フォント情報」＞「マスター」の各マスターで、デフォルトのWeightの値の100を先ほど決めた数値に置き換えます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/multiple-masters-part-1-setting-up-masters/05275f733d-1606865185/interpolation-11.gif">

### その他の値の入力

さて、フォント情報の「マスター」タブに他の入力欄があるのが見えてしまったので、これを秘密にはしておけなくなったようです。そうです、ご期待の通り、「全ての」エントリが「全ての」マスターを往復する限り、そこにある「全ての」数値は補間生成されます。言い換えれば、1つのマスターにだけ、例えば、アラインメントゾーンを入力するのでは不十分です。他の全てのマスターにも同様に対応するゾーンを同じ順番で入力しなくてはなりません。こうすることで、Glyphsはどの数字の間で補間を生成するか把握します。これはステム値、垂直メトリクス、そしてカスタムパラメータで入力された全ての数値でも行われます。  

[マルチプルマスター・2：アウトラインの互換性の確保](https://glyphsapp.com/learn/multiple-masters-part-2-keeping-your-outlines-compatible)に続きます。  

********

サンプルフォント： Graublau、Jordana氏 提供  

<br />

Update 2014-06-20: ナッジ移動のPro Tipの誤記訂正（Jeff Kellemさんありがとう）。  
Update 2015-07-21: 3つの次元についてとGlyphs 2に更新。  