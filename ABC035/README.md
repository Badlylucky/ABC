# ABC035
Atcoder Beginner Contest035の自分の解答

普通に1完。Dはおそらく典型の何か。

# C
その面が白か黒かはひっくり返された回数の奇偶さえ求めれば容易に求まるので、何回ひっくり返すかを効率よく数え上げる。

こういうのはimos（差分法）を使ったあと和分でまとめるのが鉄板。差分で`[l,r)`の区間をひっくり返す計算規則を定め、後に足した。

* lからrまでをひっくり返す操作においては、`dif[l]`を+1、`dif[r+1]`を-1した。
* 1-indexedなので答えは1～nの区間にある。ただしnがひっくり返された場合がうまく反映できないので、配列はn+2のサイズで取る。
* 最後に答えの配列で順次和分を取る。取り方は区間が`[l,r)`であることに気をつけ、`ans[i]=ans[i-1]+dif[i]`とした。

上記のことに気をつけ、サンプルを出したら想定通り動いたので提出したら通った。デバッグが極めて難しいため何回やっても慣れない苦手な問題だ。

# D
ダイクストラ+DP的な何か？

まず最適な動き方が存在するとすれば、1番の町からある町に一直線に出かけ、そこで限界まで採掘をし、ギリギリで1番に帰るというものだろうと考えた。しかし今回のケースは行きと帰りのコストが違うので必ずしもこれが最適とは言い切れず、またO(N^2logN)かかりTLEしてしまう（部分点解と思われる）。

もう少し拡張してある時間iに町jにいるときの最高獲得金額を求めるdp\[i]\[j]を考えた。しかしこれもtの制約から配列が定義できなくなってしまう。

### 追記（解説読んだ）
逆辺の最短経路を考える問題。これは思いつきたかった。

あと1つの町に留まるのが正解であった。

初期化最大値を見誤ってWA。long longと分かっているならそれに合わせた最大値を使おう（long longの場合1e17-1）。