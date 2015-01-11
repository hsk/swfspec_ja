## SWF 7 アクション [#deb58666]

SWF 7 では、次のアクションが使用可能です。

* [ActionDefineFunction2](#ActionDefineFunction2)
* [ActionExtends](#ActionExtends)
* [ActionCastOp](#ActionCastOp)
* [ActionImplementsOp](#ActionImplementsOp)
* [ActionTry](#ActionTry)
* [ActionThrow](#ActionThrow)

### ActionDefineFunction2 [#ActionDefineFunction2]

ActionDefineFunction2 は、 [ActionDefineFunction](アクション_SWF_5_アクションモデル_スクリプトオブジェクト#ActionDefineFunction) と似ています。

追加の機能として、関数の Activation オブジェクトで未使用の変数の作成を防ぐことと、数に関するレジスタで局所変数の交換を可能にすることによって関数の処理速度を上げています。

ActionDefineFunction2 では、1 つの関数につき 256 個のプライベートなレジスタを割り当てます。
パラメータかローカル変数をレジスタと置き換えることができます。関数の Activation オブジェクトに保存する値の替わりになります。
（Activation オブジェクトは暗黙的にローカルスコープにあり、中に名前付きの引数・ローカル変数を含みます。Activation オブジェクトの詳細については ECMA-262 をご覧ください。）

ActionDefineFunction2 also includes six flags to instruct Flash Player to preload variables,
and three flags to suppress variables. By setting PreloadParentFlag, PreloadRootFlag,
PreloadSuperFlag, PreloadArgumentsFlag, PreloadThisFlag, or
PreloadGlobalFlag, common variables can be preloaded into registers before the function
executes (_parent, _root, super, arguments, this, or _global, respectively). With flags
SuppressSuper, SuppressArguments, and SuppressThis, common variables super,
arguments, and this are not created. By using suppress flags, Flash Player avoids preevaluating
variables, thus saving time and improving performance.
No suppress flags are provided for _parent, _root, or _global because Flash Player always
evaluates these variables as needed; no time is ever wasted on pre-evaluating these variables.
Specifying both the preload flag and the suppress flag for any variable is not allowed.
The body of the function that ActionDefineFunction2 specifies should use ActionPush and
ActionStoreRegister for local variables that are assigned to registers. ActionGetVariable and
ActionSetVariable cannot be used for variables assigned to registers.

ActionDefineFunction2  は、 Flash Player 6 release 65 以降でサポートされます。

__リンク__
・Activation オブジェクトの解説
http://www2u.biglobe.ne.jp/~oz-07ams/prog/ecma262r3/10_Execution_Contexts.html

|フィールド|型|コメント|
| --- | --- | --- |
|ActionDefineFunction2|ACTIONRECORDHEADER|ActionCode = 0x8E|
|FunctionName|STRING|関数の名前。空の場合匿名|
|NumParams|UI16|パラメータの数|
|RegisterCount|UI8|レジスタの割り当て数。最大255。 (0 から 254)|
|PreloadParentFlag|UB[1]|0 = ___parent__ をレジスタにプリロードしない&br;1 = ___parent__ をレジスタにプリロードする|
|PreloadRootFlag|UB[1]|0 = ___root__ をレジスタにプリロードしない&br;1 = ___root__ をレジスタにプリロードする|
|SuppressSuperFlag|UB[1]|0 = __super__ 変数を作る&br;1 = __super__ 変数を作らない|
|PreloadSuperFlag|UB[1]|0 = __super__ をレジスタにプリロードしない&br;1 = __super__ をレジスタにプリロードする|
|SuppressArgumentsFlag|UB[1]|0 = __arguments__ 変数を作る&br;1 = __arguments__ 変数を作らない|
|PreloadArgumentsFlag|UB[1]|0 = __arguments__ をレジスタにプリロードしない&br;1 = __arguments__ をレジスタにプリロードする|
|SuppressThisFlag|UB[1]|0 = __this__ 変数を作る&br;1 = __this__ 変数を作らない|
|PreloadThisFlag|UB[1]|0 = __this__ をレジスタにプリロードしない&br;1 = __this__ をレジスタにプリロードする|
|Reserved|UB[7]|常に 0|
|PreloadGlobalFlag|UB[1]|0 = ___global__ をレジスタにプリロードしない&br;1 = ___global__ をレジスタにプリロードする|
|Parameters|REGISTERPARAM[NumParams]|下記 REGISTERPARAM 参照|
|codeSize|UI16|続くコードのバイト数|

__REGISTERPARAM__
|フィールド|型|コメント|
| --- | --- | --- |
|Register|UI8|ActionCode|
|ParamName|STRING|パラメータ名|

### ActionExtends [#ActionExtends]

|フィールド|型|コメント|
| --- | --- | --- |
|ActionExtends|ACTIONRECORDHEADER|ActionCode = 0x69|

### ActionCastOp [#ActionCastOp]

|フィールド|型|コメント|
| --- | --- | --- |
|ActionCastOp|ACTIONRECORDHEADER|ActionCode = 0x2B|

### ActionImplementsOp [#ActionImplementsOp]

|フィールド|型|コメント|
| --- | --- | --- |
|ActionImplementsOp|ACTIONRECORDHEADER|ActionCode = 0x2C|

### ActionTry [#ActionTry]

|フィールド|型|コメント|
| --- | --- | --- |
|ActionTry|ACTIONRECORDHEADER|ActionCode = 0x8F|
|Reserved|UB[5]|ActionCode|
|CatchInRegisterFlag|UB[1]|ActionCode|
|FinallyBlockFlag|UB[1]|ActionCode|
|CatchBlockFlag|UB[1]|ActionCode|
|TrySize|UI16|ActionCode|
|CatchSize|UI16|ActionCode|
|FinallySize|UI16|ActionCode|
|CatchName|If CatchInRegisterFlag = 0, STRING|ActionCode|
|CatchRegister|If CatchInRegisterFlag = 1, UI8|ActionCode|
|TryBody|UI8[TrySize]|ActionCode|
|CatchBody|UI8[CatchSize]|ActionCode|
|FinallyBody|UI8[FinallySize]|ActionCode|

### ActionThrow [#ActionThrow]

|フィールド|型|コメント|
| --- | --- | --- |
|ActionThrow|ACTIONRECORDHEADER|ActionCode = 0x2A|

### 移動 [#u331bbd4]
* 前のページ : [SWF 7 アクションモデル](アクション_SWF_7_アクションモデル)
* 次のページ : [SWF 9 アクションモデル](アクション_SWF_9_アクションモデル)
