# 複雑なアウトラインのフォントの作成

[(Original page)](https://glyphsapp.com/learn/creating-fonts-with-complex-outlines)  

<br />

by Rainer Erich Scheichelbauer  

<br />

20 December 2016  

********

グランジフォント、手書きフォント、滲んだ活版印刷フォント。複雑なフォントを作るあなたのためのチュートリアルです。  

********

現在のフォント技術は主として「通常の」書体が対象です。つまり使われている技術仕様では次のようなフォントが想定されています。  

* アウトラインはシンプルで、ノード数は可能な限り最少である。
* 極点にノードがある（[良いパスの描画についてはこちらを参照](https://glyphsapp.com/learn/drawing-good-paths)）。
* 複数のグリフで同じような形状のパーツを共有する（例えば、小文字の n 、h 、m の肩パーツはほぼ同じ形である）。
* まとまった数（大抵の場合、数百〜千個ほど）のグリフがある。

さて、もしあなたのフォントがこの前提条件から一つでも「外れて」いたら、それがいわゆる「複雑な」アウトラインです。もしあなたのフォントのアウトラインがそうであれば、サブルーチン化やヒンティングを行い、場合によってはパスを調整する必要もあるかもしれません。そうしないとフォントの出力ができないかもしれませんし、さらに悪いことには、出力してリリースできたもののエンドユーザのパフォーマンスに支障がでて、大量のサポートメールを受け取る羽目になるかもしれません。それじゃいけませんね。  

複雑なアウトラインというのは何かというと、こういうものです。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-fonts-with-complex-outlines/dd1eb73526-1605628244/adinah.png">

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-fonts-with-complex-outlines/3cf594dd98-1605628244/fairwater.png">

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-fonts-with-complex-outlines/c448017852-1605628244/letterpress.png">

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-fonts-with-complex-outlines/a8d1f420bd-1605628244/weingut.png">

タイプフェイス： [Adinah](http://handfoundry.com/work/#/adinah/) Andy Lethbridge氏、[Fairwater](http://lauraworthingtontype.com/family/fairwater-collection/) Laura Worthington氏、[Letterpress](http://www.facetype.org/?font=letterpress) Marcus Sterz氏、[Weingut](http://www.facetype.org/?font=weingut) Georg Herold-Wildfellner氏

### サブルーチン

サブルーチン化とは、CFFフォント（つまり、PostScriptアウトラインを含んだフォントで、拡張子は.otf）においてファイルサイズを節約する仕組みで、アウトラインから反復的な構造を探し出し、それらをいわゆる「サブルーチン」というものに格納しようとするものです。コンポーネントに少し似ていますが、これはグリフまるごとだけではなく、パスや曲線も扱います。これは出力時に自動で行われるので、通常では気にする必要はありません。  

サブルーチン化は、同じような形状がたくさんあって、グリフ数が数百〜数千程度のような、普通のサイズのフォントで最も効果的に働きます。グランジフォントやスキャンフォントのように、異なる形状があまりに多い場合、サブルーチン化は限界に達します。アウトラインが非常に複雑で細かかったり、グリフあたりのノード数が非常に多かったりする場合もそうです。または、多くのCJKフォントのように、グリフ数が非常に多い、例えば2万個とかそれ以上の数のグリフがあるフォントの場合でもそうなります（もっと知りたいですか？ [CJKフォントのサブルーチン化に関するKen Lunde氏のブログ記事を読んでください](https://blogs.adobe.com/CCJKType/2012/02/subroutinization.html)）。これらのどれかに当てはまる場合、出力に異常に時間がかかることに気が付くでしょう。これはサブルーチン化アルゴリズムが何万～何億ものアウトラインから同じような形状を探し出しているからです。大量の図形の中で同じ形状があっても、再利用されているのはごくわずかだったりすると、サブルーチンのせいで、フォントサイズが小さくなるどころか大きくなってしまう場合があり得ます。フォントが全く出力されない場合すらあります。  

「Disable Subroutines」パラメータは、サブルーチン化をオフにします。「ファイル」＞「フォント情報」＞「インスタンス」からそれぞれのインスタンスに行き、各インスタンスの「カスタムパラメータ」テーブルで、＋アイコンから新しいパラメータを追加し、「プロパティ」を「Disable Subroutines」に切り替え、「値」欄に表示されるチェックボックスをオンにします。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-fonts-with-complex-outlines/3ea3dcf968-1605628244/disablesubroutines.png">

次の場合はサブルーチン化の無効化を検討してみてください。  

* **グリフ数が非常に多い**。フォントに含まれるグリフが数千個やそれ以上。
* **似た形状がない**。グランジ、手書き、活版印刷、またはランサムノートフォントのように、フォント全体のポイントとしてはグリフの見ためがなるべく揃っていない。
* **アウトラインが極めて細密**。ドロップキャップ、シンボル、アイコン、イラスト、ディンバットフォントなど。
* **ノード数が多い**。一つのグリフに最低でも3桁個のノードがある。

### ヒンティング

[ヒンティング](https://www.glyphsapp.com/learn/hinting-manual-postscript-hinting)とはアウトライン部分にヒント情報を追加する処理です。ヒントは、グリフのどの部分が重要なステムか、グリッド・フィットで保持すべきか犠牲にするかという、ラスタライザーの決定を補助します。グリッド・フィットとは、「アウトラインを歪めて」ピクセルのグリッドに落とし込む処理です。  

ええ、そうなんです。「ヒンティングとは形状を保持するものではなく、逆に歪ませるものです」。ヒンティングは、小さなサイズのピクセルへとうまく落とし込むために、形状への忠実度を犠牲にします。その結果画面上のテキストはよりきれいに、より鮮明に、より統一感が出て、さらに読みやすくなります。しかし、ヒンティングにはアウトラインに多くの条件が必要です。それは出来るだけきれいで「普通」でなければならないのです。  

次の場合はヒンティングを付けないことを検討してみてください。  

* 意図的に一貫性をもたせていない、不均質な、**形状に似たところがない**フォント。
* ある文字の終筆を次の文字の入筆と正確に一致させなければならない、**連続するスクリプトのフォント**。
* **極めて細密なアウトライン**のフォント。
* グリフあたりの**ノード数が非常に多い**フォント。
* 「ファイル」＞「フォント情報」＞「マスター」で**アライメントゾーンがない**フォント。
* 「ファイル」＞「フォント情報」＞「マスター」で**スタンダードステムが設定されていない**フォント。
* 以下のような**通常ではないアウトライン**を持つフォント。
    * 極点にノードがない。
    * ステムの太さが異なっていたり、不均質である。
    * アライメントゾーンに常には届かない。
    * 「ラフ」や「ハッチング」のような装飾効果だけでなく、インライン、アウトライン、点線、影、3D効果といったフィルタをかけて制作している。

フォントのヒンティングを避けるには、[オートヒンティング](https://www.glyphsapp.com/learn/hinting-postscript-autohinting)を無効にすることと、設定されたヒントを手動で削除することの、2つを行う必要があります。オートヒンティングを削除するには、単に「ファイル」＞「出力」ダイアログで「オートヒント」オプションを無効にするだけです。あるいは、もちろん「ファイル」＞「フォント情報」＞「インスタンス」で「Autohint」カスタムパラメータの値をオフにします。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-fonts-with-complex-outlines/af0117a245-1605628244/autohintingoff.png">

これまでに手動で設定されたヒントを削除するには、フォントビューで左下の隅にある歯車アイコンを押下して、「スマートフィルタを追加」を選択します。表示されたダイアログで、スマートフィルタに何か妥当な名前をつけ、「ヒンティングされている：はい」を設定します。「OK」を押下してダイアログを確定し左のサイドバーからスマートフィルタを選択します。そしてグリフを探してヒントを手動で削除します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-fonts-with-complex-outlines/54e0417f3c-1605628244/glyphswithhints.png">

もしくは、もっと簡単に、手動によるヒントを削除するスクリプトがあります。私の[GitHubのmekkablue Scriptsリポジトリ](https://github.com/mekkablue/Glyphs-Scripts/)の、「Hinting」＞「Delete all Hints in Font」、などなどです。インストール方法はリポジトリのreadmeに書かれています。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-fonts-with-complex-outlines/3b2b870441-1605628244/hintingscripts.png">

そうして完成したOpenTypeフォントにヒントが混入していないかを確かめるために、フォントをテストします。出力したOTFをGlyphsで開き、前の段落で説明したスマートフィルタを適用します。あるいは、[DTL OTMaster](http://fontmaster.nl)といったアプリでグリフを検査します。  

### パス

これまで複雑なパス、つまりノード数の多いパスについて説明しました。あなたは複雑なアウトラインをデザインし、局所的なフォント関係者の提案に沿ってサブルーチン化とヒンティングを無効にした、善良な市民であるとします。それでも、CFFベースのOTFでは**多数の小さな曲線セグメント**が問題になり得るので、まだ問題があるかもしれません。  

まず、そういうフォントは画面上では問題ないかもしれませんが、プリンタでは「サブパスが多すぎて」エラーになることがあります。ラスタライズの際に、それぞれの小さな曲線セグメントはたくさんの小さな線分、いわゆる「サブパス」と呼ばれるものに分割されます。これらは本当に小さいので、ラスタライズの解像度の閾値を大きく下回ってしまいます。レーザープリンタでは、この解像度は比較的高いかもしれませんが、足し合わされて完全な曲線セグメントへと置き換えられることになるサブパスは、非常に短く、もちろん、数も非常に多くなります。これは、たくさんのサブパスに分割された曲線セグメントを拡大したものです。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-fonts-with-complex-outlines/b3e7208123-1605628244/subpaths.png">

次に、そういうフォントをMicrosoft Windowsで扱うとパフォーマンスに問題が生じる可能性があります。例えば、6文字の単語を入力して、それから、文字が次々と現れるまで10秒とかそのくらい待つという感じです。そもそもWindowsはCFFアウトラインの扱いに問題を抱えていて、レドモンド（訳注：MS社の本拠地）からやって来た我々の善き友人たるOSにとって「複雑な」CFFはあまりにも遠い橋になりかねません。  

この問題を扱うには2つの方法があります。  

1つ目は、デザインに問題なければ、全ての曲線セグメントを線分に置き換えることです。この解決策の背景となる根拠とはレンダリングは曲線セグメントより線分の方がずっと容易であることです。  

これを行うプラグインがあります。Retractorです。「ウィンドウ」＞「プラグインマネージャ」から探し出してインストールしましょう。このプラグインは「フィルタ」カスタムパラメータを使えば出力時に自動で起動させられます（詳細は[フィルタのreadme](https://github.com/mekkablue/Retractor)を参照）。グランジフォント、滲みフォント、活版印刷フォントといった、非常に小さな曲線セグメントを持つフォントでは通常はこれを推奨します。  

アウトラインに大きめの曲線セグメントがある時は、全てを小さな線分へ置き換えるラフフィルタ（「フィルタ」＞「ラフ」）を使ってみてはいかがでしょうか。変位させる値は小さめか、おそらく0でも構いませんが、「セグメントのサイズ」は少しだけ大きくしましょう。このフィルタもまたカスタムパラメータによって起動させることができて、フィルタのウィンドウの左下の隅にある歯車アイコンからクリップボードにコピーし、「ファイル」＞「フォント情報」＞「インスタンス」で「カスタムパラメータ」テーブルにペーストすればOKです。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/creating-fonts-with-complex-outlines/fa378c1989-1605628244/roughen.png">

2つ目は、デザイン上曲線セグメントをきちんと保持する必要がある場合、フォントをTrueTypeアウトラインで出力することを検討してください。ここでの考え方は、実際はTrueTypeの方がCFF/PostScriptよりも複雑な処理をできるということです。フォントをTrueTypeで出力するには、「ファイル」＞「出力」＞で「True Type として保存」オプションをオンにするか、「ファイル」＞「フォント情報」＞「インスタンス」で「Save as TrueType」カスタムパラメータを使用します。簡単ですね。  
