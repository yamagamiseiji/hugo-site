+++
title = "Give me a break!"
date = 2020-04-22T10:21:00+09:00
draft = false
+++

新型コロナによってたくさんの国民の **生命財産** が脅威にさらされています。それに対するわが国政府の対応はあまりにもひどい。腹立たしくも情けなく恥ずかしい思いで、日々ストレスが溜まっています。国民から巻き上げた **税金** をどうして国民のために使えないのか。もういい加減にして欲しい！ **'Give me a break !'** と叫びたい気持ちです。

**税金** といえば、4月に入ってから **Ledger-cli** と **gnuplot** で3月までの1年間に納税した税金の取りまとめをしました。「租税公課」の金額そのものはLedgerで簡単に獲得できますが、それを表にして見るだけでなく、月ごとの納税額の推移を可視化しました。それ自体はそんなに複雑な作業ではありません。

しかし一つ問題があります。納税金額は **月ごとの変動** がとても大きい。たとえば、100万円を超える月がある一方、別の月は数万円レベルとかゼロ円ということもありえます（ヒトそれぞれですが・・・）。こんな風に極端な **外れ値** を含むデータを「見える化」するのはちょっとやっかいです。

よく見かけるのは、棒グラフに **波線** などを入れてY軸を **中断** する方法。グラフを途中でカットする線は日本語では「中略波線」とか「省略線」、「中断線」とか言うようですが、サイエンスの世界ではそれを使ってグラフを描くことは禁忌になっています。その他、ドーナツチャート（円グラフ）も避けるべきとされます。グラフの原点をゼロ以外の数値にしないようにという指導もされます。経理・会計の世界とサイエンスの世界とでは図に求められるものが異なっているようです。

ところで、この **中断線** は英語では **break** といいます。途中でカットされた棒グラフは **histogram with break** でしょうか。

コロナへの政府の対応に憤慨して **give me a break!** って叫ぶ感じで、この際、禁断の **breakつき棒グラフ** を描いてみようと思い、やってみました。くれぐれも良い子は真似をしないでくださいね（笑）


### Y軸にbreakを入れてみる {#y軸にbreakを入れてみる}

こんな感じになります（金額はでたらめです）。

<a id="org1f4a511"></a>

{{< figure src="/broken-histogram.png" caption="Figure 1: Breakを入れた棒グラフの例（納税額の推移）" width="90%" >}}

