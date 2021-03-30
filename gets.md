# getsとgets.chompとgets.to_iの違い
`gets`は**改行**が発生するが、`gets.chomp`は**改行をなくしてくれる**<br>
At Corderは標準で末尾に改行が入るから、chompをつけたほうが良い
*大前提：chompは文字列
>self の末尾から rs で指定する改行コードを取り除いた文字列を生成して返します。ただし、rs が "\n" ($/ のデフォルト値) のときは、実行環境によらず "\r", "\r\n", "\n" のすべてを改行コードとみなして取り除きます。

標準入力を数値として受け取る場合は、to_iを用いる

## getsは順番に入力される
```
カリー
30
ウォーリアーズ
```
上のように与えられた場合は、下のようにすることで、順番に入力される。
```
name = gets #入力一行目
number = gets #入力二行目
team = gets #入力三行目
```
---
最初に行数が与えられるパターンは、こんな感じにできるかも。
もっといい方法ありそうだが。
```
input_line = gets.chomp
input = []
input_line.to_i.times { input << gets.chomp }
```
---
一行で与えられた数値を、空白で区切って配列(文字列)として受け取るとき
```
30 30 10
```

```
input_line = gets.chomp.split('')
```
---
一行で与えられた数値を、空白で区切って配列(数値)として受け取るとき
```
input_line = gets.chomp.split.map(&:to_i)
```
---
上記の例は個別に受け取ることも可能
```
a, b = gets.chomp.split.map(&:to_i)
```

