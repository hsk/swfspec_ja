## DefineBitsJPEG4 [#x2a64eb0]

|フィールド|型|コメント|
| --- | --- | --- |
|Header|RECORDHEADER (long)|タグタイプ = 90|
|CharacterID|UI16|このキャラクタの ID|
|AlphaDataOffset|UI32|ImageData のバイト数|
|DeblockParam|UI16|デブロッキングフィルターに渡すパラメータを提供する。&br;デブロッキングフィルターの強さを 0 ～ 100% で、 8.8 固定小数点形式を使って指定する。|
|ImageData|UI8[データサイズ]|JPEG, PNG, GIF89a のいずれかの圧縮済み画像データ|
|BitmapAlphaData|UI8[アルファデータサイズ]|ZLIB で圧縮されたアルファデータの配列。&br;タグに JPEG データが含まれる場合にのみサポートされる。&br;1 バイトが 1 ピクセルにそれぞれ対応する。&br;解凍後のサイズは JPEG 画像の (width * height) に一致しなければならない (must)。|
