## ScriptLimits [#ma40ec58]

ScriptLimits タグには 2 つのフィールドがあり、デフォルトの最大再帰深度と ActionScript のタイムアウト時間をオーバーライドします。

MaxRecursionDepth フィールドは、 ActionScript の最大再帰制限を指定します。
デフォルトでは 256 にセットされています。これは、 0 より大きい数で変更することが可能です。

ScriptTimeoutSeconds フィールドは、 ActionScript の最大処理秒数を指定します。
これは、警告ダイアログボックスが表示されるまでの秒数で、停止するかそのまま続行するか選ぶことができます。
デフォルト値はプラットフォームによって違い、 15 ～ 20 秒の範囲で設定されています。
このデフォルト値は変更可能です。

ScriptLimits は、 SWF 7 以降で使用可能です。

### ScriptLimits [#b8baef3e]

|フィールド|型|コメント|
| --- | --- | --- |
|Header|[RECORDHEADER](SWFの構造要約_タグのフォーマット)|タグタイプ = 65|
|MaxRecursionDepth|[UI16](基本的なデータ型_整数型とバイトオーダー)|再帰の最大の深さ|
|ScriptTimeoutSeconds|[UI16](基本的なデータ型_整数型とバイトオーダー)|警告ダイアログボックスが表示されるまでの&br;ActionScript の最大実行時間|

### 移動 [#u331bbd4]
* 前のページ : [EnableDebugger2](制御タグ_EnableDebugger2)
* 次のページ : [SetTabIndex](制御タグ_SetTabIndex)
