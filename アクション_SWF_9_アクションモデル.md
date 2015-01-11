#  SWF 9 アクションモデル [#ia6db2e3]

SWF 9 では、 DoABC アクション定義タグが追加されました。
このタグには、 .abc バイトコードブロックが含まれ、 ActionScript 3.0 仮想マシンによって処理されます。
DoABC タグは、 ActionScript 3.0 バイトコードを扱うための入れ物として使われます。

↑
DoABC †
DoABC タグは DoAction に似ています (実行用のバイトコード列を定義する)。
DoABC タグに入ったバイトコードは、 ActionScript 3.0 仮想マシンで実行されます。

フィールド	型	コメント
Header	RECORDHEADER	タグタイプ = 82
Flags	UI32	32 ビットのフラグ値です。ここには次のビットセットを入れることができます。
kDoAbcLazyInitializeFlag = 1:
これは、ABC ブロックがすぐには実行されないことを示します (パースのみ可)。後で finddef が見つかった時に？実行されます。
Name	STRING	バイトコードの名前
ABCData	BYTE[]	ActionScript 3.0 仮想マシンによってパース可能な .abc バイトコードのブロックです。タグの終わりまで続きます。
ABCData フィールドのフォーマットの詳細

・Adobe ActionScript Virtual Machine 2 (AVM2) Overview
http://learn.adobe.com/wiki/display/AVM2/ActionScript+Virtual+Machine+2
http://www.adobe.com/content/dam/Adobe/en/devnet/actionscript/articles/avm2overview.pdf

移動 †
前のページ : SWF 7 アクション
次のページ : SWF 10 アクションモデル
