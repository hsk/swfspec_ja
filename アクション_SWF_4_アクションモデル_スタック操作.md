## スタック操作 [#m1ace71f]

このセクションではスタック操作について記述します。

### ActionPush [#ActionPush]

ActionPush は、 1 つ以上の値をスタックにプッシュします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionPush|[ACTIONRECORDHEADER](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionRecordHeader)|ActionCode = 0x96|
|Type|[UI8](基本的なデータ型_整数型とバイトオーダー)|0 = 文字列リテラル&br;1 = 浮動小数点数リテラル&br;次の型は SWF 5 以降で使用可能です。&br;2 = null&br;3 = undefined&br;4 = register&br;5 = Boolean&br;6 = double&br;7 = integer&br;8 = constant 8&br;9 = constant 16|
|String|If Type = 0, [STRING](基本的なデータ型_文字列の値)|null 終端文字列|
|Float|If Type = 1, [FLOAT](基本的なデータ型_浮動小数点数)|32 bit IEEE 単精度浮動小数点数 (リトルエンディアン)|
|RegisterNumber|If Type = 4, [UI8](基本的なデータ型_整数型とバイトオーダー)|レジスタ数|
|Boolean|If Type = 5, [UI8](基本的なデータ型_整数型とバイトオーダー)|ブール値|
|Double|If Type = 6, [DOUBLE](基本的なデータ型_浮動小数点数)|64 bit IEEE 倍精度浮動小数点数 (リトルエンディアン)|
|Integer|If Type = 7, [UI32](基本的なデータ型_整数型とバイトオーダー)|32 bit 整数 (リトルエンディアン)|
|Constant8|If Type = 8, [UI8](基本的なデータ型_整数型とバイトオーダー)|コンスタントプールのインデックス (インデックス < 256)&br;(ActionConstantPool 参照)|
|Constant16|If Type = 9, [UI16](基本的なデータ型_整数型とバイトオーダー)|コンスタントプールのインデックス (インデックス >= 256)&br;(ActionConstantPool 参照)|

ActionPush は、 1 つ以上の値をスタックに積みます。
Type フィールドはプッシュする値の型を指定します。
Type = 1 の場合、 32 bit IEEE 単精度浮動小数点数の値をプッシュします。
PropertyId は FLOAT でプッシュされます。
ActionGetProperty と ActionSetProperty は PropertyId を使って名前付きオブジェクトのプロパティにアクセスします。

Type = 4 の場合、レジスタ数の値がプッシュされます。
Flash Player は 4 つまでのレジスタをサポートしています。
ActionDefineFunction2 を使うことによって、 256 個までのレジスタを使うこともできます。

ActionPush の最初のフィールドの ACTIONRECORD の中の Length 値は、 ACTIONRECORD に続く Type と値の総バイトサイズを定義します。
1 つ以上の Type と値のフィールドの組が最初のフィールドに続き、これらを合計したサイズが ACTIONRECORD の Length フィールドにセットされます。

### ActionPop [#ActionPop]

ActionPop は、スタックから値をポップし、スタック上の値を破棄します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionPop|[ACTIONRECORDHEADER](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionRecordHeader)|ActionCode = 0x17|

### 移動 [#u331bbd4]
* 前のページ : [SWF 4 アクション](アクション_SWF_4_アクションモデル_SWF_4_アクション)
* 次のページ : [算術演算](アクション_SWF_4_アクションモデル_算術演算)
