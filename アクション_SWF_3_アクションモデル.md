## SWF 3 アクションモデル [#rc340ad1]

SWF 3 のアクションモデルは、 11 個の命令から成ります。

|命令|参照|説明|
| --- | --- | --- |
|Play|[ActionPlay](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionPlay)|現在のフレームの再生を開始|
|Stop|[ActionStop](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionStop)|現在のフレームの再生を停止|
|NextFrame|[ActionNextFrame](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionNextFrame)|次のフレームに移動|
|PreviousFrame|[ActionPreviousFrame](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionPreviousFrame)|前のフレームに移動|
|GotoFrame|[ActionGotoFrame](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionGotoFrame)|指定されたフレームに移動|
|GotoLabel|[ActionGoToLabel](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionGoToLabel)|指定されたラベルの付いたフレームに移動|
|WaitForFrame|[ActionWaitForFrame](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionWaitForFrame)|指定されたフレームで停止|
|GetURL|[ActionGetURL](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionGetURL)|指定された URL の取得|
|StopSounds|[ActionStopSounds](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionStopSounds)|再生中のサウンドを全て停止|
|ToggleQuality|[ActionToggleQuality](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionToggleQuality)|表示品質を High と Low で切り替え|
|SetTarget|[ActionSetTarget](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionSetTarget)|次のアクションのコンテキストを名前の付いたオブジェクトに切り替え|

上のリストのアクションは、ボタンの状態遷移時もしくは SWF 3 アクションによって起動されます。
アクションはその場で実行されるのではなく、後で実行するためにリストに追加されていきます。
このリストは、 ShowFrame タグかボタンの状態が変わった時に実行されます。
この時、リストの中のアクションから他のアクションを呼び出すことができます。
アクションは、空になるまで実行されます。
デフォルトでは、タイムラインアクションの Stop 、 Play 、 GoToFrame は、それが含まれるファイル自身に適用されます。
しかし、 SetTarget アクションは、 Flash ユーザインターフェイスの中の __Tell ターゲット (Tell Target)__ を呼び、常にアクションコマンドは他のファイルかスプライトに送られます。

### 移動 [#u331bbd4]
* 前のページ : [[アクション]]
* 次のページ : [SWF 3 アクション](アクション_SWF_3_アクションモデル_SWF_3_アクション)
