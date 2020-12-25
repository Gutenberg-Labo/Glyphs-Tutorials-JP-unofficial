# 複数レイヤーのカラーフォントの作成

[(Original page)](https://glyphsapp.com/learn/creating-a-layered-color-font)  

<br />

by Rainer Erich Scheichelbauer  

<br />

1 December 2016  
Published on 16 September 2014

********

Glyphsを使えば、複数レイヤーのカラーフォントを簡単に作成できます。その方法を説明します。

********

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-layered-color-font/17a16877d2-1605628236/Sapperlot.png">

複数レイヤーフォントはユーザにとって楽しいものですが、作成者の作業はいつも大変でした。でも、それがとても簡単になりました。Glyphsは、複数レイヤーフォントのデザイナー向けに大きな改善をいくつか行いました。

### マスターとインスタンスの作成

レイヤーがマスターになります。そこで「ファイル」＞「フォント情報」＞「マスター」を選択し、必要なレイヤーの数だけフォントマスターを追加します。そのそれぞれに異なる「カスタム」名と値を指定してください。例えば「Front」「Side」「Bottom」、1、2、3、などです。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-layered-color-font/9f2fbc4c4d-1605628235/colorfont-1.gif">

そして作業中は、マスターごとに異なるプレビューカラーを割り当てることができます。というのも全レイヤーが同じ色のレイヤーフォントなんて面白くないからです。やり方は次の通りです。カスタムパラメータのセクションのすぐ上にある小さな＋アイコンを押下して、新しいカスタムパラメータを追加します。「プロパティ」ポップアップから「Master Color」を選択すると、「値」フィールドにカラーピッカーが表示されます。カラーピッカーをクリックし、それぞれの色を選択します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-layered-color-font/5a7f3badab-1605628235/colorfont-2.png">

ヒント、ヒント。オーバープリント効果をシミュレートしたい場合、透明度の選択も可能です。  

それができたら、「Master Color」パラメータを選択し、クリップボードにコピー（Cmd-C）します。そして他の各マスターに移動して、その度に、「カスタムパラメータ」セクションをクリックして、ペースト（Cmd-V）します。その後はカラーピッカーをクリックすれば、簡単に各レイヤーの色を変更できます。パワーユーザであるならサイドバーで複数のマスターをCmdキーを押しながら選択すれば、全てのマスターレイヤーのパラメータを一度に追加またはペーストできます。  

さて、「フォント情報」ウィンドウで、「インスタンス」タブに切り替えます。そこで、先ほど使ったのと全く同じウェイト値を持つインスタンスを作成します。そうするには、左下の＋アイコンをクリックし、ポップアップメニューから「全マスターをインスタンスとして追加」を選択します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-layered-color-font/405be428bc-1605628235/colorfont-3.png">

「全く」同じ値を使うと、補間が行われることはありません。ここでは補間したいのではなく、異なるレイヤーを描画して出力したいだけなのでそれでOKです。

### レイヤーグリフの編集

「フォント情報」ウィンドウを閉じると、フォントウィンドウに戻ります。大文字の I をダブルクリックしましょう。簡単な文字なので、試したり編集してみるのに最適です。  

ウィンドウ上部にあるマスターボタンか、または Cmd-1、Cmd-2、Cmd-3 のショートカットで、レイヤーの切り替えができます。サイドバーパレット（Cmd-Opt-P）の「レイヤー」セクションに、カスタム名がレイヤー色とともにポップアップ表示されます。各レイヤー名の左側には、小さな目のアイコンがあります。閉じている目を全てクリックして開けます。すると、編集中に全マスターのレイヤーが一度に表示されます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-layered-color-font/1ff69474e3-1605628235/colorfont-4.png">

Cmd-1 を押して「Front」レイヤーに移動し、キャップハイトからベースラインまでの長方形を、大文字の I として描きます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-layered-color-font/409c099317-1605628235/colorfont-5.png">

それから、長方形を選択したままにして、クリップボードにコピーし（Cmd-C）、「Side」レイヤーに切り替え（Cmd-2）て、ペースト（Cmd-V）します。  

一番左のノード2つを選択ツール（V）で選択し、次のように、右下に移動させます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-layered-color-font/9f176f7048-1605628235/colorfont-6.png">

全てを選択して（Cmd-A）、クリップボードにコピーし（Cmd-C）、「Bottom」レイヤーに切り替えて（Cmd-3）、貼り付けます。ここで、「Bottom」レイヤーの上端が「Front」レイヤーのベースに揃うように、上2つのノードを左下の位置まで移動させます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-layered-color-font/a1d1a01964-1605628235/colorfont-7.png">

ここで Option キーを押しながら、「パス」メニューから「全マスターのパス方向を修正」（Cmd-Opt-Shift-R）を選択してください。スペースバーを押して一時的にプレビュー表示するか、単純にテキストツール（T）に切り替えれば、全てが期待通りに動作するかを確認できます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-layered-color-font/fae16b9ae7-1605628235/colorfont-8.png">

おめでとう。最初のレイヤーグリフができました。

### マルチプルレイヤーの編集

編集については、「全レイヤー選択」ツールがあって、これで表示中のレイヤーにある任意のポイントが編集できます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-layered-color-font/493cdc6a67-1605628236/colorfont-9.gif">

いくつかのメニューコマンドは一度に全てのレイヤーで動作します。「グリフ」＞「全マスターのメトリクス情報を更新」（Cmd-Opt-Ctrl-M）が使えますし、「パス」＞「全マスターのパス方向を修正」（Cmd-Opt-Shift-R）ならもう使っています。

### メトリクスの維持とカーニングの同期

もう1つ大きな課題があります。全てのマスターを全く同じ幅にすることです。要は、ある色で幅を変更したら、他の色のレイヤーも全てそれに揃えなければなりません。もちろん Cmd-1 、2 、3 ……で全てのマスターの幅を変更し、同じくメトリックを変更することは「できます」。でももっとスマートな方法があります。  

「ファイル」＞「フォント情報」＞「マスター」（Cmd-I）で、カスタムパラメータ「Link Metrics With First Master」を全てのマスターに追加します。これで全ての幅の変更がこのパラメータを持つ全てのマスターで同期されます。また「幅の変更」だけでなく、「カーニングの変更」も全てのマスター間で同期されます。やったね。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-layered-color-font/55982ab8be-1605628236/colorkerning.gif">

メトリクスとカーニングを最初のマスターではなく、別のマスターと同期させたいときがあります。その場合、「Link Metrics with Master」パラメータを使います。「値」にマスター名を入力します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-a-layered-color-font/330f5af643-1605628236/linkmetricswithmaster.png">

### レイヤーフォントをInDesignで適用

他のプロジェクトと同様にフォントをエクスポートします。いつものように、[Adobe Fonts](https://glyphsapp.com/tutorials/testing-your-fonts-in-adobe-apps)フォルダを使うことをお勧めします。  

さて、InDesignで行うべきは、完全に同じ内容のテキストフレームを複数用意し、それぞれを別のスタイルで重ねることです。[これは InDesign の配置とリンクツールを使えば実現できます](http://www.lynda.com/articles/indesign-secrets-how-to-place-and-link-text-without-its-formatting)。

### Illustratorでフォントを重ねる

Adobe Illustratorでエリアタイプのオブジェクト（つまりテキストボックス内のテキスト）を整列させるにあたって問題が1つあります。デフォルトでは、アプリはテキストボックスの最初のベースラインに合わせてオフセットを自動で調整します。そのために、「Illustratorではフォントの小文字 d を測定して、」そのアセンダーの高さを最初の行のオフセットとして使っています。これは冗談ではなくて、AIは本当にそうしています。  

問題は、カラーレイヤーでは、小文字のdで全てのレイヤーの縦の最大値が偶然同じになるなんてむしろ起こらないということです。その結果、レイヤーが揃わず、カラーフォントを買った人からサポート依頼メールを大量に受け取るかもしれません。  

対策としてできることは2つあります。1つは、Adobe Illustratorの全てのエリアタイプのオブジェクトで、ベースラインのオフセット設定を変える方法をユーザに告知することです。整列させたいテキストボックスを全て選択し、「タイプ」＞「エリアタイプオプション」から、「最初のベースライン」オプションで「固定」または「リーディング」を選択します。ただし、経験豊富なユーザでもこの設定は知らない場合が多いのでご注意ください。そして彼らはあなたに連絡する前に、このフォントに怒った投稿をInstagramで公開してしまうというリスクがあります。  

あるいは、2つ目は、小文字 d の全レイヤーの上部に、ごく小さな、多分ちょうど1ユニット幅の正方形を追加することです。全ての色のレイヤーの同じ高さにコピー＆ペーストして、この文字の中で最も高いパスオブジェクトとなるようにしてください。デザインの中でちょうど良い位置を探して、あまり目立たないようにしてください。そうすれば、Illustratorは小文字 d を測定して、全てのレイヤーを同じ高さとして検出し、デフォルトでそれらを全て揃えます。そしてあなたの受信箱がサポート依頼で溢れかえることもないでしょう。  

なお繰り返しますが、AIでフォントをテストするためにも、[Adobe Fontsフォルダ](https://glyphsapp.com/tutorials/testing-your-fonts-in-adobe-apps)を使うようにしてください。

### Sapperlot ソースファイル

とにかく、いい感じのものがこれでいけます。Thomas Maier氏（DrTypo）のSapperlotというフォントのように。Thomasは `.glyphs` ファイルをオープンソースで公開してくれてますので、[彼のGitHubページにアクセスして](https://github.com/DrTypo/sapperlot)よく見てみてください。  

[![](https://glyphsapp.com/media/pages/learn/creating-a-layered-color-font/15eaf016bb-1605628236/colorfont-10.png)](https://github.com/DrTypo/sapperlot)

********

サンプルフォント： [SAPPERLOT](https://github.com/DrTypo/sapperlot)、Thomas Maier氏 提供  

<br />

Update 2014-12-24: 「Illustratorでフォントを重ねる」の段落を追加。  
Update 2016-11-30: 「Link Metrics With First Master」パラメータについての段落を追加。  
Update 2016-12-01: 誤記と更新日時を修正。  
Update 2017-01-18: 「Link Metrics With Master」パラメータについてのスクリーンショットと段落を追加。
