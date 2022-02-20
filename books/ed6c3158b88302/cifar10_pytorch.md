---
title: "Cifar10をPytorchでやってみる"
---

# 用語説明

## cifar10とは

[cifar10]は、60000枚の32x32ピクセルのカラー画像のデータセット。
10個のクラス(飛行機、車、鳥...)がある。

初心者用のデータセットの1つで、難易度はMNIST < Fashion MNIST = cifar10だと思っています。

## Colaboratory

googleが提供している、GPU/TPUつきのpython実行環境
機械学習でよくつかうライブラリがすでにインストールされている
実行時間制限があるので注意

# Colaboratoryのプログラムの補足

## GPUの選択

「ランタイム」→「ランタイムのタイプを変更」→「GPU」を選びましょう。

## イテレーター

配列と同じようなもの。前から順番に取り出すことができる。

```python
hoge = [1, 2, 3]
hoge_iter = iter(hoge)

print(next(hoge_iter)) # 1
print(next(hoge_iter)) # 2
print(next(hoge_iter)) # 3
print(next(hoge_iter)) # StopIteration
```

for文の中ではイテレーターが使われている。

```python
for value in [100, 200, 300]:
    print(value)
# 100
# 200
# 300
```

イテレーターは、配列より速度が多少遅くなることと引き換えに、プログラミングで便利な機能がたくさんついたものです。

## one-hot encoding

今回は、10個のラベル(クラス)があります。

入力に画像が与えられたときに、その画像がどのラベルなのかを出力するとき、出力の形式はどうすればよいでしょうか？

例えば、0~9の整数を出力するということができます。しかし、これだと一番可能性が高いラベルしかわかりませんし、実際のところどれくらいAIがそのラベルだと思っているか(確信度)を表現できません。

現在、よく使われている方法は、**one-hot encoding**という方法で、ラベルが10個なら出力値も10個にするというものです。また、出力値の合計は1になるようにします。そうすることで、出力値=(AIが計算した)確率ととらえることができます。

## 精度評価の方法

基本的に、AccuracyよりF値のほうが良い

[Accuracyなどの混同行列の評価が使えない理由](https://qiita.com/Derek/items/01a5009b10adc19edc24)

[機械学習 – 精度、適合率、再現率、F値について](https://pystyle.info/ml-accuracy-precision-recall-f-measure/)
