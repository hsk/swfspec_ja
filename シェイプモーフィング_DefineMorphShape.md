### DefineMorphShape [#DefineMorphShape]


|フィールド|型|コメント|
| --- | --- | --- |
|Header|RECORDHEADER|タグタイプ = 46|
|CharacterId|UI16|ID for this character|
|StartBounds|RECT|Bounds of the start shape|
|EndBounds|RECT|Bounds of the end shape|
|Offset|UI32|Indicates offset to EndEdges|
|MorphFillStyles|MORPHFILLSTYLEARRAY|Fill style information is stored in&br;the same manner as for a&br;standard shape; however, each&br;fill consists of interleaved&br;information based on a single&br;style type to accommodate&br;morphing.|
|MorphLineStyles|MORPHLINESTYLEARRAY|Line style information is stored&br;in the same manner as for a&br;standard shape; however, each&br;line consists of interleaved&br;information based on a single&br;style type to accommodate&br;morphing.|
|StartEdges|SHAPE|Contains the set of edges and&br;the style bits that indicate style&br;changes (for example, MoveTo,&br;FillStyle, and LineStyle).&br;Number of edges must equal&br;the number of edges in&br;EndEdges.|
|EndEdges|SHAPE|Contains only the set of edges,&br;with no style information.&br;Number of edges must equal&br;the number of edges in&br;StartEdges.|

### 移動 [#u331bbd4]
* 前のページ : [[シェイプモーフィング]]
* 次のページ : [DefineMorphShape2](シェイプモーフィング_DefineMorphShape2)
