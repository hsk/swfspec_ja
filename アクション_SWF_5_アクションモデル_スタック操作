## スタック操作 [#ae234506]

### ActionBitAnd [#ActionBitAnd]

ActionBitAnd は 2 つの数値をスタックからポップし、ビットごとの AND を計算して、結果を S32 型の数値としてスタックにプッシュします。
引数は、 AND を実行する前に 32 ビットの符号なし整数に変換されます。
結果は __符号付き__ 32 ビット整数になります。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionBitAnd|ACTIONRECORDHEADER|ActionCode = 0x60|

ActionBitAnd は次のことを行います。

1. arg1 と arg2 をスタックからポップする
1. 結果をスタックにプッシュする

### ActionBitLShift [#ActionBitLShift]

ActionBitLShift はシフト回数 arg 、 値 value の順にスタックからポップし、
value は 32 ビットの符号付き整数に変換、arg の下位 5 ビットのみがシフト回数として使用されます。
arg は左シフトの回数を指します。
ActionBitLShift は結果の値を S32 型の数値としてスタックにプッシュします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionBitLShift|ACTIONRECORDHEADER|ActionCode = 0x63|

ActionBitLShift は次のことを行います。

1. arg, value の順にスタックからポップする
1. 結果をスタックにプッシュする

### ActionBitOr [#ActionBitOr]

ActionBitOr は 2 つの数値をスタックからポップし、ビットごとの OR を計算して、結果を S32 型の数値としてスタックにプッシュします。
引数は、 OR を実行する前に 32 ビットの符号なし整数に変換されます。
結果は __符号付き__ 32 ビット整数になります。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionBitOr|ACTIONRECORDHEADER|ActionCode = 0x61|

ActionBitOr は次のことを行います。

1. arg1 と arg2 をスタックからポップする
1. 結果をスタックにプッシュする

### ActionBitRShift [#ActionBitRShift]

ActionBitRShift はシフト回数 arg 、 値 value の順にスタックからポップし、
value は 32 ビットの符号付き整数に変換、arg の下位 5 ビットのみがシフト回数として使用されます。
arg は右シフトの回数を指します。
ActionBitRShift は結果の値を S32 型の数値としてスタックにプッシュします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionBitRShift|ACTIONRECORDHEADER|ActionCode = 0x64|

ActionBitRShift は次のことを行います。

1. シフト回数をスタックからポップする
1. 値をスタックからポップする
1. 結果をスタックにプッシュする

### ActionBitURShift [#ActionBitURShift]

ActionBitURShift はシフト回数 arg と、値 value をスタックからポップします。
値は 32 ビット符号付き整数に変換され、シフト回数は下位 5 ビットのみが使われます。
arg は右シフトの回数を指します。
ActionBitURShift は結果を UI32 型の値としてスタックにプッシュします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionBitURShift|ACTIONRECORDHEADER|ActionCode = 0x65|

ActionBitURShift は次のことを行います。

1. シフト回数をスタックからポップする
1. 値をスタックからポップする
1. 結果をスタックにプッシュする

### ActionBitXor [#ActionBitXor]

ActionBitXor は 2 つの値をスタックからポップし、ビットごとの XOR を実行した後、結果を S32 型の数値としてスタックにプッシュします。
引数は XOR の実行前に 32 ビットの符号なし整数に変換されます。
結果は __符号付き__ 整数として扱われます。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionBitXor|ACTIONRECORDHEADER|ActionCode = 0x62|

ActionBitXor は次のことを行います。

1. arg1 、 arg2 をスタックからポップする
1. 結果をスタックにプッシュする

### ActionDecrement [#ActionDecrement]

ActionDecrement はスタックから値をポップし、それを数値型に変換した後、 
1 デクリメントした結果をスタックにプッシュします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionDecrement|ACTIONRECORDHEADER|ActionCode = 0x51|

ActionDecrement は次のことを行います。

1. 数値をスタックからポップする
1. 結果をスタックにプッシュする

### ActionIncrement [#ActionIncrement]

ActionIncrement はスタックから値をポップし、それを数値型に変換した後、 
1 インクリメントした結果をスタックにプッシュします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionIncrement|ACTIONRECORDHEADER|ActionCode = 0x50|

ActionIncrement は次のことを行います。

1. 数値をスタックからポップする
1. 結果をスタックにプッシュする

### ActionPush (拡張版) [#ActionPush]

SWF 5 では、 8 つの新しいデータ型が追加されました。
詳しくは [ActionPush](アクション_SWF_4_アクションモデル_スタック操作#ActionPush) をご覧ください。

### ActionPushDuplicate [#ActionPushDuplicate]

ActionPushDuplicate は、スタックの最上段にあるものを複製してスタックにプッシュします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionPushDuplicate|ACTIONRECORDHEADER|ActionCode = 0x4C|

### ActionReturn [#ActionReturn]

ActionReturn は戻り値としてスタック上にプッシュされた値を返します。
戻り値が不正な値の場合は破棄されます。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionReturn|ACTIONRECORDHEADER|ActionCode = 0x3E|

ActionReturn は次のことを行います。

1. 値をスタックからポップする

### ActionStackSwap [#ActionStackSwap]

ActionStackSwap は、スタック最上段にある 2 つの ScriptAtoms を入れ替えます。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionStackSwap|ACTIONRECORDHEADER|ActionCode = 0x4D|

ActionStackSwap は次のことを行います。

1. Item1, Item2 の順でスタックからポップする
1. Item2, Item1 の順でスタックにプッシュする

### ActionStoreRegister [#ActionStoreRegister]

ActionStoreRegister はスタックの次のオブジェクトを読み込み (ポップしない) 、 4 つのうち 1 つのレジスタに保存します。
ActionDefineFunction2 が使われている場合、 256 個のレジスタが使用可能になります。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionStoreRegister|ACTIONRECORDHEADER|ActionCode = 0x87|
|RegisterNumber|UI8||

ActionStoreRegister は、タグ内の RegisterNumber フィールドによりレジスタ番号を決定します。

### 移動 [#u331bbd4]
* 前のページ : [数学](アクション_SWF_5_アクションモデル_数学)
* 次のページ : [SWF 6 アクションモデル](アクション_SWF_6_アクションモデル)
