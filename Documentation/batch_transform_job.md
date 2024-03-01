# Transform Job Duration and Segment length

When using the Transfrom job, the time taken to comple a job depends on the audio segment length, type of the instance used and number of instances. Bellow is the table of experiments

|SM Job name |instance type  |full audio length|instance count|Segment length (sec)|duration (min)|
|---------------------------|---------------|-------|---|----|--|
|STT-NS-3500-1709286538203	|ml.m5.xlarge	|3500	|8	|30	 |11|
|STT-NS-3500-1709290256827	|ml.m5.xlarge	|3500	|8	|50	 |11|
|STT-NS-3500-1709294277370	|ml.m5.xlarge	|3500	|4	|50	 |17|
|STT-NS-3500-1709271107174	|ml.g4dn.xlarge	|3500	|1	|60	 |60|
|STT-NS-3500-1709287548567	|ml.m5.xlarge	|3500	|8	|60	 |12|
|STT-NS-3500-1709284000532	|ml.m5.xlarge	|3500	|8	|60	 |12|
|STT-NS-3500-1709288457864	|ml.m5.xlarge	|3500	|8	|100 |16|

Note that all other variables being equal the best duration was with 8 x `ml.m5.xlarge` with 50 sec or 30 sec segment langth. Since 50 sec will lead to less segments, let's pick that.

## Transcriptioin quality and segment length 

An interesting observation was that, the transcription when the segment length is 50 sec is better than 100 sec for the same model and spec. Bellow are two examples I found illustrating the point.
The audio file is in [media](../media/STT_NS_3500_chop_00001.aac)
```
100 sec segments
ཆུང་ཆུང་ནས་བྱས་ནས་ད་ལྟ་བར་དུ་ཀ་ཅི་ད་ [བོད་ཡིམ་] འདྲ་བོ་ལབ་ན་རེད་རཱ།
50 sec segments
ཆུང་ཆུང་ནས་བྱས་ནས་ད་ལྟ་བར་དུ་ཀ་ཅི་ད་ [དུས་ཡུན་] འདྲ་བོ་ལབ་ན་རེད་རཱ།

100 sec segments
ཨོ་དེའི་སྐབར་ལ་ [ཅིག་] བཤད་དགོས་བསམ་སོང་།
50 sec segments
ཨོ་དེའི་སྐབར་ལ་ [གཅིག་] བཤད་དགོས་བསམ་སོང་།
```