## フロー制御 [#z5d69556]

### ActionJump [#ActionJump]

ActionJump は、無条件分岐を作成します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionJump|ACTIONRECORDHEADER|ActionCode = 0x99|
|BranchOffset|SI16|オフセット|

ActionJump は BranchOffset フィールドのバイト数をプログラムカウンタに加算します。
オフセットは符号付きの値です。分岐は –32,768 バイトから 32,767 バイトの範囲で行われます。
オフセット 0 は、 ActionJump アクションのすぐ次のアクションを指します。

### ActionIf [#ActionIf]

ActionIf は、条件テスト付きの分岐を作成します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionIf|ACTIONRECORDHEADER|ActionCode = 0x9D|
|BranchOffset|SI16|オフセット|

ActionIf は次のことを行います。

1. 数値の ''Condition'' をスタックから取得します。
1. ''Condition'' を Boolean に変換します。
1. ''Condition'' が true かどうかテストします。
__Condition__ が true の時、 BranchOffset フィールドのバイト数をプログラムカウンタに加算します。

```
(注)
SWF 4 ファイルを再生中の時は、 ''Condition'' は Boolean に変換されません。
true ではないことの代わりに 0 と比較されます。
```

オフセットは符号付きの値です。分岐は –32,768 バイトから 32,767 バイトの範囲で行われます。
オフセット 0 は、 ActionIf アクションのすぐ次のアクションを指します。

### ActionCall [#ActionCall]

ActionCall は、サブルーチンを呼び出します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionCall|ACTIONRECORDHEADER|ActionCode = 0x9E|

ActionCall は次のことを行います。

1. 値をスタックからポップします。
この値は、フレームラベルにマッチする文字列か、もしくはフレーム番号を指す数値になります。
ムービークリップ中の、これから呼ばれるフレームを識別するための文字列は接頭辞を使うことができます。
1. フレームの場所を見つけられた時は、目的のフレームに含まれるアクションを実行します。
目的のフレームのアクションを実行した後は、 ActionCall 命令の後からまた実行が再開されます。
1. フレームが見つからなかった時は何も行いません。

### 移動 [#u331bbd4]
* 前のページ : [型変換](アクション_SWF_4_アクションモデル_型変換)
* 次のページ : [変数](アクション_SWF_4_アクションモデル_変数)

