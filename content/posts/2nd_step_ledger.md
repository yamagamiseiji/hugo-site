+++
title = "プレーンテキストファイルで「複式」家計簿（2）"
date = 2019-05-16T00:00:00+09:00
draft = false
+++

## はじめに {#はじめに}

 **`Ledger`** というプレーンテキストファイルに基づいて使える複式簿記、しかもコマンドラインで使える複式簿記がどれほど使い勝手が良いか、分かりやすくまとめようとしばらく試行錯誤していました。しかし、結局、体系的に良さを紹介するのはギブアップしました。ネット上には（英語が多いですが）たくさんの網羅的、体系的な紹介記事があります。それに対して屋上屋を架すのはむだだと悟りました。そこで、またまた申し訳ありませんが、備忘をかねて **ランダム** な小さな事例集というか、ちょっとした **カンニングペーパ** 風なメモにしました。


## トランザクション記帳について {#トランザクション記帳について}


### 日付けの手抜き入力 {#日付けの手抜き入力}


#### 毎回、2019/と西暦まで入力するのがうざい {#毎回-2019-と西暦まで入力するのがうざい}

次のように、第1行目に **`Y 2019`** とか書くと、西暦年の入力は不要になります：

```nil
Y 2019
05/01  * Petty Cash
	Expenses:Cash
	Assets:BKみずほ
```


#### 日付けの半自動入力 {#日付けの半自動入力}

けど、実際にはもっと便利な方法があります。

 **`C-c C-a`** でミニバッファに「Transaction: 2019/05/」が表示されます。
 **`RET`** すると、今日の日付けが自動的にjournalに書き込まれます。記帳したいトランザクションの日付けが今日でなければ、その日付けを手入力します。いずれの場合にも、日付け順にみてしかるべき場所に、新規トランザクションの種（日付けのみ）が記入されます。


### トランザクション名、アカウント名などの手抜き記帳 {#トランザクション名-アカウント名などの手抜き記帳}

 **`TAB`** などによる補完や入力修正機能を使うと、キーを叩く回数を節約できます。たとえば次のようなトランザクションを記帳したいとしましょう：

```nil
2019/05/16 Amazon
    Expenses:Grocery:Food
    Liabilities:VisaCard
```

必要なキー入力は：

```shell
C-c C-a RET am RET
TAB e TAB g TAB ESC RET
l TAB v TAB
```

**`RET,TAB,ESC`** 以外の一般文字キーで、入力したのは
**`am, e, g, l, v`** の6文字だけです。ボクがゆっくりタイプしても10秒程度で金額以外は記帳が終わります。

なお既存のjournalの中に頭文字が同じアカウント名やカテゴリ名があると、手数が増えます。なので、できるだけ最初の第1文字かせいぜい第2文字まででアカウント名などを同定・識別できるようなネーミングを考えておきましょう。（ファイル名を決める際に共通する一般教養ですがｗ）

もちろんトランザクション、アカウント名に日本語を使っていてもぜんぜん大丈夫。補完や修正は有効にはたらきますが、変換キーを叩かなければならないので、アルファベットだけよりは手数は増えます。


### コピペを活用 {#コピペを活用}

Journalには同じお店や支払先などからのトランザクションが繰り返しでてきます。その時には、コピー元となるトランザクションの上にカーソルを置いて、
 **`C-c C-k`** するとEmacsの下半分に次のようなカレンダーが表示されます。

<a id="orgbc783fa"></a>

{{< figure src="/emacs_calendar.png" caption="Figure 1: Emacs内に表示されるカレンダー" width="95%" >}}

その中から適当な日にちを選んでクリックします。日付けが選んだ日に変更された上で、
journal中の正しい日付け位置に複写されたトランザクションが挿入されます。そこで金額だけ修正すればおわり。（家計簿では、金額の修正も必要ないなことが多いのに驚いています）


## 絞り込みReportの表示 {#絞り込みreportの表示}


### よく使う絞り込み {#よく使う絞り込み}

簡単に絞り込みreportを表示する方法をメモしておきます。元帳ledgerファイルのデフォルト指定は終わっているという前提です。指定が終わっていない場合には、ledgerコマンドの後ろに「-f hogehoge.ledger」を追加してください。


#### クルマ関係経費だけ表示 {#クルマ関係経費だけ表示}

```shell
$ ledger b cars
```

**`b`** は **`balance`** の略です。上のように、carsと小文字にしても、大文字になっているCarsも拾ってくれます。


#### クルマ、食費、教養娯楽の経費の表示 {#クルマ-食費-教養娯楽の経費の表示}

```shell
$ ledger b cars food 娯楽
```

並べて書いた経費カテゴリの「すべて」についてのバランスが表示されます。


#### 上の経費からケーブルTV（など）を除外した表示 {#上の経費からケーブルtv-など-を除外した表示}

```shell
$ ledger b cars food 娯楽 and not TV
```

カテゴリ名にTVを含む経費は除外して表示します。


#### 昨日の食費の表示 {#昨日の食費の表示}

```shell
$ ledger b -p yesterday
```

**`-p`** は **`--period`** の略です。「yesterday」と指定しただけでOKなのがクールですｗ


#### この１か月のクルマ関係経費の表示 {#この１か月のクルマ関係経費の表示}

```shell
$ ledger b cars -p this momth
```

これで、この1ヶ月間のクルマ関係経費になります。
yesterday, this monthの他、次のような期間指定が可能です（詳しくはマニュアルを参照してください）：

