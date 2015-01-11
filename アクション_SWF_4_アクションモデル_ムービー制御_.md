## ムービー制御 [#pcb63ee1]

### ActionGetURL2 [#ActionGetURL2]

ActionGetURL2 は、 URL からデータを取得します (スタックベース版)。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionGetURL2|ACTIONRECORDHEADER|ActionCode = 0x9A&br;Length は常に 1|
|SendVarsMethod|UB[2]|0 = None&br;1 = GET&br;2 = POST|
|Reserved|UB[4]|常に 0|
|LoadTargetFlag|UB[1]|0 = ターゲットはブラウザのウインドウ&br;1 = ターゲットはスプライトへのパス|
|LoadVariablesFlag|UB[1]|0 = ロードする内容は変数でない&br;1 = ロードする内容は変数|

ActionGetURL2 は次のことを行います。

1. ''Target'' をスタックからポップする
* LoadTargetFlag が 0 の時、 ''Target'' はウインドウになる。
__Target__ を空文字列にすると、現在のウインドウを指す。
* LoadTargetFlag が 1 の時、 ''Target'' はスプライトへのパスになる。
__Target__ パスはスラッシュまたはドットを使ったシンタックスで表記する。
1. スタックから ''URL'' をポップする
__URL__ は検索する URL を指定する。
1. SendVarsMethod フィールドで、 HTTP リクエスト時の method を指定する。
* SendVarsMethod が 0 の時、フォームリクエストではない状態になり、ムービークリップの変数はエンコードと送信が行われない。
* SendVarsMethod が 1 の時、 HTTP GET リクエストを指定する。
* SendVarsMethod が 2 の時、 HTTP POST リクエストを指定する。
1. SendVarsMethod が 1 (GET) か 2 (POST) の時、現在のムービークリップの変数は x-www-form-urlencoded エンコーディングで  ''URL'' に送信される。

LoadVariablesFlag がセットされている時、サーバからのレスポンスの MIME タイプが application/x-www-form-urlencoded で、 body が __var1=value1&var2=value2&...&varx=valuex__ というような形式になっていると仮定します。
このレスポンスは、画面に表示される代わりに、 ActionScript の変数化されます。
LoadTargetFlag が 0 の時は、この変数はタイムライン変数となり、 LoadTargetFlag が 1 の時は、指定されたスプライトの変数となります。

LoadVariablesFlag を指定しない状態で LoadTargetFlag が指定された時は、サーバからのレスポンスの MIME タイプが application/x-shockwave-flash で、 body が SWF ファイルであると仮定されます。
このレスポンスは、 HTML ドキュメントとしてではなく、 子ファイルとして指定されたスプライトにロードされます。


### ActionGotoFrame2 [#ActionGotoFrame2]

ActionGotoFrame2 は、 フレームに移動します (スタックベース版)。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionGotoFrame2|ACTIONRECORDHEADER|ActionCode = 0x9F|
|Reserved|UB[6]|常に 0|
|SceneBiasFlag|UB[1]|シーンバイアスフラグ|
|Play flag|UB[1]|0 = フレームに移動した後停止&br;1 = フレームに移動した後再生|
|SceneBias|If SceneBiasFlag = 1, UI16|スタックの引数により指定されたフレームに追加する数|

ActionGotoFrame2 は次のことを行います。

1. スタックから ''frame'' を 1 つポップする
* ''frame'' が数値の時、数値を n とすると、次に表示されるフレームは、現在のムービークリップの n 番目のフレームになる。
* ''frame'' が文字列の時、 ''frame'' はフレームラベルとして扱われる。現在のムービークリップにラベルが存在する時、そのラベルの付いたフレームが現在のフレームになる。他の場合、アクションは無視される。
1. ''frame'' のラベルか数値は、ターゲットパスの接頭辞を付けることができる。
例えば、 /MovieClip:3 もしくは /MovieClip:FrameLabel のようにする。
1. Play flag がセットされている時、指定されたフレームに移動した後、それを囲むムービークリップの再生が開始される。
セットされていない場合、指定されたフレームに移動した後、停止する。

### ActionSetTarget2 [#ActionSetTarget2]

ActionSetTarget2 は、現在のコンテキストを設定します (スタックベース版)。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionSetTarget2|ACTIONRECORDHEADER|ActionCode = 0x20|

