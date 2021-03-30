# map(&:to_i)とはなんなのか？
標準入力でスペース区切りの数値を、配列として受け取る場合は以下のように記述できる。
```
numbers = gets.chomp.split.map(&:to_i)
```
このときの、map(&:to_i)とはなんなのか？  

## map.(&:to_i)までの処理
```
numbers = gets.chomp.split
```
[![Image from Gyazo](https://i.gyazo.com/9ca5ee2f607aee45a190ea72585f0d36.gif)](https://gyazo.com/9ca5ee2f607aee45a190ea72585f0d36)

文字列として配列に格納できる

## mapで数値に変換
先程の配列をmapを使って数値に変換する場合、以下のようになる.
```
numbers.map{|n| n.to_i}
```
[![Image from Gyazo](https://i.gyazo.com/e4987d8f58bcd4a15786bb316fc9e171.gif)](https://gyazo.com/e4987d8f58bcd4a15786bb316fc9e171)

つまり、標準入力でスペース区切りの数値を、配列として受け取る場合、省略なしで記述すると以下のようになる。
```
numbers = gets.chomp.split.map{|n| n.to_i}
```

## &は何をしてるのか？
ヒントはここにありました。  
https://docs.ruby-lang.org/ja/latest/class/Proc.html#block
>Proc オブジェクトをブロック付きメソッド呼び出しに使う
ブロック付きメソッドに対して Proc オブジェクトを `&' を指定して渡すと呼び出しブロックのように動作します。しかし、厳密には以下の違いがあります。これらは、Proc オブジェクトが呼び出しブロックとして振舞う際の制限です。

問題なし
```
(1..5).each { break }  
```
LocalJumpError が発生します。  
```
pr = Proc.new { break }  
(1..5).each(&pr)
```

ブロックをProc.newで