```example
october
oct
this week(day, month, quarter, year)
next week
last week
;
monthly
monthly in 2004
weekly from oct
weekly from last month
from sep to oct
from 10/1 to 10/5
monthly until 2005
from apr
until nov
last oct
weekly last august
```


#### もっとこまかく期間を限定して経費を表示 {#もっとこまかく期間を限定して経費を表示}

```shell
$ ledger b cars -b 04/01 -e 04/20
```

この例では、04/01から06/30までの期間におけるクルマ関係経費を表示します。
 **`-b`** は **`-begin=*、 *`-e=** は **`-end`** の略です。


### Register report {#register-report}

ここまでのreportではすべて、バランス（残高）の金額だけが表示されます。例えば、上の最後の例（＝期間限定のクルマ関係経費バランス）では次のような結果になります：

```nil
$ ledger b cars -b 04/01 -e 04/20
	  30,890 JPY  Expenses:Cars
	  15,530 JPY    ガソリン
	   2,700 JPY    整備
	  12,660 JPY    通行料金
--------------------
	  30,890 JPY
```

この「b」を「r」にするだけで、バランス金額だけでなく、各トランザクションの日付や支出先などの詳細レポートが表示されます：

```nil
$ led r cars -b 04/01 -e 04/20

19-Apr-04 ENEOS SS       Expenses:Cars:ガソリン    7,374 JPY   7,374 JPY
19-Apr-11 沼田往復        Expenses:Cars:通行料金   10,640 JP   18,014 JPY
19-Apr-15 シェル石油      Expenses:Cars:ガソリン    8,156 JP   26,170 JPY
19-Apr-17 大師往復        Expenses:Cars:通行料金    2,020 JPY  28,190 JPY
19-Apr-18 ENEOS SS       Expense:Cars:整備         2,700 JPY  30,890 JPY
```


### その他いろいろ {#その他いろいろ}


#### トランザクション名での絞り込み {#トランザクション名での絞り込み}

```shell
$ ledger -r @starbacks
```

アカウント名ではなくて、特定のトランザクション（取引）先の名前で整理したいことがあります。上の例のように **`@`** （atのつもりですねｗ）をつけるとスタバでの支出のレポートを得ることができます。


#### クレカ名での絞り込み {#クレカ名での絞り込み}

あるクレジットカードでどれ位の支出をしたか、これは頻繁にチェックしますね。たとえばVisaCardでの支出をみたければ：

```shell
$ ledger r visa
```

期間指定をしなければ、びっくりするほどの行数（と金額）が表示されます。それだけ支出したってことですので、反省材料になります。もちろん、合計金額だけでよければ：

```shell
$ ledger b visa
```

これでVisaCardについての「Liabilities」（負債）の金額が表示されます。


#### 手元にいくら残っているかしら？ {#手元にいくら残っているかしら}

```shell
$ ledger b -e 05/20 ^Assets ^Liabilities --invert
```

過去のある年月日における純資産（的な）ものをチェックできます。はたして家計簿で何の意味があるかよく分かりませんがｗ


## 使い勝手について {#使い勝手について}


### セキュリティとの関連で {#セキュリティとの関連で}

Ledgerプログラムには、 **クラウド** 対応機能が内蔵されていない点が不満であるとの意見があります。けれども仕訳帳journalデータをクラウドに上げておけば、いつでもどこでも瞬時に記帳や編集、レポート作成ができます。しかし、一般のクラウドサービスに上げておいて、万が一データが流出したら、家計簿といえどもちょっとマズイ。企業会計でそれが起こったらただじゃあ済まないと思います。

そこで、journalデータを **gpg** で **暗号化** してからクラウドに上げることにしました。これで、必要に応じて、暗号化されたファイルを手元のPCにダウンロードし、それを復号化して記帳、編集、レポートを作成することが可能となります。データのセキュリティと使い勝手がほどよくバランスしたと思います。


### レポートの可視化について {#レポートの可視化について}

多くの家計簿・会計ソフトでは、見た目も華やかなグラフ出力が標準的についてきます。それに比べると、Ledgerはとてもプアｗ　というかほぼゼロです。

Ledgerでも、どうしてもやりたければ、 **gnuplot** と連携できます。gnuplotですよ！個人的には長い付き合いがあるし、自然に使えるという意味ではとても好感度高く、学生言葉で言えば「萌えます」。　しかし、もともと配布されている限りでは、Ledger内のgnuplotグラフはぜんぜん美しくないです。

けど、家計簿で可視化して見なければならないこと、または他人にプレゼンして理解してもらわなければならないことがあるかしら？と考えてみると、あまり思いつきません。会社の経理とは異なり、家計は固定費が大きく、変動する部分が小さいので、変動部分だけを数値で見れば済む感じ。ただ、株式とか投資信託とか金とかプラチナとか（w）を保有していて、その資産状態を日々、チェックする（という趣味）をお持ちの方は、変動を可視化して「ふむふむ」と満足したり、「あらら」と心配したりするには可視化の機能がもっと充実が望ましいでしょう。


#### CSVの入出力について {#csvの入出力について}

上の可視化問題とも関連しますが、LedgerはCSVとの親和性がとても高いです。
CSVを経由して他の会計ソフトや描画機能と連携することでたいがいの問題は解消するように思われます。この点については、後日ということで・・・


## Acknowledgment {#acknowledgment}