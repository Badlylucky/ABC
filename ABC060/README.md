# ABC060
Atcoder Beginner Contest060の自分の解答

考察ミスが判明して3完

# B
互除法の問題。cがaとbのgcdで割り切れるならば解が存在する。

# C
最後は必ずT秒お湯が出る。

それまではmin(t[i+1]-t[i],T)秒間お湯が出る。

# D
w_iの制約に注目して、w_1で割った剰余に注目することにより普通のDPに落とし込めると思ったが、そもそもDPが正しく動いていない＆この変換を行ったときw_i=0となる場合にうまく計算できないという考察ミスが起こり、ここでギブアップ。

DP力がなさすぎる

### 追記（解説読んだ）
まーた全探索だった。。。

このパターン何度目や。。。最悪