ActionSetTarget2 は、ターゲットをスタックからポップし、それを現在のアクティブコンテキストに設定します。
このアクションは [ActionSetTarget](アクション_SWF_3_アクションモデル#ActionSetTarget) とほぼ同じ動作をしますが、式の評価結果をターゲットパスとして使用することができます。

### ActionGetProperty [#ActionGetProperty]

ActionGetProperty は、ファイルプロパティを取得します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionGetProperty|ACTIONRECORDHEADER|ActionCode = 0x22|

ActionGetProperty は、次のことを行います。

1. スタックから ''index'' をポップします。
1. スタックから ''target'' をポップします。
1. ターゲットパス ''target'' にあるムービークリップの、列挙されたプロパティの中の ''index'' から値を取得し、スタックにプッシュします。

次の表は、プロパティインデックスのリストです。
_quality, _xmouse, _ymouse プロパティは、 SWF 5 以降で使用可能です。

|プロパティ|値|
| --- | --- |
|_X|0|
|_Y|1|
|_xscale|2|
|_yscale|3|
|_currentframe|4|
|_totalframes|5|
|_alpha|6|
|_visible|7|
|_width|8|
|_height|9|
|_rotation|10|
|_target|11|
|_framesloaded|12|
|_name|13|
|_droptarget|14|
|_url|15|
|_highquality|16|
|_focusrect|17|
|_soundbuftime|18|
|_quality|19|
|_xmouse|20|
|_ymouse|21|

### ActionSetProperty [#ActionSetProperty]

ActionSetProperty は、ファイルプロパティをセットします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionSetProperty|ACTIONRECORDHEADER|ActionCode = 0x23|

ActionSetProperty は、次のことを行います。

1. ''value'' をスタックからポップする
1. ''index'' をスタックからポップする
1. ''target'' をスタックからポップする
1. ターゲットパス ''target'' にあるムービークリップの、列挙されたプロパティの中の ''index'' の内容を ''value'' に設定します。

### ActionCloneSprite [#ActionCloneSprite]

ActionCloneSprite は、スプライトをコピー (クローン) します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionCloneSprite|ACTIONRECORDHEADER|ActionCode = 0x24|

ActionCloneSprite は、次のことを行います。

1. ''depth'' をスタックからポップする
1. ''target'' をスタックからポップする
1. ''source'' をスタックからポップする
1. ''source'' で指定されたムービークリップを、新しい名前 ''target'' を使ってコピーし、Z オーダー ''depth'' に配置します。

### ActionRemoveSprite [#ActionRemoveSprite]

ActionRemoveSprite は、クローンスプライトを取り除きます。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionRemoveSprite|ACTIONRECORDHEADER|ActionCode = 0x25|

ActionRemoveSprite は、次のことを行います。

1. ''target'' をスタックからポップする
1. ターゲットパス ''target'' で指定されたクローンスプライトを取り除きます。

### ActionStartDrag [#ActionStartDrag]

ActionStartDrag は、ムービークリップのドラッグを開始します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionStartDrag|ACTIONRECORDHEADER|ActionCode = 0x27|

ActionStartDrag は、次のことを行います。

1. ''target'' をスタックからポップする
__target__ は、ドラッグするムービークリップの識別子です。
1. ''lockcenter'' をスタックからポップする
__lockcenter__ が 0 でない場合、ドラッグするムービークリップの中心がマウスのポジションに固定されます。
0 の場合、ドラッグするムービークリップはマウスのポジションからの相対的な位置にドラッグ開始時に移動されます。
1. ''constrain'' をスタックからポップする
1. ''constrain'' が 0 でない場合、
* y2 をスタックからポップする
* x2 をスタックからポップする
* y1 をスタックからポップする
* x1 をスタックからポップする

### ActionEndDrag [#ActionEndDrag]

ActionEndDrag は、ドラッグ操作を終了します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionEndDrag|ACTIONRECORDHEADER|ActionCode = 0x28|

### ActionWaitForFrame2 [#ActionWaitForFrame2]

ActionWaitForFrame2 は、フレームのロード完了を待ちます (スタックベース版)。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionWaitForFrame2|ACTIONRECORDHEADER|ActionCode = 0x8D&br;Length は常に 1|
|SkipCount|UI8|スキップするアクションの数|

ActionWaitForFrame2 は、次のことを行います。

1. ''frame'' をスタックからポップする
1. ''frame'' がロードされている時、現在のアクションの次の n 個のアクションをスキップします。n は SkipCount で指定します。（仕様書ミス、実際にはロードされていない時にスキップする）

__frame__ の値は、 [ActionGotoFrame2](#ActionGotoFrame2) と同じ方法で評価されます。

### 移動 [#u331bbd4]
* 前のページ : [変数](アクション_SWF_4_アクションモデル_変数)
* 次のページ : [ユーティリティ](アクション_SWF_4_アクションモデル_ユーティリティ)
