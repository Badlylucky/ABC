# ABC032
Atcoder Beginner Contest032の自分の解答

実装ェ・・・

# C
しゃくとり法。なのだが、0除算などの例外処理が多くなかなか大変。

まず、数列に0が含まれている場合は全区間取っても積は0なので全区間取る。

また、数列の要素がすべてkより大きい場合どの区間を取ってもkを上回ってしまうので答えは0。

それ以外の場合は、端から順番に区間積をしゃくとりによって求める。途中lとrが逆になったりk以上の要素がある場合にどういうふうにふるまうかがやや不安なまま提出したがAC。数列の区間いじる問題は何回やっても慣れない。

# D
ただのナップサック。ただし典型1-0ナップサックすべてのパターンについて単一のコードで実装する必要があり超面倒。

似たようなコードを使い回す場合、**2回ぐらいならそのままコピペしたほうが結果的に安上がり**になる。

データセット2とデータセット3はそれぞれ重さ、価値を制約条件とするナップサック。こちらは普通に実装すれば問題ない。

問題はデータセット1。制約の問題上DP的手法は使えないがn\<=30であるため全探索しても間に合いそうと判断して実装→TLE。bit全探索を使って自明に2^30回ループする場合にTLEすることを確認できたので、再帰で枝刈りしつつ全部ナップサックに入る場合は全部入れるという前処理を取ったら通った。しかしこれは明らかにコーナーケースで落ちるやり方なので改善点を探したい。

### 追記（解説読んだ）
***10^9は間に合わない。覚えよう！***

O(2^N)が間に合わなそうなとき、半分全列挙というテクニックを使うとO(SlogS)(S=2^(N/2))程度には減らすことができる。明らかにDPが使えなさそうなときには検討すべき。

全要素を半分に分けて半分ずつ全探索して取れる値の候補を列挙し、片側のひとつの要素に対して適合するものを二分探索等を使ってもう片側から探す。

重さがマックスギリギリだからといって、価値が最大化されるわけではないので価値が最大のものをその中で全探索する（これ系のミス前もやったな？）。

でもこの全探索だとO(S^2)くらいにならないかな？

### 追記
https://twitter.com/refine_P/status/1103908899906699264

半分ソート後に半分の情報を「重さw以下で実現できる最大の価値v」と置き換えることで全探索の必要がなくなる。