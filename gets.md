# getsとgets.chompの違い
`gets`は**改行**が発生するが、`gets.chomp`は**改行をなくしてくれる**<br>
At Corderは標準で末尾に改行が入るから、chompをつけたほうが良い

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

最初に行数が与えられるパターンは、こんな感じにできるかも。
もっといい方法ありそうだが。
```
input_line = gets.chomp
input = []
input_line.to_i.times { input << gets.chomp }
```

一行で与えられた数値を、空白で区切って配列として受け取るとき
```
30 30 10
```

```
input_line = gets.chomp.split('')
```
