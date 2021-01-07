# フォントの命名

[(Original page)](https://glyphsapp.com/learn/naming)  

<br />

by Rainer Erich Scheichelbauer  

<br />

12 November 2020  
Published on 31 August 2017  

********

フォント名は重要ですが、それはフォントのユーザへの表示方法で不可欠なフォントメニューのグループ化と表示順を決めるからです。フォントファミリーの命名は少し厄介ですが、以下のチュートリアルで紹介する最高のヒントはあなたは幸せにするでしょう。  

********


フォントの命名には良い慣例を取り入れることが大切です。フォント名がフォント内の6つの異なる場所に格納されていることがそれを難しくしています。または実際には、さらにもういくつかの場所に格納されます。そうなるとさらに複雑です。ご存知だとは思いますが、歴史的経緯です。  

うおお、そしてフォントの名前情報はアプリごとに違う方法で読み取られることになります。私たちは以下をベストプラクティスとして提案します。  

### ファミリー名とサブファミリー（スタイル）名

基本的に、同じ「ファミリー名」のフォントは、ユーザインターフェース内で何らかの形でグループ化されます。これをどう正確に行うかは、もちろん、フォントを扱うソフトウェアに依存します。「ファミリー名」は「ファイル」＞「フォント情報」＞「フォント」＞「名前」で設定できます。  

<img alt="" height="75%" src="https://glyphsapp.com/media/pages/learn/naming/ddd0cce358-1605628246/familyname.png" width="75%">

ファミリー内の個別のフォントは、サブファミリー名（別名：スタイル名）で区別する必要がありますが、これは「ファイル」＞「フォント情報」＞「出力スタイル」の「名前」フィールドで設定します。典型的なスタイル名は、「Regular」、「Italic」、「Bold」、「Medium」、「Light Italic」、「Display Bold」、「Caption Italic」などです。つまり、いくつかのキーワードの組み合わせです。  

* ウェイト： 「Thin」、「Light」、「Extralight」、「Regular」、「Medium」、「Semibold」、「Bold」、「Extrabold」、「Heavy」、「Black」、…
* 字幅： 「Compressed」、「Condensed」、「Extended」、「Expanded」、…
* 傾斜： 「Italic」、「Oblique」、「Upright Italic」、「Backslant」、…
* オプティカルサイズ： 「Display」、「Text」、「Caption」、「Small」、…

もちろん、どんなスタイル名でもOKです。自分のデザインに合っていれば「Felt Tip」や「Hatched」、「Outline」などお好きな名前をつけて構いません。名前にアクセント付きラテン文字が入っていても現在のソフトウェアならさほど問題はないはずです。  

デフォルトのファミリー名（「ファイル」＞「フォント情報」＞「フォント」＞「名前」で設定したもの）とは異なるファミリー名にしたいインスタンスがある場合は、インスタンスごとに「ファイル」＞「フォント情報」＞「出力スタイル」で一般のプロパティに「Family Names（ファミリー名）」を追加できます。  

そうすると、最終的には以下のようなネーミングとなるでしょう。  

| ファミリー名 | サブファミリー（スタイル）名 |
|--------------|------------------------------|
| MyFontFamily | Regular                      |
| MyFontFamily | Italic                       |
| MyFontFamily | Bold                         |
| MyFontFamily | Bold Italic                  |
| MyFontFamily | Semibold                     |
| MyFontFamily | Semibold Italic              |
| MyFontFamily | Black                        |
| MyFontFamily | Black Italic                 |
| MyFontFamily | Condensed                    |
| MyFontFamily | Condensed Italic             |
| MyFontFamily | Condensed Bold               |
| MyFontFamily | Condensed Bold Italic        |
| MyFontFamily | Condensed Semibold Italic    |
| MyFontFamily | Condensed Black              |
| MyFontFamily | Condensed Black Italic       |

### ローカル名

しかしながら、互換性を最大限確保するために、ファミリー名とスタイル名は素のASCII文字列の、短い、英単語にしておく方が良いです。これを飛び超えて、非ASCII文字列（例えば、日本語やアルメニア語、チェコ語など）を使いたい場合は、「ローカライズされた」名前を追加すると良いでしょう。  

ファミリー名をローカライズするには、「ファイル」＞「フォント情報」＞「フォント」に進み、「一般」セクションの＋アイコンを押下して一般のプロパティを追加し、ポップアップから「Family Names（ファミリー名）」を選択し、それから言語を選択して名前を設定します。  

<img alt="" height="75%" src="https://glyphsapp.com/media/pages/learn/naming/3cf25fefde-1605628246/localizedfamilyname.png" width="75%">

「一般」の横にある＋アイコンを押下して「Family Names（ファミリー名）」を追加します。削除するにはOptキーを長押しして項目の横に現れる−アイコンを押下します。  

デフォルトのファミリー名ではない名前で表示させたい言語ごとにエントリを追加します。選択できる言語が限られていますが、この仕様は遠い遠い昔に遥か彼方の銀河で書かれたものだからです。アイスランド語、アフリカーンス語、モンゴル語、マレー語、マケドニア語をサポートしていて、フラマン語とオランダ語の区別すらしているというのに、全ての言語のカバーはしていません。あなたに必要な言語がメニューにない場合は申し訳ありませんが、この件で私たちにできることはあまりありません。  

スタイル名をローカライズするには、「ファイル」＞「フォント情報」＞「出力スタイル」でそれぞれのインスタンスに一般プロパティ「Style Names（スタイル名）」を追加します。言語の追加は、「ファミリー名」の場合と全く同じです。そういえば、「出力インスタンス」の「ファミリー」名もローカライズ可能で、つまり、「ファイル」＞「フォント情報」＞「出力スタイル」＞「一般」から一般の設定の「Family Names（ファミリー名）」で行えます。これはいくつかのインスタンスでファミリー名をカスタムしており、それらもローカライズする必要がある場合に便利です。  

同時に、例えばデザイナー名や製造者名といった、その他多くのエントリもローカライズ可能です。どうやって？ もちろん、それぞれの一般プロパティからです。この例では「Designers（デザイナー）」と「Manufacturers（製造者）」です。追加した項目がローカライズ可能なものであれば、言語メニューが表示されフォントに必要な他言語のバリエーションをいつでも追加できます。  

### スタイルリンク

「スタイルリンク」という機能でそれぞれのフォントの間にファミリーの関係を設定できます。あるインスタンスを別のインスタンスの太字、イタリック、または太字イタリックなどとして定義できます。これは「ファイル」＞「フォント情報」＞「出力スタイル」の「スタイルリンク」セクションでとても簡単に行えます。やるべきことは、太字もしくはイタリックのチェックボックスをオンにして、関連するインスタンス名を入力するだけです。このように。  

<img alt="" height="75%" src="https://glyphsapp.com/media/pages/learn/naming/2d793bd018-1605628246/stylelinking.png" width="75%">

> ### Pro Tip
> スタイルリンクの入力欄には「Regular」は入力せずに単に空白のままにしておいて構いません。その場合にはGlyphsは「Regular」を想定します。エラーの原因が1つ減ります。  

スタイルリンクの設定で、いわゆる「RIBBIファミリー」を作成できます。RIBBIとは、**R**egular、**I**talic、**B**old、**B**old **I**talicの略です。ちょっと限定的ですが、その用途はOfficeソフトで太字やイタリックのボタンやキーボードショートカットを有効にすることです。これがうまくいけば、TextEditではCmd-Bでレギュラーとボールドの切り替えができますし、WindowsのWordではCtrl-Iで正体とイタリックの切り替えができます。ちなみに、Adobe InDesignでも同じ用途でCmd-Shift-BとCmd-Shift-Iが使えます。  

言い換えると、スタイルリンクの目的は4つのスタイル間を関係づけることだけで、それ以上ではありません。もう一つ考慮すべきことは、リンクされたスタイルはMicrosoft Officeのフォントメニューには表示されないということです。表示されるのはレギュラーのみで、リンクされたボールド、イタリック、ボールドイタリックのスタイルには、BボタンとIボタン（またはそれぞれのキーボードショートカット）のみからアクセスできます。そこでスタイルリンクには次のような戦略をお勧めします。  

* 「Bold」インスタンスに「『Regular』のボールド」を設定。
* 「Italic」インスタンスに「『Regular』のイタリック」を設定。
* 「Bold Italic」インスタンスに「Regular のボールド イタリック」を設定（注意：「『Bold』のイタリック」や「『Italic』のボールド」にはしない）。
* 他の全てのイタリック体には、それぞれの正体の「イタリック」を設定。例えば、「Semibold Italic」には「『Semibold』のイタリック」を設定。
* 残りの全ての正体では、設定は空白のままとする。

それで、全てがうまくいくと、フォントファミリーの設定は次のようになります。  

| ファミリー名 | サブファミリー（スタイル）名 | スタイルリンク                        |
|--------------|------------------------------|---------------------------------------|
| MyFontFamily | Regular                      | -                                     |
| MyFontFamily | Italic                       | Regular の「イタリック」              |
| MyFontFamily | Bold                         | Regular「のボールド」                 |
| MyFontFamily | Bold Italic                  | Regular「のボールド」「イタリック」   |
| MyFontFamily | Semibold                     | -                                     |
| MyFontFamily | Semibold Italic              | Semibold の「イタリック」             |
| MyFontFamily | Black                        | -                                     |
| MyFontFamily | Black Italic                 | Black の「イタリック」                |
| MyFontFamily | Condensed                    | -                                     |
| MyFontFamily | Condensed Italic             | Condensed の「イタリック」            |
| MyFontFamily | Condensed Bold               | Condensed「のボールド」               |
| MyFontFamily | Condensed Bold Italic        | Condensed「のボールド」「イタリック」 |
| MyFontFamily | Condensed Semibold           | -                                     |
| MyFontFamily | Condensed Semibold Italic    | Condensed Semibold の「イタリック」   |
| MyFontFamily | Condensed Black              | -                                     |
| MyFontFamily | Condensed Black Italic       | Condensed Black の「イタリック」      |

### WindowsおよびOffice向けのフォント命名

現在のMicrosoft Wordは「ファミリー名」と「サブファミリー（スタイル）名」、あるいは、存在するならば、「WWSファミリー名」と「WWSサブファミリー名」に注目しています。WWSとは**W**eight、**W**idth、**S**lopeの略です。  

> ### Good to know
> 技術文書では、「ファミリー名」と「サブファミリー（スタイル）名」は通常は Name ID 1 および Name ID 2 となっています。そしてWWS名は Name ID 21（WWSFamilyName）および Name ID 22（WWSSubfamilyName）として知られます。  
> 「Name ID」という用語は、コンパイルされたフォントファイルに名前情報を格納する方法である、OpenType Namingテーブルのエントリのことを指します。詳細は[Namingテーブルの仕様](https://www.microsoft.com/typography/otspec/name.htm)を参照してください。  

Microsoft社のフォントメニューは、ファミリーに存在するのがRegular、Bold、Italic、および Bold Italicのみ、つまり、上記のようにフォント間にRIBBIスタイルのスタイルリンクが設定されたモデルのフォントファミリーを想定しています。この4つから外れたスタイルはとにかく別のフォントファミリと考えなければなりません。そういうことで、マイクロソフト社は公式にこの命名法を推奨しています。  

| ファミリー名（ID 1）            | サブファミリー（スタイル）名（ID 2） |
|---------------------------------|--------------------------------------|
| MyFontFamily                    | Regular                              |
| MyFontFamily                    | Italic                               |
| MyFontFamily                    | Bold                                 |
| MyFontFamily                    | Bold Italic                          |
| MyFontFamily Semibold           | Regular                              |
| MyFontFamily Semibold           | Italic                               |
| MyFontFamily Black              | Regular                              |
| MyFontFamily Black              | Italic                               |
| MyFontFamily Condensed          | Regular                              |
| MyFontFamily Condensed          | Italic                               |
| MyFontFamily Condensed          | Bold                                 |
| MyFontFamily Condensed          | Bold Italic                          |
| MyFontFamily Condensed Semibold | Regular                              |
| MyFontFamily Condensed Semibold | Italic                               |
| MyFontFamily Condensed Black    | Regular                              |
| MyFontFamily Condensed Black    | Italic                               |

といった感じです。言い換えれば、「サブファミリー（スタイル）名」（ID 2）はRIBBIスタイルの内の1つにしかなれません。その他のウェイト、字幅、傾斜に関する情報は全て「ファミリー名」（ID 1）に入ります。これはもちろん、前のセクションの表から大きく異なることがわかります。この命名にはいくつか問題があります。扱いが難しいことです。「ファミリー名」パラメータをいくつもいくつも追加しなければならず、さらに悪いことには、スタイル名がほとんどが同じなので、「ファイル」＞「フォント情報」＞「出力スタイル」で見落としてしまうでしょう。また、Wordでは正しいかもしれませんが、DTPプログラムのような他のアプリにとっては理想的ではないかもしれません。  

でもちょっと待ってください……  

良いニュースがあります。**その必要はありません**。Glyphsがその処理を出力時に自動で行います。スタイルリンク情報に基づき、Name ID 1 と Name ID 2 はNamingテーブルの「Windows」の名前に沿って設定されます（そうです、Namingテーブルの情報は、Mac用と、Windows用に、2回保存されます。理由は聞かないでください）。
というわけで、複雑過ぎて理解できなくなるので、ここからは、デフォルトのファミリー名やスタイル名（フォント情報で入力したもの）をName IDで参照することはしません。  

何らかの理由で、この自動化がうまくいかなかった場合、つまり、WordのBボタンとIボタンで期待するスタイルになっていない場合は、「Style Map Family Names」という一般プロパティからスタイルのマッピングを制御できます。プロパティのポップアップに説明があるので引用します。  

> **Style Map Family Names：** 太字、イタリック、ボールドイタリックのスタイルマッピングで使うファミリー名。これにより大きなフォントファミリーの中にサブファミリーを作成できます。フォントファミリー名を共有して、フォントのスタイルリンクのグループを形成できます（レギュラー、イタリック、太字、ボールドイタリック：OS/2テーブル内のfsSelectionのビットの設定で定義される）。Glyphsは4つの個別のウェイトのリンクに、インスタンスの「Style Name（スタイル名）」フィールドと「スタイルリンク」セクションのエントリを使用します。  

繰り返しますが、この設定は必要ない可能性が高いし、名前をローカライズするならなお必要ないでしょう。しかし念のため。  

### WWS名：Name ID 21 と Name ID 22

次の場合は、Name ID 21 と Name ID 22 とも呼ばれる、WWS名「だけ」が必要です。  

* ファミリーに、ウェイト、字幅、傾斜「以外の」スタイルのバリエーションがある、つまり、そのフォントが非WWS軸を持つ場合。
* そして「その非WWS軸が非正規な値」を持つ、つまり、純粋にウェイト、字幅、傾斜だけでは表現できないスタイルのフォントである場合のみ。

ここでフォントファミリーに、「Subhead」や「Display」、「Caption」といったオプティカルサイズのバリエーションを追加するとします。上の表にあるフォントであれば新しい「オプティカルサイズ」軸は非正規な値ではないのでWWS名は必要ありません。しかし今追加する新しいフォントは、「オプティカルサイズ」軸で特殊な、非正規の位置にあるため、WWS名が必要となります。  

そしてこれを動作させるには「通常ではない名前の別のファミリー」を作成して、そのファミリー名を ID 21 に入れ、しかし「全ての太さ、字幅、傾斜の情報」は ID 22 に留めます。つまり、Name ID 22 はRIBBI名のみならず、「Medium Extended Italic」や「Bold Condensed Oblique」のように太さ、字幅、傾斜のカテゴリに該当する名前を「なんでも」扱います。  

| ファミリー名 | サブファミリー（スタイル）名   | WWSファミリー名（Name ID 21） | WWSサブファミリー名（Name ID 22） |
|--------------|--------------------------------|-------------------------------|-----------------------------------|
| MyFontFamily | Display Light                  | MyFontFamily Display          | Light                             |
| MyFontFamily | Display Light Italic           | MyFontFamily Display          | Light Italic                      |
| MyFontFamily | Display Medium Extended        | MyFontFamily Display          | Medium Extended                   |
| MyFontFamily | Display Medium Extended Italic | MyFontFamily Display          | Medium Extended Italic            |
| MyFontFamily | Display                        | MyFontFamily Display          | Regular                           |
| MyFontFamily | Display Italic                 | MyFontFamily Display          | Italic                            |
| MyFontFamily | Display Bold                   | MyFontFamily Display          | Bold                              |
| MyFontFamily | Display Bold Italic            | MyFontFamily Display          | Bold Italic                       |
| MyFontFamily | Display Semibold               | MyFontFamily Display          | Semibold                          |
| MyFontFamily | Display Semibold Italic        | MyFontFamily Display          | Semibold Italic                   |

これをGlyphsでどうやるかって？ 簡単です。「ファイル」＞「フォント情報」＞「出力スタイル」で、それぞれのフォントに適切なカスタムパラメータを追加します。WWSファミリー名には一般プロパティの「WWS Family Name（WWSファミリー名）」を使用し、WWSサブファミリー名には「WWS Subfamily Name（WWSサブファミリー名）」を追加します。ってこんなの誰が知るもんですか。  

**Note 1：** Name ID 21 および 22 に設定があるか否かと、OS/2テーブルのfsSelectionの8ビット目の状態は正確に対応していなくてはなりません。この意味がわからなくても、Glyphsはこれを自動で処理しますので、ご心配なく。  

**Note 2：** 「MyFontFamily Compressed」のように、スタイル名を純粋にWWSで表現できる場合、Name ID 21 と 22 は不要です。覚えてますよね？ しかし実際は、このfsSelectionのbit 8が設定されていれば、Name ID 21 と 22 の設定の有無は排除しない仕様になっています。なので暇があってその気になれば、これをどのフォントにも追加できます。しかし全く、こんな話はとっとと終わらせて、代わりにアイスを食べましょう。自分でfsSelectionの8ビット目を制御したい場合は、カスタムパラメータ「Has WWS Names」をインスタンスに追加してください。OpenType仕様によれば、このビットは「フォントが『name』ID 21 と 22 の使用を必要とすることなく、ウェイト／字幅／傾斜のファミリーに一致する『name』テーブルの文字列を持つ」ことを示しています。これはフォントの命名が「既にWWSスキームに沿っている」場合に「のみ」意味があることに留意してください。  

### Adobeメニュー向けのフォント命名

Adobeメニューではフォントはファミリー名に基づいてサブメニューに並べ替えられます。これは、非推奨の名前である「優先名」（Name ID 16 と 17）としても知られる「Typographic名」で上書きできます。そこでサブメニューの配置が気に入らない場合は、「Typographic Family Names」を使って独自のサブメニューを作り、残りの個別のフォント名を「Typographic Subfamily Names」に入れられます。どちらも一般プロパティから、「ファイル」＞「フォント情報」＞「出力スタイル」のウィンドウ右上の隅にある＋アイコンの押下によって追加できます。  

サブメニューの中では、フォントは次の順番で、並べ替えられます。  

1. 字幅クラス順
2. ウエイトクラス順
3. 傾斜（正体かイタリックか）
4. 最後に、スタイル名のアルファベット順

<img alt="" src="https://glyphsapp.com/media/pages/learn/naming/2b2bc97ab6-1605628246/adobemenuorder.png" width="80%">

「字幅」メニュー（1）で字幅クラスを、「ウェイト」メニュー（2）でウエイトクラスを、「イタリック」ボタン（3）で傾斜を、そしてもちろん、「スタイル名」（4）でアルファベット順を設定できます。  

> ### Hint
> （VistaまでのバージョンのWindows上の）古いバージョンのMS Officeは250未満のウェイトクラスのフォントを自動的に太らせていました。そのためウェイトクラス200のExtralightがウェイトクラス300のLightよりも太く見えるという奇妙な現象が起きることがあります。これを避けるには、最低のウェイトクラスを250以上にしてください。もちろん、Windows Vista以降の新しいバージョンのMS Officeを使うユーザだけを対象にする場合や、MS Officeを全く使わない場合は、これを無視して100から始めても構いません。しかし、TrueTypeフォントが「埋め込まれた」Wordファイルではまだ影響があるという報告を受けています。  

字幅とウェイトのクラスでさらに区別が必要な場合は（いくつかのオプションではメニューの右側に同じ値が表示されるため）、一般プロパティの「字幅クラス」と「ウエイトクラス」で順序の値を直接設定できます。例えば、レギュラー（400）とミディアム（500）の間に追加のウェイトが必要なら、「ウェイトクラス」に `450` と入力します。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/naming/f47d3e30a9-1605628246/custom-weightclass.png">

<img alt="" src="https://glyphsapp.com/custom-weightclass">

これはつまり何でも好きなようにできるということです！ 全てのフォントを同じサブメニューに入れたければ、全てのフォントで「Typographic Subfamily Names」を同じにすればよいのです。しかし、フォントを異なるサブメニューに配置したければ、同じくこのパラメータを異なるものにします。  

ただしこれらのパラメータを設定しなくてはならいのは「ファミリー名およびスタイル名のエントリと異なる場合」だけであることを忘れないでください。それ以外の場合は必要ありません。言い換えれば、優先名を使うのはファミリー名とスタイル名で設定したデフォルトを「上書き」するときだけです。そして言うまでもありませんが、同じ値で上書きしても意味はありません。  

> **例：** ウェイトと字幅の軸があるフォントファミリーを考えます。これには5つの字幅と9つの太さ、つまり計45個のフォントがあるとします。このときのサブメニューを想像してみてください……うへぇ。このとき2つの選択肢があります。  
> （A）45個のフォントを全て1つのメニューに入れておく場合。この場合は上記の設定から何も変更する必要はありません。おめでとう、これから飲みに行けます。  
> （B）フォントを字幅別の5つのサブメニューに入れる場合。そうすると、フォントメニューの項目は1つでは済まず5つに増えて乱雑になりますが、少なくともサブメニューの項目はそれぞれ9つずつで済みます。この場合は、「通常ではない」字幅の全てに「Typographic Subfamily Names」、例えば、「MyFont Compressed」、「MyFont Condensed」、「MyFont Semiextended」、「MyFont Extended」などを使うことになります。「通常の」字幅は、「通常の」ファミリー名「MyFont」で十分です。したがって、Typographic Subfamily Name（別名：優先名）は必要ありません。  

### Windows対Mac：フルネーム対Mac互換フルネーム

Windowsでは、例えばメニューなどで、フォントのフルネームの表示に Name ID 4（「Full Font Name」または「Full Name」）を使用します。通常のフルネームはファミリー名と、続けてスペース、さらに続けてサブファミリー（スタイル）名で構成されます。Glyphsもこの方法で ID 4 のエントリを自動生成しています。これを上書きするには「Name Table Entry」カスタムパラメータを使用します（後述）。ここまでは、順調です。  

Macも同じ目的で Name ID 4 を使用します。それは、フォントに Name ID 18（「Compatible Full Name」）が存在しない限りです。言い換えれば、何らかの理由から、Macのメニューに ID 4 での名前が表示されるのが耐えられない場合、「ファイル」＞「フォント情報」＞「出力スタイル」でインスタンスに「Compatible Full Names（Mac互換フルネーム）」という一般プロパティを追加すれば表示名を変えられます。  

言うまでもなく、これは本当に正当な理由がある場合にのみ行ってください。「Compatible Full Names（Mac互換フルネーム）」を使用すると、クロスプラットフォームでドキュメントの相互運用性が損なわれる可能性があります。警告しましたよ。  

### Compatible Name Table

nameテーブルのエントリが適切になるようにGlyphsは自動でうまくやりくりするので、出力フォントはAdobeアプリケーションや、同様にMac上のMicrosoft OfficeやCoreTextアプリでも最適に機能するということを上で申し上げました。ほとんどのアプリはこのやり方でカバーされます。  

しかしながら、時折、不満を持つカスタマーは現れるものです。特にQuark XPressやレガシーなバージョンのFontExplorerのユーザです。これらのアプリでフォントファミリーが正しくグループ化されないという苦情を受けた場合は、`Compatible Name Table` というカスタムパラメータを使用します。Glyphsはこれによってレガシースタイルのnameテーブルを出力します。  

このパラメータはQuark XPressとFontExplorerでフォントファミリーを適切にグループ化します。しかし、Microsoft Officeを含む他のアプリでは、ファミリーのグループ化を混乱させてしまいます。残念ですが、全部はフォローできません。  

### PostScript名

PostScript名はPostScript Type 1時代の遺産です。いくつかのアプリや、（特にPostScriptベースの）ファイルフォーマットの中には文書内に格納するフォント情報としてPostScript「フォント」名（nameテーブル ID 6 、最新バージョンの仕様では単に「PostScript Name」）を使用するものがあります。PostScript「Full」Name（nameテーブル ID 4 、現在の仕様では単に「Full Font Name」）は、人間の読者のみが対象です。繰り返しますが、両方ともGlyphsが自動的に設定しますので、単にアプリをいじくりまわすだけという理由ならほとんどの場合は何もしなくても問題ありません。自分で設定しなければならないよほどの理由がない限り、このチュートリアルの次の見出しまで読み飛ばして構いません。  

**PostScript「フォント」名**（「PostScript Name」、ID 6）は「ファイル」＞「フォント情報」＞「出力スタイル」の「Font Name（フォント名）」という一般プロパティで設定できます。これは2つの理由から厄介です。名前の長さと、文字種の制限です。技術的には、最大長は127文字で、これはほぼ全てのフォントで大丈夫なはずです。しかし、[Adobe Type Manager](http://www.adobe.com/products/atmlight.html)（ATM）のようなレガシーなソフトウェアの中には前半部分、つまり63文字までしか区別できないものがあります。つまり、2つのフォントでPostScriptフォント名の最初の63文字が同じだと、古いアプリでは区別されなかったり、誤動作が起きるかもしれません。良いニュースとしては、レガシーなソフトウェアを気にしないのであれば、この制限は無視して構いません。しかしレガシーなソフトウェアとの互換性を気にする場合、この制限はさらに過酷になる可能性があります。初期のPostScriptインタプリタは29文字まで（そう、29なんです）しか文字を保持できません。うげぇ。  

> ### Pro Tip
> 29文字の制限はEOTウェブフォントにも適用されます。EOTはとっくの昔に時代遅れのフォーマットとなっていますが、クライアントはInternet Explorer 6との互換性を主張するかもしれません。そのため、EOTを書き出していた場合は、PostScriptフォント名も設定し、それが29文字以内に収まるようにしておくと良いでしょう。  

文字種の制限ですが、PostScriptフォント名には、制御文字、スペース、PostScript言語で予約された `[](){}<>/%` の10文字を除いた、7ビットのASCIIコード「だけ」しか使うことができません。ハイフン `-` は、ファミリー名とサブファミリー（スタイル）名を繋ぐために予約されています。つまり、使えるのは以下の文字だけです。  

```language-plaintext
!"#$&'*+,-.0123456789:;=?@ABCDEFGHIJKLMNOPQRSTUVWXYZ\^_@abcdefghijklmnopqrstuvwxyz|~
```

どういうことかというと「MyFont Condensed Extrabold Italic」を「MyFont-CondensedExtraboldItalic」とすれば、文字長は31文字となります。ここであなたのクライアントから、文字数を29文字しか扱えない1988年のイメージセッターをサポートしなければならないという要求があったとしましょう。この長さ制限をクリアするには、スタイル名にあたる部分を「CdXBdIt」に省略します。完全なフォント名は、こうして、「MyFont-CdXBdIt」となって、14文字に収まりました。これで博物館に収蔵された機械の埃を払えるでしょう。  

アドビは[Tech Note #5088](http://wwwimages.adobe.com/content/dam/acom/en/devnet/font/pdfs/5088.FontNames.pdf)で、スタイル名の略語として以下を推奨しています。  

| 略語 | スタイル名                 |
|------|----------------------------|
|  Bd  | Bold                       |
|  Bk  | Book                       |
|  Blk | Black                      |
|  Cm  | Compressed                 |
|  Cn  | Condensed                  |
|  Ct  | Compact                    |
|  Dm  | Demi（接頭辞）             |
|  Ds  | Display                    |
|  Ex  | Extended                   |
|  Hv  | Heavy                      |
|  Ic  | Inclined                   |
|  It  | Italic                     |
|  Ks  | Kursiv（独語：イタリック） |
|  Lt  | Light                      |
|  Md  | Medium                     |
|  Nd  | Nord                       |
|  Nr  | Narrow                     |
|  Obl | Oblique                    |
|  Po  | Poster                     |
|  Rg  | Regular                    |
|  Sl  | Slanted                    |
|  Sm  | Semi（接頭辞）             |
|  Su  | Super                      |
|  Th  | Thin                       |
|  Ult | Ultra（接頭辞）            |
|  Up  | Upright                    |
|  X   | Extra（接頭辞）            |

<!--
「Nord」がどういう意味かなんて聞かないでください。私だって今まで見たことがありません。本当ですって。読む奴なんか居るかと思ってAdobe Tech Noteのライターが冗談で混入したのでしょう、多分。古き良き時代の窓のない後ろの部屋で、彼らはそういうことを面白がっていたに違いありません。  
-->

疑問に思われた方のために、「Nord」と「Nord Italic」とは[Roger Excoffon氏による有名な書体、Antique Olive](http://www.signes.org/set.php?id=551)ファミリーのウェイトとして1960年に最初に公開されました。幅広でとても太い断面です。これのデジタル版がAdobe Libraryにあったことから、Adobe社がまとめた際にリストに追加されました。私の知る限り、これが唯一の使用例です。  

そして**PostScript「フル」ネーム**（「Full Font Name」、ID 4）というのがありますが、これも「ファイル」＞「フォント情報」＞「出力スタイル」＞「一般」から一般プロパティ「Full Name（フルネーム）」で設定できます。これは、「ユーザ向け表示」を想定したフォントの「完全な名前」なので、人間にとっての読みやすさが鍵であり、スペースを含むことが許されます。Adobe社によれば、「フォントメニューでの表示に適した」名前でなくてはなりません。  

ということは書きたいように書いても完全に自由なんですね？ ……ええと、そうでもありません。Adobe Tech Note #5088によれば、一部のシステムは「ファミリーのグループに分類するため」にフォントのファミリー名とPostScriptフルネームを一致させるそうです。したがって、PostScriptフルネームはファミリー名から始まらなければなりません。PostScriptフルネームは「スタイル属性の追加によって完成します——一般的にはウェイト、字幅、傾斜、オプティカルサイズの順序で設定します」（Adobe Technote #5088）。例えば、「Bold Extended Italic Display」、「Medium Condensed Oblique Caption」、「Semibold Oblique」、「Compressed Poster」、「Light」などです。  

繰り返しますが、（PostScript）「Font Name（フォント名）」と「Full Name（フルネーム）」の設定は、本当にそうしたいという抑えきれない衝動に駆られ、設定できなければ暴走してしまう場合だけにしてください。そうでなければ、このことは忘れて、2つのPostScript名の設定はGlyphsに任せてください。いずれにせよこれらは簡単に生成できますので。  

### Nameテーブルのエントリ

もし自分のしていることが何か分かっていて、何も恐れるものがないのなら、nameテーブル全体を自分でも構築できます。ありとあらゆるプラットフォーム上で、ありとあらゆるエンコーディングをされた、ありとあらゆる言語用に、nameテーブルの各エントリを設定できます。やるべきことは、「ファイル」＞「フォント情報」＞「出力スタイル」でインスタンスを選択し、カスタムパラメータに「Name Table Entry」を追加して、その値に以下の構造体を1つ入力するだけです。  

`nameID; nameString`  
**例：** `4; MyFont Bold Italic` （Windows用の英語フルネーム）  

> ### Note
> バージョン2.5以前のGlyphsではnameテーブルのエントリでセミコロンの後にスペースが追加されてしまいます。このバグは修正されました。アプリの古いバージョンとの互換性を維持する必要がある場合は、スペースを除去してセミコロンの直後から名前を開始することをお勧めします。  

<br />

> この場合、`platformID` は 3（Windows）、続いて `encID` は 1（Unicode）、そして `langID` は 0x0049 （Windowsで英語）と想定されます。  

`nameID platformID; nameString`  
**例：** `4 1; MyFont Bold Italic` （Mac用の英語フルネーム）  

> `platformID` が 1（Mac）に指定された場合、`encID` と `langID` の両方は 0（MacRomanおよびMacで英語）と想定されます。  

`nameID platformID encID langID; nameString`  
**例：** `4 3 1 0x040C; MaPolice Gras Oblique` （Windows用のフランス語フルネーム）  

> `platformID` が 1（Mac）の場合、`encID` には 0 から 32 までの数値を、`langID` には 0 から 150 までの数値を指定できます（[Macintoshのプラットフォーム固有のエンコーディングIDと言語ID](https://www.microsoft.com/typography/otspec/name.htm#encLangIDs_platID1)を参照）。  
> `platformID` に 3（Windows）を指定した場合、`encID` は 0 から 10 までの数値に、`langID` は 0x8000 以下の16進数にしなければなりません （[Windowsのプラットフォーム固有のエンコーディングIDと言語ID](https://www.microsoft.com/typography/otspec/name.htm#encLangIDs_platID3)を参照）。  

`platformID` には、Macintoshの場合の 1、Windowsの場合の 3 のいづれかを指定できます。オプションである `encID` と `langID` は、`platformID` に応じた、WindowsまたはMacintoshのいづれかのエンコーディングIDと言語IDを表します。これらは0から65536までの数値でなければならず、10進数、8進数、または16進数で入力できます。AFDKO構文の仕様では「10進数は 0 以外の数字から始まり、8進数は数字の 0 から始まり、16進数は数字および16進文字の a〜f または A〜F に 0x の接頭辞がつかなければならない」と規定されています。  

ここだけの話、本当に重要なのはプラットフォームID 1 の「Macintosh」とプラットフォームID 3 の「Windows」の2つだけ、いや実際は、本当は、ID 3 の「Windows」だけです。他のプラットフォームID 0 の「Unicode」、ID 2 の「ISO」、ID 4 の「カスタム」は、全くではないにしろ、ほとんど使われません。そのうちの1つ、ID 2 の「ISO」は、公式に非推奨とすらなっています。それにしても、nameテーブルのエントリを自分自身で設定する場合、特に入力値が長くなるパラメータを選択する場合は用心してください。プラットフォーム別にエンコーディングIDと言語IDの途方もないリストがあります。もう、どこかへ召されそうになれますよ。あはは。ということで、これを本当に自身でやることになったなら、[Microsoft OT Spec. Microsoft OT Spec: The Naming Table](https://www.microsoft.com/typography/otspec/name.htm)のウェブページを何度も見に行くことになるでしょう。ここにはあなたのフォントオタク心が求めてやまない全てのエンコーディングIDと言語IDがリストアップされています。  

以下はアスタリスク付きを除いて、`<nameID>` で設定できるnameテーブルのエントリの簡単な表です。リンク先はMicrosoft社の仕様ページです。  

|                                                              nameID | 説明         |
|--------------------------------------------------------------------:|:-------------|
|   [ID 0](https://www.microsoft.com/typography/otspec/name.htm#nid0) | 著作権表示。 |
| * [ID 1](https://www.microsoft.com/typography/otspec/name.htm#nid1) | フォントのファミリー名。 |
| * [ID 2](https://www.microsoft.com/typography/otspec/name.htm#nid2) | フォントのサブファミリー名（別名：「スタイル名」）。 |
| * [ID 3](https://www.microsoft.com/typography/otspec/name.htm#nid3) | 一意のフォント識別子（別名：「Unique identifier string」）。アプリケーションはこれによってフォントを識別できます。ファミリ名とスタイル名、バージョン番号と作成年の組合せであることが多いです。 |
|   [ID 4](https://www.microsoft.com/typography/otspec/name.htm#nid4) | 完全なフォント名（別名：「PostScript Full Name」）。完全で固有な、人間が読めるフォント名。Windowsで使用されます。ファミリー名（ID 1）とスタイル名（ID 2）の間にワードスペースを挟んで組み合わせたものであることが多いです。 |
| * [ID 5](https://www.microsoft.com/typography/otspec/name.htm#nid5) | バージョン文字列。フォントベンダからのリリース情報とバージョン情報。通常は「Version」という単語の後にバージョン番号 x.xxx が続きます。「versionStringパラメーターでも設定可能です。」 |
| * [ID 6](https://www.microsoft.com/typography/otspec/name.htm#nid6) | フォントのPostScript名（別名：「PostScript Font Name」）。「postscriptFontNameパラメータでも設定可能です。」 |
|   [ID 7](https://www.microsoft.com/typography/otspec/name.htm#nid7) | 商標文字列。オプションですが、フォントを商標として登録した場合だけは必須です。 |
|   [ID 8](https://www.microsoft.com/typography/otspec/name.htm#nid8) | 製造者名。 |
|   [ID 9](https://www.microsoft.com/typography/otspec/name.htm#nid9) | デザイナー名。 |
| [ID 10](https://www.microsoft.com/typography/otspec/name.htm#nid10) | 説明。任意のテキスト。「改訂情報、推奨する使用法、履歴、フィーチャーなどを含めることができます。」 |
| [ID 11](https://www.microsoft.com/typography/otspec/name.htm#nid11) | ベンダのURL。URLプロトコル、つまり `http://` とかから始めるのを忘れずに。 |
| [ID 12](https://www.microsoft.com/typography/otspec/name.htm#nid12) | デザイナーのURL。URLプロトコル、つまり `http://` とかから始めるのを忘れずに。 |
| [ID 13](https://www.microsoft.com/typography/otspec/name.htm#nid13) | ライセンス説明。ユーザがフォントについて可能なこと不可能なことを1〜2文で要約したもの。例えば、インストール可能なデバイス数や再販不可など。 |
| [ID 14](https://www.microsoft.com/typography/otspec/name.htm#nid14) | ライセンス情報のURL。使用許諾契約書の全文を含むウェブページへのリンク。 |
| [ID 16](https://www.microsoft.com/typography/otspec/name.htm#nid16) | Typographicファミリー名（別名：「Preferred family name」）。ID 1 と異なる場合にのみ設定します。 |
| [ID 17](https://www.microsoft.com/typography/otspec/name.htm#nid17) | Typographicサブファミリー名（別名：「Preferred subfamily name」）。ID 2 と異なる場合にのみ設定します。 |
| [ID 18](https://www.microsoft.com/typography/otspec/name.htm#nid18) | Mac互換フルネーム。マッキントッシュのみ。ID 4 と異なる場合にのみ設定します。 |
| [ID 19](https://www.microsoft.com/typography/otspec/name.htm#nid19) | サンプルテキスト。一部のアプリでフォントのプレビューした時に表示されます。 |
| [ID 20](https://www.microsoft.com/typography/otspec/name.htm#nid20) | PostScript CID findfont名。公式には非推奨ですが、CJKフォントではまだ使用されています。 |
| [ID 21](https://www.microsoft.com/typography/otspec/name.htm#nid21) | WWSファミリー名。ID 16 および ID 17 のエントリがWWS形式に沿っていない場合（つまり、ID 17 のエントリにウェイト、字幅、傾斜以外の属性の修飾子が含まれる場合）に、WWSに準拠したファミリー名を設定するために使用します。 |
| [ID 22](https://www.microsoft.com/typography/otspec/name.htm#nid22) | WWSサブファミリー名。ID 21と併用され、ID 16 と ID 17 のエントリーがWWS形式に沿っていない場合にこのIDはWWSに沿った（ウェイト、字幅、傾斜の属性のみが記述される）サブファミリー名を提供します。 |
| [ID 23](https://www.microsoft.com/typography/otspec/name.htm#nid23) | 明るい背景パレット名。COLR/CMAPカラーフォント用に予約されています。 |
| [ID 24](https://www.microsoft.com/typography/otspec/name.htm#nid24) | 暗い背景パレット名。COLR/CMAPカラーフォント用に予約されています。< |
| [ID 25](https://www.microsoft.com/typography/otspec/name.htm#nid25) | PostScript名プレフィックスのバリエーション。バリアブルフォントにこれが存在すると、PostScript Name Generation for Variation Fontsアルゴリズムでファミリー名のプレフィックスとして使用されます。 |

これらのエントリのほとんどには、通常はUIのテキスト入力フィールドか、または専用のカスタムパラメータといったよりよい設定手段があります。もしこれをやる場合は、通常ではWindows用の名前のみを設定すれば回避できます。言い換えれば、パラメータ `<nameID>; <nameString>` の短縮形を使えば終わりです。  

繰り返しますが、これはGlyphsの生成するnameテーブルが何らかの理由でうまく機能しない場合と、自分が何をしているのか分かっている場合にのみ行ってください。やってみたいからというだけのために自分で設定すると、何かが壊れる可能性があります。  

<!---
### STATテーブル
フォント内のデータは全てフォントファイル内のテーブルに格納されますが、そのうちの1つにSTATと呼ばれるものがあります。STATとは「Style Attributes」の略で、バリアブルフォントには必須で、バリアブルではないフォントではオプションなOpenTypeテーブルの名前です。なので、フォントの将来性を考えるなら、STATテーブル（も）追加しておくのは良い考えです。Glyphsは、「ファイル」＞「フォント情報」＞「出力スタイル」の「Export STAT Table」カスタムパラメータでSTATテーブルをサポートしています。  

<img alt="" height="75%" src="https://glyphsapp.com/media/pages/learn/naming/eb8159fdb8-1605628246/exportstattable.png" width="75%">
--->

********

このチュートリアルの説明に多くの情報を提供してくれたMicrosoft社のRob McKaughan氏に感謝します。いくつかの文章はRobのものを直接引用しました。  

<br />

Update 2017-12-17: 誤記を訂正し、「preferredFamilyName」（Typographic Family Names）パラメータについての説明を追加。  
Update 2017-12-17: Antique Olive Nordについての段落を追加（Jean François Porchezさんありがとう！）。nameテーブルのエントリとEOTのPostScript名についていくつかの情報を追加（Phil Garnhamさんありがとう！）。  
Update 2018-07-05: 全てのName IDをパラメータで設定できるようになったため、「Name Table Entry」パラメータについての古い制限を削除。  
Update 2019-03-19: 誤記を訂正し、MaFonteをMaPoliceに、Mac RomanをMacRomanに置換（Nathalieさんありがとう）。  
Update 2019-11-14: 表現を最新の仕様に更新（Joachimさんありがとう）。  
Update 2020-11-13: Glyphs 3用に更新。  
