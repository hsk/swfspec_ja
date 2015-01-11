## Sorenson H.263 Bitstream Format [#g762b2c6]

### H263VIDEOPACKET [#H263VIDEOPACKET]

|フィールド|型|コメント|
| --- | --- | --- |
|PictureStartCode|UB[17]|Similar to H.263 5.1.1&br;0000 0000 0000 0000 1|
|Version|UB[5]|Video format version&br;Flash Player 6 supports 0 and 1|
|TemporalReference|UB[8]|See H.263 5.1.2|
|PictureSize|UB[3]|000: custom, 1 byte&br;001: custom, 2 bytes&br;010: CIF (352x288)&br;011: QCIF (176x144)&br;100: SQCIF (128x96)&br;101: 320x240&br;110: 160x120&br;111: reserved|
|CustomWidth|If PictureSize = 000, UB[8]&br;If PictureSize = 001, UB[16]&br;Otherwise absent&br;Note: UB[16] is not the same&br;as UI16; there is no byte&br;swapping.|Width in pixels|
|CustomHeight|If PictureSize = 000, UB[8]&br;If PictureSize = 001, UB[16]&br;Otherwise absent&br;Note: UB[16] is not the same&br;as UI16; there is no byte&br;swapping.|Height in pixels|
|PictureType|UB[2]|00: intra frame&br;01: inter frame&br;10: disposable inter frame&br;11: reserved|
|DeblockingFlag|UB[1]|Requests use of deblocking&br;filter (advisory only, Flash&br;Player may ignore)|
|Quantizer|UB[5]|See H.263 5.1.4|
|ExtraInformationFlag|UB[1]|See H.263 5.1.9|
|ExtraInformation|If ExtraInformationFlag = 1,&br;UB[8]&br;Otherwise absent|See H.263 5.1.10|
|...||The ExtraInformationFlag-&br;ExtraInformation sequence&br;repeats until an&br;ExtraInformationFlag of 0 is&br;encountered|
|Macroblock|MACROBLOCK|See following|
|PictureStuffing|varies|See H.263 5.1.13|


## Macro block [#u1ef1aec]

### MACROBLOCK [#MACROBLOCK]

|フィールド|型|コメント|
| --- | --- | --- |
|CodedMacroblockFlag|UB[1]|See H.263 5.3.1&br;If 1, macro block ends here|
|MacroblockType|varies|See H.263 5.3.2&br;Can cause various fields (see&br;following) to be absent|
|BlockPattern|varies|See H.263 5.3.5|
|QuantizerInformation|UB[2]|See H.263 5.3.6&br;00: -1&br;01: -2&br;10: +1&br;11: +2|
|MotionVectorData|varies[2]|See H.263 5.3.7&br;A horizontal code followed by a&br;vertical code|
|ExtraMotionVectorData|varies[6]|See H.263 5.3.8&br;Three more MotionVectorData&br;code pairs are included when&br;MacroblockType is INTER4V|
|BlockData|BLOCKDATA[6]|See H.263 5.4&br;Four luminance blocks followed&br;by two chrominance blocks|


### Block data [#nc248b0e]

|7-bit LEVELs||||11-bit LEVELs|||
| --- | --- | --- | --- | --- | --- | --- |
|Index|Level|Code||Index|Level|Code|
| --- | --- | --- | --- | --- | --- | --- |
|-|-64|FORBIDDEN||-|-1024|FORBIDDEN|
|0|-63|1000 001||0|-1023|1000 0000&br;001|
|.|.|.||.|.|.|
|61|-2|1111 110||1021|-2|1111 1111 110|
|62|-1|1111 111||1022|-1|1111 1111 111|
|-|0|FORBIDDEN||-|0|FORBIDDEN|
|63|1|0000 001||1023|1|0000 0000&br;001|
|64|2|0000 010||1024|2|0000 0000&br;010|
|.|.|.||.|.|.|
|125|63|0111 111||2045|1023|0111 1111 111|

### 移動 [#u331bbd4]
* 前のページ : [[ビデオ]]
* 次のページ : [Screen Video ビットストリームフォーマット](ビデオ_Screen_Video_ビットストリームフォーマット)
