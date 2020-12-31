# バリアブルフォントの作成

[(Original page)](https://glyphsapp.com/learn/creating-a-variable-font)  

<br />

by Rainer Erich Scheichelbauer  

<br />

14 December 2020  
Published on 8 March 2018  


********

バリアブルフォントは今までにない可能性の世界を開きます。Glyphsなら作成は簡単です。

********

## バリアブルフォントとは？

もし[John Hudson氏による素晴らしい紹介記事](https://medium.com/@tiro/https-medium-com-tiro-introducing-opentype-variable-fonts-12ba6cd2369)を読んだことがなければ、今すぐその手を止めて、読みに行ってください。いや、本当に。  

読みました？ OK、ではGlyphsで、バリアブルフォントを設定していきますよ。さあ始めましょう。  

## Step 1 補間軸の定義

<!-- new: -->
補間生成をするには、最初に「デザインスペース」を設定する必要があります。デザインスペースとは、高校で習う直交座標系のように、軸によって定義された座標系のことです。ただし、x、y、z軸の代わりに、ウェイト、幅、斜体といった、タイポグラフィに適した「デザイン」補間軸を用います。  

そして、「ファイル」＞「フォント情報」＞「フォント」＞「補完軸」で、＋アイコンを押下して軸を追加します。  

<img alt="Adding an axis" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/0af68ab5db-1605628247/axes-plus.png">

「ファイル」＞「フォント情報」を選択し、「フォント」タブで「補完軸」の横にある＋アイコンをクリックすると、新たなデザイン補間軸が追加されます。  

表示された補間軸の欄から、使いたい補間軸を選びます。ウェイト、幅、イタリック、斜体、オプティカルサイズ、そして[提案されている新しい補間軸](https://github.com/Microsoft/OpenTypeDesignVariationAxisTags)の中から、公式に「登録された」補間軸を選べます。あるいは、独自の「プライベート」補間軸を作成できます。  

> ### Pro Tip
> 独自の「プライベート」補間軸を作成する場合でも、4文字のタグを選択する必要があります。将来起こりうる仕様更新との衝突を避けるために、プライベートタグは「全て大文字」にすることが推奨されています。例えば、「Smile」なら `SMIL` とか「Rotation」なら `ROTN` などです。これは全て大文字のタグは私的利用のために公式に予約されているためです。定義済みの補間軸は必ず小文字となっています。  

補間軸はほとんどいくらでも追加できますが、それぞれに固有の4文字のタグをつけなくてはなりません。この例では、定義済みの `wght` タグを持つ「登録された」補間軸「Weight」にこだわります。  

## Step 2 マスターの設定

<!-- new: -->
同じ「ファイル」＞「フォント情報」ウィンドウで、「マスター」タブに切り替えて、[マルチプルマスターのプロジェクトと同じよう](./multiple-masters-part-1-setting-up-masters.html)に、ウィンドウの左下の隅にある＋アイコンを押下してマスターを追加します。今の例では、「Light」と「Bold」の、2つのマスターを追加します。  

<!-- unchanged, except I REORDERED point 1 and 2, and the FIRST SENTENCE of point 3: -->
それぞれのマスターで、次の設定を選択してください。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/91175c744e-1608028536/master-setup.gif">

1. 一番重要なのは、各マスターの**補完軸上の座標**を設定することです。この例では「ウェイト」の値を、例えばLightマスターで50、Boldマスターで200というように設定します。デザイナーの多くはWeight軸の値にステムの太さを使用したいと考えますが、値に「明確な差」さえあれば、どんな値を入力してもよく、そうであればGlyphsは中間のインスタンスを計算できます。この例なら、インスタンスは50から200の間の値、例えば75、120、182などで計算できます。
2. それぞれのマスターに適切な**マスター名**をつけましょう。今の例では、「Light」と「Bold」が良さげだと思います。これらのマスター名は最終的なフォントファイルには出力されません。マスター名はGlyphs上での作業で自分の方針を決めるのに重要です。
3. オプションで、それぞれのマスターの「一般」セクションの「Icon」のポップアップから**マスターアイコン**を選択してください。小文字の n で表されたウェイト×幅の総当たりの組合せから選べます。下の部分にグリフ名を入力すると、Glyphsはそのそれぞれのグリフの画像をマスターアイコンに使用します。もう一度言いますが、これは自分だけの指針なので、自分が納得できるものを選んでください。

<!-- removed paragraphs -->
OK、マスターが設定できたので、それぞれのマスターに図形を追加します。さあ行きましょう。  

## Step 3 互換性のあるグリフの作図

手短かつ簡潔に説明するために、このチュートリアルでは大文字の A にこだわることにします。ステム幅が約50ユニットであるライト体（Cmd-1）の A を作図します。  

<img alt="" height="300px" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/66d04fb9c0-1605628247/a_lightmaster.png">

<!-- reordered this sentence between the pictures -->
……そして幅が200ユニットのボールド体（Cmd-2）の A を作図します。  

<img alt="" height="300px" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/37ab8a82ae-1605628247/a_boldmaster.png">

<!--added the first sentence: -->
「グリフ」＞「アンカーを自動設置」（Cmd-U）か、あるいはもっと良いのはOptionキーを押しながら「グリフ」＞「全てのマスターでアンカーを自動設置」（Cmd-Opt-U）を選択してアンカーを追加します。最も重要なことは、[マルチプルマスターでの設定と同じように](https://glyphsapp.com/learn/multiple-masters-part-2-keeping-your-outlines-compatible)、2つのマスター間で全てのアウトラインとアンカーの互換性を保つことです。  

> ### Pro Tip
> 「表示」＞「マスター互換性 を表示」（Ctrl-Opt-Cmd-N）で互換性の確認ができ、「フィルタ」＞「シェイプの順序を変更」で各マスター上の図形をドラッグして順序を修正できます。  

## Step 4 定義済みインスタンスの追加

<!-- changed wording: Exports, not Instances: -->
バリアブルフォントを作成して、いかに無数のインスタンスを設定していたとしても、デザインスペースの中からいくつかの場所を選び出してフォントのサブメニューのインスタンスに定義できます。「ファイル」＞「フォント情報」＞「出力スタイル」で、定義済みのインスタンスを好きなだけ追加します。左下の＋アイコンで新しいインスタンスを追加するか、左のサイドバーで既存のインスタンスをオプションキーを押しながらドラッグして複製します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/60fb8c117a-1605628248/newinstance.png">

それぞれのインスタンスでやるべきことはこれだけです。  

<img alt="Setting up the instances" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/3e69cfceec-1608028536/fontinfo_instances.png" width="600px">

<!-- order of points 3 & 4 changed: -->
1. 適切な**スタイル名**を設定してください。今の例なら、例えば、「ライト」、「レギュラー」、「ミディアム」、「セミボールド」、「ボールド」、「エクストラボールド」です。
2. オプションで、「名前」の直下にあるポップアップメニューから**ウェイトと幅のクラス**を選択できます。欠点として、これは関係する「静的な」フォントの出力のみに適用され、バリアブルフォントには書き込まれません。これについては[フォントの命名](https://glyphsapp.com/learn/naming)のチュートリアルをご参照ください。
3. それぞれの補間軸に適した**デザインスペースの座標**を選びます。ウェイトの分布については[マルチプルマスター・3](https://glyphsapp.com/learn/multiple-masters-part-3-setting-up-instances)のチュートリアルを参照してください。
4. **スタイルリンク**を選択します。正体では、通常はここは空白のままにしておき、太字の時だけ「Regular」の「ボールド」にします。そしてそれぞれの斜体ではその正体に対応した「イタリック」、例えば、セミボールドのイタリックなら「Semibold」の「イタリック」にします。斜体だけのインスタンスは「Regular」の「イタリック」で、太字の斜体は「ボールド」の「イタリック」です。これについては[フォントの命名](https://glyphsapp.com/learn/naming)のチュートリアルをご参照ください。
5. そしてこれはとても言いにくいことなのですが、OTVarのインスタンスでは**カスタムパラメータはほとんど動作しません**。大半のフィルタなど、図形のポストプロセスが行われる場合は特にそうです。カスタムパラメータをインスタンスで設定しても、アプリケーションはこれらをぬけぬけと無視します。なぜかって？ アウトラインの互換性が脅かされるからです。
<!-- ignore this for now please
5. オプション： **Variable SubfamilyName** を選択してインスタンスの（スタイルの）名前を上書きします。静的なフォントとバリアブルフォントの「両方の」出力に同じインスタンスを使用していて、何らかの理由で、「静的なスタイルとバリアブルのスタイルで異なるスタイル名」を使いたい場合、このパラメータでバリアブルのスタイル名を特定して設定できます。
-->

<!-- this is new: -->
## Step 5 バリアブルフォントの設定の追加

そうです、カスタムパラメータは機能しません。大半の場合においてそうする意味があります。例えば、同じバリアブルフォントの別のインスタンスで文字集合を違うものにするなんてことは当然ながらできません。スライダを動かしたらグリフが消えたり現れたりするなどありえない（許されない）ので無理もありません。インスタンスで「Export Glyphs」と「Remove Glyphs」パラメータが無視されるのはこれが理由です。そして他のパラメータについても同様の理論的な理由があることがわかるでしょう。  

しかし「バリアブルフォント全体」にパラメータを適用できるとしたらどうでしょう？ ええ、できるんです。左下の隅にある＋アイコンの中のメニューから、「add Variable Font Setting」を選択します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/f56d27395c-1608028536/newvfsetting.png">

……そして「Keep Glyphs」パラメータでグリフのサブセット化、その他のパラメータでOpenType機能やクラスの変更、異なるファミリ名の設定など、やりたい設定を全て行います。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/5350d1f437-1608028536/variablefont-setting.png">

## Step 6 バリアブルフォントの出力とテスト

「ファイル」＞「出力」を選択し、「バリアブルフォント」タブに移動します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/ef74f1fada-1608028536/export-otvar.png" width="450px">

もし最新のAdobe Illustrator、Adobe Photoshop（CC 2018以降）、InDesign（CC 2020以降）をお持ちであれば、[Adobe Fontsフォルダに出力](https://glyphsapp.com//learn/testing-your-fonts-in-adobe-apps)して、文字パネルでフォントを選択し、スライダーのある小さなポップアップを開くと、「太さ」軸のテストができます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/7f11f7e22b-1605628248/illustrator.gif" width="400px">

そうでなければ、ファイルドロップでフォントをテストできる素晴らしいサイトがあります。私の推しはRoel Niesken氏による最高な[Wakamai Fondue](https://wakamaifondue.com)、ABC Dinamoによる[Font Gauntlet](https://dinamodarkroom.com)（バリアブルフォントのアニメーション化もできます）、そしてもちろんLaurence Penney氏による[Axis Praxis](https://www.axis-praxis.org)です。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/4334a74878-1605628248/axispraxis.gif">

または、mekkablueのスクリプトをインストールして、「Test」＞「Variable Font Test HTML」を実行すると、最後に出力されたOTVarファイルの隣にHTMLファイルが生成され、そのファイルのあるフォルダがFinderで開きます。あとはそのHTMLをブラウザにドラッグ＆ドロップするだけです。  

> ### Hint
> この記事を書いている時点で、macOS High Sierra以降、またはiOS 11以降をお使いであれば、ブラウザには現在の[Chrome](https://www.google.com/chrome/browser/desktop/index.html)かSafariを使うのがベストなようです。古いバージョンのOSのSafariではバリアブルフォントはサポートされません。FirefoxやEdgeも同様に動作するはずですが、本当に最新バージョンのブラウザを使っていることを確認してください。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/c8d45e3f38-1605628251/otvartest.gif" width="470px">

## バグの回避

AdobeのOTVarの実装にはバグがあります。そのため、IllustratorやPhotoshopでフォントの補間生成が正しく行われないときは、フォントのせいではないかもしれません。症状は様々で、スライダーを動かしてもグリフが全く反応せずに静止したままだったりとか、スライダーを動かしていると、例えばこんな感じの小さな汚い引っ掛かりが現れたりします。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/681f87958c-1605628247/ai-glitch.png">

これが起きた場合は、アウトラインの開始点を変えてみてください。それでAIのレンダリングのバグを回避できる場合があることが判明しています。いずれにしても、Webブラウザでは同じ不具合が生じないのであれば、それはフォントのせいではありません。そして簡単なテストケースを含むAIファイルと一緒に、フォントファイルを[Adobeサポートへ送れば](https://www.adobe.com/products/wishform.html)ベストでしょう。  

> **更新情報：** 最近のバージョンのCCでは、こういったレンダリングの問題は非常に稀になっています。実際にCC 2021ではこれらの問題は見られませんでした。  

もう1つの厄介な実装のバグがAppleのレンダラー・CoreTextの奥に潜んでいます。LSBに異同があるとコンポーネントの配置位置の計算に誤りが生じます。a の動作が正しいのに対し、a-ウムラウトの動作が予期されるものから外れている様子を見てください。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/c7d5cc3cb9-1605628249/neartatteredcondor-small.gif">

これはMacのほぼ全てブラウザを含む、CoreTextレンダリングを使用する全ての環境で生じます。この場合で、出力の際に全てのコンポーネントグリフを確実に分解するのが最善の解決策です。これを行う一番良い方法は、「ファイル」＞「フォント情報」＞「フォント」＞「カスタムパラメータ」に `Decompose Components in Variable Font` パラメータを追加することです。言うまでもありませんが、Apple社がこの問題を修正してくれないと、結果としてTTFはファイルサイズが膨れ上がり、ウェブでの使用に適しません。  

~~私たちはApple社にこのバグを報告していますが、お手元に良いケースがあったら、あなたも[Apple社へご報告](https://bugreport.apple.com)をお願いします。~~  

> **更新情報：** Apple社はこの問題に対応しました。macOS 10.13の最新の不具合修正、またはそれ以降のバージョンのmacOSをお使いください。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/73317cc3a2-1605628248/opsz-bug.gif">

また別のバグがApple社のレンダリングにあります。「オプティカルサイズ」の補間軸（`opsz`）の解釈がSafariで誤っていることです。スライダーの位置が最小（左端）で、最大値のレンダリング結果が表示されます。これはSafariのみで生じており、他のブラウザでは生じません。これまた、[Apple社へご報告をお願いします](https://bugreport.apple.com)。  

それから、バリアブルフォントではパスの重なりによって生じるレンダリングの問題があります。本当はバグではないのですが、ユーザからそう見えるかもしれません。図形の縁が（部分的に）重なった2つのパスのセグメントによって描かれた場合、アンチエイリアス処理がかかると1本だけのアウトラインで描かれた「きれいな」縁よりも濃く見えてしまいます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/1db2eb35e3-1605628249/overlaps-before.png">

これを解決する唯一の方法は、図形の縁が常に1つのパスだけで描かれるようにアウトラインを「きれいに」引き直すことです。例えばこんな感じです。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/46d3e39f31-1605628249/overlaps-after.png">

大抵の場合、重なったパスを合体してからアウトラインを開くかノードを再接続すればこの問題を解決できます。「アウトラインを開く」と「ポイントを再接続」の機能はそれぞれのノードを選択してからそのコンテキストメニューで利用できます。アウトラインを開くにはノードを個別に、ノードを再接続するにはアウトラインのノードを「ペア」で選択してください。  

<!-- replaced a paragraph -->
> ### Pro Tip
> これらの機能を頻繁に使わなければならない場合、キーボードショートカットを設定したくなるでしょう。そうなったときのために、メニューの「パス」＞「その他」に「ポイントの再接続」と「アウトラインを開く」を追加しました。「Glyphs」＞「環境設定」＞「ショートカット」＞「メニュー」でショートカットを設定してください。  

<!-- changed formatting (no blockquote, removed "Hint:") -->
[mekkablueのスクリプト](https://github.com/mekkablue/Glyphs-Scripts/)の「Paths」＞「Rewire Fire」は、再接続すべきノードを探すのに役立ちます。全てのノードを見つけることはできませんが、通常は「ほとんど」の場合で上に示したようにきれいではない縁が原因です。「nodes on top of line segments」を探すオプションを使います。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/4842cffd06-1605628249/rewirefire.png">

## オプション：仮想マスターの追加

一部のグリフのみに適用される補間軸が必要な場合を考えてみてください。例えば、横棒の高さは、 A 、 E 、 F 、 H などに適用できますが、S 、 D 、 J 、 O といった文字や、文字ではない数字、句読点、記号などには適用されません。全てのフォントにマスターを新しく作るのは無意味だと思いませんか？ むしろ、横棒を持つグリフにだけマスターを追加したいと思うでしょう。さて、そんなときのために、「仮想マスター」というものがあります。  

<ol>
<li>
<p>「ファイル」＞「フォント情報」＞「フォント」で、補間軸パラメータに新しい補間軸を追加します。これは標準で用意された補間軸ではないので、名前は任意のものにします。今の例なら、「Crossbar Height（横棒の高さ）」という名前と「CRSB」という4文字のタグが良いでしょう。</p>
<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/ae397c2848-1608028536/newaxis.png">
</li>
<li>
<p>同じウィンドウのタブで、「Virtual Master」というカスタムパラメータを追加し、「Weight」軸にLightマスターの値（この例では50）を、「Crossbar Height」軸に最小の値（0としましょう）を入力します。</p>
<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/acfd41e2b9-1608028536/virtualmaster.png">
</li>
<!-- the last sentence is new: -->
<li>
<p>「ファイル」＞「フォント情報」＞「マスター」ですべてのマスターを確認し、「Crossbar Height」の補間軸上の座標が 0 ではなく、例えば 100 になっていることを確認します。これはこの値がデータ的に何らかの意味を持つということを示します。この例の場合では、0 は横棒が可能な限り最も低い位置にあることを表し、100 は可能な限り最も高い位置あることを表します。全てのマスターを選択すれば全マスターを一度に編集できます。</p>
<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/5dfee3f29e-1608028536/vm-editallmasters.png">
</li>
</ol>

これでフォント情報に仮想マスターが設定されたので、作図すべきグリフのそれぞれに横棒の低いバージョンを追加できます。  

<!-- points 2-4 are new: -->
<ol>
<li>
<p>編集ビューでグリフを開きます。</p>
</li>
<li>
<p>「レイヤー」パレットで、＋アイコンを押下して「Light」レイヤーを複製します。現在の日時を名前としたバックアップレイヤーが作成されます。</p>
</li>
<li>
<p>バックアップレイヤーを右クリックしてコンテキストメニューから「レイヤーのタイプ」＞「中間マスター」を選択し、レイヤーを中間マスターにします。</p>
<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/b0e03234b6-1608028536/vm-choose-layertype.png">
</li>
<li>
<p>中間マスターをダブルクリックし、現れたポップアップダイアログで、そのマスターのデザインスペースの座標にあたるウェイト（この例の50はLightのマスターであることを表す）と横棒の高さ（この例の0は横棒が最も低い位置にあることを表す）を設定します。</p>
<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/49619157bb-1608028536/vm-intermediate-layer.png">
</li>
<li>
<p>そして横棒の高さが0の場合に文字がどうなるかを作図します。</p>
<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/06c9c585ba-1608028536/lowcrossbar.png">
</li>
</ol>

<!-- 1st and last sentence are new:-->
ここで良いお知らせです。微調整の必要がなければ、Boldのマスターのブレースレイヤーは追加する必要はありません。バリアブルフォントでは2つの補間軸の差分（ノードの動き）は互いに補完し合っており横棒の低い太字が追加されます。なので最良の戦略は1つのマスターのみでもうまく動作するかどうかを見て、結果が不十分だった場合にのみ追加することになります。  

以上です。あとは出力して、Illustrator、Axis Praxis、あるいはVariable Font Test HTML scriptでフォントを再びテストするだけです。さあ、どうぞ！ 横棒の位置をベースラインの方へ下げるための2つ目の補間軸が表示されます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/cc7d72c734-1605628247/2nd_axis.png">

実質的に、デザインスペースに2つ目の次元を追加しました。その際はマスターを「矩形に配置」することが推奨されており、原点のマスターに対して垂直方向または水平方向に配置するならもっと良いです。この例では、Lightのマスターに対してBoldのマスターは水平方向に配置され（1つ目の座標軸のみの差）、横棒が低い位置のマスターは垂直方向に配置されます（2つ目の座標軸のみの差）。この方法は、説明したようにマスターを配置し、作成した差分を垂直方向と水平方向に追加するだけで、デザインスペースの矩形内の任意の点に届くので、管理が最も容易です。  

<!-- only the first paragraph and UI names have changed, e.g. Exports instead of instances -->
## オプション：原点マスターの変更

フォントに格納されるアウトラインのセットは1つだけです。OTVarに非対応のソフトウェアではこの「デフォルトのアウトライン」だけが表示されます。このデフォルトは通常は最初のマスターです。しかし、別のマスターをデフォルトに選ぶこともできます。それには、「ファイル」＞「フォント情報」＞「フォント」または「ファイル」＞「フォント情報」＞「出力スタイル」の「Variable Font Setting」で、「Variable Font Origin」というカスタムパラメータを追加します。その値には、マスターの名前をポップアップメニューから選びます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/21b3f33130-1608028536/origin.png">

そうです、「マスター」でなければなりません。「インスタンス」のどれかを原点にしたい場合は、そのインスタンスをマスターとして追加する必要があります。「ファイル」＞「フォント情報」＞「出力スタイル」で、原点として定義したいインスタンスを選択し、ウィンドウの左下の隅にある＋アイコンを押下して、現れるポップアップメニューから「Instance as Master」を選択します。これで「ファイル」＞「フォント情報」＞「マスター」にマスターが追加されるので、それをバリアブルフォントの原点に設定できます。  

考慮すべき点が2つあります。  

* **デフォルトのスタイル：** バリアブルフォントの背景にある基本的な考え方の1つは、「最もよく使用されるインスタンス」をデフォルトに選べるということです。マルチプルマスターでは、デザインスペースの極端な位置（つまり、最も使われないインスタンス）をデザインしてその間を全て補間生成していました。バリアブルフォントではその逆の手法が可能です。最も重要なアウトラインのみをデザインスペースの中央に配置し、他の全てのインスタンスをそのアウトラインから派生させます。したがって「デスクトップフォント」では、原点にはレギュラー体を選ぶか、またはユーザにとってそのフォントファミリーの「デフォルトのスタイル」となるものを選びます。他のウェイトが全て機能しない場合には、それがユーザの使えるウェイトとなります。
* **ファイルサイズ：** 中間マスターを増やすと、ノードの差分の数が増えるので、要は、最終的なファイルサイズも大きくなります。補間軸の設定が1つの場合、差分の数は、それ以上ではないとしてもおそらく2倍にはなります。別の言葉で言えば、「ウェブフォント」の場合は、ファイルサイズと読み込み時間を抑えたいので、「デザインスペースの極端な位置にあたる」マスターの1つを選ぶ方が合理的です。

## オプション：補間軸の位置

「ファイル」＞「フォント情報」＞「マスター」で、「Axis Location」というパラメータを追加できます。これでマスターの補間軸上の座標を変更できます。ユーザに見せる値をマスターやインスタンスで設定した補間値とは違うものにしなくてはならない場合に意味があります。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/3d0993da87-1608028536/axislocation.png">

<!-- paragraph replaced: -->
この例では、ウェイトは `usWeightClass` の1から1000の値に関連するのでWeightスライダーの範囲が50から200というのは仕様から外れていると議論できます。さら言えば、100（Hairline）から、400（Regular）、700（Bold）、900（Heavy）という範囲で、100刻みの値には意味があります。するとこの例では、Lightマスターは300（Light）のウェイトに、Boldマスターは800（Extrabold）以上のウェイトに相当します。  

<!-- paragraph commented out, not sure if it still works that way, currently a bug in Glyphs 3: -->
<!--
> **Note：** 「Axis Location」パラメータを追加すると、バリアブルフォントに出力される補間軸が実質的に変更されます。つまり「Virtual Master」パラメータがある場合は、その影響がある補間軸の座標もそれに合わせなければなりません。しかし、ブレースレイヤーとブラケットレイヤーの数値は、元の補間値で形成されるデザインスペースにまだ由来しているため、変更は行わないでください。
-->

<!-- all points have been reworked, new headline too (used to be "Limitations") -->
## 動作すること／動作しないこと

もう慣れてしまったかもしれませんが、バリアブルフォントには思ったようには動作しない点もあります。  

1. 上でも簡単に述べましたが「ファイル」＞「フォント情報」＞「出力スタイル」の**カスタムパラメータによるポストプロセス**は全て無視されます、アウトラインの互換性や文字集合の一貫性を損う可能性が高いためです。これにはフィルタやRenameパラメータも含まれます。
2. **コーナーコンポーネントとセグメントコンポーネント**は動作します。しかし挙動が違います。バリアブルフォントでは、これらは補間生成の「前」に適用されるのに対し、昔ながらのマルチプルマスターの設定では、後から挿入されます。
3. **中間マスターとオルタネートレイヤー**は両方とも機能します。
4. **オルタネート**レイヤーはコンポーネントグリフには変換しません。しかしそれをスクリプトで解決する方法はあります。以下を参照してください。
5. **ブラシ**は、全てのマスターで同じように適用されていれば動作します。
6. **パスをオフセット**は現在のところ確実には動作しません。「2次ベジェに変換（TrueType）」はアウトラインの互換性を損なう可能性があります。

## 本当はオプションではありませんが：STATテーブル

全てのバリアブルフォントを含む、新しいフォントでは、命名情報はSTATテーブルに格納されます。STATは「Style Attributes」の略で、補間軸、インスタンス、「表示文字列」または「名前文字列」と呼ばれるものといった情報が含まれます。「表示文字列」とは補間軸上のセクション名で、例えば、ウェイトの補間軸はLight、Regular、Medium、Semibold、Boldに、幅の補間軸はCondensed、Regular、Extendedといったセクションに分けられます。  

この背景にある考え方はユーザ側のスライダーの設定に関わらずユーザが現在使用中のインスタンスをアプリケーションが命名できることです。実質的には、複数の補間軸が設定されている場合、相応しい名前を持つn次元のフィールドが想定されます。例えば、フォントにウェイトと幅の補間軸がある場合、下の表のようなウェイトの列と幅の列が想定されます。そしてBoldセクションのウェイトとCondensedセクションの幅の組合せたものを命名するときは、アプリケーションは単に表示文字列を組合わせれば良く、ジャジャーン——「Bold Condensed」となります。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/548c57f6cd-1605628249/STAT_Table.svg">

他の表示文字列と組み合わされたときに省略される表示名は「elidable（省略可能）」とされます。通常では「Regular」や「Normal」などのデフォルトスタイル名がこれに当たります。レギュラーの幅と組み合わされたセミボールドのウェイトは、通常は「Semibold Regular」ではなく「Semibold」と呼ばれます。またはイタリック体と組み合わされたレギュラーのウェイトは、「Regular Italic」ではなく単に「Italic」と呼ばれます。このように、表示名「Regular」は省略可能とみなされます。  

通常は、Glyphsは定義済みインスタンス名を分析してこれをかなり賢く処理します。しかし、STATテーブルのエントリで、表示文字列がファイル内に適切に保存されなかったことが判明した場合は、「ファイル」＞「フォント情報」＞「出力スタイル」の次の2つのパラメータで管理できます。  

* **Style Name as STAT entry：** インスタンスのスタイル名を補間軸の範囲を表す組み合わせ可能な表示文字列として使用します。値には、表示文字列が適用される補間軸の4文字のタグを使用します。これは1つの補間軸では非正規で他の全ての補間軸では正規であるインスタンスでのみ使用してください。正規の属性には省略可能な名前があってスタイル名に表示されないからです（例えば、「Semibold」や「Condensed」など）。「例」：Lightのインスタンスでは、Lightはウェイトの補間軸上の値であることから、このパラメーターを値「wght」で使用します。
* **Elidable STAT Axis Value Name：** パラメータ値で指定された補間軸に対しインスタンスのスタイル名を省略可能なものとして宣言します。値には、それぞれの補間軸の4文字のタグを使用します。通常は、このパラメータをレギュラーのスタイルに追加し、省略可能な表示文字列の名前である補間軸ごとに1つ追加します。「例」：Regularと呼ばれるインスタンスは「Elidable STAT Axis Value Name」パラメータを2つ持ち、その値は1つは「wght」でもう1つは「wdth」です。

<!-- COMMENTED OUT
> **Pro tip：** STATテーブルの重要性はますます高まっています。そう遠くない将来、多くのアプリケーションでフォントをまず最初に読み込むときにこれが必要になるでしょう。どこで知った情報かは聞かないで欲しいのですが、Windows用のフォントを公開したい（または公開し続けたい）のであれば、全てのフォントにSTATの装備が求められるということをお伝えしておきます。**ヒント、ヒント：**これには正体（値0）と斜体（値1）を区別するためのイタリック補間軸（`ital`）が含まれます。
-->

## 補間軸のマッピング

補間軸についてもう1つ。明らかに、補間軸はどこかで始まってどこかで終わります。ユーザインターフェースでは、補間軸の始まりと終わりはスライダーの左端と右端の位置によって表すことができます（通常ではそう表されています）。もちろん、その間にある全てはこの両端の間で均等に分散されています。別の言葉で言えば、補間生成の25%を表示するには、スライダーを1/4の位置に置き、補間生成の50%を表示するには、スライダーをちょうど真ん中の位置に置く、などします。理にかなっていますよね。  

ちょっと待って。本当にそうでしょうか？ よく考えてみると、これに意味があるのはユーザがアクセスできるインスタンスが、スライダーの範囲「全体に」（多かれ少なかれ）「均等に」分布している場合だけです。議論のために、重要な位置がスライダーのごく一部の範囲に詰め込まれていて、スライダーの大部分がユーザにとってあまり役に立たないという状況を考えてみましょう。  

これは実際に「Weight」軸（`wght` タグ）の場合で生じます。（ほぼ全ての）ウェイトの補間生成は、様々なウェイトのスタイルは均等には分布しません。最も細字のマスターの細さと最も太字のマスターの太さから、補間軸に沿った複数の「焦点」にグループ分けされた、より多くのスタイルが生成されます。例えば、「非常に細い」ウェイトから「普通の」、つまり「そんなに極端な太字ではない」ウェイトまでを補間生成すると、スタイルはスライダーの細字側の端に集中します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/c39fe8015d-1605628247/axis-distribution2.png">

なぜでしょうか？ それは原則として、スライダーを「どの位置で」動かしても、スライダー上の等距離の移動はユニットの同じ変化に対応するからです。例えば、スライダーをある場所で往復するとデザインが10ユニット変化し、別の場所で往復すると同じように10ユニット変化します。ところで、ステム幅を10ユニット増やすというのは、元が数ユニットしかないヘアライン体にとっては「大きなこと」です。しかしミディアムやセミボールドの場合は、元のステム幅と比べると、ごく小さな変化に過ぎないので、全く同じ10ユニットでも実質的には「無視できます」。  

あまり極端な細字ではない細字、ブックやレギュラーあたりのウェイトから、非常に太いウルトラヘビーのウェイトがスライダーのもう一方の端であるような場合は、逆になります。この時、スタイルはスライダーの範囲の太字側の端に集中します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/e37b072f5f-1605628247/axis-distribution3.png">

どうしてそうなってしまうのでしょうか？ ええと、つまり状況が上と逆で、今回は変化するのは文字の「白い部分」だからです。「超絶、非常に」太いデザインでは、余白が非常に少ないので白い部分が10ユニット増減するというのは「大きなこと」です。しかし、平均的なブックからセミボールドのデザインあたりの「普通の」範囲のウェイトでは、さっきと同じ状況になります。スタイルは離れて配置されます。  

それとこれを組み合わせると、「非常に細い」ウェイトから「非常に太い」ウェイトまでの補間生成では普通はスライダーの範囲の両端にスタイルが集中するということが明らかです。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/f69cb8c066-1605628247/axis-distribution1.png">

しかし一方で、ユーザはこの分布の問題なんか気にしませんよね？ ユーザからしたら、さまざまなスタイルへアクセスするには、このように補間軸全体に均等に分布している方が一番便利です。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/87ebae4ef4-1605628247/axis-distribution4.png">

言い換えるなら、均等に分布する「ユーザがアクセスしやすい」位置を、然るべき分布になっている「デザインの」位置になんとかして変換する必要があるということです。このように。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/f4d9fd4bb0-1605628247/axis-distribution5.png">

これを「補間軸のマッピング」といいます。補間軸上でユーザが「見た」ものを、補間軸上でユーザが実際に「使う」ものへとマッピングします。そしてそのようなマッピングは、「ファイル」＞「フォント情報」＞「フォント」＞「カスタムパラメータ」の「Axis Mappings」パラメータで実現できます。しかしどうやって設定するのでしょうか？ 簡単です。  

1. Weight軸の両端、つまり、最も細字と最も太字のマスターの位置を決めます。例えば、Lightマスターが50でBoldマスターが200のプロジェクトを作っているとします。
2. Weight軸を区切るインスタンスの数を決めます。今の例では、Light、Regular、Medium、Semibold、Bold、Extraboldの、6つのインスタンスがあるとします。
3. スタイル間の間隔の大きさを計算します。両端の差をスタイルの数から1を引いた数で割ります。例：（200 − 50）÷（6 − 1）＝ 30（6つのスタイルの間に区切りは5個あるので、1を引く）
4. 一番細いウェイトに繰り返し間隔を追加していくと一番太いウェイトになる形で、ユーザがアクセスするスライダーの位置が均等な分布になるように計算します。例：Light＝50、Regular＝80、Medium＝110、Semibold＝140、Bold＝170、Extrabold＝200。
5. そして「ファイル」＞「フォント情報」＞「フォント」「カスタムパラメータ」に「Axis Mappings」パラメータを追加して値を編集します。

<br />

* 左側の列で「Weight」軸を選択し、＋アイコンでマッピングペアを各スタイルに1つずつ、合計6つ追加します。
* マッピングペアの左の列に、上で計算したユーザのアクセスしやすいスライダー位置を均等に配置します。
* マッピングペアの右の列に、然るべき分布にあるデザインの位置、言い換えれば、「ファイル」＞「フォント情報」＞「インスタンス」にある実際の「Weight」補間値を追加します。

全ての設定がうまくできたら、このような感じになります。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/46f1106735-1605628247/axis-mapping-parameter.png">

> **Tip：** 両端のマスターを確実にマッピングしてください。両端（この例ではLightが50、Extraboldが200です）にスタイルを配置しなかった場合は、「両方の列に同じ値」が設定されて、とにかくマッピングに追加されます。  


パラメータをビジュアル表示に切り替えて補間軸のマッピングを微調整することもできます。点を結ぶ線をクリックすればマッピングポイントが追加されます。点を選択して座標を下部で編集します。左側がユーザーがアクセスする数値、右側が実際のデザインの値です。既存の点を上下にドラッグするとデザインの値が変更されます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/2409646d6e-1605628248/axis-mapping-visual.png">

技術的には、これはいわゆる[Axis Variations](https://docs.microsoft.com/en-us/typography/opentype/spec/avar)テーブル、別名 `avar` を作成しています。これは補間軸を「変化」させます。  

**Pro tip：** ウェイトの補間軸の値は「usWeightClass」の値のリスト、つまり 100＝Hairline、200＝Thin、300＝Light、400＝Regular、500＝Medium、600＝Semibold、700＝Bold、800＝Extrabold、900＝Heavy に準拠していなくてはならないと仕様に定められています。これを実現するには、これらの値にマスターの位置を関連付け、「ファイル」＞「フォント情報」＞「マスター」の「Axis Location」パラメータでこれらの値を使用するだけです。この例では、LightマスターにAxis Location パラメータを追加してWeight＝300に（Lightインスタンスに相当するため）、Boldマスターにも同じく追加してWeight＝800に（Extraboldインスタンスに相当するため）設定します。  

通常は、補間軸のマッピングで生じるのはスライダを端から端へドラッグしたときのフォントの挙動の微妙な変化だけです。そのため、全てが意図した通りに動作しているかどうかを確認するのは難しいでしょう。となると `avar` テーブルを検査する特別なツールが必要です。幸いにも、[Laurence Penney氏のSamsa](https://www.axis-praxis.org/samsa/)がそういったツールです。フォントをページにドラッグ＆ドロップし、「Axes」インスペクタで、「Show avar」オプションをオンにしてください。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/c7602a05ec-1605628249/samsa-avar.png">

そしてスライダーをドラッグし、スライダー上での表示位置（上）と実際のデザインの分布（下）とのマッピングを表す緑色の矢印を確認します。視覚化された情報の上にマウスオーバーしてツールチップがポップアップするまで待つと、突っ込んだ追加情報が得られます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/ad92920b18-1605628249/samsa-tooltip.png">

説明すると、`avar` の値は -1.0 、 0.0 、 +1.0 の間にあります。Glyphsは通常 0.0 から +1.0 の間で補間生成を行います。言い換えるなら、`avar` では、Lightマスターは 0.0 に、Boldマスターは +1.0 に対応します。例えば、上のツールチップ画像では、現在のスライダーの位置 550.4（0.562988…または56.3%）は実際のデザイン位置では 540.38（0.550476…または55%）で、ミディアム（500）とセミボールド（600）の中間であることが示されています。  

## 便利なスクリプト

[mekkablueのスクリプト集](https://github.com/mekkablue/Glyphs-Scripts/)（リンク先readmeにインストール手順あり）には、バリアブルフォントを動作させるのに便利なスクリプトがいくつかあります。  
<ol>
<li>
<p><strong>「Interpolation」＞「Composite Variabler」：</strong> コンポーネントグリフ内で使われているコンポーネントの<a href="https://glyphsapp.com/learn/alternating-glyph-shapes">オルタネートレイヤー</a>を再複製します。またブレースレイヤーをコンポーネントグリフ内でも動作させます。例えば、ウェイトが太くなるにつれ二階建てから一階建てに切り替わるというブレースレイヤーを持つ小文字の <code>g</code> の場合、<code>gcircumflex</code> 、<code>gcommaaccent</code> 、<code>gbreve</code> といったコンポーネントグリフ中でブラケットレイヤーを再複製する必要があります。なおスクリプトの実行後にブラケットレイヤーを分解する必要があります。</p>
<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/b83a70f895-1605628248/mekkablue-compound-variabler.png">
</li>
<li>
<p><strong>「Kerning」＞「Zero Kerner」：</strong> あるマスターにはが存在するが別のマスターでは欠落しているカーニングペアに値が 0 のグループカーニングを追加します。OTVar出力でカーニングの補間生成を可能にするのに役立ちます。カーニングの欠落、特に一部のマスターにだけカーニングペアが設定されている場合に使います。</p>
<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-variable-font/a733c89468-1605628248/mekkablue-zero-kerner.png">
<p><strong>更新情報：</strong> Glyphs 2.6.5、ビルド1300以上では、Zero Kernerはもう必要ありません。</p>
</li>
</ol>

## 追加資料

バリアブルフォントについてもっと深く知りたいですか？ そのためのリンクをいくつか用意しました。  

* マイクロソフト社： [OpenType仕様](https://docs.microsoft.com/en-us/typography/opentype/spec/)
* Microsoft GitHub： [OpenType Design Variation Axis Tags](https://github.com/Microsoft/OpenTypeDesignVariationAxisTags) の新規タグ提案
* Tom Rickner氏による裏話「[from TrueType GX to Variable Fonts](https://www.monotype.com/resources/articles/part-1-from-truetype-gx-to-variable-fonts/)」
* Irene Vlachou氏による要点ガイド「[Building variable fonts with Feature Variations](https://github.com/irenevl/variable-fonts-with-feature-variations)」
* Roel Niesken氏による [Wakamai Fondue](https://wakamaifondue.com)（「What can my font do?」）
* ABC Dinamoによる [Font Gauntlet](https://dinamodarkroom.com)
* Laurence Penney氏による [Axis Praxis](https://www.axis-praxis.org)
* Laurence Penney氏による [Samsa](https://www.axis-praxis.org/samsa/) バリアブルフォント解析ツール（[GitHub上のソースコード](https://github.com/Lorp/samsa)）
* Nübel兄弟による [Font Drop](https://fontdrop.info)
* Travis Kochel氏による [I Can Variable Font「Notes on generating variable fonts」](https://github.com/scribbletone/i-can-variable-font)
* Andrey Kuzmin氏による [Font Dimensions](https://github.com/w0rm/elm-font-dimensions) バリアブルフォント次元可視化ツール
* Underware氏による楽しいショーケースとコンセプトページ： [Very Able Fonts](http://very-able-fonts.com)
* Nick Sherman氏による [V-Fonts](https://v-fonts.com/)「a simple resource for finding and trying variable fonts」
* Christoph Koeberlin氏によるリンク集 [variable fonts resource list](https://typefacts.com/links/variable-fonts)（一部ドイツ語ですが、引かないでください）</li>
</ul>

<!--
## Animation
* Laurence Penney氏による[Muybridge Horse animation](http://www.axis-praxis.org/playground/horse/)
* https://etc.supply/animating-a-variable-font-with-css/
* Laurence Penney： [Variable Fonts Experiments]( https://codepen.io/collection/XqRLMb/) バリアブルフォントのテキスト効果の実験集
Codepen
OTVarフォントにアニメーションを実装する予定なら [mekkablueスクリプトリポジトリ](http://github.com/mekkablue/Glyphs-Scripts)に利用可能なスクリプトがあります
* 「Masters」＞「OTVar Player」
* 「Masters」＞「Insert Brace Layers for Rotating Components」
* 「Masters」＞「Insert Brace Layers for Movement Along Background Path」
-->

********

STATテーブル サンプルフォント： Plantago 、Viktor Solt-Bittner氏、Schriftlabor氏  
謝辞： Rob McKaughan氏よりこのチュートリアルにコメントとアドバイスをいただきました。  

<br />

Update 2018-03-16: 誤記訂正（Jeff Kellemさんありがとう）。  
Update 2018-06-22: 例示の値の表現を明確化（Karlさんありがとう）。  
Update 2018-11-20: 「Variable Font Origin」パラメータ名を更新。  
Update 2019-02-15: Font GauntletとWakamai Fondueへのリンクを追加。テスト用スクリプトとブラウザのサポート情報を更新。「バグの回避」を追加。  
Update 2019-03-13: 「追加資料」を追加。  
Update 2019-03-04: 誤記を訂正して出力ウィンドウの「Variation Fonts」を「Variable Fonts」に置換（Nathalie Dumontさんありがとう）。  
Update 2019-03-20: 誤記訂正、「Add Instance as Master」を「Instance as Master」に置換、Nick Sherman氏のV-Fontsへのリンクを更新（Nathalie Dumontさんありがとう）。  
Update 2019-10-23: 「便利なスクリプト」を追加。  
Update 2019-12-04: アンチエイリアスの問題に関するセクションを追加。  
Update 2020-03-08: Safariのオプティカルサイズのバグについての段落、「Rewire Fire」スクリプトに関するhint、追加資料にSamsaを追加。  
Update 2020-06-14: 「補間軸のマッピング」の章を追加、「便利なスクリプト」を更新、SafariのオプティカルサイズのバグのGIFを追加。  
Update 2020-07-09: 「Rewire Fire」スクリプトに関する段落の語句をマイナーチェンジ。  
Update 2020-11-17: 部分的にGlyphs 3に適応。  
Update 2020-12-14: 大部分とスクリーンショットをGlyphs 3用に更新。  
