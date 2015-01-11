## PlaceObject2 [#x2482337]

PlaceObject2 タグは、PlaceObject タグの機能を拡張したものです。
PlaceObject2 タグはキャラクタを表示リストに追加すること、既に表示リストに存在するキャラクタの属性を変更することの両方が可能です。
PlaceObject2 タグは SWF 4 ～ 5 にかけてわずかに変更されました。SWF 5 では、__クリップアクション__ が使用可能になります。

このタグはフラグのグループから始まり、どのフィールドを使用するかを示します。
CharacterId, Matrix, ColorTransform, Ratio, ClipDepth, Name, ClipActions がオプションで使用可能です。
Depth フィールドだけは常に必要となります。

depth は キャラクタのスタック順を決定します。
低い depth のキャラクタは、高い depth のキャラクタの下に表示されます。
depth が 1 のキャラクタは、スタックの一番下に表示されます。
1 つのキャラクタには、 1 つだけの depth が与えられます。
これは、表示リスト中のキャラクタが depth により一意に定まることを意味します (CharacterId を必要としません)。

PlaceFlagMove と PlaceFlagHasCharacter タグは、キャラクタを新しく表示リストに追加するか、既に表示リストに存在するキャラクタを変更するか、どちらか 1 つを指します。

フラグの意味は次の通りです。

* PlaceFlagMove = 0 かつ PlaceFlagHasCharacter = 1
新しいキャラクタ (CharacterId を持った) が、表示リストの指定した depth に配置されます。他のフィールドは新しいキャラクタの属性をセットします。

* PlaceFlagMove = 1 かつ PlaceFlagHasCharacter = 0
指定した depth のキャラクタを変更します。他のフィールドの内容で、このキャラクタの属性を変更します。depth がキャラクタごとに 1 つずつ別の値を割り当てられるので、キャラクタの特定に CharacterId フィールドを必要としません。

* PlaceFlagMove = 1 かつ PlaceFlagHasCharacter = 1
指定した depth のキャラクタを取り除き、新しいキャラクタ (CharacterId を持った)を指定した depth に配置します。他のフィールドは、新しいキャラクタの属性に使用されます。

例えば、一続きのフレームにまたがって移動するキャラクタの、最初のフレームで PlaceFlagHasCharacter がセットされていて、 PlaceFlagMove がそれ以降のフレームでセットされるとします。最初のフレームでは指定した depth と変形行列でキャラクタを作成します。続くフレームでは指定した depth にあるキャラクタの変形行列を入れ替えます。

PlaceObject2 のオプションのフィールドは次のような意味になります。

* CharacterId フィールドは表示リストに追加するキャラクタを指定します。
CharacterId は、新しいキャラクタを追加しようとする時にのみ使われます。
既に表示リストに存在するキャラクタを変形しようとするときは CharacterId フィールドを使いません。
* Matrix フィールドは位置・拡大縮小・回転を指定します。新しくキャラクタを作成する時、変更する時の両方で使います。
* ColorTransform フィールドは色の変化を適用します。新しくキャラクタを作成する時、変更する時の両方で使います。
* Ratio フィールドはモーフィングの比率を指定します。新しくキャラクタを作成する時、変更する時の両方で使います。このフィールドは、キャラクタが DefineMorphShape を使って定義されている時にのみ適用され、モーフィングの適用度を調整します。Ratio が 0 の時はモーフィング開始時の状態、Ratio が 65535 の時はモーフィングが終わった時の状態でキャラクタを表示します。値は 0 ～ 65535 の間で指定でき、中間の状態は Flash Player が補完して表示します。
* ClipDepth フィールドはキャラクタの追加時に使用され、マスクしたい depth の一番上の値を指定します。ClipDepth が 0 の時はキャラクタのクリッピングを行いません。
* Name フィールドはキャラクタの名前を指定します。新しくキャラクタを作成する時、変更する時の両方で使います。このフィールドは通常、スプライトと共に使用され、SetTarget アクションでスプライトを特定する時に使います。これは、スプライト内部でアクションが実行できるようにします。
* ClipActions フィールドは、スプライトキャラクタを配置する時にのみ有効になります。これは、イベントハンドラを定義するために使用します。



### PlaceObject2 [#ba8b20fb]

