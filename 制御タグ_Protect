## Protect [#yd815d25]

Protect タグは、ファイルがオーサリング環境での編集用にインポートできないことを示します。
Protect タグにデータがない場合 (tag length = 0)、 SWF はインポート不可になります。
このタグがファイル中に含まれる場合、オーサリングツールはロード時にファイルを編集不可として扱います。

Protect タグがデータを含む場合 (tag length is not 0)、 SWF ファイルはパスワードが一致した時にインポート可能になります。
タグに含まれるデータは null 終端文字列で、 MD5 でハッシュ化されたパスワードを指定します。
パスワードの指定は、 SWF 5 以降で使用可能です。

MD5 アルゴリズムは Poul-Henning Kamp によって書かれたもので、フリーで配布されています。
これは FreeBSD ツリーの src/lib/libcrypt/crypt-md5.c にあります。
EnableDebugger タグも、 MD5 ハッシュアルゴリズムが使われています。

Protect タグは SWF 2 以降で使用可能です。

### Protect [#b55f078a]

|フィールド|型|コメント|
| --- | --- | --- |
|Header|[RECORDHEADER](SWFの構造要約_タグのフォーマット)|タグタイプ = 24|

### 移動 [#u331bbd4]
* 前のページ : [FrameLabel](制御タグ_FrameLabel)
* 次のページ : [End](制御タグ_End)
