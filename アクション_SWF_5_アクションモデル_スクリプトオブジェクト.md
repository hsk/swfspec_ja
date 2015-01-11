## スクリプトオブジェクト [#aadc7a7d]

### ActionCallFunction [#ActionCallFunction]

ActionCallFunction は、関数を実行します。
これには ActionScript の組み込み関数 (parseInt のような) と、ユーザ定義関数、ネイティブ関数が含まれます。
より詳しい情報は ActionNewObject をご覧ください。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionCallFunction|ACTIONRECORDHEADER|ActionCode = 0x3D|

ActionCallFunction は次のことを行います。

1. 関数名 (String) をスタックからポップする
1. ''numArgs'' (int) をスタックからポップする
1. 引数をスタックからポップする
1. 引数を渡して、関数を呼び出す
1. 関数の戻り値をスタックにプッシュする
戻り値が無い場合 (関数が return ステートメントを持たない場合)、 __push undefined__ メッセージがコンパイラにより生成され、スタックにプッシュされます。
__undefined__ の戻り値はスタックから取り除かれる必要があります。

全ての呼び出しアクション (ActionCallMethod, ActionNewMethod, ActionNewObject, ActionCallFunction) と初期化アクション (ActionInitObject, ActionInitArray) は、引数が逆の順序でスタックに積まれます。右端の引数が最初に詰まれ、左端の引数が最後に積まれます。
これにより、引数の使用時には順序通りにポップされます。

### ActionCallMethod [#ActionCallMethod]

ActionCallMethod は ActionNewMethod のように、メソッド (関数) をスタックにプッシュします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionCallMethod|ACTIONRECORDHEADER|ActionCode = 0x52|

名前付きのメソッドが存在する場合、 ActionCallMethod は次のことを行います。

1. メソッドの名前をスタックからポップする
メソッド名が空文字列か undefined の場合、 __object__ はメソッドのコンテナオブジェクトではなく、関数オブジェクト (function object) になります。
例えば、 CallMethod が __object__ => obj と空文字のメソッド名で呼び出された場合、次の構文と同等の意味になります。
__obj();__
メソッド名に foo が指定された時は、
__obj.foo();__
と同等の意味になります。
1. ScriptObject の ''object'' をスタックからポップする
1. 引数の数 ''args'' をスタックからポップする
1. 引数をスタックからポップする
1. 引数を渡して、メソッドを呼び出す
1. メソッドか関数の戻り値をスタックにプッシュする
戻り値が無い場合 (関数が return ステートメントを持たない場合)、 __push undefined__ メッセージがコンパイラにより生成され、スタックにプッシュされます。
__undefined__ の戻り値はスタックから取り除かれる必要があります。

全ての呼び出しアクション (ActionCallMethod, ActionNewMethod, ActionNewObject, ActionCallFunction) と初期化アクション (ActionInitObject, ActionInitArray) は、引数が逆の順序でスタックに積まれます。右端の引数が最初に詰まれ、左端の引数が最後に積まれます。
これにより、引数の使用時には順序通りにポップされます。


### ActionConstantPool [#ActionConstantPool]

ActionConstantPool は、新しいコンスタントプールを作成します。
古いコンスタントプールが存在する時は上書きされます。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionConstantPool|ACTIONRECORDHEADER|ActionCode = 0x88|
|Count|UI16|次に続く定数の数|
|ConstantPool|STRING[Count]|文字列定数|


### ActionDefineFunction [#ActionDefineFunction]

```
(注)
ActionDefineFunction は SWF 7 以降では滅多に使用されません。
これは ActionDefineFunction2 に置き換えられました。
```

ActionDefineFunction は、与えられた名前と本体サイズで関数を定義します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionDefineFunction|ACTIONRECORDHEADER|ActionCode = 0x9B|
|FunctionName|STRING|関数名 (空の場合、匿名関数)|
|NumParams|UI16|パラメータの数|
|param 1|STRING|パラメータ名 1|
|param 2|STRING|パラメータ名 2|
|・&br;・&br;・|||
|param N|STRING|パラメータ名 N|
|codeSize|UI16|続くコードのバイト数|

ActionDefineFunction は FunctionName, NumParams, [param1, param2, …,
param N], codeSize の順でパースされます。
ActionDefineFunction は、次のことを行います。

1. アクションタグから関数名をパースする
1. タグのパラメータをスキップする
1. タグからコードサイズをパースする
DefineFunction タグの後には、 codeSize で指定されたバイト数のアクションデータが続きます。これは、関数の本体になります。
1. 関数用のコードを得る

