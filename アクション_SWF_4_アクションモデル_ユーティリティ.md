## ユーティリティ [#f0a22bf9]

### ActionTrace [#ActionTrace]

ActionTrace は、デバッグ用の文字列を送信します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionTrace|ACTIONRECORDHEADER|ActionCode = 0x26|

ActionTrace は次のことを行います。

1. 値をスタックからポップする
1. Flash オーサリングツールの &quot;ムービーのテスト&quot; モードの場合、 ActionTrace はポップした値をデバッグウインドウに追加する
(デバッグレベルが &quot;None&quot; でない時)

Flash Player の中では何も起こりません。

### ActionGetTime [#ActionGetTime]

ActionGetTime は、 Flash Player が起動してからの時間をミリ秒単位で報告します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionGetTime|ACTIONRECORDHEADER|ActionCode = 0x34|

ActionGetTime は次のことを行います。

1. Flash Player が起動してからの時間を、ミリ秒単位の整数の値で割り出す
1. その値をスタックにプッシュする

### ActionRandomNumber [#ActionRandomNumber]

ActionRandomNumber は、乱数を生成します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionRandomNumber|ACTIONRECORDHEADER|ActionCode = 0x30|

ActionRandomNumber は次のことを行います。

1. ''maximum'' をスタックからポップする
1. 最小値 0 、最大値 (''maximum'' - 1) の範囲で、整数の乱数を生成する
1. 生成された値をスタックにプッシュする

### 移動 [#u331bbd4]
* 前のページ : [ムービー制御](アクション_SWF_4_アクションモデル_ムービー制御)
* 次のページ : [SWF 5 アクションモデル](アクション_SWF_5_アクションモデル)
