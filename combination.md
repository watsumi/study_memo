# combination
3C1
```
# to_a（数値のまま）
> [1,2,3].combination(2).to_a
=> [[1, 2], [1, 3], [2, 3]]

# map(文字列変換)
> [1,2,3].combination(2).map {|arr| arr.map(&:to_s) }
=> [["1", "2"], ["1", "3"], ["2", "3"]]
```

# repeated_combinationで重複順列を作る
```
> [1,2,3].repeated_combination(2).to_a
=> [[1, 1], [1, 2], [1, 3], [2, 2], [2, 3], [3, 3]]
```