ActionDefineFunction は、次の方法で使用することができます。

__使用法 1__
匿名関数をスタックにプッシュします。
この関数は __関数リテラル__ で、命令文の代わりに式で表現されます。
匿名関数は次のような ActionScript で定義されます。

```
area = (function () {return Math.PI * radius *radius;})(5);
```

__使用法 2__
指定された FunctionName と関数定義により変数をセットします。
こちらは、より慣例的な方法で次のような ActionScript で定義されます。

```
function Circle(radius) {
　this.radius = radius;
　this.area = Math.PI * radius * radius;
}
```

### ActionDefineLocal [#ActionDefineLocal]

ActionDefineLocal は、ローカル変数の定義と値の設定を行います。
変数が既に存在する場合は、新しいもので置き換えられます。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionDefineLocal|ACTIONRECORDHEADER|ActionCode = 0x3C|

ActionDefineLocal は次のことを行います。

1. 値 (value) をスタックからポップする
1. 名前 (name) をスタックからポップする

### ActionDefineLocal2 [#ActionDefineLocal2]

ActionDefineLocal2 は、ローカル変数を定義しますが値をセットしません。
変数が既に存在する場合は何も行いません。
ローカル変数の初期値は __undefined__ になります。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionDefineLocal2|ACTIONRECORDHEADER|ActionCode = 0x41|

ActionDefineLocal2 は次のことを行います。

1. 名前 (name) をスタックからポップする

### ActionDelete [#ActionDelete]

ActionDelete は名前付きのプロパティを ScriptObject から削除します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionDelete|ACTIONRECORDHEADER|ActionCode = 0x3A|

ActionDelete は次のことを行います

1. 削除するプロパティの名前をスタックからポップする
1. プロパティを削除するオブジェクトをスタックからポップする

### ActionDelete2 [#ActionDelete2]

ActionDelete2 は名前付きのプロパティを削除します。
Flash Player は最初、現在のスコープでプロパティを探します。
見つけられなかった場合、より大きいスコープへと範囲を広げてプロパティを探します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionDelete2|ACTIONRECORDHEADER|ActionCode = 0x3B|

ActionDelete2 は次のことを行います

1. 削除するプロパティの名前をスタックからポップする

### ActionEnumerate [#ActionEnumerate]

ActionEnumerate は、 ActionScript オブジェクトの全ての &quot;スロット&quot; の名前を取得します。
オブジェクト __obj__ の、全ての名前を表す記号を __X__ とすると、 __obj.X__ のような形式で表されるものを検索します。
ActionEnumerate は、 ActionScript の __for .. in__ 文の実装に使われます。

```
(注)
特別なスロット名は省略されます。
特別な名前のリストは、 ECMA-262 標準の、 DontEnum の項目を調べてみてください。
```

__リンク__
    * ''Under Translation of ECMA-262 3rd Edition''
http://www2u.biglobe.ne.jp/~oz-07ams/prog/ecma262r3/
        * ''8 型 (Types)''
http://www2u.biglobe.ne.jp/~oz-07ams/prog/ecma262r3/8_Types.html#section-8.6

|フィールド|型|コメント|
| --- | --- | --- |
|ActionEnumerate|ACTIONRECORDHEADER|ActionCode = 0x46|

ActionEnumerate は次のことを行います。

1. オブジェクト変数の名前 (スラッシュ区切りかドット区切りで表される) をスタックからポップする
1. スロット名のリストの終わりを指すために、 null 値をスタックにプッシュする
1. それぞれのスロット名 (文字列) をスタックにプッシュする

```
(注)
プッシュする順番は未定義です。
```

### ActionEquals2 [#ActionEquals2]

ActionEquals2 は ActionEquals と似ていますが、 ActionEquals2 は型を区別します。
等価比較アルゴリズムは [ECMA-262](http:__www.ecma-international.org_publications_standards_ecma-262.htm) Section 11.9.3 を使用します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionEquals2|ACTIONRECORDHEADER|ActionCode = 0x49|

ActionEquals2 は次のことを行います。

1. arg1 をスタックからポップする
1. arg2 をスタックからポップする
1. 戻り値をスタックにプッシュする

### ActionGetMember [#ActionGetMember]

ActionGetMember は、名前付きプロパティをオブジェクトから検索し、そのプロパティの値をスタックにプッシュします。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionGetMember|ACTIONRECORDHEADER|ActionCode = 0x4E|

ActionGetMember は次のことを行います。

