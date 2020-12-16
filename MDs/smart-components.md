# 図形の再利用：スマートコンポーネント

[(Original page)](https://glyphsapp.com/learn/smart-components)  

<br />

by Rainer Erich Scheichelbauer

<br />

30 March 2015

********

スマートコンポーネントは、特にCJK部首の場合に、グリフのパーツ図形を再利用するための非常に優れた機能ですが、ラテン文字のパーツでも使えます。スマートに使いこなしてみましょう！

********

小文字の n の肩パーツを、例えば、小文字の m や h に再利用するとします。確かに、[スラブセリフ体を作る時に説明](https://glyphsapp.com/tutorials/serif-components)したようにコンポーネントを使えば再利用は可能です。しかし通常のコンポーネントを使うには1つ問題があります。それはサイズが固定であるということです。  

m の肩の場合は調整する必要があります。大半の人は幅をもう少し狭めたいと考えるでしょう。1つの文字中に肩パーツが2つあることで生じる懐はかなり大きいからです。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/d788a41214-1605628237/shoulder-m.png">

また、ほとんどのデザイナーは小文字の h で、分岐部分を下げて切れ込みの量が n と釣り合うようにします。h のステムは n の上側のセリフと違って簡単には調整できないからです。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/6ef7997498-1605628237/shoulder-h.png">

これが、サイズが固定である通常のコンポーネントがここでは役に立たない理由です。もっと良い解決策が必要です。

### スマートグリフの設定

肩パーツを「スマートコンポーネント」にします。n の肩パーツをダブルクリックして選択します。次に右クリックしてコンテキストメニューを表示し、「選択パスをコンポーネント化」を選択します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/b53ce33d96-1605628237/componentFromSelection.png">

これは他のグリフでも再利用できるパーツになるので、「コンポーネントのグリフ名」の入力では `_part` から始まる名前を付けます。アンダースコアで始まる名前で作成されたグリフは、デフォルトでは出力に含まれないので、こうすることは合理的でもあります。スマートコンポーネントはフォント中に複数あることを想定して、コンポーネント名はドットから始まるサフィックスで終わらせましょう。今の場合は `.shoulder` が良いでしょう。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/d2650f8a15-1605628237/nameOfTheComponentGlyph.png">

`_part.shoulder` という名の分割グリフができました。この肩パーツにアンカーを追加して他のパーツと接続できるようにしましょう。まずは、m が作れるように、続くパーツに接続用のアンカーを追加します。これに `connect` という名前をつけ、ステムの右端に合わせましょう。  

>**Tip:** スマートコンポーネントの名前には、`_part` の代わりに `_smart` というプレフィックスも使えます。  

そして、`_part.shoulder` には、吸着先のパーツに繋がるためのアンカーが必要です。吸着先のアンカーが `connect` という名であるならば、対応するアンカーは先頭にアンダースコアをつけた `_connect` という名でなければなりません。これらのアンカーはすべて同じ高さ（つまりy座標）になければならないので、アンカーはベースライン上に置くことをお勧めします。すると、このようになります。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/908fe8f6ba-1605628237/partWithAnchors.png">

このパーツは名前が `_part` で始まるので、「スマートグリフ」として認識されます。しかしレイヤーが追加されない限り、まだまだスマートとは言えません。そこで、現在のレイヤーを2回コピーして、それらに `NarrowShoulder` と `LowCrotch` という名をつけましょう。これはパネルサイドバーの「レイヤー」セクション（Cmd-Opt-P）で行えます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/4e766032d9-1605628237/layersPanel.png">

さて、`NarrowShoulder` レイヤーをアクティブにして、パーツを少し細身にしてみましょう：肩パーツの右半分を選択し、Ctrl キーと Option キーを押しながら左矢印キーを押します。選択部分が左に移動し、周囲のハンドルがそれに比例して調整されます。同時にシフトキーも押すと10ユニット移動します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/2e9cda6fed-1605628237/nudgeShoulder.gif">

`LowCrotch` レイヤでも同じことを行いますが、今度は左端の2つのノードを選択して、分岐部分を低く下げます。この簡単な変形はとりあえずのものです。図形は後からでも調整可能です。  

ここで、`_part.shoulder` をアクティブにしたまま、キャンバス内で右クリックしてコンテキストメニューを表示させて、「スマートグリフ設定を表示」を選択します。または、「編集」＞「選択範囲の情報」（Cmd-Opt-I）を選択しても同じことができます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/8d21ec35ed-1605628237/showSmartGlyphSettings.png">

表示されたダイアログシートで、＋アイコンを押下して `shoulderWidth` というプロパティを追加し、「Limits」に `0` と `100` を入力します。プロパティ名と数値は多かれ少なかれ任意ですが、「Bottom」値は「Top」値よりも小さくする必要があります。またその値はあなたにとって意味のあるものでなければなりません。ここでは私は肩の最小幅を表す値に0を、最大幅を表す値に100を選びました。  

そして、`crotchDepth` という2つ目のプロパティを追加して `-100` から `0` までの範囲を指定します。私としては、`-100` は分岐部分が最も低い位置の場合を表し、`0` は通常の位置の分岐を表します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/ce114547e4-1605628237/smartProperties.png">

それから、ダイアログシートの「レイヤー」タブに切り替えます。ここで、Glyphsに対しどのレイヤーでプロパティ値がどれにあたるかを指定します。今の場合は、次のようになります。

* 「Regular」レイヤー： `crotchDepth 0` 、`shoulderWidth 100`
* 「NarrowShoulder」レイヤー： `crotchDepth 0` 、`shoulderWidth 0`
* 「LowCrotch」レイヤー： `crotchDepth -100` 、`shoulderWidth 100`

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/a35565abee-1605628237/smartLayers.png">

全てのレイヤーでプロパティを全て設定したら、「OK」ボタンをクリックしてダイアログを終了します。

### スマートコンポーネントの調整

さて、h 、m 、n といったグリフに戻って、肩のパーツを削除し、「グリフ」＞「コンポーネントの追加」（Cmd-Shift-C）から `_part.shoulder` をコンポーネントとして挿入します。  

そして、コンポーネントを右クリックし、コンテキストメニューから「スマートコンポーネントの設定を表示」を選択するか、また、あるいは、コンポーネントを選択して「編集」＞「選択情報」（Cmd-Opt-I）を選択すると、スライダダイアログが表示されます。配置したスマートコンポーネントをスライダで補間します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/b6343dc0ad-1605628237/sliders.png">

アンカーを活用するには、 `connect` アンカーで「ステム」をスマートグリフにすると合理的です。またおそらくは上部のセリフに湾曲を変えるための別のレイヤーを追加すれば、さまざまな角度の切れ込みが実現ができます。いずれにしろ、`_part.stem` はこのようになるでしょう。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/1a164d3c3a-1605628237/stem.png">

アンカーによる自動整列はグリフの「全ての」パーツがコンポーネントである場合にのみ機能します。グリフ内に通常のパスが存在すると、自動整列は直ちに無効となり、アンカーは無視されます。  

さて、例えば小文字の m の場合、最初にコンポーネントの `_part.stem` を配置し、続けて `_part.shoulder` を2回配置します。アンカーでうまく繋がることがわかるでしょう。そしてまた、スマートコンポーネントをパラメータで調節できます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/9db59642c9-1605628237/smartM.png">

### CJK部首をスマートコンポーネントに

スマートコンポーネントの本来の目的は、CJK統合漢字をより効率的にデザインすることでした。中国語・日本語・韓国語では、いくつかの文字が再利用されてもっと複雑な表意文字になります。これらの文字は他の文字の根（ラテン語「radix」）となるので、部首（英語「radical」）と呼ばれます。  

そのため、`_part` で始まるグリフだけではなく、全てのCJK部首もまたスマートグリフとみなされます。当然ながら、スマートコンポーネントの設定はもっと複雑なものになります。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/c7d47b4f62-1605628237/CJKradical.png">

### バウンディングボックスによるスマートな拡大・縮小

`Height` および `Width` という名前（大文字始まり）のプロパティがある場合、「表示」 > 「バウンディングボックスを表示」（Cmd-Opt-Shift-B）をオンにすると、ボックスの白丸のドラッグで `Height` と `Width` プロパティが操作できます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/b3a1623dbe-1605628237/cjkweightwidth.gif">

このスマートコンポーネントなら、スライダなんかよりずっと便利で直観的にサイズを操作できます。  

### スマートハンドル

こうして、高さと幅について無様なスライダーを撤去することができました。しかし他の全てのパラメータではどうでしょう？ いえ、心配は要りません。Glyphs 2.5 以降では、スマートコンポーネントで独自のハンドルを追加できるようになりました！ やり方を説明します。  

スマートグリフのレイヤーの全てに、プロパティ名のついたアンカーを追加します。そして、最も然るべき位置にそれらを配置します。以下の2つのCJK部首のスマートレイヤーを見比べて、「Right Arm」アンカーの位置に注目してください。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/c8f54f747e-1605628237/smarthandles.png">

アンカー名とプロパティ名が完全に一致していることを確認してください。プロパティの全てをアンカー名として追加する必要はありません。しかし追加するアンカーは全てのレイヤーにある必要があります。すると、スマートコンポーネントでは（プロパティスライダの代わりに）ドラッグ可能なハンドルがグリフに表示されます：  

<img alt="" src="https://glyphsapp.com/media/pages/learn/smart-components/90d66b754d-1605628237/smarthandles.gif">

ね、すごいでしょ？

********

サンプルフォント：Vesper、Rob Keller 氏および Kimya Gandhi 氏 提供  

<br />

Update 2017-12-11: 注記に代替可能な名前 `_smart` を追記。スマートな拡大・縮小とスマートハンドルを追記。  
Update 2018-12-07: 誤記訂正、ウェイトじゃなくて、高さ。やれやれ。
