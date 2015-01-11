## SWF video tags [#hd2a28b3]

## DefineVideoStream [#f664ff9b]

### DefineVideoStream [#DefineVideoStream]

|フィールド|型|コメント|
| --- | --- | --- |
|Header|RECORDHEADER|タグタイプ = 60|
|CharacterID|UI16|ID for this video character|
|NumFrames|UI16|Number of VideoFrame tags&br;that makes up this stream|
|Width|UI16|Width in pixels|
|Height|UI16|Height in pixels|
|VideoFlagsReserved|UB[4]|Must be 0|
|VideoFlagsDeblocking|UB[3]|000 = use VIDEOPACKET&br;value&br;001 = off&br;010 = Level 1 (Fast deblocking&br;filter)&br;011 = Level 2 (VP6 only, better&br;deblocking filter)&br;100 = Level 3 (VP6 only, better&br;deblocking plus fast deringing&br;filter)&br;101 = Level 4 (VP6 only, better&br;deblocking plus better&br;deringing filter)&br;110 = Reserved&br;111 = Reserved|
|VideoFlagsSmoothing|UB[1]|0 = smoothing off (faster)&br;1 = smoothing on (higher&br;quality)|
|CodecID|UI8|2 = Sorenson H.263&br;3 = Screen video (SWF 7 and&br;later only)&br;4 = VP6 (SWF 8 and later only)&br;5 = VP6 video with alpha&br;channel (SWF 8 and later only)|

## VideoFrame [#i47192e4]

### VideoFrame [#VideoFrame]

|フィールド|型|コメント|
| --- | --- | --- |
|Header|RECORDHEADER|タグタイプ = 61|
|StreamID|UI16|ID of video stream character of&br;which this frame is a part|
|FrameNum|UI16|Sequence number of this frame&br;within its video stream|
|VideoData|if CodecID = 2&br;H263VIDEOPACKET&br;if CodecID = 3&br;SCREENVIDEOPACKET&br;if CodecID = 4&br;VP6SWFVIDEOPACKET&br;if CodecID = 5&br;VP6SWFALPHAVIDEOPACKET&br;if CodecID = 6&br;SCREENV2VIDEOPACKET|Video frame payload|

### 移動 [#u331bbd4]
* 前のページ : [On2 Truemotion VP6 ビットストリームフォーマット](ビデオ_On2_Truemotion_VP6_ビットストリームフォーマット)
* 次のページ : [[バイナリデータ]]
