---
title: "GENESIS Summer School参加記録"
emoji: "🍣"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: []
published: false
---

# はじめに

[GENESIS Summer School](https://tms.riken.jp/misc/genesis-summer-school2022/)は理化学研究所が主催している、MD計算用ソフトウェアGENESISとスーパーコンピューター「富岳」を使いMD(分子動力学)計算を学ぶプログラムです。

本記事は、GENESIS Summer Schoolに参加して学んだことのうち、**公開されている資料に書いてある情報を**まとめています。(配布された資料などを許可なく持ち出すことが禁止されているため)

ただし、私自身が初心者のため間違いがあるかもしれません。

# MDの基本とGENESISの使い方

## 分子動力学(MD)とは

[分子動力学法](https://ja.wikipedia.org/wiki/分子動力学法)は粒子(原子・分子など)の動きをシミュレーションする方法です。例えば、ある分子2つを真空中に配置したときに、分子がどのように動くかを計算するのに必要なのが分子動力学です。

### ニュートン力学により座標、速度、加速度を求める

最も基本的なMDの計算方法は、高校で勉強するニュートン力学を使います。


その粒子に与えられる力がわかると、加速度が計算できます。

```math
\mathbf F =  m \frac{d^2\mathbf r}{dt^2} = m \mathbf a
```

加速度が計算できると、速度や位置が計算できるようになります。
具体的には、ある時刻$t$での座標、速度、加速度をそれぞれ$\mathbf r(t), \mathbf v(t), \mathbf a(t)$とすると、

```math
\mathbf r(t+\Delta t) = \mathbf r(t) + \mathbf v(t) \Delta t \\
\mathbf v(t+\Delta t) = \mathbf v(t) + \mathbf a(t) \Delta t
```

となります。

$\mathbf F(t) = m \mathbf a(t)$ を使えば、力$F(t)$と初期条件$\mathbf r(0), \mathbf v(0), \mathbf a(t)$がわかれば任意の時刻の座標、速度、加速度がわかることになります。


:::message
粒子にかかる力Fが常にわかるなら、粒子の座標は計算できる
:::

参考記事: [分子動力学法](https://ja.wikipedia.org/wiki/分子動力学法)

### 力$F$を計算する方法

力$\mathbf F$は、ポテンシャル$V$によって計算できます。

```math
\mathbf F = - \nabla V (= -grad V)
```

山にボールがあるとき、ボールは高いところから低いところへと落ちていきます。
ポテンシャルは高さに該当し、ポテンシャルが高いところから低いところの方向に力を受けるということを上の式は示しています。

つまり、粒子にかかる力Fを調べるのは、粒子が存在する空間の力場を調べることと同じです。

そして、代表的な力場としてAMBER力場があります。

```math
\begin{eqnarray*}
V&=& \sum_{bonds} k_b (l-l_0)^2 \\
&+& \sum_{angles} k_b(\theta - \theta_0)^2 \\
&+& \sum_{torsions} \sum_n \frac{1}{2} V_n  (1+cos(n\omega - \gamma)) \\
&+& \sum_{i,j \notin bonding}{\epsilon_{ij}[(\frac{r_{0ij}}{r_{ij}})^{12}-(\frac{r_{0ij}}{r_{ij}})^6]+\frac{q_iq_j}{4\pi\epsilon_0r_{ij}}}
\end{eqnarray*}
```

第1項は原子間の距離に関す



参考記事
- [ポテンシャル - Wikipedia](https://ja.wikipedia.org/wiki/%E3%83%9D%E3%83%86%E3%83%B3%E3%82%B7%E3%83%A3%E3%83%AB)
- [AMBER (分子動力学) - Wikipedia](https://ja.wikipedia.org/wiki/AMBER_%28%E5%88%86%E5%AD%90%E5%8B%95%E5%8A%9B%E5%AD%A6%29)


# gREST法の紹介


# GENESIS/QSimulateによるQM/MM計算

# MD計算に基づくクライオ電顕フレキシブル・フィッティング

# チュートリアル1

# チュートリアル2
