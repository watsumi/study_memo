# size,length,countの違い
`size`,`length`はレシーバーが持っている**要素数情報***を参照<br>
`count`は`Enumerableモジュール`で定義されているメソッドで、**each処理を回した結果**を表示する<br>
そのため、要素数が多い場合countを実行すると処理速度が遅くなる場合がある
