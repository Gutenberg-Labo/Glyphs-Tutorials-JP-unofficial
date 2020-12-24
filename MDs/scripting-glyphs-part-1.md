# Glyphsでスクリプト パート1

[(Original page)](https://glyphsapp.com/learn/scripting-glyphs-part-1)  

<br />

by Rafał Buchner & Rainer Scheichelbauer  

<br />

1 December 2020  
Published on 22 June 2012

********

Pythonのチュートリアル・第1回です。予備知識は必要ありません。この第1回目は、「マクロパネル」ウィンドウでの最初のステップです。

********

この複数回のチュートリアルで、Pythonを使い始めましょう。午前中に全部に目を通し、お昼を食べたら、その日の午後には初めてのスクリプトが書けます。楽しんでください！

### マクロパネル

メニューの「ウィンドウ」から「マクロパネル」（Opt-Cmd-M）を選択します。このようなウィンドウが現れます。

<img alt="" src="https://glyphsapp.com/media/pages/learn/scripting-glyphs-part-1/554ce0317a-1607121762/macrowidnow-0.png">

上半分はPythonのコードを記述する場所です。下半分でGlyphsがあなたのコードに反応して動作します。横方向の区切り線は好きな位置までドラッグできます。それでは、Glyphsが反応するコードを何か入力してみましょう。まずは上半分に次の行を入力してください。  

```language-python
print( "Hello World!" )
```

大文字／小文字の区別は重要なので、`Print` じゃなくて、`print` と書いてください。<br />
 `print` コマンドの後の開きカッコは極めて重要です。クォーテーションは本来のカーブしている引用符ではなくて、真っ直ぐなマヌケ引用符（タイポグラフィ的に言えば、これは本当はインチ記号）です。printとクォーテーションの間のスペースは必要ありませんが、閉じるクォーテーションは必要です。使うクォーテーションはシングルクォーテーション `'...'` でもダブルクォーテーション `"..."` でも構いません。  

実行ボタン（Cmd-Return、fn-Return、拡張キーボードではEnter）を押下すると、このような表示になるはずです。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/scripting-glyphs-part-1/e071fa1446-1607121762/macrowindow-1.png">

### 文字列、整数、不動小数点、オブジェクト

さて、Pythonの `print` コマンドは実行結果の領域に何かを出力します。このコマンドのカッコの中にあるものは何でも出力されます。テキストはクォーテーションで囲む必要があります。プログラマたちはこれを数字ではなくて文字列と呼びます。  

数字といえば、Pythonに任意の計算結果を出力させることもできます。Pythonは整数（「整数」）と小数（「不動小数点」）を区別して扱っていて、入力値が整数か小数かによって結果も同じように出力されます。5を2で割ると結果は2となりますが、5.0を2.0で割ると2.5となります。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/scripting-glyphs-part-1/c18e7c01e3-1607121762/macrowindow-2.png">

「実行」（Cmd-Return）を何度か押下していると、実行結果の領域はすぐに溢れかえってしまうでしょう。「消去」（Cmd-K）を押下して一掃してください。

### オブジェクト

さて、Pythonにちょっと他のものを表示させてみましょう。これを試してみてください。  

```language-python
print( Glyphs )
```

結果はそんなに驚くようなものではありません。しかしこの `Glyphs` は文字列でも数値の計算でもなく、オブジェクトと呼ばれるものです。さて、`Glyphs` というオブジェクトは他のサブオブジェクトを含んでいます。そうしたサブオブジェクトを参照するには、`Glyphs` にピリオドを付けてサブオブジェクトの名前を追加します。これを試してみてください。  

```language-python
print( Glyphs.fonts )
print( Glyphs.font )
```

するとPythonはカッコの中に現在開いているフォントのリストを出力し（ `print Glyphs.fonts` の結果）、加えて最前面のフォントを出力します（ `print Glyphs.font` の結果）。もしフォントを開いていなければ、空のリスト（中に何も入っていないカッコ）と `None` が結果として出力されます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/scripting-glyphs-part-1/ce67f5ad4c-1607121762/macrowidnow-3.png">

### リスト

フォントをいくつか開いてから、マクロパネルに戻って「消去」（Cmd-K）を押下し、もう一度「実行」（Cmd-Return）を押下します。別のフォントを前面に持ってきて再度コードを実行するとどうなるかを見てください。  

そんな感じで、「Glyphs.fonts」はフォントのリストを返します。リスト内のフォントを個別に参照するには、次のように、0から始まる数字を、ブラケットに入れて追加します。  

```language-python
print( Glyphs.fonts[0] ) # 1st open font, same as Glyphs.font
print( Glyphs.fonts[1] ) # 2nd open font
```

そうそう、ナンバーサイン `#` はコメントを表します。この後に続く文字はすべて無視されます。コードに説明のコメントを挿入しておくのは良いアイデアです。何年も後になってスクリプトを修正したり適応させようとするときに、自分のコメントに感謝することになります。本当ですよ。  

そして多分もうお気づきだと思いますが、`Glyphs.font` は `Glyphs.fonts[0]` のショートカットとして使えます。  

そしてご想像の通り、フォントにもサブオブジェクトがあります。それらもまた、ピリオドとオブジェクト名を追加することで参照できます。これを試してみてください。  

```language-python
print( Glyphs.font.glyphs )
```

グリフIDもしくはグリフ名をブラケットに入れて追加すれば、グリフを個別に参照できます。これを試してみてください。  

```language-python
print( Glyphs.font.glyphs[7] )
print( Glyphs.font.glyphs["a"] )
```

ここでも、ピリオドを追加すればグリフに含まれる情報をいくらでも参照できます。これを試してみてください。  

```language-python
print( Glyphs.font.glyphs["a"].name )
print( Glyphs.font.glyphs["a"].category )
print( Glyphs.font.glyphs["a"].subCategory )
print( Glyphs.font.glyphs["a"].unicode )
```

コピー＆ペーストが使えることは、覚えておいてください。行を毎回入力しなおす必要はありません。

### 変数

まあ確かに、グリフ情報を参照するのにこれはちょっと効率の悪いやり方です。b について同じ情報を得るために、4行に渡って a を b に変換しなければなりません。なので変数を導入します。  

```language-python
glyphname = "b"
print( Glyphs.font.glyphs[glyphname].name )
print( Glyphs.font.glyphs[glyphname].category )
print( Glyphs.font.glyphs[glyphname].subCategory )
print( Glyphs.font.glyphs[glyphname].unicode )
```

全ての情報を改行せずに1行にまとめるときは、printコマンドの終わりにコンマを打って `end=" "` を追加してください。  

```language-python
glyphname = "b"
print( Glyphs.font.glyphs[glyphname].name, end=" " )
print( Glyphs.font.glyphs[glyphname].category, end=" " )
print( Glyphs.font.glyphs[glyphname].subCategory, end=" " )
print( Glyphs.font.glyphs[glyphname].unicode end=" " )
```

さて、プログラミングとは全てを何度も再入力せずに済むようにすることです。繰り返しの作業はPythonに任せるべきです。全ての行に同じものが書かれていますよね？ それ用に別の変数を追加し、見やすいように空行を1つ追加します。  

```language-python
glyphname = "b"
myGlyph = Glyphs.font.glyphs[glyphname]

print( myGlyph.name, end=" " )
print( myGlyph.category, end=" " )
print( myGlyph.subCategory, end=" " )
print( myGlyph.unicode )
```

これで私たちが変更するのは1行目のグリフ名だけにできました。

### ループ処理

ところで例えば、フォント内のそれぞれのグリフの情報を得るには、どうすれば良いでしょうか？ 確かに、ブロック全体を何百回とコピー＆ペーストして全てのグリフ名を変更することはできます。でもそれはロボットではない人間にとっては飽き飽きする作業なので、Pythonにやらせてしまいましょう。  

```language-python
for myGlyph in Glyphs.font.glyphs:
    print( myGlyph.name, end=" " )
    print( myGlyph.category, end=" " )
    print( myGlyph.subCategory, end=" " )
    print( myGlyph.unicode )
```

`print` の行が全てインデントされていることに注意してください。行のインデントが全て同じになっている限り、ある個数のスペースやタブが使えます。Pythonはインデントの仕方がちょっとうるさいので、1つのスタイルを決めて「それにこだわって」ください。私はタブが好きなので、今後の例ではタブを使うことにします。  

Pythonは全てのグリフを1つずつ処理しては、その度にグリフ情報の行を表示します。はい！ これが、実際に使える、このチュートリアルの最初の成果です。例えば、これをコピーしてメールにペーストすればステータスレポートにすることができます。これをもう少し便利なものにするべく、`print` コマンドを1つだけ残してコードを2行にまとめましょう。  

```language-python
for myGlyph in Glyphs.font.glyphs:
    print( myGlyph.name, myGlyph.category, myGlyph.subCategory, myGlyph.unicode )
```

さて、開いている全てのフォントのグリフ情報のレポートを出しましょう。幸いにも、インデントは入れ子にできます。これでどうでしょう。  

```language-python
for myFont in Glyphs.fonts:
    print()
    print( "Report for:", myFont.familyName )
    for myGlyph in myFont.glyphs:
        print( myGlyph.name, myGlyph.category, myGlyph.subCategory, myGlyph.unicode )
```

レポートに別の情報を含めたいですか？ [Glyphs Python Documentation](http://docu.glyphsapp.com/#gsglyph "Glyphs.app Python Scripting API Documentation — Glyphs.app Python Scripting API 0.3 documentation")にアクセスし、他にどんなGlyphのオブジェクト（「GSGlyph」）やFontのオブジェクト（「GSFont」）があって何ができるか見てください。  

[パート2](https://glyphsapp.com/learn/scripting-glyphs-part-2)では、GSGlyphをもう少し深く、ノードの扱いまで掘り下げます。  

********

Update 2014-10-04: Glyphs.fontのショートカットと、パート2へのリンクを追加。  
Update 2015-07-30: スクリーンショットをGlyphs 2に更新。  
Update 2016-12-08: スクリーンショットを更新、書式を修正、Glyphs.currentDocumentをGlyphs.fontに差し替え。  
Update 2016-12-09: 最初の段落を追加。  
Update 2020-12-02: Python3に更新。