1. メンバ関数の名前 ''name'' をスタックからポップする
1. ScriptObject ''object'' をスタックからポップする
1. プロパティの値をスタックにプッシュする

例えば、オブジェクト __obj__ のプロパティ __foo__ に次のように値が割り当てられた時、

```
obj.foo = 3;
```

ActionGetMember の __object__ を obj に、 __name__ に foo を指定すると、スタックに 3 をプッシュします。
指定されたプロパティが存在しない時は、 __undefined__ をスタックにプッシュします。

__object__ パラメータは Object 型にする必要はありません。
__object__ パラメータが number, Boolean, string のようなプリミティブ型の場合は、一時的なラッパーオブジェクト Number, Boolean, String へと自動的に変換されます。
これにより、ラッパーオブジェクトのメソッドが、プリミティブ型に対してでも呼び出すことができます。
例えば次の例は、 5 と表示されます。

```
var x = &quot;Hello&quot;;
trace (x.length);
```

この例の変数 x には、プリミティブ文字列 &quot;Hello&quot; が代入されています。
x は、 String 型のラッパーオブジェクトに一時的にラップされ、その上で length プロパティを取得します。

### ActionInitArray [#ActionInitArray]

ActionInitArray は ActionInitObject と同様に、 ScriptObject 内の配列の初期化を行います。
新しく作成されたオブジェクトはスタックにプッシュされます。
スタックには、新しく作成されたオブジェクトの参照のみが積まれます。
ActionInitArray の後に続く SetVariable か SetMember アクションにより、新しく作成されたオブジェクトを変数に代入することができます。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionInitArray|ACTIONRECORDHEADER|ActionCode = 0x42|

ActionInitArray は要素数 (elems) をスタックからポップした後、 [arg1, arg2, …, argn] をポップします。

ActionInitArray は次のことを行います。

1. 引数 (または要素) の数をスタックからポップする
1. 引数がある場合、 ActionInitArray は、指定された要素数の配列オブジェクトを初期化する
1. ScriptObject として配列を初期化する
1. オブジェクトの型を ''Array'' にセットする
1. スタックから値をポップし、それを配列の初期値として代入する

全ての呼び出しアクション (ActionCallMethod, ActionNewMethod, ActionNewObject, ActionCallFunction) と初期化アクション (ActionInitObject, ActionInitArray) は、引数が逆の順序でスタックに積まれます。右端の引数が最初に詰まれ、左端の引数が最後に積まれます。
これにより、引数の使用時には順序通りにポップされます。

### ActionInitObject [#ActionInitObject]

ActionInitObject は ActionInitArray と同じようにオブジェクトを初期化します。
新しく作成されたオブジェクトはスタックにプッシュされます。
スタックには、新しく作成されたオブジェクトの参照のみが積まれます。
ActionInitArray の後に続く SetVariable か SetMember アクションにより、新しく作成されたオブジェクトを変数に代入することができます。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionInitObject|ACTIONRECORDHEADER|ActionCode = 0x43|

ActionInitObject は要素数 (elems) をスタックからポップした後、 [value1, name1, …, valueN, nameN] をポップします。

ActionInitObject は次のことを行います。

1. 初期プロパティの数をスタックからポップする
1. ScriptObject としてオブジェクトを初期化する
1. オブジェクトの型を Object にセットする
1. 初期プロパティをそれぞれスタックからポップする
各初期プロパティは、最初に値がポップされ、次に名前がポップされます。
名前は文字列に変換されますが、値はどのような型でもかまいません。

全ての呼び出しアクション (ActionCallMethod, ActionNewMethod, ActionNewObject, ActionCallFunction) と初期化アクション (ActionInitObject, ActionInitArray) は、引数が逆の順序でスタックに積まれます。右端の引数が最初に詰まれ、左端の引数が最後に積まれます。
これにより、引数の使用時には順序通りにポップされます。

### ActionNewMethod [#ActionNewMethod]

ActionNewMethod は、新しいオブジェクトを作成するためにコンストラクタ関数を呼び出します。
新しいオブジェクトが作成され、コンストラクタ関数に __this__ キーワードが渡されます。
コンストラクタ関数に引数を指定することもできます。
コンストラクタ関数の戻り値は破棄されます。
ActionCallMethod や ActionNewObject と同じように、新しく作成されたオブジェクトはスタックにプッシュされます。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionNewMethod|ACTIONRECORDHEADER|ActionCode = 0x53|

ActionNewMethod は次のことを行います。

