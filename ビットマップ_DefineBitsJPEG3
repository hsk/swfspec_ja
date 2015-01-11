## DefineBitsJPEG3 [#x2a64eb0]

|フィールド|型|コメント|
| --- | --- | --- |
|Header|RECORDHEADER (long)|タグタイプ = 35|
|CharacterID|UI16|このキャラクタの ID|
|AlphaDataOffset|UI32|ImageData のバイト数|
|ImageData|UI8[データサイズ]|JPEG, PNG, GIF89a のいずれかの圧縮済み画像データ|
|BitmapAlphaData|UI8[アルファデータサイズ]|ZLIB で圧縮されたアルファデータの配列。&br;タグに JPEG データが含まれる場合にのみサポートされる。&br;1 バイトが 1 ピクセルにそれぞれ対応する。&br;解凍後のサイズは JPEG 画像の (width * height) に一致しなければならない (must)。|
