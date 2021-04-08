# n!(nの階乗)
## Integerクラスを使う
```ruby
class Integer
  def factorial
    (1..self).inject(1,:*)
  end
end
```

## 再帰
```ruby
def fact(x)
  x == 0 ? 1 : x * fact(x - 1)
end
```

## 素因数分解を使って無理矢理
```
prime_divisionで素因数分解 
（ex) Prime.prime_division(25) -> [[5, 2]] 
(ex) 25.prime_division -> [[5, 2]] 
```

```ruby
require 'prime'
M = 10 ** 9 + 7

def fact(x)
  if x == 1
    return 1
  end
  
  h = Hash.new(0)
  1.upto(x) do |i|
    i.prime_division.each do |k, v|
    h[k] += v
    end
  end
  
  res = []
  h.each do |key, val|
    res << key ** val
  end
  return res.inject {|result, item| result * item }
end
```
例えば...
```
4! = 1 x 2 x 3 x 4 = 1 x 2^3 x3
```
となるので、素数を掛け合わせていくことで解ける。

