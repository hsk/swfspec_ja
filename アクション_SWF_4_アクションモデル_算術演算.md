## 算術演算 [#e6e4ace7]

このセクションでは、算術演算について記述します。

### ActionAdd [#ActionAdd]

ActionAdd は 2 つの値を加算し、結果をスタックにプッシュします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionAdd|ACTIONRECORDHEADER|ActionCode = 0x0A|

ActionAdd は次のことを行います。

1. 値 A をスタックからポップする。
1. 値 B をスタックからポップする。
1. A と B を浮動小数点数に変換する。数値でない値の場合は 0 とする。
1. A と B の値を加算する
1. A + B の結果をスタックにプッシュする

### ActionSubtract [#ActionSubtract]

ActionSubtract は 2 つの値を減算し、結果をスタックにプッシュします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionSubtract|ACTIONRECORDHEADER|ActionCode = 0x0B|

ActionSubtract は次のことを行います。

1. 値 A をスタックからポップする。
1. 値 B をスタックからポップする。
1. A と B を浮動小数点数に変換する。数値でない値の場合は 0 とする。
1. B から A の値を減算する
1. B - A の結果をスタックにプッシュする

### ActionMultiply [#ActionMultiply]

ActionMultiply は 2 つの値を乗算し、結果をスタックにプッシュします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionMultiply|ACTIONRECORDHEADER|ActionCode = 0x0C|

ActionMultiply は次のことを行います。

1. 値 A をスタックからポップする。
1. 値 B をスタックからポップする。
1. A と B を浮動小数点数に変換する。数値でない値の場合は 0 とする。
1. A と B の値を乗算する
1. A * B の結果をスタックにプッシュする

### ActionDivide [#ActionDivide]

ActionMultiply は 2 つの値を除算し、結果をスタックにプッシュします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionDivide|ACTIONRECORDHEADER|ActionCode = 0x0D|

ActionDivide は次のことを行います。

1. 値 A をスタックからポップする。
1. 値 B をスタックからポップする。
1. A と B を浮動小数点数に変換する。数値でない値の場合は 0 とする。
1. B を A の値で除算する
1. B / A の結果をスタックにプッシュする
1. SWF 5 以降: A が 0 の場合、結果の値として NaN, Infinity, -Infinity のいずれかがスタックにプッシュされる。
SWF 4: A が 0 の場合、結果の値が文字列の #ERROR# になる。

### 移動 [#u331bbd4]
* 前のページ : [スタック操作](アクション_SWF_4_アクションモデル_スタック操作)
* 次のページ : [数値比較](アクション_SWF_4_アクションモデル_数値比較)
