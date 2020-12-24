# Glyphsのダウンロード／更新ができない時

[(Original page)](https://glyphsapp.com/learn/cannot-download-or-update-glyphs)  

<br />

by Rainer Erich Scheichelbauer  

<br />

15 December 2020  
Published on 26 March 2020

********

Safari でアクセスできませんか？ サイトが開きませんか？ Glyphsの更新ができませんか？ 「ウィンドウ」＞「プラグインマネージャー」が真っ白なままですか？ ここでは再びダウンロード出来るように、その対策を説明します。

********

### URLから直接ダウンロード

アプリはupdatesサーバからダウンロードできます。

* Glyphs 3: <https://updates.glyphsapp.com/latest3.php>
* Glyphs 2: <https://updates.glyphsapp.com/latest2.php>
* Glyphs Mini 2: <https://updates.glyphsapp.com/latestMini2.php>

このURLを直接試してみてください。もしダウンロードできず、ブラウザにエラーメッセージが表示された場合は、以下の手順を実行して下さい。

### 破損したhostsファイルの修正

過去にあったケースでは、アプリの更新やダウンロードができなかった時に一番よくある原因は、「hostsデータベース」ファイルの破損です。詳しく言うと、それは `/etc/hosts/` 内にあるテキストファイルなのですが、いくつかの悪い「ヘルパー」ツールがこれをいじってしまうことがあります。これを修正するには、単純にTerminal.appで次のコマンドを実行します。パスワードを聞かれたら入力してください。  

```command
sudo sed -i '' '/glyphsapp/d' /etc/hosts
```

Terminal.appを触るのは不安で、どうしたらいいかわからないという方のために、手をお貸しします。以下の手順に従ってください。

<ol>
<li>
上記の行を選択してクリップボードにコピー（Cmd-C）します。
</li>
<li>
Terminal.appを立ち上げ、必要であれば新しいタブを開きます（Cmd-T）。
<ul>
<li>
Terminal.appの場所がわからない場合、Spotlight検索を開き（キーボードショートカットを変更していなければ、デフォルトではCmd-Space）、<code>term</code> …と入力してリターンキーを押します。
</li>
</ul>
</li>
<li>先ほどコピーした行をTerminal.appにペーストします。すると次のようになるはずです（あなたの場合は「mekkablue」ではなくて、あなた自身のユーザアカウント名が表示されます）。<br />
<img alt="" src="https://glyphsapp.com/media/pages/learn/cannot-download-or-update-glyphs/cbeee89f97-1605628254/terminal-sed-1.png">
</li>
<li>リターンキーを押して入力を確定すると、こんな感じでパスワード入力を求められます。<br />
<img alt="" src="https://glyphsapp.com/media/pages/learn/cannot-download-or-update-glyphs/bf127700a3-1605628254/terminal-sed-2.png">
</li>
<li>
そこでMacのログインパスワードを入力します。<strong>注意：他の場所でパスワードを入力したとき表示される中黒の点々（•••）はここでは表示されません。それでOKです。</strong>ターミナルでパスワードを入力する時はそうなっている、それだけです。パスワードは「何も見えずに」入力しなければなりません。つまり、これまでにキーを何回押したかはわからないまま、リターンキーを押して確定してください。
</li>
<li>
入力が全て正しく行われたら、処理が静かに行われ、ターミナルは次のコマンド待ちの状態になります。<br />
<img alt="" src="https://glyphsapp.com/media/pages/learn/cannot-download-or-update-glyphs/752e370c2b-1605628254/terminal-sed-3.png">
</li>
</ol>

この後は、ログアウトして再びログインするか、あるいはMacを再起動してください。  

<img alt="" src="https://glyphsapp.com/media/pages/learn/cannot-download-or-update-glyphs/9f0d323213-1608562153/restart.png">

うまくいったでしょうか？ おめでとうございます。これでGlyphsをエンジョイできます。なお、「ヘルパー」ツールについては次のセクションを参照してください。

### 「ヘルパー」アプリの削除

システムメンテナンスツールとか、システムオプティマイザーとか、ウイルス対策アプリとか使っていませんか？ たとえば、Avastとか、CleanMyMacとか、MacCleanerとか？  

**アンインストールしてください。**  

いや、本当に。こいつらを消して。  

これらの「ツール」のほとんどは、Macには完全に無用の長物です。実際のところ、これらのほとんどは「マルウェアそのもの」です。もちろん、この種のソフトウェアのベンダーたちは、あなたを怖がらせ、ありとあらゆる嘘を並べては驚かせて、そのツールであなたのMacを「保護」します。その戯言を真に受けてはいけません。それどころか、真実は、Macにはウイルスは存在しないし、macOSは自己防衛機能を持った非常に優れたオペレーティングシステムです。ヘルパーやオプティマイザー、メモリクリーナーなんて、他人が売りつけようとしているものは一切必要ありません。「一切」です。  

言うまでもなく、マルウェアのベンダーたちは、今述べたことは「神話」だと主張するでしょう。だまされないでください。Macでこういったツールの使用が役に立つなんてシナリオは私には考えられません。私からのアドバイスはこれらの全てのメンテナンスツールやウイルス対策アプリを削除すること。こいつらにできるのは台無しにすることくらいです。  

いつもの原因たちです。

* **CleanMyMac**：Glyphsをぶち壊すことがわかっています。こいつはアプリを「管理」するふりをする機能を持っていますが、実際にはアプリの機能を台無しにして破壊します。CleanMyMacをアンインストールして、Macを再起動し、Glyphsを再ダウンロードして再インストールしてください。
* **Avast**（または他の同じようなMac用ウイルス対策アプリ）：私が「これまで」見た限り、こいつはMacの動作を遅くし、時には極端に遅くして、毎回の動作ごとにカーソルを回転ビーチボールにしやがります。ウイルスを検出したり脅威を「ブロックした」とか表示するので、このソフトを使うと安心できる気がしますが、そんなのナンセンスです。Avastをアンインストールして、Macを再起動し、Glyphsを再ダウンロードして再インストールしてください。
* **MacCleaner**：ド直球のマルウェアで、インターネット接続を乗っ取っておのれらの広告ページにリダイレクトします。控えめに言って邪悪だと思います。Macを再び完全に機能させるには、こんな奴は駆除して、Macを再起動し、Glyphsを再ダウンロードして再インストールしてください。
* **Little Snitch**：本当はマルウェアではありません。しかし扱い方を知らないと、同じく動作を台無しにしてしまう可能性があります。Glyphs.appからの接続と、`updates.glyphsapp.com` および `glyphsapp.com` への接続を「すべて許可」にしてください。使い方がわからなければ、Little Snitchはアンインストールして、Macを再起動し、Glyphsを再ダウンロードして再インストールしてください。

大事なことなので2回言います。これらのアプリは使い続けると、問題が発生「します」。こいつらを消してくれないと私たちはあなたを助けられません。マジで。  

ほんと毒舌でごめんなさい。

### インターネット接続の確認

そうです。インターネット接続を確認しましょう。

* ウェブサイトはまだ開けますか？
* 他のサイトから他のアプリやzipファイルをダウンロードできますか？

この質問のどちらかが「いいえ」なら、別の方法でネットに接続してください。現在の接続が不十分か、特定のファイル形式のダウンロードがブロックされています。  
両方の質問に「はい」なら、次の質問をご確認ください。

* 同じMacの別のユーザアカウントではアプリをダウンロードできますか？

もし「はい」なら、ユーザ設定に何か問題があります。ブラウザの設定の削除を検討してください。Shiftキーを押したまま再起動してキャッシュをリセットし、それからキーを何も押さずに再起動することを検討してください。  
これに「いいえ」なら、次の質問です。

* 別のMacではアプリをダウンロードできますか？

「はい」の場合、お使いのMacの設定に問題があります。最初の手順のhostsファイルの修正は行いましたか？ それをもう一度やってみてください。Macの再起動を忘れないでくださいね。それでもうまくいかなかったなら、次にいきましょう。

### DNSサーバの不良

再起動しても、まだうまくいきませんか？ DNSサーバーを `1.1.1.1` か、 `8.8.8.8` あるいは `8.8.4.4` に変更して、もう一度試してみてください。やり方は次の通りです。

1. 「システム環境設定」を開きます。
2. 「システム環境設定」の、「ネットワーク」を開きます。
3. 「ネットワーク」で、右下にある「詳細」ボタンをクリックします。
4. 現れたダイアログシートで、上部にある「DNS」というタブを選択します。
5. 「DNSサーバ」と書かれたフィールドの下にある「＋ボタン」をクリックします。
6. エントリに `1.1.1.1` を追加し、リターンキーを押して確定します。
7. OKボタンを押してダイアログシートを確定します。
8. 環境設定の画面に戻り、「適用」をクリックします。

<img alt="" src="https://glyphsapp.com/media/pages/learn/cannot-download-or-update-glyphs/b15b4e201e-1605628253/dns-server.png">

これでうまくいくか試してみてください。うまくいかなかったら、Macを再起動してみてください。それでもうまくいかないときは、同じ手順をもう一度行いますが、ステップ6で代わりに `8.8.8.8` または `8.8.4.4` を使用してください。そしてもう一度、Macを再起動してみてください。

> 背景情報：[1.1.1.1 の裏話](https://blog.cloudflare.com/announcing-1111/)と
[GoogleのDNSサーバ・8.8.8.8 と 8.8.4.4 について](https://developers.google.com/speed/public-dns)はこちらをご覧ください。

### フォーラムへの報告

ここまでやってもうまくいかなかった場合、それは本当に、本当にレアケースです。お疲れ様です。Terminal.appで次のコマンドを実行し、その結果を[フォーラム](https://forum.glyphsapp.com)へ報告してください。

```command
ping -o updates.glyphsapp.com
dig updates.glyphsapp.com
curl -I https://updates.glyphsapp.com/
```

> ヒント：3行すべてを一度にコピー（Cmd-C）して、Terminal.appに切り替え、新しいTerminalタブ（Cmd-T）にペースト（Cmd-V）して、リターンキーを押し、終わるまで数秒待ってから、全選択（Cmd-A）して、内容をフォーラムの新規投稿にコピペすればOKです。入力欄のコードオプションで書式を整えてください。そうしていただけたら読みやすいです。

そうしたら助けに行きます。macOSのバージョン（Sierra？ High Sierra？ Mojave？ Catalina？）とお使いのハードウェア（iMacか、MacBookかなど）の情報もお忘れなく。  

参考までに、結果はこのような感じになるはずです。</p>

```language-shell
mekkabook-air:~ mekka$     ping -o updates.glyphsapp.com

PING updates.glyphsapp.com (172.104.142.40): 56 data bytes
64 bytes from 172.104.142.40: icmp_seq=0 ttl=51 time=25.713 ms
--- updates.glyphsapp.com ping statistics ---
1 packets transmitted, 1 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 25.713/25.713/25.713/0.000 ms

mekkabook-air:~ mekka$     dig updates.glyphsapp.com

; <<>> DiG 9.10.6 <<>> updates.glyphsapp.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 8784
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;updates.glyphsapp.com.     IN  A

;; ANSWER SECTION:
updates.glyphsapp.com.  3521    IN  A   172.104.142.40

;; Query time: 182 msec
;; SERVER: 83.169.184.33#53(83.169.184.33)
;; WHEN: Thu Mar 26 22:33:23 CET 2020
;; MSG SIZE  rcvd: 66

mekkabook-air:~ mekka$     curl -I https://updates.glyphsapp.com/

HTTP/2 403
server: nginx
date: Thu, 26 Mar 2020 21:33:23 GMT
content-type: text/html; charset=utf-8
content-length: 162
strict-transport-security: max-age=15768000; includeSubDomains; preload;
x-frame-options: SAMEORIGIN
x-content-type-options: nosniff
x-xss-protection: 1; mode=block

mekkabook-air:~ mekka$
```

いくつかの単語は違うはずですが（特に日付、時刻、マシン名、ログイン名）、それ以外の部分は大体同じになるはずです。あなたの結果と比較するとすでに手掛かりがあるかもしれません。しかしフォーラムで見てみましょう。そこでお手伝いいたします。  

********

Update 2020-04-02: 細かい文法を修正、DNSのスクリーンショットを追加、DNSサーバに関する背景情報のリンクを追加。  
Update 2020-07-29: 最初の段落にプラグインマネージャーへの言及と、Glyphs Miniタグを追加。  
Update 2020-12-16: Glyphs 3のリンクを追加、マイナーチェンジ。
