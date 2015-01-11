## SymbolClass [#n3e63162]

SymbolClass タグは、 SWF ファイル内のシンボルと ActionScript 3.0 クラスとの紐付けに使用されます。
これは、ExportAssets タグの ActionScript 3.0 版です。
キャラクタ ID が 0 の場合、クラスが SWF のメインタイムラインに紐付けられます。
これは、 SWF の root クラスを意味します。

SymbolClass タグ内のクラス一覧は、他の SWF ファイルで使うことができます
(StartSound2, DefineEditText (HasFontClass), PlaceObject3 (PlaceFlagHasClassName, PlaceFlagHasImage) 参照)。

例えば、ある SWF ファイルに埋め込まれたカスタムフォントの Font クラスをエクスポートして、同じ Web サイト上の 10 個の SWF ファイル間で共有するというようなことができます。


### SymbolClass [#yafccf3f]

|フィールド|型|コメント|
| --- | --- | --- |
|Header|[RECORDHEADER](SWFの構造要約_タグのフォーマット)|タグタイプ = 76|
|NumSymbols|[UI16](基本的なデータ型_整数型とバイトオーダー)|このタグにより紐付けるシンボルの数|
|Tag1|[UI16](基本的なデータ型_整数型とバイトオーダー)|シンボルに紐付けるための&br;16 bit のキャラクタタグ ID|
|Name1|[STRING](基本的なデータ型_文字列の値)|シンボルに紐付けるための&br;ActionScript 3.0 クラスの fully-qualified なクラス名&br;このクラスは、 DoABC タグにより既に宣言されている必要がある|
|・&br;・&br;・|||
|TagN|[UI16](基本的なデータ型_整数型とバイトオーダー)|シンボル N のタグ ID|
|NameN|[STRING](基本的なデータ型_文字列の値)|シンボル N の fully-qualified なクラス名|

### 移動 [#u331bbd4]
* 前のページ : [ImportAssets2](制御タグ_ImportAssets2)
* 次のページ : [Metadata](制御タグ_Metadata)
