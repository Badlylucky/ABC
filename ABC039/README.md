# ABC039
Atcoder Beginner Contest039の自分の解答

アルゴリズムいらないが面倒ゲー

# C
データ構造知らないと苦労しそうな問題。知ってるならmapかenumで殴るだけだが（難しさの割に）実装が面倒すぎる。

# D
周囲8方向を精査するやつ、bitで楽できそうだけどやり方がわからないのでif文無限に書いてしまう。

逆方向の操作について考える。正方向の操作が「周り8方向の画素のうち、一つでも黒い画素があったらその画素を黒くする」なので、逆方向の操作は「周り8方向の画素がすべて黒ければ、その画素を黒くする」である（「一つでも〇〇」の逆は「すべて□□」）。

では、与えられた文字列に対して逆方向の操作を実行して元の画像を復元する。実はこの操作は、possibleである場合は完全に全射なので対応するものがあることがわかる（証明よくわからん）。impossibleの場合は周り8方向に黒い画素がない黒い画素の情報が失われるため逆方向にすると実質的に違った画像になってしまう。

ここで、possibleならば正方向⇔逆方向は何回やっても同じ結果になることに対し、impossibleならば逆方向→正方向と操作を進めると異なる結果になることが分かった。したがって逆方向、正方向の順番で操作を行い、元の画像と一致するかどうか確かめればよい。

変換前の文字列（逆操作をしたあとの文字列）を出力する必要があるほか、処理順の関係でうまくいかないので元の画像、逆方向の操作をした結果の画像、正方向の操作をした結果の画像はすべて異なる変数に保持しなければならない。面倒。