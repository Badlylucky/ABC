# ABC095
Atcoder Beginner Contest095の自分の解答

全完したので水色昇格！　やったぜ！……だがここからが地獄の始まりだ

# B
一通り作った後必要な素が少ないやつをひたすら作る。

# C
a+b < 2cの場合、すべてAピザあるいはBピザを買う場合が最小となる。

a+b > 2cの場合、少なくともmin(x,y)枚分だけはABピザを頼んだほうがよいことが分かる。では、すべてABピザを頼んだほうがよい場合はどのような場合か？

簡単のため、a < b, x < yとする。このとき、すべてABピザを買うときと多い分だけBピザを買うときの合計金額はそれぞれ以下のようになる。

> c\*y\*2

> c\*x\*2 + b\*(x-y)

先程の質問は、「c\*y\*2 < c\*x\*2 + b\*(x-y)が成立するのはいつか？」と聞いているに等しい。この不等式を移項して整理すると 2\*c < bとなるので、結局のところ多い方のピザの金額をABピザ2枚の金額が下回るならすべてABピザにすると金額は最小になる、ということになる。

# D
摂取カロリーを最大化するような移動方法は、ある位置まで時計回りに進むか反時計回りに進む、もしくはある位置まで時計回りに進んだ後別の位置まで反時計回りに進むあるいはその逆の4通りである。これを求めていく。

移動方向は一様なので、スタート地点（座標0）を基準にしてそこから時計回り、あるいは反時計回りにi個寿司を食べたときの（移動による消費カロリー）を含む摂取カロリーの累積和を求める。当然解はこれらの組み合わせ中の最大値になってくるわけだが、重複して寿司を食べないように気をつける必要がある。今回はのケースではそれぞれ時計回りにx個、反時計回りにy個たべたとき、x+y>n+1となっていたときは重複が発生している。

あとはこれらに気をつけて時計回りと反時計回りの累積和それぞれの場合において、純粋に戻らない場合と戻る場合を逐一比較していき、その最大値を求めれば良い。この方法だとO(n^2)となり、部分点を取れる。

戻る場合に注目する。戻る場合にどこまで戻ると摂取カロリーを最大化できるかというと、単純に逆方向の累積和が最大のときである（普通に進む時はそうだとは限らない点に注意）。ただしここでも重複が起こらないように注意する。

したがってi番目までで最も累積和が大きくなる番地をO(n)かけてあらかじめ求めておけば、戻る場合の最大値はO(1)で計算できるので全体の計算量をO(n)まで落とせる。よって満点を取ることができた。