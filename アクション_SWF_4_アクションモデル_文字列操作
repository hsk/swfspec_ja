## 文字列操作 [#h434919c]

### ActionStringEquals [#ActionStringEquals]

ActionStringEquals は、2 つの文字列が等しいかテストします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionStringEquals|ACTIONRECORDHEADER|ActionCode = 0x13|

ActionStringEquals は、次のことを行います。

1. 値 A をスタックからポップする
1. 値 B をスタックからポップする
1. A と B の 2 つの文字列を比較する。
比較時は大文字小文字が区別される。
1. 2 つの文字列が等しい時、
SWF 5 以降: true がスタックにプッシュされる。
SWF 4: 1 がスタックにプッシュされる。
1. 等しくない時、
SWF 5 以降: false がスタックにプッシュされる。
SWF 4: 0 がスタックにプッシュされる。

### ActionStringLength [#ActionStringLength]

ActionStringLength は、1 つの文字列の長さを取得します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionStringLength|ACTIONRECORDHEADER|ActionCode = 0x14|

ActionStringLength は、次のことを行います。

1. 文字列をスタックからポップする
1. 文字列の長さを測って、スタックにプッシュする

### ActionStringAdd [#ActionStringAdd]

ActionStringAdd は、2 つの文字列を連結します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionStringAdd|ACTIONRECORDHEADER|ActionCode = 0x21|

ActionStringAdd は、次のことを行います。

1. 値 A をスタックからポップする
1. 値 B をスタックからポップする
1. BA の順番で文字列を連結し、スタックにプッシュする

### ActionStringExtract [#ActionStringExtract]

ActionStringExtract は、文字列の一部分を取り出します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionStringExtract|ACTIONRECORDHEADER|ActionCode = 0x15|

ActionStringExtract は、次のことを行います。

1. 数値の ''count'' をスタックからポップする
1. 数値の ''index'' をスタックからポップする
1. 文字列の ''string'' をスタックからポップする
1. ''string'' の、 ''index'' から始まる ''count'' 文字数分を取り出してスタックにプッシュする
1. ''index'' か ''count'' が整数でない場合は結果が空文字列になる

### ActionStringLess [#ActionStringLess]

ActionStringLess は、文字列が他の文字列より小さいかテストします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionStringLess|ACTIONRECORDHEADER|ActionCode = 0x29|

ActionStringLess は、次のことを行います。

1. 値 A をスタックからポップする
1. 値 B をスタックからポップする
1. バイトごとの比較で B < A となる場合、
SWF 5 以降: true をスタックにプッシュする
SWF 4: 1 をスタックにプッシュする
1. 他の場合、
SWF 5 以降: false をスタックにプッシュする
SWF 4: 0 をスタックにプッシュする

### ActionMBStringLength [#ActionMBStringLength]

ActionMBStringLength は、マルチバイト文字列の長さを取得します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionMBStringLength|ACTIONRECORDHEADER|ActionCode = 0x31|

ActionMBStringLength は、次のことを行います。

1. 文字列をスタックからポップする
1. 文字列の長さを測ってスタックにプッシュする。

これはマルチバイト版の ActionStringLength です。
2 バイト文字をサポートするシステムでは、 2 バイト文字が 1 文字としてカウントされます。

### ActionMBStringExtract [#ActionMBStringExtract]

ActionMBStringExtract は、マルチバイト文字列の長さを取得します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionMBStringExtract|ACTIONRECORDHEADER|ActionCode = 0x35|

ActionMBStringExtract は、次のことを行います。

1. 数値の ''count'' をスタックからポップする
1. 数値の ''index'' をスタックからポップする
1. 文字列の ''string'' をスタックからポップする
1. ''string'' の、 ''index'' から始まる ''count'' 文字数分を取り出してスタックにプッシュする
1. ''index'' か ''count'' が整数でない場合は結果が空文字列になる

これはマルチバイト版の ActionStringExtract です。
2 バイト文字をサポートするシステムでは、 2 バイト文字が 1 文字としてカウントされます。

### 移動 [#u331bbd4]
* 前のページ : [論理演算](アクション_SWF_4_アクションモデル_論理演算)
* 次のページ : [型変換](アクション_SWF_4_アクションモデル_型変換)
