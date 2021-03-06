# ABC068
Atcoder Beginner Contest068の自分の解答

# B
nの制約を0以上と勘違いして1WA。コンパイルしなかったのが悪いのか。

# C
O(M^2)となるので間に合わないのではと思いつつもそれ以外に思いつかなかったのでとりあえず愚直解で通してみたら通った。

実際には最大でも辺の数だけしか調べないのでO(M)である。

# D
色々書いてみて任意のkにする条件を調べてみたが、あまり見えてこなかった。

全体としては和を1減らす操作なので、おそらくsumを(n-1)*n以下にする操作数になるのだと思うが、よく分からない。

n以下の数字にする方法とnの倍数にする方法は分かったが、この方法ではn<=50くらいまでしか判定できない。

n個の数列のうちk個をnにして残りを0にするとk回で条件を満たす数列が作れる。n個の数列をすべてn+kにするとn\*k回で条件を満たす数列が作れる。

### 追記（解説見た）
逆から考える問題。この系統はいくつか解いているが未だに苦手である。特に今回は半端に取っ掛かりを得ているので逆から考えようとは一切思わなかった。

逆から考えると数列の中であるものをn増やし、残りのものを1減らすという操作になる。これを1～nまですべて行うと全体を1増やす操作に等しくなる。このことからある値からスタートして全てを1増やす操作を適切な回数行ったあと、残りの回数分だけ操作をそのままなぞればよい。ただし、この方法だと、普通に実装すると最後の部分で0未満になってしまうことがあることに注意する。これを回避するには、初期値をn-1にすればよい。