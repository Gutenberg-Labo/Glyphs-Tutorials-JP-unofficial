# リガチャー（合字）

[(Original page)](https://glyphsapp.com/learn/ligatures)  

<br />

by Rainer Erich Scheichelbauer  

<br />

3 December 2020  
Published on 25 October 2012

********

リガチャーの作り方を知りたいですか？ 超簡単です。やってみましょう。

********

文字と文字がぶつかって見た目が悪くなるときがあります。後ろの文字まで届く小文字の f でよく起こります。l や b 、h のような、アセンダーのある文字とぶつかってしまうのです。となると書体デザイナーはリガチャーグリフの作成を決断することになります。

### リガチャーの作成

<p>小文字の f と小文字の h がぶつかり合うとします。</p>
<figure><img alt="" src="https://glyphsapp.com/media/pages/learn/ligatures/bb452c8657-1605628224/liga-1.png"></figure>
<p>いけませんね。そこで「グリフ」＞「グリフを追加...」を選択して `f_h` 、つまり、リガチャーの要素にあたるそれぞれのグリフ名をアンダースコアでつなげたものを入力します。Glyphsは `f` と `h` のコンポーネントからリガチャーを事前に用意します。</p>
<figure><img alt="" src="https://glyphsapp.com/media/pages/learn/ligatures/69d6031e0e-1605628224/liga-2.png"></figure>
<p>さて、これらのコンポーネントをそれぞれパスへ変換し、元の `f` や `h` へのリンクを削除します。これは「グリフ」メニューから「コンポーネントを分解」（Cmd-Shift-D）を選択すれば行えます。これでアウトラインが用意できました。</p>

> ### Pro Tip
> マルチプルマスターの場合、Optionキーを押すとメニューのコマンドが「グリフ」＞「全てのマスターでコンポーネントを分解」（Cmd-Opt-Shift-D）に変わります。

<img alt="" src="https://glyphsapp.com/media/pages/learn/ligatures/ac1bc0fae4-1605628224/liga-3.png">

アウトラインを好きなように編集できます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/ligatures/2515f3c07a-1605628224/liga-4.png">

はいはい、笑わないで。確かにリガチャーの作成はあまり得意じゃないですよ。そんなことより、とにかく、グリフの作成はこれで完了です。ところでグリフはどうやったら動作するのでしょうか？

### リガチャー用フィーチャーの作成

リガチャーはOpenTypeフィーチャーによって動作します。作成したリガチャーのグリフに適切な名前がついていたら、Glyphsはリガチャーを自動で作成します。「ファイル」＞「フォント情報」（Cmd-I）を開いて、「フィーチャー」タブに行き、左下にある「更新」ボタンを押下するだけです。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/ligatures/8def759af7-1607121762/features-updated.png">

そしてGlyphsは、多分数あるフィーチャーの中で、`dlig` というフィーチャーを生成します。これをクリックするとフィーチャーのコードが表示されます。  

```features-code
sub f h by f_h;
```

これはつまり、`f` – `h` と続く文字列をリガチャーグリフ `f_h` に置き換えることを意味します。正に私たちがやりたいことです。イェーイ！

### liga 対 dlig

でもちょっと待ってください。なぜ `dlig` なのでしょうか？ これは[任意のリガチャー（discretionary ligatures）](https://docs.microsoft.com/en-us/typography/opentype/spec/features_ae#dlig)の略で、このフィーチャーは「デフォルトでは無効」、つまりユーザが最初に有効にしなくてはならないということを意味します。  

デフォルトで有効にするには、`liga`（[通常のリガチャー（standard ligatures）](https://docs.microsoft.com/en-us/typography/opentype/spec/features_ko#liga)）というフィーチャーに含めます。一番良い方法はグリフ名に `.liga` というサフィックスを追加することです。今の例でいえば、リガチャーのグリフ名を `f_h.liga` に変更します。  

さあこの丸まった矢印のボタンを再び押しましょう。ご覧ください、`liga` フィーチャーにこの行が含まれました。  

```features-code
sub f h by f_h.liga;
```

そうです！ ちなみに、いくつかのリガチャーは即刻 `liga` に登録されるので、サフィックスは要りません。そういうリガチャーは次のもので全部です。  

```
fi
fl
f_f
f_f_i
f_f_l
```

`fi` と `fl` が上記の命名規則に従っていないことに気付かれたかもしれません。それはこれらが歴史的な例外だからです。この2つのグリフ名はOpenTypeのずっと以前から存在していました。やりたければグリフ名を `f_i` 、`f_l` にしても構いませんが、実際のところ、`.liga` サフィックスを付けないと `dlig` になってしまいます。

### リガチャーのテスト

実際に動作するかどうか試してみませんか？ 編集タブ（Cmd-T）を開き、リガチャーになる文字列を含む単語、例えば、今の場合なら「hifhum」と入力してください（この単語には意味はないと思いますが、もし意味があったなら、嫌な意味ではありませんように）。そしてウィンドウの左下の隅にある「フィーチャー」ボタンを押下して現れたポップアップメニューからリガチャーのフィーチャーを選択してください。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/ligatures/9f6a439b9a-1607121762/features-menu.png">

するとリガチャーが適用されます。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/ligatures/20d112b386-1605628224/liga-7.gif">

もしうまくいかなかったら、グリフ名が正しいことを確認してから「フォント情報」＞「フィーチャー」で「更新」ボタンを押すか、あるいは編集ビューのフィーチャーのポップアップメニューから「フィーチャーを更新」を選択するかして、フィーチャーのコードを再生成してみてください。  

さてさて、そんなところです。リガチャー作成を楽しんでください！  

********

Update 2016-02-19: スクリーンショットをGlyphs 2に更新。  
Update 2019-04-10: メニューの「レイヤー」を「グリフ」に変更。  
Update 2020-12-04: リンクとスクリーンショットを更新、Glyphs 3にマイナーチェンジ。
