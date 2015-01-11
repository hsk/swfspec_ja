## ClipEventFlags [#b855efc2]

CLIPEVENTFLAGS シーケンスは、スプライトに適用するイベントハンドラのタイプを指定します。
SWF 5 以前は、 CLIPEVENTFLAGS は 2 バイトで構成され、 SWF 6 以降では 4 バイトで構成されます。

### CLIPEVENTFLAGS [#b9486589]

|フィールド|型|コメント|
| --- | --- | --- |
|ClipEventKeyUp|[UB](基本的なデータ型_ビット値)[1]|Key up イベント|
|ClipEventKeyDown|[UB](基本的なデータ型_ビット値)[1]|Key down イベント|
|ClipEventMouseUp|[UB](基本的なデータ型_ビット値)[1]|Mouse up イベント|
|ClipEventMouseDown|[UB](基本的なデータ型_ビット値)[1]|Mouse down イベント|
|ClipEventMouseMove|[UB](基本的なデータ型_ビット値)[1]|Mouse move イベント|
|ClipEventUnload|[UB](基本的なデータ型_ビット値)[1]|Clip unload イベント|
|ClipEventEnterFrame|[UB](基本的なデータ型_ビット値)[1]|Frame イベント|
|ClipEventLoad|[UB](基本的なデータ型_ビット値)[1]|Clip load イベント|
|ClipEventDragOver|[UB](基本的なデータ型_ビット値)[1]|SWF 6 以降: mouse drag over イベント&br;他の場合: 常に 0|
|ClipEventRollOut|[UB](基本的なデータ型_ビット値)[1]|SWF 6 以降: mouse rollout イベント&br;他の場合: 常に 0|
|ClipEventRollOver|[UB](基本的なデータ型_ビット値)[1]|SWF 6 以降: mouse rollover イベント&br;他の場合: 常に 0|
|ClipEventReleaseOutside|[UB](基本的なデータ型_ビット値)[1]|SWF 6 以降: mouse release outside イベント&br;他の場合: 常に 0|
|ClipEventRelease|[UB](基本的なデータ型_ビット値)[1]|SWF 6 以降: mouse release inside イベント&br;他の場合: 常に 0|
|ClipEventPress|[UB](基本的なデータ型_ビット値)[1]|SWF 6 以降: mouse press イベント&br;他の場合: 常に 0|
|ClipEventInitialize|[UB](基本的なデータ型_ビット値)[1]|SWF 6 以降: initialize イベント&br;他の場合: 常に 0|
|ClipEventData|[UB](基本的なデータ型_ビット値)[1]|Data received イベント|
|Reserved|If SWF version >= 6, [UB](基本的なデータ型_ビット値)[5]|常に 0|
|ClipEventConstruct|If SWF version >= 6, [UB](基本的なデータ型_ビット値)[1]|SWF 7 以降: construct イベント&br;他の場合: 常に 0|
|ClipEventKeyPress|If SWF version >= 6, [UB](基本的なデータ型_ビット値)[1]|Key press イベント:|
|ClipEventDragOut|If SWF version >= 6, [UB](基本的なデータ型_ビット値)[1]|Mouse drag out イベント|
|Reserved|If SWF version >= 6, [UB](基本的なデータ型_ビット値)[8]|常に 0|

SWF 6 で追加されたイベントは、Flash オーサリングツールの __ボタンムービークリップ__ 用のものです。これはスプライトの組で構成され、ボタンと同じようにスクリプトを書くことができます (BUTTONCONDACTION 参照)。
ClipEventDragOver から ClipEventPress までのイベントはボタンの状態遷移イベントです。これらはボタンイベントの説明のところに詳細が書かれています。

KeyDown と KeyUp イベントでは押されたキーを識別しません。これらのイベントのハンドラは、キーボードのキーのいずれかが押された時に実行されます (特殊なキーの場合もあります)。ハンドラの中でどのキーが押されたか特定する場合には、ActionScript の Key オブジェクトのメソッドを呼び出します。

KeyPress イベントでは、KeyDown ・ KeyUp イベントと違って、押されたキーもしくは ASCII 文字を特定します (CLIPACTIONRECORD、BUTTONCONDACTION 参照)。

### 移動 [#u331bbd4]
* 前のページ : [PlaceObject3](表示リスト_表示リストタグ_PlaceObject3)
* 次のページ : [RemoveObject](表示リスト_表示リストタグ_RemoveObject)
