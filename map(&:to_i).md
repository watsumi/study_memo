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

ブロックをProc.newでProcオブジェクトとした場合、`&`を指定して渡さないとブロックとして動作してくれないために、&を使っているということでした。

[![Image from Gyazo](https://i.gyazo.com/58486adbc773169e17ab0dd762445a13.gif)](https://gyazo.com/58486adbc773169e17ab0dd762445a13)

## :to_iは何をしているのか？
結論からいうと、Procオブジェクトを自動的に生成し、第一引数を数値に変換しています。    
ヒントはこちらに。  
https://docs.ruby-lang.org/ja/latest/method/Symbol/i/to_proc.html

>instance method Symbol#to_proc
>to_proc -> Proc[permalink][rdoc][edit]
>self に対応する Proc オブジェクトを返します。
>生成される Proc オブジェクトを呼びだす(Proc#call)と、 Proc#callの第一引数をレシーバとして、 self という名前のメソッドを残りの引数を渡して呼びだします。
>生成される Proc オブジェクトは lambda です。
```
:object_id.to_proc.lambda? # => true
```
明示的に呼ぶ例
```
:to_i.to_proc["ff", 16]  # => 255 ← "ff".to_i(16)と同じ
```
暗黙に呼ばれる例
```
# メソッドに & とともにシンボルを渡すと
# to_proc が呼ばれて Proc 化され、
# それがブロックとして渡される。
(1..3).collect(&:to_s)  # => ["1", "2", "3"]
(1..3).select(&:odd?)   # => [1, 3]
```
