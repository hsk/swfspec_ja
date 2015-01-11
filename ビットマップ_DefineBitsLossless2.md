## DefineBitsLossless2 [#l617ef6f]

|フィールド|型|コメント|
| --- | --- | --- |
|Header|RECORDHEADER (long)|タグタイプ = 36|
|CharacterID|UI16|このキャラクタの ID|
|BitmapFormat|UI8|圧縮データのフォーマット&br;3 = 8-bit カラーマップ画像&br;5 = 32-bit ARGB 画像|
|BitmapWidth|UI16|ビットマップ画像の幅|
|BitmapHeight|UI16|ビットマップ画像の高さ|
|BitmapColorTableSize|If BitmapFormat = 3, UI8&br;他の場合使用しない|色テーブルに使用する色の数 - 1。&br;最大 256 色。|
|ZlibBitmapData|If BitmapFormat = 3, ALPHACOLORMAPDATA&br;If BitmapFormat = 4 or 5, ALPHABITMAPDATA|ZLIB 圧縮されたビットマップデータ|

### ALPHACOLORMAPDATA [#ALPHACOLORMAPDATA]
|フィールド|型|コメント|
| --- | --- | --- |
|ColorTableRGB|RGBA[color table size]|Defines the mapping from color&br;indices to RGBA values.&br;Number of RGBA values is&br;BitmapColorTableSize + 1.|
|ColormapPixelData|UI8[image data size]|Array of color indices. Number&br;of entries is BitmapWidth *&br;BitmapHeight, subject to&br;padding (see note preceding&br;this table).|

### ALPHABITMAPDATA [#ALPHABITMAPDATA]
|フィールド|型|コメント|
| --- | --- | --- |
|BitmapPixelData|ARGB[image data size]|Array of pixel colors. Number of&br;entries is BitmapWidth *&br;BitmapHeight. The RGB data&br;must already be multiplied by&br;the alpha channel value.|
