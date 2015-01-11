## SWF 6 アクション [#o6cdb9d4]

SWF 6 では、次のアクションが使用可能です。

* [DoInitAction](#DoInitAction)
* [ActionInstanceOf](#ActionInstanceOf)
* [ActionEnumerate2](#ActionEnumerate2)
* [ActionStrictEquals](#ActionStrictEquals)
* [ActionGreater](#ActionGreater)
* [ActionStringGreater](#ActionStringGreater)

### DoInitAction [#DoInitAction]

DoInitAction は、 [DoAction](アクション_SWF_3_アクションモデル#DoAction) タグと似ています。
これは、実行するための一連のバイトコードを定義します。
DoInitAction によって定義されたアクションは、DoAction により定義されたアクションの実行前に、 1 度だけ実行されます。

たまに、 ActionScript によって最初のスプライトが作られる前に、アクションが実行されないといけない場合があります。
よくあるのは、 ActionScript のスプライトクラスに関連した Object.registerClass の呼び出しです。
この呼び出しは一般的に、 ActionScript の #initclip プラグマの中に見つけることができます。
DoInitAction は、この #initclip プラグマの実装に使われます。

DoInitAction タグは、アクションを適用したいスプライトを 1 つ指定します。
1 つのフレームにいくつもの DoInitAction を含めることができます。
これらのアクションは、タグの出現した順に実行されます。
しかし、 SWF ファイル中では、 DoInitAction タグは各スプライトに 1 つだけしか含めることができません。

DoInitAction タグに含まれるアクションは、フレーム中の普通のアクションの実行前に、タグの出現時点で即時実行されます。
この動作は、 1 回目のフレーム出現時にのみ適用されます。
再生位置の調整により、後で同じフレームが出現した時には、 DoInitAction の内容はスキップされます。

SWF 9 以降で、 FileAttributes タグの ActionScript3 フィールドが 1 にセットされている場合、 DoInitAction タグに含まれる内容は無視されます。

```
(注)
DoAction タグの開始直後にアクションを設定しても、 DoInitAction タグと同じ効果は得られません。
Flash Player は、DoAction タグの最初のアクションの前に、タグに関連するスプライトオブジェクトを作成します。
DoInitAction に含まれるアクションは、それらの実行前に発生します。
```

|フィールド|型|コメント|
| --- | --- | --- |
|Header|[RECORDHEADER](SWFの構造要約_タグのフォーマット)|タグタイプ = 59|
|Sprite ID|[UI16](基本的なデータ型_整数型とバイトオーダー)|アクションを適用するスプライト|
|Actions|[ACTIONRECORD](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionRecord)[0 以上]|実行するアクションのリスト|
|ActionEndFlag|[UI8](基本的なデータ型_整数型とバイトオーダー)|常に 0|

### ActionInstanceOf [#ActionInstanceOf]

ActionInstanceOf は、 ActionScript の instanceof() 演算子を実装します。
これは Boolean 値を返す演算子で、左オペランド (通常、オブジェクト) が、右オペランドに渡したコンストラクタ関数で表されるクラスのインスタンスであるかどうかを示します。

SWF 7 以降では、 ActionInstanceOf はインターフェイスもサポートします。
右オペランドのコンストラクタに、インターフェイスオブジェクトの参照を渡し、かつ左オペランドがそのインターフェイスを実装している場合、 ActionInstanceOf は、左オペランドが右オペランドのインスタンスであるかどうか、正確に報告します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionInstanceOf|[ACTIONRECORDHEADER](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionRecordHeader)|ActionCode = 0x54|

ActionInstanceOf は、次のことを行います。

1. スタックから、 ''constr'' 、 ''obj'' を順番にポップする
1. ''obj'' が、 ''constr'' のインスタンスかどうか判定する
1. 戻り値 (ブール値) をスタックにプッシュする

### ActionEnumerate2 [#ActionEnumerate2]

ActionEnumerate2 は [ActionEnumerate](アクション_SWF_5_アクションモデル_スクリプトオブジェクト#ActionEnumerate) と似ていますが、引数を String 型のオブジェクト名で渡す代わりに、スタック上にオブジェクトの型を入れて渡します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionEnumerate2|[ACTIONRECORDHEADER](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionRecordHeader)|ActionCode = 0x55|

ActionEnumerate2 は、次のことを行います。

1. ''obj'' をスタックからポップする
1. スタックに null 値をプッシュする。これは、スロット名の配列の最後を示す
1. ''obj'' の、各スロット名を String 型でスタックにプッシュする

```
(注)
スロット名の配列の順番は未定義。
```

### ActionStrictEquals [#ActionStrictEquals]

ActionStrictEquals は [ActionEquals2](アクション_SWF_5_アクションモデル_スクリプトオブジェクト#ActionEquals2) と似ていますが、
引数の型を考慮した等価判定を行います。
ActionScript で、 ‘===’ 演算子を実装するのに使われます。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionStrictEquals|[ACTIONRECORDHEADER](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionRecordHeader)|ActionCode = 0x66|

ActionStrictEquals は、次のことを行います。

1. arg1 と arg2 をスタックからポップする
1. スタックに Boolean 型の戻り値を 1 つプッシュする

### ActionGreater [#ActionGreater]

ActionGreater は、 [ActionLess2](アクション_SWF_5_アクションモデル_数学#ActionLess2) と逆のことを行います。
以前は、引数をプッシュする順番を入れ替えて [ActionLess](アクション_SWF_4_アクションモデル_数値比較#ActionLess), [ActionNot](アクション_SWF_4_アクションモデル_論理演算#ActionNot) と実行することでエミュレートしていたので ActionGreater はありませんでした。
しかし、この引数入れ替えによる処理はいくつかのケースで驚いたことが起こっていました。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionGreater|[ACTIONRECORDHEADER](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionRecordHeader)|ActionCode = 0x67|

ActionGreater は、次のことを行います。

1. arg1 と arg2 をスタックからポップする
1. arg2 > arg1 で比較する
1. スタックに Boolean 型の戻り値を 1 つプッシュする

### ActionStringGreater [#ActionStringGreater]

ActionStringGreater は、 [ActionStringLess](アクション_SWF_4_アクションモデル_文字列操作#ActionStringLess) と逆のことを行います。
このアクションコードは、 ActionGreater と同じ理由で追加されました。 

|フィールド|型|コメント|
| --- | --- | --- |
|ActionStringGreater|[ACTIONRECORDHEADER](アクション_SWF_3_アクションモデル_SWF_3_アクション#ActionRecordHeader)|ActionCode = 0x68|

ActionStringGreater は、次のことを行います。

1. arg1 と arg2 をスタックからポップする
1. バイトごとに arg2 > arg1 で比較する
1. スタックに Boolean 型の戻り値を 1 つプッシュする

### 移動 [#u331bbd4]
* 前のページ : [SWF 6 アクションモデル](アクション_SWF_6_アクションモデル)
* 次のページ : [SWF 7 アクションモデル](アクション_SWF_7_アクションモデル)
