## Screen Video bitstream format [#i34d34cf]


### SCREENVIDEOPACKET [#SCREENVIDEOPACKET]

|フィールド|型|コメント|
| --- | --- | --- |
|BlockWidth|UB[4]|Pixel width of each block in&br;the grid. This value is stored&br;as&br;(actualWidth / 16) - 1, so&br;possible block sizes are a&br;multiple of 16 and not more&br;than 256.|
|ImageWidth|UB[12]|Pixel width of the full image.|
|BlockHeight|UB[4]|Pixel height of each block in&br;the grid. This value is stored&br;as (actualHeight / 16) - 1, so&br;possible block sizes are a&br;multiple of 16 and not more&br;than 256.|
|ImageHeight|UB[12]|Pixel height of the full image.|
|ImageBlocks|IMAGEBLOCK[n]|Blocks of image data. See&br;preceding for details of how&br;to calculate n. Blocks are&br;ordered from bottom left to&br;top right, in rows.|


## Image block [#i19108a0]

### IMAGEBLOCK [#IMAGEBLOCK]

|フィールド|型|コメント|
| --- | --- | --- |
|DataSize UB[16]|Note: UB[16] is not the same&br;as UI16; no byte swapping&br;occurs.|Size of the compressed block&br;data that follows. If this is an&br;interframe, and this block is not&br;changed since the last&br;keyframe, DataSize is 0 and&br;the Data field is absent.|
|Data|If DataSize > 0,&br;UI8[DataSize]|Pixel data compressed using&br;ZLIB. Pixels are ordered from&br;bottom left to top right in rows.&br;Each pixel is three bytes: B,&br;G, R.|

### 移動 [#u331bbd4]
* 前のページ : [Sorenson H.263 ビットストリームフォーマット](ビデオ_Sorenson_H.263_ビットストリームフォーマット)
* 次のページ : [Screen Video V2 ビットストリームフォーマット](ビデオ_Screen_Video_V2_ビットストリームフォーマット)
