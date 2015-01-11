## 変数 [#p31e05a5]

### ActionGetVariable [#ActionGetVariable]

ActionGetVariable は、変数の値を取得します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionGetVariable|ACTIONRECORDHEADER|ActionCode = 0x1C|

ActionGetVariable は、次のことを行います。

1. スタックから文字列で名前をポップする。この名前は、取得する変数の名前。
1. 変数の値をスタックにプッシュする。

他の実行コンテキスト中の変数は、変数名にターゲットパスとコロンからなる接頭辞を付けて参照します。
例えば /A/B:FOO は、 /A/B にあるムービークリップの変数 FOO を参照します。

### ActionSetVariable [#ActionSetVariable]

ActionSetVariable は、変数の値を設定します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionSetVariable|ACTIONRECORDHEADER|ActionCode = 0x1D|

ActionSetVariable は、次のことを行います。

1. スタックから値をポップする
1. 設定する変数名を表す名前をスタックからポップする
1. 現在の実行コンテキストにある変数名に値をセットします。

他の実行コンテキスト中の変数は、変数名にターゲットパスとコロンからなる接頭辞を付けて参照します。
例えば /A/B:FOO は、 /A/B にあるムービークリップの変数 FOO を参照します。

### 移動 [#u331bbd4]
* 前のページ : [フロー制御](アクション_SWF_4_アクションモデル_フロー制御)
* 次のページ : [ムービー制御](アクション_SWF_4_アクションモデル_ムービー制御)
