## PlaceObject [#b72ee706]

PlaceObject タグは、キャラクタを表示リストに追加します。
CharacterId によって追加するキャラクタを特定します。
Depth フィールドはキャラクタのスタック順を指定します。
Matrix フィールドはキャラクタの位置・拡大縮小・回転を指定します。
PlaceObject タグのサイズが Matrix フィールドの最後の場所を超える場合は、レコードに ColorTransform フィールドが付加されていると仮定します。
ColorTransform フィールドは、色の効果を指定します (透明度のような)。これはキャラクタに適用されます。
表示リストには 1 回以上、同じキャラクタを異なる深度と変形行列を使って追加できます。

```
(注)
PlaceObject は、 SWF 3 以降のバージョンでは滅多に使われることはありません。
これは、 PlaceObject2 と PlaceObject3 に置き換えられました。
```

### PlaceObject [#n9fe2ee9]
|フィールド|型|コメント|
| --- | --- | --- |
|Header|[RECORDHEADER](SWFの構造要約_タグのフォーマット)|タグタイプ = 4|
|CharacterId|[UI16](基本的なデータ型_整数型とバイトオーダー)|配置するキャラクタの ID|
|Depth|[UI16](基本的なデータ型_整数型とバイトオーダー)|キャラクタの深度|
|Matrix|[MATRIX](基本的なデータ型_MATRIX_レコード)|変形行列データ|
|ColorTransform (オプション)|[CXFORM](基本的なデータ型_色変換レコード)|色変換データ|

### 移動 [#u331bbd4]
* 前のページ : [表示リストタグ](表示リスト_表示リストタグ)
* 次のページ : [PlaceObject2](表示リスト_表示リストタグ_PlaceObject2)
