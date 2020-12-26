# Glyphsでスクリプト・3

[(Original page)](https://glyphsapp.com/learn/scripting-glyphs-part-3)  

<br />

by Rafał Buchner & Rainer Scheichelbauer  

<br />

1 December 2020  
Published on 17 July 2012  

********

オブジェクトモデルを理解したので、オリジナルのスクリプトで「スクリプト」メニューを拡張できます。  

********

このチュートリアルは、最初に[Glyphsでスクリプト・1](./scripting-glyphs-part-1.md")と[Glyphsでスクリプト・2](./scripting-glyphs-part-2.md)を読み終わっていることが前提です。  

Glyphsのメニューバーに「スクリプト」というメニューがあることに気がついているかもしれません。書いたスクリプトをこのメニュー内に配置しましょう。まずは、良いテキストエディタが必要です。個人的には、コーディングをとても楽しく簡単にする特別な機能を持った、[TextMate](http://macromates.com/)（60ドル）と[SublimeText](https://www.sublimetext.com)（80ドル）の2つが好きです。ベテランのMacユーザなら[BBEdit](https://www.barebones.com/products/bbedit/index.html)（50ドル）、[Smultron](https://www.peterborgapps.com/smultron/)（15ドル）、[Coda](https://www.panic.com/coda/buy.html)（100ドル）も好きでしょう。このうちのどれかにライセンス料をお支払い済みかもしれませんが、もしそうなら、Pythonのコーディングでもそのエディタをあっさり続けて使えます。でも予算が限られているとか、今はコーディングをいくつか試すだけで買うかどうかは後から決めたいのであれば、無料の[TextWrangler](http://www.barebones.com/products/TextWrangler/)、[SubEthaEdit](https://subethaedit.net)、[Atom](https://atom.io)、または最近非常に人気のある[Visual Studio Code](https://code.visualstudio.com/)を使ってもよいでしょう。  

どのエディタを使うにしても、Cmd-Nを押下して新しいドキュメントを作成し、次のフォルダに保存します。  

`~/Library/Application Support/Glyphs/Scripts/`  

チルダ（ `~` ）はホームフォルダを表します。ヒント：保存ダイアログで、Cmd-Shift-Gを押して「フォルダの場所を入力」機能を呼び出して、上の行をペーストします。[前回](./scripting-glyphs-part-2.md)書いたPythonのコードを立派なスクリプトにするために、ファイル名は `Glyph Shaker.py` などにしてください。そうです、末尾を `.py` にするとPythonスクリプトになります。それでは、コーディングに進みましょう……  

最初の一歩です。メニュータイトルを入力し、ファイルのエンコーディングを宣言し、簡単な説明を追加するところから始めます。  

```language-python
#MenuTitle: Glyph Shaker
__doc__="""
Goes through all selected glyphs and slaps each of their nodes around a bit.
"""
```

Pythonではコメントはナンバーサイン（ `#` ）から始まるので、最初の行は実際にはコメントです。しかしながら、Glyphsは `#MenuTitle:` から始まるコメントを「スクリプト」メニューに載せる名前として解釈します。スクリプト内にそういうコメントがない場合、代わりにファイル名が使われます。しかし、今回のスクリプトは「スクリプト」メニューで「Glyph Shaker」として表示されます。  

2行目もまたコメントですが、今度は、この行を読み込むのはPythonで、つまり `.py` ファイルの文字エンコーディングです。何かしらの考えがあって、意図している場合を除いて、常にUTF-8を選んでください。  

その次の行は、`__doc__` という特殊な変数の宣言です。これはいわゆる「docstring（ドキュメンテーション文字列）」と呼ばれるもので、Pythonオブジェクトや、または、今の場合ではスクリプトについての、短い説明文のテキストを格納します。3個並んだクォーテーションは複数行の文字列を表すので、必要に応じていくつかの段落に及ぶ説明文を追加できます。このdocstringは、Glyphsの「スクリプト」メニューのプルダウンで、スクリプト名にマウスポインタが置かれたときに表示される、ツールのTipに使用されます。  

それでは、[前回と同じく](./scripting-glyphs-part-2.md)乱数生成機能を呼び出さなくてはなりません。  

```language-python
import random
random.seed()
```

それから現在選択している全てのレイヤーを取得して、`selectedLayers` 変数に取り込みます（全ての文字の全てのレイヤー／マスターと混ざらないように、実際に見ているものだけにします）。こうなります。  

```language-python
selectedLayers = Glyphs.font.selectedLayers
```

これで、`selectedLayers` で、それぞれのレイヤーのそれぞれのパスのそれぞれのノードを当り、`-50` から `50` の間のランダムな量を動かせるようになりました。  

```language-python
for thisLayer in selectedLayers:
    for thisPath in thisLayer.paths:
        for thisNode in thisPath.nodes:
            thisNode.x += random.randint( -50, 50 )
```

全てうまくできたら、おおよそこんな感じになっているはずです。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/scripting-glyphs-part-3/8df07cdaed-1605628219/glyphshaker-new.png">

以上です。スクリプトを保存し、Glyphsに戻って「スクリプト」メニューを見てみましょう。……なんてこった？！ Glyph Shakerスクリプトがありません！ というのはまずGlyphsにScriptsフォルダを再スキャンするよう指示する必要があったからです。次のようにします。メニューを開けているときに「Option」キーを押すと、「Scripts フォルダを開く」という項目が「スクリプトメニューを更新」に変わります。それをしたら、`#MenuTitle:` の後に指定した名前でスクリプトが表示されます。  

さあ、大っ嫌いなフォントを開いて、憎き文字どもを選択し、「スクリプト」メニューから「Glyph Shaker」を選択すれば、ようやくそいつらに相応しい打撃を与えられます。Cmd-Opt-Rのショートカットを使って何度も何度も連打しましょう。これでも喰らえ、ヘルベチカめ！  

お疲れ様です。コーヒーとアイスクリームで休憩しましょう。そして次のステップに進む準備ができたら、[第4回・Pythonのイントロダクション](https://glyphsapp.com/learn/scripting-glyphs-part-4)に進みましょう。  

********

Update 2014-10-04: エンコードの行を追加、docstringの説明を更新。  
Update 2016-12-08: スクリーンショットを修正（Friedrich Althausenさんありがとう）  
Update 2017-05-24: 第4回への言及を追加。  
Update 2018-12-26: テキストエディタへのリンクをさらに追加。  
Update 2020-12-02: Python3に更新。  
