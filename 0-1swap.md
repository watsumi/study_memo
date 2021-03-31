## 数列の要素を一つだけ入れ替えて昇順にできるか？

標準入力
```
N
p1 p2...pN
```
回答
```
len = gets.to_i
num = gets.split(' ').map(&:to_i).to_enum
sort_num = num.sort.to_enum

diff = []
loop do
  diff << num.next - sort_num.next 
end

if diff.count(0) == len
  puts :YES
else
  puts len - diff.count(0) == 2? :YES: :NO
end
```

### to_enum

[![Image from Gyazo](https://i.gyazo.com/657d94b0dd7083dce1c01c093a4917f3.png)](https://gyazo.com/657d94b0dd7083dce1c01c093a4917f3)
