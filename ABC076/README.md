# ABC076
Atcoder Beginner Contest076の自分の解答

# C
方向性を全く間違えていたのでえらく時間を食ってしまった。find関数は使わない。

tの文字列はほぼ間違いなくsの文字列より短いので、その場合についてのみ考える。

もしもsの中のどこかにtが含まれる場合、sは途中に部分文字列tを含む文字列となる。したがってsの範囲内でtをスライドさせ、tがその中に当てはまる部分を探せば良い。当てはまる可能性のある場所は、s.length()-t.length()+1通り存在する（仮にtがsより長い場合、この段階で弾かれる）。マッチングは?で被覆されている場所もあるので1文字ずつ行う。

sはtを部分文字列として含むものの中で辞書順最小であるので、前から調べていった場合最後にtが入れる場所にtを入れて残りをaで埋め尽くした文字列が答えとなる。

# D

難しく、方針が二転三転した果てにWA。

ある制限速度区間iについて考える。このとき、この区間が始まったときの時間を0とすると時間はt=[0,t[i]]と表せる。このとき、t=0における速度は前及び次の制限速度に注意するとmin(v[i],v[i-1])、t=t[i]における速度はmin(v[i],v[i+1])である。

ここでx軸に時間、y軸に速度を取るようなグラフを考える。このとき進んだ距離はこのグラフの[0,t[i]]における面積となる。このグラフにおいて速度の移り変わりを考えると、必ず以下のようになる。

1. t=0における速度からv[i]まで加速する。
2. v[i]のまま進行する。
3. v[i]からt=t[i]における速度まで減速する。

1と3において、面積を最大化するため加速度は1m/s^2とする。となると、1は関数y=x+min(v[i],v[i-1])、3は関数y=-x+t[i]-min(v[i],v[i+1])としてグラフ上に表せることが分かる。この区間に制限速度が存在しないとすると、1と3の関数が囲む面積が距離となる。

実際には2の関数y=v[i]によっても制限される。したがって1と3が囲む面積から1と2と3で囲まれた面積を引いたものが距離となる。どちらも1と3の交点を求めることで求められる。

1と3が囲む面積について、1と3の交点で分けることで2つの台形の面積の和として表される。1と2と3で囲まれた面積について、1と3の交点のy座標がv[i]よりも大きければ存在する。また、この図形の形は必ず直角二等辺三角形になる。したがってこの面積は(y-v[i])^2で求められる。

穴はなさそうにしか思えないのだがWA。

### 追記（解説読んだ）

上の方法だともっと先の速度に間に合わないことがあるそうだ。

0.5秒ごとに注目すると、速度は0.5m/s上がるか下がるか変わらないかのどれかである。