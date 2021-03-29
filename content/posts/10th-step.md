+++
title = "プレーンテキストファイルで「複式」家計簿（10）"
date = 2019-12-03T21:05:00+09:00
draft = false
+++

今回をもって、とりあえずシリーズ的なイントロ的投稿は **打ち止め** にします。今後は、これまで以上にトピックベースの **ショート・ショート** 形式での記事にします。


## 帳簿の厳密さ・細かさについて {#帳簿の厳密さ-細かさについて}

このシリーズの [(3)](http://org2-wp.kgt-yamy.tk/2019/06/07/post-686/)で、小額キャッシュの扱いについて、「あまり細かいことはさておいて大雑把に行きましょう」という風な記述をしました。現在は、この考え方はかなり変わってきています。

帳簿の **細かさ** に関する自分自身の考え方を次のような5段階で評価するとしたら、かつては「やや大雑把 **2**.」でしたが、現時点では「やや細かい **4**.」から「とても細かい **5**. 」の中間、数値で言うと **4.5** でしょうか。

{{< figure src="/framed-scale.jpg" >}}


### そのきっかけは {#そのきっかけは}

かなり以前になりますが、Ledger-cliと複式簿記に関するネット上の記事を渉猟していて、偶然どこかのサイトで帳簿の細かさに関する議論を読みました。

そこで書かれていたことは、欧米ユーザの **大雑把派** と **細かい派** によるそれぞれの立場の主張のぶつけあい。なかなかおもしろかったのですが、その議論のなかで **細かい派** の投稿中に **「著名な誰それ」** （＝投稿中には当然、実名が書いてありました）ならば1セントの誤差もないように帳簿を付けるだろう、という風な言い回しがありました。

最近になって、その **「著名な誰それ」** が誰だったかを思い出そうとして、ネット上でいろいろと検索をし再発見を試みましたが見つからない（涙）。ぼんやりとした記憶で、苗字の頭文字に **B** があったような気がして、たとえばBaconについて調べたり・・・。この２、３か月間、無駄に時間を浪費していました。

ところがあるとき、フト、もしかしたら **苗字** じゃなくてファーストネームだったかも？と思い、B、B、Bとアタマの中でぐるぐる考えていたら、突然 **Benjamin?** がひらめきました！　あ、ベンジャミン・フランクリンかも？！　さっそくフランクリンの自伝をキンドルで取り寄せて確認しました。間違いありません！ **ベンジャミン・フランクリン** でした！


### で、フランクリンですが・・・ {#で-フランクリンですが}

カミナリが電気であることを実験で実証したことで有名な他、米国合衆国憲法の起草者のひとりだとか、実に広範囲な領域で１８世紀に大活躍した歴史上のビッグネーム。アメリカの最高額のお札（100ドル札）の人物といえば、あーぁ、あの顔ね！と、知らない人はいないほどの超有名人です。

{{< figure src="/oval-franklin.jpg" caption="Figure 1: ベンジャミン・フランクリン（1706〜90年）" width="90%" >}}

\#ベンジャミンの写真（100ドル札）

つまりネット上のフォーラムでの **細かい派** の発言（まだその記事は再発見できていません）はベンジャミンフランクリンの

```text
A penny saved is a penny earned.
```

という言葉や、彼がとても細かく会計帳簿をつけていたことなどを念頭において書かれたもの、つまり会計帳簿では **１セント** といえどもないがしろにすべきではないという主張ですね。以前にこのシリーズ[(4)](http://org2-wp.kgt-yamy.tk/2019/07/27/post-754/)で紹介した **「帳簿の世界史」** の中でも「ベンジャミン・フランクリンの会計術」という節が設けられていて、フランクリンが複式簿記の **使い手** だったことが紹介されています。

きちんとした帳簿を大事にする考え方はじつは彼ひとりのものではなく、同時代のジョージ・ワシントン（1732〜99年）の書いた細かい帳簿がワシントン大統領図書館2013（バージニア州マウントバーノンMount Vernon）に残されているそうです。

＜参考URL＞
<https://note.mu/filius/n/n890c7ca90781>

<https://current.ndl.go.jp/e1499>


#### 翻ってわが国を見ると（涙） {#翻ってわが国を見ると-涙}

わが国では、政府や議会、地方自治体、あるいはある種の **政治屋** は民衆から吸い上げた税金に関わる **記録** や **金銭** の扱いが実にずさんですよね。われわれ庶民や私企業には小うるさいことを言うくせに、中央政府は、帳簿や明細書などの記録やデータを常識では考えられないレベルで無法な扱いをしています。ここ数年、そうした事例が次から次へと白日のもとにさらされています。 **前近代的** というよりも **旧石器時代** 以前というべき情けない状況。

これども、公的なお金の使い方のデタラメさに心底 **憤慨** している自分がいる一方で、さて自分に関わる経理になると、かなり大雑把で使途不明な支出があっても割に平気で笑ってすごしています。金銭について細かいことを言うのは **男子の美学** に反するといった思いがどこかにあるのかも知れません。しかし考えてみれば、これはひどい話です。公と私で、これほどに乖離した意見や態度を持つのは、根本的な人格統合性の欠如、支離滅裂の状態だと思います。

このことに気づき反省をしたこともあって、最近になってお金のフローはできるだけ細かくトラッキングすべきという考えに変わってきた次第です。


#### ところで脇道にそれますが・・・ {#ところで脇道にそれますが}

さてこの一件で思い出したのは、大学と大学院時代を通しての恩師＝ **八木冕先生** （1915〜1988）のこと。学部で心理学を専攻することを決めたのは２年生の秋に八木先生のガイダンスを受けたからです。いまでも駒場の教室での先生のガイダンスをありありと思い出せます。またその後、大学に職を得ることができたのも先生のお陰だと思っています。

さて学生または院生時代（1972年前後）、先生のお名前の **冕（べん）** の文字が珍しいので、先生にその意味や由来を直接お伺いしたことがあります。その時の先生のご説明：

```text
「冕」とは冠（かんむり）のことである
親が、人の上にたつような立派な人間になるようにと選んだ
それに加えて、ベンジャミンにあやかってBenという音を選んだ
```

八木先生のお父様の世代の時代背景を考えると、このベンジャミンはほぼ間違いなく **ベンジャミン・フランクリン** だと思います。まさかこんな風に巡り巡ってベンジャミン・フランクリンがボクの眼前に現れるとは、 **まことに人生というものは不思議なものです** 。


## ということで、今回のTips＆Hints {#ということで-今回のtips-hints}


### 領収書・請求書などへのリンク {#領収書-請求書などへのリンク}

わが国でも「 **電子帳簿保存法** （1988年施行）」の制定・改定によって、すべての領収書を電子化して保存することが可能となりました。2017年には、スマホやデジカメで撮影した領収書やレシートも電子保存できるようになりました。

これで、制度的には大小を問わずすべての事業者、それから政治団体などの収支のトラッキングと事後の検証がとても簡単にできるようになりました。にもかかわらず、領収書を何らかの形で保存することを **義務化** しようとしないのはまったく不思議ですね。

さてLedger-cliでも、最近の多くの会計ソフトと同じように各トランザクションごとに、その元となる証憑書類をPDFなどの画像ファイルにして「添付」できます。Ledgerの場合には厳密に「添付」と言えるかどうか微妙ですが、書類をスキャンし **画像ファイル** にして保存し、そのファイルへのパスを **コメント** として記入することで、「添付」と同等の機能を実現できます。

たとえばレシートをDropbox上に保存する場合には、次のようにそのURLを書いておきます：

```nil
2019/11/22 * セブンイレブン
    ; https://www.dropbox.com/preview/hogehoge/receipts/sample.pdf?role=personal
    Expenses:飲み物                           150 JPY
    Assets:nanaco
```

では実際にレシート画像を見るときにはどうするか？

当面は、 `M-x org-mode` でORGモードにしてURLをクリックすることにします。そうするとEmacs内の別窓にレシートが表示されます。ローカルなファイルとして保存した場合には：

```nil
; [[file:~/ledger-directory/receipt/sample.pdf]]
```

これでORGモードにしてクリック＆ビューが可能です。なお、Ledger-modeにしたままでも、URLクリック＆ビューができるらしいですが、それは後日ということで・・・。

レシートのURLやファイル名・パスなどを書いたコメントに次のようにtagをつけておくと、後日、検索をする時に便利です：

```nil
; :receipts:   [[file:~/ledger-directory/receipt/sample.pdf]]
```

こうしておいて、 `led p %receipt` すれば、ファイル保存されているレシートとトランザクションが抽出できます。

政治家の政治資金など税金を使う仕事や、事業をしている場合には、上の例のような150円などという小額のレシートはもちろん、たとえ１円のレシートでもちゃんと保管すべきだと思います。

市井の一市民の家計簿ではさすがにそこまでは不要。 **大きな買い物** をして、しばらくの間、証憑書類として領収書を保存しておきたいような場合に限って保存・記録したらよいと思います。


### プリペイドカードと商品券（ギフト券）のトラッキングについて {#プリペイドカードと商品券-ギフト券-のトラッキングについて}

**プリペイドカード** も **商品券** （ギフト券）もいわば小額のキャッシュのような側面があります。これらをきちんとトラッキングするのはベンジャミン・フランクリン的には意味のあることだと思います（笑）


### プリペイドカード {#プリペイドカード}

これはとても簡単。 `Assets:プリペイドカード` アカウントの下に個別のプリペイドカード名をぶら下げます。わたしの場合には `Kuroneko` 、 `Suica` それから `nanaco` を設け、 `Suica` の下には自分用（me）と妻用（wife）アカウントを用意しています：

```nil
$ led bal プリカ --empty
	  10,235 JPY  Assets:プリペイドカード
	   2,300 JPY    Kuroneko
	   3,701 JPY    Suica
		   0      me
	   1,168 JPY      wife
	   3,066 JPY    nanaco
--------------------
	  10,235 JPY
```

balレポートに `--empty` オプションを付けているので、残高ゼロのmeのsuicaもリストされています。

このシリーズ [(9)](http://org2-wp.kgt-yamy.tk/2019/10/04/post-826/) でパソリを使って **suica** を読み取る方法を紹介しましたが、その後、読み取ったデータをCSVファイルにして見やすく表示するスクリプトの整備が終わり、現在とても便利に使っています。それらについては別の機会に紹介することにします。


### 商品券（ギフト券） {#商品券-ギフト券}

最初に現在手持ちの商品券の残高を **期首残高** （Opening Balance）として登録します。商品券も `Assets:商品券` アカウントの配下に次のようにアカウントを作っていきます：

```nil
2019/10/01 * Opening Balance
    ;  商品券
    Assets:商品券:デパート	 20,000 JPY
    Assets:商品券:VisaGift	 20,000 JPY
    Assets:商品券:JTB旅行券	100,000 JPY
    Assets:商品券:Premium	      0 JPY
    Assets:商品券:QUOカード	      0 JPY
    Equity:Opening Balance
```


#### 商品券を入手した際の転記 {#商品券を入手した際の転記}

商品券の入手方法や経路はさまざまです。考え始めるときりがありませんが、主な類型を次に例示します。

<!--list-separator-->

-  ケース１＝ギフトでもらった

    一番多いのは商品券を **ギフト** としてもらうというケースでしょう。たとえばカーディーラーからもらったQUOカードは：

    ```nil
    2019/11/10  QUOカード
        Assets:商品券:QUOカード	500 JPY
        Income:神奈川スバル		-500 JPY
    ```

    これは簡単ですね。

<!--list-separator-->

-  ケース２＝自費でカードを購入する

    逆に、QUOカードを自費で購入する際にはちょっと面倒です。QUOカードの場合には、3,000円以上の **高額カード** は額面と購入価格の間に差額がないので簡単ですけれど、額面が3,000円未満のカードでは、購入価格は **額面プラスアルファ** になります。たとえば500円カードは530円になります。これの転記例は：

    ```nil
    2019/11/01  QUOカード購入先
        Assets:商品券:QUOカード	500 JPY
        Expenses:商品券差損		30 JPY
        Assets:Cash			-530 JPY
    ```

    ここでは、 `Expenses:商品券差損` というアカウントに差額を収納しています。

<!--list-separator-->

-  ケース３＝「プレミアム付き商品券」

    **消費税増税** 対策の一つとして「プレミアム付き商品券」が2019年10月1日から入手できるようになりました。プレミアム賞品券は、額面25,000円の商品券を20,000円で購入できます。

    **差額の5,000円** がどこから来るのか本当のところは知りませんが（ウソです。知ってます。ボクラの税金ですｗ）とりあえず発行元が市町村になっているので、次のように転記できます：

    ```nil
    2019/11/03  プレミアム商品券購入
       Assets:商品券:Premium    25000 JPY
       Income:横浜市            -5000 JPY
       Assets:Cash             -20000 JPY
    ```


#### 商品券を利用したショッピングの転記 {#商品券を利用したショッピングの転記}

多くの商品券はキャッシュと同じように扱えます。けれどもプレミアム商品券は **お釣りをもらえない** というちょっと変わった決まりです。そんなプレミアム商品券の使用形態ごとの転記法の例は次のとおりです：

```nil
2019/11/11  商品券使用-1
    ;　おつりなし　過不足なく商品券のみ使用
    Expenses:Food		1500 JPY
    Assets:商品券:Premium

2019/11/12  商品券使用-2
    ;　おつりなし　キャッシュとの合わせ技
    Expenses:Food		1800 JPY
    Assets:商品券:Premium	-1000 JPY
    Assets:Cash			-800 JPY

2019/11/13  商品券使用-3
    ; おつりを貰わず、損する買い物をした
    Expenses:Food		2880 JPY
    Expenses:商品券差損		120 JPY
    Assets:商品券:Premium	-3000 JPY
```

上のケース３でも `Expenses:商品券差損` への収納を使うことになります。このアカウントを使うことで「 **雑費** 」に落としこまずに済みます。


#### 商品券使用のトラッキング {#商品券使用のトラッキング}

買い物ごとに使用された **商品券額** のレポートは次のようにします：

```nil
$ led reg 商品券:premium -b 11/10
2019/11/12 そうてつローゼン	Assets:商品券:Premium	-2,000 JPY	-2,000 JPY
2019/11/13 FoodShow		Assets:商品券:Premium	-1,000 JPY	-3,000 JPY
2019/11/14 イトーヨーカドー	Assets:商品券:Premium	-500 JPY	-3,500 JPY
```

商品券を使った買い物の **全額** をレポートするには次のようにします：

```nil
$ led reg ^expenses and expr 'any(account =~ /assets:商品券/)' -b 11/10 -S date
2019/11/12 そうてつローゼン    Expenses:Grocery:YOK      2,284 JPY   2,284 JPY
2019/11/13 FoodShow           Expenses:交際費:Gifts     1,080 JPY    3,364 JPY
2019/11/14 イトーヨーカドー    Expenses:交際費:Gifts       620 JPY    3,984 JPY
```

これくらいまで商品券をトラッキングができれば、「 **雑収入** 」に格納するよりはすっきりしていると思います。


### まとめ {#まとめ}


#### 「まま子三兄弟」 {#まま子三兄弟}

**プリペイドカード** と **商品券（ギフト券）** それから、前にこのシリーズで紹介した **ポイント**&nbsp;[^fn:1] 、この３つは **一部の** 経理の世界ではどちらかと言うと **まま子扱い** されています。まま子という言葉が **PC** 的に良くない言葉だとすれば、 **庶子扱い** でしょうか（笑）。

けれどもこの先、これら三兄弟が支出に占めるウエイトはどんどん大きくなってくると思います。とくに家計や小規模ビジネスの経理においては、これらをひっくるめて **「雑」** アカウントに収納するのはちょっと **大雑把** すぎ。失われる情報が大きすぎると思います。この三兄弟をきちんとトラッキングすると **心理的** にすっきりするだけでなく、経理への **不確定要素の混入** を小さくできると思います。


#### Penny talks {#penny-talks}

この年になってようやく、遅ればせながらpennyを軽んじないことの重要性を日々感じています。Pennyを大事にすることを通して経理の信頼性が高まる、またpennyをおろそかにしないためには、その前提として証憑書類の完全な保存と管理が必要です。

中世にベネチアで生まれた複式簿記は、その根底にある **ドライでクール** な思想が、極東の島国日本に来て **湿気と高温** に溶かされて「明細書はない」とか「参加者名簿は廃棄した」とかになってしまったのでしょうか。だとしたら、今日の日本国政府の信じられない **ずさん** さは、もしかしたらボクら一般市民の日常思考の深い淵に深く根を張っているのかもしれません。


## Acknowledgement {#acknowledgement}

[^fn:1]: ポイントのトラッキング このシリーズ[(8)](http://org2-wp.kgt-yamy.tk/2019/09/16/post-811/) でETCのトラッキング、[(9)](http://org2-wp.kgt-yamy.tk/2019/10/04/post-826/) ではキャッシュレス還元の例を上げました。ちなみに、現在トラッキングしているポイントは次のとおりです： ```nil $ led bal point --empty -X JPY 8,743 JPY Assets:Reward Points 4,388 JPY ANA 0 ETC 685 JPY キャッシュレス還元 4,170 JPY ヨドバシ -------------------- 8,743 JPY ```