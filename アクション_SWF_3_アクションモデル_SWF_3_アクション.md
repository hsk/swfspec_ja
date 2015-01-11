## SWF 3 アクション [#s50f71e4]

ここで挙げられたアクションは SWF 3 で使用できます。

### DoAction [#DoAction]

DoAction は、現在のフレームが完了した時に Flash Player に対してアクションのリストを実行するように指示します。
アクションは DoAction タグがフレームのどこに出現したかということに関係なく、 ShowFrame タグが出現した時に実行されます。
SWF 9 以降では、 FileAttributes タグの ActionScript3 フィールドに 1 がセットされている時、 DoAction タグの内容は無視されます。

|フィールド|型|コメント|
| --- | --- | --- |
|Header|[RECORDHEADER](SWFの構造要約_タグのフォーマット)|タグタイプ = 12|
|Actions|[ACTIONRECORD](#ActionRecord) [0 個以上]|実行するアクションのリスト&br;(次の ActionRecord 参照)|
|ActionEndFlag|[UI8](基本的なデータ型_整数型とバイトオーダー) = 0|常に 0|

### ACTIONRECORD [#ActionRecord]

ACTIONRECORD は、 ACTIONRECORDHEADER と、それに続くアクションのデータのかたまりから成ります。
ACTIONRECORDHEADER は ActionCode を使って実行するアクションを指定します。
アクションがヘッダの後にデータを必要とする場合、 ActionCode の上位ビットは 1 にセットされます。これは ActionCode が、後に続く 16 bit の長さのアクションデータのかたまりを必要とすることを示します。
注：多くのアクションで Length 以降のデータのかたまりは指定されません。その場合、命令は 1 バイトの種類のデータのみで構成されます。

### ACTIONRECORDHEADER [#ActionRecordHeader]
|フィールド|型|コメント|
| --- | --- | --- |
|ActionCode|[UI8](基本的なデータ型_整数型とバイトオーダー)|アクションコード|
|Length|If code >= 0x80, [UI16](基本的なデータ型_整数型とバイトオーダー)|ActionCode と Length フィールドを含まない、 ACTIONRECORDHEADER のバイト数|


### ActionGotoFrame [#ActionGotoFrame]

ActionGotoFrame は、 現在のファイル中の指定されたフレームに移動する命令です。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionGotoFrame|[ACTIONRECORDHEADER](#ActionRecordHeader)|ActionCode = 0x81&br;Length は常に 2|
|Frame|[UI16](基本的なデータ型_整数型とバイトオーダー)|フレームインデックス|


### ActionGetURL [#ActionGetURL]

ActionGetURL は、 UrlString で指定された URL からデータを取得する命令です。
URL は色んなタイプにすることができます。HTML ファイル、画像または他の SWF ファイル等です。
ファイルがブラウザ上で実行されている場合、 URL から取得したデータは TargetString で指定されるフレームに表示されます。
&quot;_level0&quot; と &quot;_level1&quot; は特別なターゲット名で、他の SWF ファイルを level 0 と 1 にロードするために使用されます。


|フィールド|型|コメント|
| --- | --- | --- |
|ActionGetURL|[ACTIONRECORDHEADER](#ActionRecordHeader)|ActionCode = 0x83|
|UrlString|[STRING](基本的なデータ型_文字列の値)|ターゲット URL 文字列|
|TargetString|[STRING](基本的なデータ型_文字列の値)|ターゲット文字列|

### ActionNextFrame [#ActionNextFrame]

ActionNextFrame は、現在のファイル中の次のフレームに進める命令です。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionNextFrame|[ACTIONRECORDHEADER](#ActionRecordHeader)|ActionCode = 0x04|

### ActionPreviousFrame [#ActionPreviousFrame]

ActionPreviousFrame は、現在のファイル中の前のフレームに進める命令です。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionPrevFrame|[ACTIONRECORDHEADER](#ActionRecordHeader)|ActionCode = 0x05|

### ActionPlay [#ActionPlay]

ActionPlay は、現在のフレームから再生を開始する命令です。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionPlay|[ACTIONRECORDHEADER](#ActionRecordHeader)|ActionCode = 0x06|

### ActionStop [#ActionStop]

ActionStop は、現在のフレームで再生を停止する命令です。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionStop|[ACTIONRECORDHEADER](#ActionRecordHeader)|ActionCode = 0x07|

### ActionToggleQuality [#ActionToggleQuality]

ActionToggleQuality は、High と Low で描画品質を切り替える命令です。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionToggleQualty|[ACTIONRECORDHEADER](#ActionRecordHeader)|ActionCode = 0x08|

### ActionStopSounds [#ActionStopSounds]

ActionStopSounds は、再生中の全ての音声を停止する命令です。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionStopSounds|[ACTIONRECORDHEADER](#ActionRecordHeader)|ActionCode = 0x09|

### ActionWaitForFrame [#ActionWaitForFrame]

ActionWaitForFrame は、指定されたフレームで停止する命令です。
それ以外の場合、指定された数のアクションをスキップします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionWaitForFrame|[ACTIONRECORDHEADER](#ActionRecordHeader)|ActionCode = 0x8A&br;Length は常に 3|
|Frame|[UI16](基本的なデータ型_整数型とバイトオーダー)|停止するフレーム|
|SkipCount|[UI8](基本的なデータ型_整数型とバイトオーダー)|フレームがロードされていない時のスキップするアクションの数|

### ActionSetTarget [#ActionSetTarget]

ActionSetTarget は後に続くアクションのコンテキストを切り替える命令です。
現在のファイルの名前付きオブジェクト (TargetName) に適用します。

例えば、 SetTarget アクションはスプライトオブジェクトのタイムラインを調整する時に使うことができます。
次のアクションの順序で &quot;spinner&quot; という名前のスプライトをタイムラインの最初のフレームに送信します。

1. SetTarget &quot;spinner&quot;
1. GotoFrame zero
1. SetTarget &quot; &quot; (空文字列)
1. アクション終了 (Action code = 0)

SetTarget &quot;spinner&quot; で spinner オブジェクトを SetTarget &quot;&quot; まで適用します。
これはアクションのコンテキストを現在のファイルに戻すように指定します。
ターゲット名に関する解説は DefineSprite をご覧ください。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionSetTarget|[ACTIONRECORDHEADER](#ActionRecordHeader)|ActionCode = 0x8B|
|TargetName|[STRING](基本的なデータ型_文字列の値)|アクションターゲットのターゲット|

### ActionGoToLabel [#ActionGoToLabel]

ActionGoToLabel は、ラベルで指定されたフレームに移動する命令です。
[FrameLabel](制御タグ_FrameLabel) タグを使うことでフレームにラベルを関連付けることができます。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionGoToLabel|[ACTIONRECORDHEADER](#ActionRecordHeader)|ActionCode = 0x8C|
|Label|[STRING](基本的なデータ型_文字列の値)|フレームラベル|

### 移動 [#u331bbd4]
* 前のページ : [SWF 3 アクションモデル](アクション_SWF_3_アクションモデル)
* 次のページ : [SWF 4 アクションモデル](アクション_SWF_4_アクションモデル)