Ledgerとgnuplotを組み合わせて図[1](#org1f4a511)のような **break** つき棒グラフを描く方法を紹介します。


#### Ledger-cliのクエリー {#ledger-cliのクエリー}

税額の計算をするためのLedgerクエリーは次のとおりです。

```nil
ledger reg --amount-data --collapse --monthly  ^expenses and %tax
```

ここで、 **`%tax`** は税金に関係するトランザクションにつけた **タグ** です。税金にはさまざまな名前がついています。計算の際に、それらを洩れなくすくい上げるために、記帳の段階で全て `tax` というタグをつけてあります。

オプションの意味は次のとおりです。（ ）内は短縮形です。

`--amount-data (-j)`
: 個々のトランザクションの日付と合計金額だけを出力

`--collapse (-n)`
: トップレベルのアカウントだけを出力

`--monthly (-M)`
: 月ごとにまとめて出力

このクエリーによって得られるデータの例（数値はデタラメです）：

```nil
　：
2020-01-01 7234
2020-02-01 4567
2020-03-01 8901
2020-04-01 98760
```

これをファイルに格納してgnuplotに読み込ませます。


#### gnuplotスクリプト {#gnuplotスクリプト}

**break** つきのヒストグラムはmultiplotを使って描きます。
[こちらのサイト](https://stackoverflow.com/questions/17564497/gnuplot-break-y-axis-in-two-parts)のスクリプトを参考にさせていただきました。

<!--list-separator-->

-  ターミナルと出力ファイルの指定

    出力図はPDFにして `$out_file` に出力します。

    ```nil
    set terminal pdfcairo transparent enhanced font 'Arial,10'
    set output '$out_file'
    ```

<!--list-separator-->

-  multiplotのためのパラメータを変数にして指定

    上下左右のマージンなどをこうして **変数化** することで、図のバランスの微調整が楽になります。

    ```nil
    bm = 0.15    # bmargin
    lm = 0.12    # lmargin
    rm = 0.95    # rmargin
    gap = 0.03   # gap betweein 2 charts
    size = 0.75  # plot size
    kk = 0.5     # relative height of bottom plot
    ```

<!--list-separator-->

-  Y軸の範囲（最小値、最大値）を変数にして指定

    上下の図のY（金額）の最小値と最大値を指定します。1000で割るのはY軸目盛りの金額表示を千円単位にするためです。

    ```nil
    y1 = 0
    y2 =  120000/1000
    y3 = 1000000/1000
    y4 = 1120000/1000
    ```

<!--list-separator-->

-  図のスタイルとY軸の数字のフォーマット

    ```nil
    set style histogram
    set style data histograms
    set style fill transparent solid 0.8 border -1
    set boxwidth 0.70
    set decimal locale
    set format y "%'6.0f"
    ```

<!--list-separator-->

-  multiplotの宣言と下の図

    読み込むデータファイルは変数 `$data_to_plot` で指示します。

    ```nil
    set multiplot
    set label "Amount(千円)" at screen 0.03,0.5 center front rotate font "," . 10

    set border 1+2+8
    set xtics nomirror
    set ytics nomirror
    set lmargin at screen lm
    set rmargin at screen rm
    set bmargin at screen bm
    set tmargin at screen bm + size * kk
    set yrange [y1:y2]
    set xlabel "FY 2019-20"

    plot '$data_to_plot' \
          using 0:(column(2)/1000):xticlabels(strftime('%b', strptime('%Y-%m-%d', strcol(1))))\
    	 with boxes notitle linecolor rgb "skyblue",\
       '' using 0:(column(2)/1000):(column(2) != 0 ? (sprintf("%'d",(column(2)))): "ｇ") \
    	 with labels font "Courier,8" offset 0,0.5 textcolor linestyle 0 notitle
    ```

<!--list-separator-->

-  上の図

    ```nil
    unset xtics
    unset xlabel

    set border 2+4+8
    set bmargin at screen bm + size * kk + gap
    set tmargin at screen bm + size + gap
    set yrange [y3:y4]

    MyTitle = "消費税・ガソリン税を除く納税額の推移（〜`date +"%Y/%m/%d"`）"
    set title font "Arial,12"
    set title MyTitle offset char 0, char -0.75

    plot '$data_to_plot' \
          using 0:(column(2)/1000) with boxes notitle linecolor rgb "skyblue",\
       '' using 0:(column(2)/1000):(sprintf("%'d",(column(2)))) \
    	 with labels font "Courier,8" offset 0,0.5 textcolor linestyle 0 notitle

    unset multiplot
    ```

    こんな感じです。


#### 細かいことですが・・・ {#細かいことですが}

納税金額が **ゼロの月** では数字の'0'を書かないようにします。それにはgnuplotの **三項演算子** を使います。その部分だけを抽出すると次のとおりです：

```nil
(column(2) != 0 ? (sprintf("%'d",(column(2)))):"")
```

gnuplotの三項演算子の記号は <span class="underline">**? :**</span> です。Cと同じ働きをします。例えば **a?b:c** とすると「aが真ならば、2番めの引数（b）が評価され、その値が返され、真でなければ3番めの引数（c）が評価され、その値が返されます」（gnuplot 5.2マニュアル）

つまり：

```text
colomn(2) != 0            （第2列の値がゼロではない）が真か偽か
sprintf("%'d",(column(2)))  真ならば、第2列の値に1000単位でカンマをつける
""                          偽ならばブランクにする
```

ということになります。


#### 問題点と今後の課題 {#問題点と今後の課題}

グラフに **break** を入れた図はできるだけ避けるべき図ですが、この例図のように

-   ある一部が突出した **外れ値** であることをこれみよがしに見せつける
-   それ以外の、有象無象の変動をそれなりに見せる

という特殊な目的をどうしても達成したい場合に限っては「あり」かも知れません。

なお、
[こちらの例（Gnuplot Tricks)](http://gnuplot-tricks.blogspot.com/2009/11/broken-histograms.html)
では **multiplot** ではなくて **vectors** を使うという方法をとっています。とても魅力的ですが、Y軸の数値を書く方法が思いつかなかったのでギブアップしました。もっともっと **break** が必要となったら再検討してみます。


## Acknowledgement {#acknowledgement}