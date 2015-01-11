## FrameLabel [#zeee9f1e]

FrameLabel タグは、現在のフレームに名前を付与します。
ActionGoToLabel で、フレームを特定するためにこの名前を使用します。
SWF 3 以降で使用可能です。

### FrameLabel [#g6b776ab]

|フィールド|型|コメント|
| --- | --- | --- |
|Header|[RECORDHEADER](SWFの構造要約_タグのフォーマット)|タグタイプ = 43|
|Name|[STRING](基本的なデータ型_文字列の値)|フレームの名前|

SWF 6 以降では、FrameLabel タグの __名前付きアンカー__ の拡張が使用可能です。
名前付きアンカーは特別な種類のフレームラベルで、 [ActionGoToLabel](アクション_SWF_3_アクションモデル#ActionGoToLabel) を使ってフレームを検索されます。検索時は HTML シンタックスが使われます。
ブラウザのプラグイン版でバージョン 6 以降の Flash Player は、ブラウザのロケーションバーの URL のアンカー指定がチェックされます (URL の最後に付いた、 #anchorname のような部分です)。ロケーションバーでアンカー指定がある場合、 Flash Player は同じ名前の付いた、名前付きアンカー付きの FrameLabel  タグから再生を開始します (名前が存在する場合)。それ以外の場合は、通常、フレーム 1 から再生されます。 Flash Player が名前付きアンカーのフレームに到達した時、アンカー指定をブラウザのロケーションバーに追加します。
この機能により、ユーザがブックマークに URL を追加して、SWF ファイルの同じポイントに戻ってくることができるようになります。
名前付きアンカーを作成する時は、アンカー名の終端 null バイトの後に、null でないバイトを挿入します。
これは SWF 6 以降で使用可能です。

### NamedAnchor [#p85b5e71]

|フィールド|型|コメント|
| --- | --- | --- |
|Header|[RECORDHEADER](SWFの構造要約_タグのフォーマット)|タグタイプ = 43|
|Name|Null-terminated [STRING](基本的なデータ型_文字列の値). (0 is NULL)|フレームのラベル|
|Named Anchor flag|[UI8](基本的なデータ型_整数型とバイトオーダー)|常に 1|


### 移動 [#u331bbd4]
* 前のページ : [SetBackgroundColor](制御タグ_SetBackgroundColor)
* 次のページ : [Protect](制御タグ_Protect)
