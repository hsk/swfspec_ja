## Screen Video V2 bitstream format [#l4a07312]

### SCREENV2VIDEOPACKET [#SCREENV2VIDEOPACKET]

|フィールド|型|コメント|
| --- | --- | --- |
|BlockWidth|UB[4]|Pixel width of each block in&br;the grid. This value is stored&br;as&br;(actualWidth / 16) - 1, so&br;possible block sizes are a&br;multiple of 16 and not more&br;than 256.|
|ImageWidth|UB[12]|Pixel width of the full image.|
|BlockHeight|UB[4]|Pixel height of each block in&br;the grid. This value is stored&br;as (actualHeight / 16) - 1, so&br;possible block sizes are a&br;multiple of 16 and not more&br;than 256.|
|ImageHeight|UB[12]|Pixel height of the full image.|
|Reserved|UB[6]|Must be 0|
|HasIFrameImage|UB[1]|If 1, has IFrameImage|
|HasPaletteInfo|UB[1]|If 1, has PaletteInfo|
|PaletteInfo|If HasPaletteInfo,&br;IMAGEBLOCK|One block of data to describe&br;the palette.|
|ImageBlocks|IMAGEBLOCKV2[n]|Blocks of image data. See&br;Block format for details of&br;how to calculate n. Blocks&br;are ordered from bottom left&br;to top right in rows and can&br;be a combination of&br;keyblocks and interblocks.|
|IFrameImage|If HasIFrameImage,&br;IMAGEBLOCKV2[n]|Blocks of image data&br;representing interblocks that&br;must be combined with the&br;previous keyblocks to&br;produce the image. See&br;Block format for details of&br;how to calculate n. Blocks&br;are ordered from bottom left&br;to top right in rows.|


## Image Block V2 [#t74f2ef3]

### IMAGEBLOCKV2 [#IMAGEBLOCKV2]

|フィールド|型|コメント|
| --- | --- | --- |
|DataSize|UB[16]&br;Note: UB[16] is not the same as&br;UI16; there is no byte swapping.|Size of the compressed&br;block data that follows,&br;including the ImageFormat,&br;ImageBlockHeader and Data&br;fields. If this is an interframe,&br;and this block has not&br;changed since the last&br;keyframe, DataSize is 0 and&br;the Data field is absent.|
|Format|IMAGEFORMAT|Compression format of block&br;data.|
|ImageBlockHeader|If Format’s HasDiffBlock = 1,&br;IMAGEDIFFPOSITION&br;If Format’s&br;ZlibPrimeCompressCurrent = 1,&br;IMAGEPRIMEPOSITION|Describes the format and&br;compression of Data|
|Data|If DataSize > 0, UI8[DataSize]|Pixel data compressed using&br;ZLIB. Pixels are ordered&br;from bottom left to top right&br;in rows. Each pixel is three&br;bytes: B, G, R.|


## Image format [#ufadbabd]

### IMAGEFORMAT [#IMAGEFORMAT]

|フィールド|型|コメント|
| --- | --- | --- |
|Reserved|UB[3]|Must be 0|
|ColorDepth|UB[2]|00: 24-bit RGB image&br;10: 15/7-bit hybrid color&br;image|
|HasDiffBlocks|UB[1]|If 1, the data starts and stops&br;on specific rows within the&br;block and does not represent&br;the entire block.|
|ZlibPrimeCompressCurrent|UB[1]|If 1, the current data block&br;was produced with the ZLIB&br;priming technique of&br;compression.|
|ZlibPrimeCompressPrevious|UB[1]|If 1, the previous data block&br;was produced with the ZLIB&br;priming technique of&br;compression.|

## Image block diff position [#db66992e]

### IMAGEDIFFPOSITION [#IMAGEDIFFPOSITION]

|フィールド|型|コメント|
| --- | --- | --- |
|RowStart|UI8|Indicates the first scan line of&br;the block that contains the&br;image data.|
|Height|UI8|Indicates the height, in&br;contiguous scan lines, of the&br;image data.|

## Image block prime position [#h9d8668a]

### IMAGEPRIMEPOSITION [#IMAGEPRIMEPOSITION]

|フィールド|型|コメント|
| --- | --- | --- |
|Block column|Ui8|Indicates the position of the&br;source block.|
|Block row|Ui8|Indicates the position|

### 移動 [#u331bbd4]
* 前のページ : [Screen Video ビットストリームフォーマット](ビデオ_Screen_Video_ビットストリームフォーマット)
* 次のページ : [On2 Truemotion VP6 ビットストリームフォーマット](ビデオ_On2_Truemotion_VP6_ビットストリームフォーマット)
