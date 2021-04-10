| メソッド | 出力後の改行 | 配列の表示 | 呼び出すメソッド | 戻り値 | 対象者 |
|:-:|:-:|:-:|:-:|:-:|:-:|
| puts | あり | 要素ごとに改行 | to_s | nil | 一般ユーザ |
| print  | なし | 改行しない | to_s | nil | 一般ユーザ |
| p | あり | 改行しない | inspect | 引数のオブジェクト | 開発者(デバック用) |

## 配列の要素を半角区切りで出力
### 1次元配列
```ruby=
array = ["red", "blue", "white"]
puts array.join(' ')
->red blue white
```

### 多次元配列
```ruby=
array = ["red", ["blue", "gold", ["green", "pink"]], ["white", "brown"]]
puts array.join(' ')
```