1. メソッドの名前をスタックからポップする
1. ScriptObject をスタックからポップする
メソッドの名前が空の場合、 ScriptObject は関数オブジェクトとして扱われ、これをコンストラクタ関数として呼び出します。
メソッドの名前が空でない場合、 ScriptObject 内の、そのメソッドを呼び出します。
1. 引数の数をスタックからポップする
1. メソッド呼び出しを実行する
1. 新しく作成されたオブジェクトをスタックにプッシュする
特定の戻り値が無い場合 (関数が return 文を持たない場合)、コンパイラは __push undefined__ を生成し、それをスタックにプッシュします。
この戻り値の __undefined__ は、スタックからポップされる必要があります。

全ての呼び出しアクション (ActionCallMethod, ActionNewMethod, ActionNewObject, ActionCallFunction) と初期化アクション (ActionInitObject, ActionInitArray) は、引数が逆の順序でスタックに積まれます。右端の引数が最初に詰まれ、左端の引数が最後に積まれます。
これにより、引数の使用時には順序通りにポップされます。

### ActionNewObject [#ActionNewObject]

ActionNewObject は、コンストラクタ関数を呼び出します。
新しいオブジェクトが作成され、コンストラクタ関数に __this__ キーワードが渡されます。
オプションで、コンストラクタ関数の引数をスタック上に指定することもできます。
コンストラクタ関数の戻り値は破棄されます。
ActionCallMethod や ActionNewMethod と同じように、新しく作成されたオブジェクトはスタックにプッシュされます。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionNewObject|ACTIONRECORDHEADER|ActionCode = 0x40|

ActionNewObject は次のことを行います。

1. オブジェクト名 (文字列) ''this'' をスタックからポップする
1. ''numArgs'' (int) をスタックからポップする
1. 引数をスタックからポップする
1. 名前付きオブジェクトのコンストラクタ関数を呼び出す
コンストラクタ関数には指定された引数が渡され、新しく作成されたオブジェクトには __this__ キーワードが使われる
1. コンストラクタ関数の戻り値は破棄される
1. 新しく作成されたオブジェクトがスタックにプッシュされる

全ての呼び出しアクション (ActionCallMethod, ActionNewMethod, ActionNewObject, ActionCallFunction) と初期化アクション (ActionInitObject, ActionInitArray) は、引数が逆の順序でスタックに積まれます。右端の引数が最初に詰まれ、左端の引数が最後に積まれます。
これにより、引数の使用時には順序通りにポップされます。

### ActionSetMember [#ActionSetMember]

ActionSetMember はオブジェクトのプロパティをセットします。
プロパティが存在していなかった場合は、新しく作成されます。
存在するプロパティが指定された時は上書きされます。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionSetMember|ACTIONRECORDHEADER|ActionCode = 0x4F|

ActionSetMember は次のことを行います。

1. 新しい値をスタックからポップする
1. オブジェクト名をスタックからポップする
1. オブジェクトをスタックからポップする

### ActionTargetPath [#ActionTargetPath]

ActionTargetPath は、指定されたオブジェクトのターゲットパスをスタックにプッシュします。
スタック上のオブジェクトの型が MovieClip の場合、オブジェクトのターゲットパスはドット区切りの表記でスタックにプッシュされます。
オブジェクトの型が MovieClip でない場合、結果はムービークリップのターゲットパスの替わりに undefined になります。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionTargetPath|ACTIONRECORDHEADER|ActionCode = 0x45|

ActionTargetPath は次のことを行います。

1. オブジェクトをスタックからポップする
1. ターゲットパスをスタックにプッシュする

### ActionWith [#ActionWith]

スクリプトの with ブロックを定義します。

|フィールド|型|コメント|
| --- | --- | --- |
|ActionWith|ACTIONRECORDHEADER|ActionCode = 0x94|
|Size|UI16|続くコードのバイト数|

ActionWith は次のことを行います。

1. with ブロックを開始するオブジェクトをスタックからポップする
1. ActionWith タグの Size (コードの長さ) をパースする
1. 呼び出しの深さが最大の深さを超えていないかチェックする
SWF 6 以降: 最大の深さは 16
SWF 5: 最大の深さは 8
with の深さが最大の深さを上回っている場合、 Size バイトのデータは実行する代わりにスキップされる
1. ActionWith タグの後ろの Size バイトのアクションコードを with ブロックの本体とする
1. with ブロックをスコープチェーンに追加する

### 移動 [#u331bbd4]
* 前のページ : [SWF 5 アクション](アクション_SWF_5_アクションモデル_SWF_5_アクション)
* 次のページ : [型](アクション_SWF_5_アクションモデル_型)
