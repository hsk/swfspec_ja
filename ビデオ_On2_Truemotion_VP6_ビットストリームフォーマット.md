## VP6 FLV video packet [#wc5c0148]

### VP6FLVVIDEOPACKET [#VP6FLVVIDEOPACKET]

|フィールド|型|コメント|
| --- | --- | --- |
|HorizontalAdjustment|UB[4]|Number of pixels to subtract&br;from the total width. The&br;resulting width is used on the&br;stage, and the rightmost pixels&br;of the video is cropped.|
|VerticalAdjustment|UB[4]|Number of pixels to subtract&br;from the total height. The&br;resulting height is used on the&br;stage, and the rightmost pixels&br;of the video is cropped.|
|Data|UI8[n]|Raw VP6 video stream data|

## VP6 FLV Alpha video packet [#i86575fa]

### VP6FLVALPHAVIDEOPACKET [#VP6FLVALPHAVIDEOPACKET]

|フィールド|型|コメント|
| --- | --- | --- |
|Data|UI8[n]|Raw VP6 video stream data|

## VP6 SWF Alpha video packet [#i90f0e5f]

### VP6SWFALPHAVIDEOPACKET [#VP6SWFALPHAVIDEOPACKET]

|フィールド|型|コメント|
| --- | --- | --- |
|OffsetToAlpha|UI24|Offset in bytes to the alpha&br;channel video data|
|Data|UI8[OffsetToAlpha]|Raw VP6 video stream data&br;representing the color channels|
|AlphaData|UI8[n]|Raw VP6 video stream data&br;representing the alpha channel|

### 移動 [#u331bbd4]
* 前のページ : [Screen Video V2 ビットストリームフォーマット](ビデオ_Screen_Video_V2_ビットストリームフォーマット)
* 次のページ : [SWF ビデオタグ](ビデオ_SWF_ビデオタグ)
