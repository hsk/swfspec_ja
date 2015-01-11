## EnableDebugger2 [#i6de1e05]

EnableDebugger2 タグは、デバッグを有効にします。
Password フィールドは、 Protect タグと同様に MD5 アルゴリズムでハッシュ化されます。
EnableDebugger2 は SWF 6 以降で使用可能です。

### EnableDebugger2 [#e691579e]

|フィールド|型|コメント|
| --- | --- | --- |
|Header|[RECORDHEADER](SWFの構造要約_タグのフォーマット)|タグタイプ = 64|
|Reserved|[UI16](基本的なデータ型_整数型とバイトオーダー)|常に 0|
|Password|Null-terminated [STRING](基本的なデータ型_文字列の値). (0 is NULL)|MD5 ハッシュ化されたパスワード|

### 移動 [#u331bbd4]
* 前のページ : [EnableDebugger](制御タグ_EnableDebugger)
* 次のページ : [ScriptLimits](制御タグ_ScriptLimits)