最小のファイルフォーマットバージョンは SWF 3 です。

|フィールド|型|コメント|
| --- | --- | --- |
|Header|[RECORDHEADER](SWFの構造要約_タグのフォーマット)|タグタイプ = 26|
|PlaceFlagHasClipActions|[UB](基本的なデータ型_ビット値)[1]|SWF 5 以降: クリップアクション有り = 1 (スプライトキャラクタのみ)&br;他の場合: 常に 0|
|PlaceFlagHasClipDepth|[UB](基本的なデータ型_ビット値)[1]|クリップ depth 有り|
|PlaceFlagHasName|[UB](基本的なデータ型_ビット値)[1]|name 有り|
|PlaceFlagHasRatio|[UB](基本的なデータ型_ビット値)[1]|ratio 有り|
|PlaceFlagHasColorTransform|[UB](基本的なデータ型_ビット値)[1]|色変換有り|
|PlaceFlagHasMatrix|[UB](基本的なデータ型_ビット値)[1]|matrix 有り|
|PlaceFlagHasCharacter|[UB](基本的なデータ型_ビット値)[1]|キャラクタの配置|
|PlaceFlagMove|[UB](基本的なデータ型_ビット値)[1]|キャラクタの移動の定義|
|Depth|[UI16](基本的なデータ型_整数型とバイトオーダー)|キャラクタの深度|
|CharacterId|If PlaceFlagHasCharacter [UI16](基本的なデータ型_整数型とバイトオーダー)|配置するキャラクタの ID|
|Matrix|If PlaceFlagHasMatrix [MATRIX](基本的なデータ型_MATRIX_レコード)|変形行列データ|
|ColorTransform|If PlaceFlagHasColorTransform [CXFORMWITHALPHA](基本的なデータ型_アルファ値付き色変換レコード)|色変換データ|
|Ratio|If PlaceFlagHasRatio [UI16](基本的なデータ型_整数型とバイトオーダー)||
|Name|If PlaceFlagHasName [STRING](基本的なデータ型_文字列の値)|キャラクタの名前|
|ClipDepth|If PlaceFlagHasClipDepth [UI16](基本的なデータ型_整数型とバイトオーダー)|Clip depth (クリッピングレイヤー参照)|
|ClipActions|If PlaceFlagHasClipActions CLIPACTIONS|SWF5 以降: クリップアクションデータ|

### CLIPACTIONS [#ClipActions]

クリップアクションはスプライトキャラクタでのみ有効になります。
クリップアクションはスプライトキャラクタのイベントハンドラを定義します。

|フィールド|型|コメント|
| --- | --- | --- |
|Reserved|[UI16](基本的なデータ型_整数型とバイトオーダー)|常に 0|
|AllEventFlags|[CLIPEVENTFLAGS](表示リスト_表示リストタグ_ClipEventFlags)|クリップアクションで使用される全てのイベント|
|ClipActionRecords|CLIPACTIONRECORD [1 つ以上]|個々のイベントハンドラ|
|ClipActionEndFlag|If SWF version <= 5, [UI16](基本的なデータ型_整数型とバイトオーダー)&br;If SWF version >= 6, [UI32](基本的なデータ型_整数型とバイトオーダー)|常に 0|

### CLIPACTIONRECORD [#CLIPACTIONRECORD]

|フィールド|型|コメント|
| --- | --- | --- |
|EventFlags|[CLIPEVENTFLAGS](表示リスト_表示リストタグ_ClipEventFlags)|このハンドラで適用するイベント|
|ActionRecordSize|[UI32](基本的なデータ型_整数型とバイトオーダー)|このフィールド以降で次の CLIPACTIONRECORD (または ClipActionEndFlag) までのバイトオフセット|
|KeyCode|If EventFlags contain ClipEventKeyPress: [UI8](基本的なデータ型_整数型とバイトオーダー)&br;Otherwise absent|トラップするキーコード (DefineButton2 参照)|
|Actions|[ACTIONRECORD](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionRecord) [1 つ以上]|実行するアクション|

### 移動 [#u331bbd4]
* 前のページ : [PlaceObject](表示リスト_表示リストタグ_PlaceObject)
* 次のページ : [PlaceObject3](表示リスト_表示リストタグ_PlaceObject3)
