## PlaceObject3 [#PlaceObject3]

PlaceObject3 タグは、PlaceObject2 タグの機能を拡張したものです。
PlaceObject3 では、次の機能が新しく追加されました。

* PlaceFlagHasClassName フィールドは、クラス名を指定するかどうかを設定します。これは、配置するオブジェクトの型を示します。
ActionScript 3.0 では他の SWF 内のクラスを使ってタイムラインオブジェクトを配置する必要が出てきましたので、 ImportAssets は使用されなくなりました。
インスタンス化された SWF 内のオブジェクトは 16 bit のキャラクタ ID を持っていません。
この機能は Flash Player 9.0.45.0 以降でサポートされます。

* PlaceFlagHasImage フィールドは、表示リスト上の Bitmap オブジェクトの作成の仕方を設定します。
PlaceFlagHasClassName と PlaceFlagHasImage の両方が定義されている時、別の SWF ファイルから Bitmap クラスがロードされることを指し示します。すぐ次に続くフラグは、ロードされた SWF の中の BitmapData クラスの名前を指します。ここで指定された BitmapData クラスを内部データとして持つ Bitmap オブジェクトが配置されます。
PlaceFlagHasCharacter と PlaceFlagHasImage の両方が定義されている時は、 Bitmap が現在の SWF 内にあることを表します。 Bitmap の内部データとして使用される BitmapData は、次に続くキャラクタ ID で定義されます。これは、 BitmapData がクラスに結合されている場合にのみ起こります。クラスに結合されていない場合は、必要があれば DefineShape により、 Bitmap を塗りつぶします。
この機能は Flash Player 9.0.45.0 以降でサポートされます。

* PlaceFlagHasCacheAsBitmap フィールドでは、Flash Player の内部で表示オブジェクトをキャッシュするかどうかを設定します。
キャッシュすることで、オブジェクトの内容が変更されない時はレンダリングの速度が向上します。

* アルファ合成時のブレンドモードには、次のようなものが使用できます。
|Add|Layer|
|Alpha|Lighten|
|Darken|Overlay|
|Difference|Multiply|
|Erase|Screen|
|Hardlight|Subtract|
|Invert||

* 表示オブジェクトに適用できるフィルタには次のようなものがあります。フィルタの追加と共に、表示オブジェクトはビットマップキャッシュされます。
|Bevel|Drop shadow|
|Blur|Glow|
|Color matrix|Gradient bevel|
|Convolution|Gradient glow|


### PlaceObject3 [#c4b42cb4]
SWF 8 以降のバージョンで使用できます。

