## 数学 [#t699dd92]

### ActionAdd2 [#ActionAdd2]

ActionAdd2 は ActionAdd と似ていますが、データ型によって実行結果が異なります。
加算オペレータアルゴリズムは、 ECMA-262 Section 11.6.1 のものが使われます。
ActionAdd2 が文字列の連結に使われた場合、 arg1 に arg2 を連結させます。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionAdd2|ACTIONRECORDHEADER|ActionCode = 0x47|

ActionAdd2 は次のことを行います。

1. arg1 をスタックからポップする
1. arg2 をスタックからポップする
1. 結果をスタックにプッシュする

### ActionLess2 [#ActionLess2]

ActionLess2 は、arg2 が arg1 より小さいか比較し、Boolean 型の戻り値をスタックにプッシュします。
このアクションは [ActionLess](アクション_SWF_4_アクションモデル_数値比較#ActionLess) に似ていますが、
引数のデータ型によって比較の仕方が異なります。
ECMA-262 Section 11.8.5 の比較アルゴリズムが使われます。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionLess2|ACTIONRECORDHEADER|ActionCode = 0x48|

ActionLess2 は次のことを行います。

1. arg1 をスタックからポップする
1. arg2 をスタックからポップする
1. arg2 < arg1 で比較する
1. 戻り値を Boolean 型でスタックにプッシュする

### ActionModulo [#ActionModulo]

ActionModulo は x modulo y (剰余) を計算します。
y が 0 の時は NaN 値 (0x7FC00000) をスタックにプッシュします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionModulo|ACTIONRECORDHEADER|ActionCode = 0x3F|

ActionModulo は次のことを行います。

1. x, y の順番でスタックからポップする
1. x % y の値をスタックにプッシュする

### 移動 [#u331bbd4]
* 前のページ : [型](アクション_SWF_5_アクションモデル_型)
* 次のページ : [スタック操作](アクション_SWF_5_アクションモデル_スタック操作)
