## ADPCM 圧縮 [#ne45ef14]

### ADPCMSOUNDDATA [#ADPCMSOUNDDATA]

|フィールド|型|コメント|
| --- | --- | --- |
|AdpcmCodeSize|UB[2]&br;0 = 2 bits/sample&br;1 = 3 bits/sample&br;2 = 4 bits/sample&br;3 = 5 bits/sample|Bits per ADPCM code less 2.&br;The actual size of each code is&br;AdpcmCodeSize + 2.|
|AdpcmPackets|If SoundType = mono,&br;ADPCMMONOPACKET&br;[one or more]&br;If SoundType = stereo,&br;ADPCMSTEREOPACKET&br;[one or more]|Array of ADPCMPACKETs.|

### ADPCMMONOPACKET [#ADPCMMONOPACKET]

|フィールド|型|コメント|
| --- | --- | --- |
|InitialSample|SI16|First sample. Identical to&br;first sample in&br;uncompressed sound.|
|InitialIndex|UB[6]|Initial index into the&br;ADPCM StepSizeTable.|
|AdpcmCodeData|UB[4095 *&br;(AdpcmCodeSize+2)]|4095 ADPCM codes.&br;Each sample is&br;(AdpcmCodeSize + 2) bits.|

### ADPCMSTEREOPACKET [#ADPCMSTEREOPACKET]

|フィールド|型|コメント|
| --- | --- | --- |
|InitialSampleLeft|SI16|First sample for left&br;channel. Identical to first&br;sample in uncompressed&br;sound.|
|InitialIndexLeft|UB[6]|Initial index into the&br;ADPCM StepSizeTable*&br;for left channel.|
|InitialSampleRight|SI16|First sample for right&br;channel. Identical to first&br;sample in uncompressed&br;sound.|
|InitialIndexRight|UB[6]|Initial index into the&br;ADPCM StepSizeTable*&br;for right channel|
|AdpcmCodeData|UB[8190 * (AdpcmCodeSize+2)]|4095 ADPCM codes per&br;channel, total 8190. Each&br;sample is&br;(AdpcmCodeSize + 2) bits.&br;Channel data is interleaved&br;left, then right.|