|フィールド|型|コメント|
| --- | --- | --- |
|Header|[RECORDHEADER](SWFの構造要約_タグのフォーマット)|タグタイプ = 70|
|PlaceFlagHasClipActions|[UB](基本的なデータ型_ビット値)[1]|SWF 5 以降: クリップアクション有り&br;それ以外の場合、常に 0|
|PlaceFlagHasClipDepth|[UB](基本的なデータ型_ビット値)[1]|ClipDepth 有り|
|PlaceFlagHasName|[UB](基本的なデータ型_ビット値)[1]|Name 有り|
|PlaceFlagHasRatio|[UB](基本的なデータ型_ビット値)[1]|Ratio 有り|
|PlaceFlagHasColorTransform|[UB](基本的なデータ型_ビット値)[1]|ColorTransform 有り|
|PlaceFlagHasMatrix|[UB](基本的なデータ型_ビット値)[1]|Matrix 有り|
|PlaceFlagHasCharacter|[UB](基本的なデータ型_ビット値)[1]|キャラクタの配置|
|PlaceFlagMove|[UB](基本的なデータ型_ビット値)[1]|キャラクタの移動を定義|
|Reserved|[UB](基本的なデータ型_ビット値)[3]|常に 0|
|PlaceFlagHasImage|[UB](基本的なデータ型_ビット値)[1]|配置する Bitmap がクラス名かキャラクタ ID を指定する時に 1 にする。 PlaceFlagHasClassName が ClassName を使う時もしくは、 PlaceFlagHasCharacter がキャラクタ ID を使う時|
|PlaceFlagHasClassName|[UB](基本的なデータ型_ビット値)[1]|配置するオブジェクトがクラス名を使う|
|PlaceFlagHasCacheAsBitmap|[UB](基本的なデータ型_ビット値)[1]|BitmapCache を使う|
|PlaceFlagHasBlendMode|[UB](基本的なデータ型_ビット値)[1]|ブレンドモード使用|
|PlaceFlagHasFilterList|[UB](基本的なデータ型_ビット値)[1]|フィルタリスト使用|
|Depth|[UI16](基本的なデータ型_整数型とバイトオーダー)|キャラクタの深さ|
|ClassName|If PlaceFlagHasClassName or &br;(PlaceFlagHasImage and PlaceFlagHasCharacter), &br;String|配置するクラスの名前|
|CharacterId|If PlaceFlagHasCharacter, [UI16](基本的なデータ型_整数型とバイトオーダー)|配置するキャラクタの ID|
|Matrix|If PlaceFlagHasMatrix, [MATRIX](基本的なデータ型_MATRIX_レコード)|変形行列データ|
|ColorTransform|If PlaceFlagHasColorTransform, [CXFORMWITHALPHA](基本的なデータ型_アルファ値付き色変換レコード)|色変換データ|
|Ratio|If PlaceFlagHasRatio, [UI16](基本的なデータ型_整数型とバイトオーダー)||
|Name|If PlaceFlagHasName, [STRING](基本的なデータ型_文字列の値)|キャラクタの名前|
|ClipDepth|If PlaceFlagHasClipDepth, [UI16](基本的なデータ型_整数型とバイトオーダー)|ClipDepth (クリッピングレイヤ参照)|
|SurfaceFilterList|If PlaceFlagHasFilterList, FILTERLIST|オブジェクトに適用するフィルタのリスト|
|BlendMode|If PlaceFlagHasBlendMode, [UI8](基本的なデータ型_整数型とバイトオーダー)|0 or 1 = normal&br;2 = layer&br;3 = multiply&br;4 = screen&br;5 = lighten&br;6 = darken&br;7 = difference&br;8 = add&br;9 = subtract&br;10 = invert&br;11 = alpha&br;12 = erase&br;13 = overlay&br;14 = hardlight&br;15 ～ 255 は予約済み|
|BitmapCache|If PlaceFlagHasCacheAsBitmap, [UI8](基本的なデータ型_整数型とバイトオーダー)|0 = ビットマップキャッシュ無効&br;1 ～ 255 = ビットマップキャッシュ有効|
|ClipActions|If PlaceFlagHasClipActions, [CLIPACTIONS](表示リスト_表示リストタグ_PlaceObject2#ClipActions)|SWF 5 以降: クリップアクションのデータ|

### FILTERLIST [#FILTERLIST]

|フィールド|型|コメント|
| --- | --- | --- |
|NumberOfFilters|[UI8](基本的なデータ型_整数型とバイトオーダー)|フィルタの数|
|Filter|FILTER[NumberOfFilters]|フィルタのリスト|

### FILTER [#FILTER]

|フィールド|型|コメント|
| --- | --- | --- |
|FilterID|[UI8](基本的なデータ型_整数型とバイトオーダー)|0 = DropShadowFilter&br;1 = BlurFilter&br;2 = GlowFilter&br;3 = BevelFilter&br;4 = GradientGlowFilter&br;5 = ConvolutionFilter&br;6 = ColorMatrixFilter&br;7 = GradientBevelFilter|
|DropShadowFilter|If FilterID = 0, DROPSHADOWFILTER|ドロップシャドウフィルター|
|BlurFilter|If FilterID = 1, BLURFILTER|ブラーフィルター|
|GlowFilter|If FilterID = 2, GLOWFILTER|グローフィルター|
|BevelFilter|If FilterID = 3, BEVELFILTER|ベベルフィルター|
|GradientGlowFilter|If FilterID = 4, GRADIENTGLOWFILTER|グラデーショングローフィルター|
|ConvolutionFilter|If FilterID = 5, CONVOLUTIONFILTER|畳み込みフィルター|
|ColorMatrixFilter|If FilterID = 6, COLORMATRIXFILTER|カラーマトリックスフィルター|
|GradientBevelFilter|If FilterID = 7, GRADIENTBEVELFILTER|グラデーションベベルフィルター|

### COLORMATRIXFILTER [#COLORMATRIXFILTER]

カラーマトリックスフィルターは、表示リスト内のオブジェクトに対して色変換を適用します。
表示リストオブジェクトの、RGBA 入力ピクセルに対して次の方法で計算されます。

結果の RGBA ピクセルは飽和演算が施されます。
行列の値は、行ごとに上から下へ、各行は左から右へ向かって保存されます。
最後の行は常に (0,0,0,0,1) として扱われるため、これは保存する必要がありません。

&ref(ColorMatrixFilter.png,nolink);

|フィールド|型|コメント|
| --- | --- | --- |
|Matrix|[FLOAT](基本的なデータ型_浮動小数点数)[20]|カラーマトリックス値|


### CONVOLUTIONFILTER [#CONVOLUTIONFILTER]

畳み込みフィルターは、2 次元の離散値の畳み込みを実行します。
これは、次の式によって各ピクセルに対して適用されます。
F は入力ピクセルプレーン、 G は入力行列、 H は出力ピクセルプレーンを表します。

&ref(ConvolutionFilter.png,nolink);

(訳注： ↑ 数学良く分からないですが、この式Σとか抜けてる気がします。)

PreserveAlpha フラグがセットされていない場合、畳み込み処理は、各 RGBA ピクセルに適用され、飽和演算が施されます。
セットされている場合は、アルファチャネルの値のみ変更されなくなります。

Clamp フラグでは、入力ピクセルが外側にはみ出てしまった時の処理の仕方を指定します。
0 の時は、 DefaultColor フィールドにセットされた色が使われます。
1 の時は、一番近くにある有効なピクセルが入力ピクセルとして使われます。

|フィールド|型|コメント|
| --- | --- | --- |
|MatrixX|[UI8](基本的なデータ型_整数型とバイトオーダー)|水平行列サイズ|
|MatrixY|[UI8](基本的なデータ型_整数型とバイトオーダー)|垂直行列サイズ|
|Divisor|[FLOAT](基本的なデータ型_浮動小数点数)|行列値を最後に割る数|
|Bias|[FLOAT](基本的なデータ型_浮動小数点数)|行列に適用する Bias|
|Matrix|[FLOAT](基本的なデータ型_浮動小数点数)[MatrixX * MatrixY]|行列値|
|DefaultColor|[RGBA](基本的なデータ型_RGBA_色とアルファ値のレコード)|入力画像からはみ出た時に使う色|
|Reserved|[UB](基本的なデータ型_ビット値)[6]|常に 0|
|Clamp|[UB](基本的なデータ型_ビット値)[1]|Clamp モード|
|PreserveAlpha|[UB](基本的なデータ型_ビット値)[1]|アルファチャネル保護|

### BLURFILTER [#BLURFILTER]

ブラーフィルターは、サブピクセルの正確なメディアンフィルターです (ボックスフィルタとも呼ばれます)。
このフィルターは、 RGBA チャネルのそれぞれに適用されます。

次に、サブピクセルの正確さの無い、単純なメディアンフィルターの式を示します。これは、簡単にサブピクセルを正確にした版にすることが可能です。

```
注
この式は、 Flash Player で同じ結果を得る時、 BlurX と BlurY が奇数であると仮定しています。
フィルタをウインドウは常に Flash Player のピクセルの中心です。
```

&ref(BlurFilter.png,nolink);

パス数を 3 に設定すると、ガウスブラーフィルターと全く同一になります。
もっと高いパス数にすることも可能ですが、パフォーマンスの観点により、 Adobe はお勧めしません。

|フィールド|型|コメント|
| --- | --- | --- |
|BlurX|[FIXED](基本的なデータ型_固定小数点数)|水平ブラーの量|
|BlurY|[FIXED](基本的なデータ型_固定小数点数)|垂直ブラーの量|
|Passes|[UB](基本的なデータ型_ビット値)[5]|ブラーをかけるパスの数|
|Reserved|[UB](基本的なデータ型_ビット値)[3]|常に 0|

### DROPSHADOWFILTER [#DROPSHADOWFILTER]

ドロップシャドウフィルターは、ブラーフィルターをベースにしています。影のピクセルを生成するために、ブラーフィルターはアルファチャネルにのみ適用されます。

角度パラメータはラジアン単位です。
0 にセットすると、影はオブジェクトの右側に付きます。
距離はピクセル単位です。
影のピクセルを生成する時、サブピクセルはバイリニア補完されます。

Strength の値は標準の場合、固定小数点数で 1.0 になります。
影のピクセルのそれぞれの値がこの値で乗算されます。

ドロップシャドウにはいくつかの合成モードが適用可能です。影を付ける方向の内側・外側、通常モード・ノックアウトモードの設定があります。

結果の各ピクセル値は、提供された RGBA 値を乗算したものから得られます。
結果のピクセルは、元の入力ピクセルプレーンに対して指定された合成モードを適用することで合成されます。

|フィールド|型|コメント|
| --- | --- | --- |
|DropShadowColor|[RGBA](基本的なデータ型_RGBA_色とアルファ値のレコード)|影の色|
|BlurX|[FIXED](基本的なデータ型_固定小数点数)|水平ブラーの量|
|BlurY|[FIXED](基本的なデータ型_固定小数点数)|垂直ブラーの量|
|Angle|[FIXED](基本的なデータ型_固定小数点数)|影の伸びる角度 (ラジアン)|
|Distance|[FIXED](基本的なデータ型_固定小数点数)|影の距離|
|Strength|[FIXED8](基本的なデータ型_固定小数点数)|影を付ける強さ|
|InnerShadow|[UB](基本的なデータ型_ビット値)[1]|内側に付けるモード|
|Knockout|[UB](基本的なデータ型_ビット値)[1]|ノックアウトモード|
|CompositeSource|[UB](基本的なデータ型_ビット値)[1]|合成ソース (常に 1)|
|Passes|[UB](基本的なデータ型_ビット値)[5]|ブラーをかけるパスの数|

### GLOWFILTER [#GLOWFILTER]

グローフィルターは、ドロップシャドウフィルターとほぼ同じ方法で動作します。
違いは、距離と角度がないところで、わずかにこちらの方が高速に動作します。

|フィールド|型|コメント|
| --- | --- | --- |
|GlowColor|[RGBA](基本的なデータ型_RGBA_色とアルファ値のレコード)|影の色|
|BlurX|[FIXED](基本的なデータ型_固定小数点数)|水平ブラーの量|
|BlurY|[FIXED](基本的なデータ型_固定小数点数)|垂直ブラーの量|
|Strength|[FIXED8](基本的なデータ型_固定小数点数)|グローの強さ|
|InnerGlow|[UB](基本的なデータ型_ビット値)[1]|内側にグローをかけるモード|
|Knockout|[UB](基本的なデータ型_ビット値)[1]|ノックアウトモード|
|CompositeSource|[UB](基本的なデータ型_ビット値)[1]|合成ソース (常に 1)|
|Passes|[UB](基本的なデータ型_ビット値)[5]|ブラーをかけるパスの数|

### BEVELFILTER [#BEVELFILTER]

ベベルフィルターは、滑らかなベベルを表示リストのオブジェクトに対して適用します。

|フィールド|型|コメント|
| --- | --- | --- |
|ShadowColor|[RGBA](基本的なデータ型_RGBA_色とアルファ値のレコード)|影の色|
|HighlightColor|[RGBA](基本的なデータ型_RGBA_色とアルファ値のレコード)|ハイライトの色|
|BlurX|[FIXED](基本的なデータ型_固定小数点数)|水平ブラーの量|
|BlurY|[FIXED](基本的なデータ型_固定小数点数)|垂直ブラーの量|
|Angle|[FIXED](基本的なデータ型_固定小数点数)|ドロップシャドウの角度|
|Distance|[FIXED](基本的なデータ型_固定小数点数)|ドロップシャドウの距離|
|Strength|[FIXED8](基本的なデータ型_固定小数点数)|ドロップシャドウの強さ|
|InnerShadow|[UB](基本的なデータ型_ビット値)[1]|内側にシャドウをかけるモード|
|Knockout|[UB](基本的なデータ型_ビット値)[1]|ノックアウトモード|
|CompositeSource|[UB](基本的なデータ型_ビット値)[1]|合成ソース (常に 1)|
|OnTop|[UB](基本的なデータ型_ビット値)[1]|OnTop モード|
|Passes|[UB](基本的なデータ型_ビット値)[4]|ブラーのパスの数|

### グラデーショングローとグラデーションベベル [#ne11a5f9]

グラデーショングロフィルターーとグラデーションベベルフィルターは、通常のグローフィルターとベベルフィルターの拡張で、単色の代わりにグラデーションの色を使います。
合成モードのうち 1 つが指定されている時は、シャドウピクセルプレーンの単色の値に乗算を適用する代わりに、グラデーションの利得値が結果のピクセルに直接マッピングされます。

### GRADIENTGLOWFILTER[#GRADIENTGLOWFILTER]

|フィールド|型|コメント|
| --- | --- | --- |
|NumColors|[UI8](基本的なデータ型_整数型とバイトオーダー)|グラデーションに使う色の数|
|GradientColors|[RGBA](基本的なデータ型_RGBA_色とアルファ値のレコード)[NumColors]|グラデーションの色|
|GradientRatio|[UI8](基本的なデータ型_整数型とバイトオーダー)[NumColors]|グラデーションの比率|
|BlurX|[FIXED](基本的なデータ型_固定小数点数)|水平ブラーの量|
|BlurY|[FIXED](基本的なデータ型_固定小数点数)|垂直ブラーの量|
|Angle|[FIXED](基本的なデータ型_固定小数点数)|グラデーショングローのラジアン単位の角度|
|Distance|[FIXED](基本的なデータ型_固定小数点数)|グラデーショングローの距離|
|Strength|[FIXED8](基本的なデータ型_固定小数点数)|グラデーショングローの強さ|
|InnerShadow|[UB](基本的なデータ型_ビット値)[1]|内側にグローをかけるモード|
|Knockout|[UB](基本的なデータ型_ビット値)[1]|ノックアウトモード|
|CompositeSource|[UB](基本的なデータ型_ビット値)[1]|合成ソース (常に 1)|
|OnTop|[UB](基本的なデータ型_ビット値)[1]|OnTop モード|
|Passes|[UB](基本的なデータ型_ビット値)[4]|ブラーをかけるパスの数|

### GRADIENTBEVELFILTER[#GRADIENTBEVELFILTER]

|フィールド|型|コメント|
| --- | --- | --- |
|NumColors|[UI8](基本的なデータ型_整数型とバイトオーダー)|グラデーションに使う色の数|
|GradientColors|[RGBA](基本的なデータ型_RGBA_色とアルファ値のレコード)[NumColors]|グラデーションの色|
|GradientRatio|[UI8](基本的なデータ型_整数型とバイトオーダー)[NumColors]|グラデーションの比率|
|BlurX|[FIXED](基本的なデータ型_固定小数点数)|水平ブラーの量|
|BlurY|[FIXED](基本的なデータ型_固定小数点数)|垂直ブラーの量|
|Angle|[FIXED](基本的なデータ型_固定小数点数)|グラデーションベベルのラジアン単位の角度|
|Distance|[FIXED](基本的なデータ型_固定小数点数)|グラデーションベベルの距離|
|Strength|[FIXED8](基本的なデータ型_固定小数点数)|グラデーションベベルの強さ|
|InnerShadow|[UB](基本的なデータ型_ビット値)[1]|内側にグローをかけるモード|
|Knockout|[UB](基本的なデータ型_ビット値)[1]|ノックアウトモード|
|CompositeSource|[UB](基本的なデータ型_ビット値)[1]|合成ソース (常に 1)|
|OnTop|[UB](基本的なデータ型_ビット値)[1]|OnTop モード|
|Passes|[UB](基本的なデータ型_ビット値)[4]|ブラーをかけるパスの数|

### 移動 [#u331bbd4]
* 前のページ : [PlaceObject2](表示リスト_表示リストタグ_PlaceObject2)
* 次のページ : [ClipEventFlags](表示リスト_表示リストタグ_ClipEventFlags)
