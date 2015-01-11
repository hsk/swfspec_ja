## 型変換 [#d94b704a]

### ActionToInteger [#ActionToInteger]

ActionToInteger は、 1 つの値を整数型に変換します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionToInteger|ACTIONRECORDHEADER|ActionCode = 0x18|

ActionToInteger は、次のことを行います。

1. スタックから値を 1 つポップします。
1. 値を数値に変換します。
1. 小数点以降の数字を破棄し、残りを結果の整数とします。
1. 結果の整数をスタックにプッシュします。


### ActionCharToAscii [#ActionCharToAscii]

ActionCharToAscii は、 文字を ASCII コードに変換します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionCharToAscii|ACTIONRECORDHEADER|ActionCode = 0x32|

ActionCharToAscii は、次のことを行います。

1. スタックから値を 1 つポップします。
1. 最初の文字の値を、数値の ASCII 文字コードに変換します。
1. 結果の文字コードをスタックにプッシュします。


### ActionAsciiToChar [#ActionAsciiToChar]

ActionAsciiToChar は、 文字コードの値を ASCII 文字に変換します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionAsciiToChar|ACTIONRECORDHEADER|ActionCode = 0x33|

ActionAsciiToChar は、次のことを行います。

1. スタックから値を 1 つポップします。
1. 数値の値から ASCII 文字に変換します。
1. 結果の文字をスタックにプッシュします。


### ActionMBCharToAscii [#ActionMBCharToAscii]

ActionMBCharToAscii は、 マルチバイト文字を文字コードに変換します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionMBCharToAscii|ACTIONRECORDHEADER|ActionCode = 0x36|

ActionMBCharToAscii は、次のことを行います。

1. スタックから値を 1 つポップします。
1. 最初の文字の値を、数値の文字コードに変換します。
最初の文字が 2 バイト文字の一部だった場合、16 bit 幅で文字が構成されます。
最初のバイトが上位バイト、 2 番目のバイトが下位バイトとして扱われます。
1. 結果の文字コードをスタックにプッシュします。

### ActionMBAsciiToChar [#ActionMBAsciiToChar]

ActionMBAsciiToChar は、 文字コードの値をマルチバイト文字に変換します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionMBAsciiToChar|ACTIONRECORDHEADER|ActionCode = 0x37|

ActionMBAsciiToChar は、次のことを行います。

1. スタックから値を 1 つポップします。
1. 数値の値から文字に変換します。
文字が 16 bit 値 (>= 256) の場合、 2 バイト文字になります。
最初のバイトが上位バイト、 2 番目のバイトが下位バイトとして扱われます。
1. 結果の文字をスタックにプッシュします。

### 移動 [#u331bbd4]
* 前のページ : [文字列操作](アクション_SWF_4_アクションモデル_文字列操作)
* 次のページ : [フロー制御](アクション_SWF_4_アクションモデル_フロー制御)
