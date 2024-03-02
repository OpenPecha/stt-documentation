# Transform Job Duration and Segment length

When using the Transfrom job, the time taken to comple a job depends on the audio segment length, type of the instance used, max concurrent transforms and number of instances. Bellow is the table of experiments

|SM Job name |Instance type  |Full audio length (sec)|Instance count|Segment length (sec)|MaxConcurrentTransforms|Duration (min)|
|--------------------------|---------------|-----|---|----|---|--|
|STT-NS-0200-1709307131129 |ml.m5.xlarge   |200  |2  |50  |2  |6  |
|STT-NS-0200-1709308820759 |ml.m5.xlarge   |200  |2  |50  |4  |6  |
|STT-NS-0200-1709307876444 |ml.m5.xlarge   |200  |8	 |50  |2  |6  |
|STT-NS-0200-1709308364968 |ml.m5.xlarge   |200	 |1	 |50  |2  |7  |
|STT-NS-0200-1709309343000 |ml.m5.xlarge   |200	 |1	 |50  |1  |8  |
|STT-NS-3500-1709316771523 |ml.m5.xlarge   |3500 |14 |50  |2  |7  |
|STT-NS-3500-1709296723865 |ml.m5.xlarge   |3500 |16 |50  |2  |7  |
|STT-NS-3500-1709297494092 |ml.m5.xlarge   |3500 |16 |50  |4  |7  |
|STT-NS-3500-1709317339925 |ml.m5.xlarge   |3500 |13 |50  |2  |8  |
|STT-NS-3500-1709310474604 |ml.m5.xlarge   |3500 |12 |50  |2  |8  |
|STT-NS-3500-1709311731770 |ml.m5.xlarge   |3500 |8	 |50  |4  |8  |
|STT-NS-3500-1709295971938 |ml.m5.xlarge   |3500 |16 |50  |1  |9  |
|STT-NS-3500-1709286538203 |ml.m5.xlarge   |3500 |8	 |30  |1  |11 |
|STT-NS-3500-1709290256827 |ml.m5.xlarge   |3500 |8	 |50  |1  |11 |
|STT-NS-3500-1709287548567 |ml.m5.xlarge   |3500 |8	 |60  |1  |12 |
|STT-NS-3500-1709284000532 |ml.m5.xlarge   |3500 |8	 |60  |1  |12 |
|STT-NS-3500-1709288457864 |ml.m5.xlarge   |3500 |8	 |100 |1  |16 |
|STT-NS-3500-1709294277370 |ml.m5.xlarge   |3500 |4	 |50  |1  |17 |
|STT-NS-3500-1709310866526 |ml.m5.2xlarge  |3500 |8  |50  |4  |7  |
|STT-NS-3500-1709311432545 |ml.m5.2xlarge  |3500 |8  |50  |8  |7  |
|STT-NS-3500-1709312158614 |ml.m5.2xlarge  |3500 |8  |50  |2  |9  |
|STT-NS-3500-1709312950930 |ml.g4dn.xlarge |3500 |2  |50  |8  |27 |
|STT-NS-3500-1709310959319 |ml.g4dn.xlarge |3500 |2  |50  |4  |27 |
|STT-NS-3500-1709314690646 |ml.g4dn.xlarge |3500 |2  |50  |2  |27 |
|STT-NS-3500-1709316603587 |ml.g4dn.xlarge |3500 |2  |50  |1  |28 |
|STT-NS-3500-1709271107174 |ml.g4dn.xlarge |3500 |1	 |60  |1  |60 |


## Instances spec and cost 
|Instances type     |vCPU |Memory |Price per Hour $|
|-------------------|-----|-------|----------------|
|ml.m5.xlarge       |4    |16     |0.23            |
|ml.m5.2xlarge      |8    |32     |0.461           |
|ml.g4dn.xlarge     |4    |16     |0.7364          |


Note that all other variables being equal the best duration was with 8 x `ml.m5.xlarge` with 50 sec or 30 sec segment langth. Since 50 sec will lead to less segments, let's pick that.

## Transcriptioin quality and segment length 

An interesting observation was that, the transcription when the segment length is 50 sec is better than 100 sec for the same model and spec. Bellow are two examples I found illustrating the point.
The audio file is in [media](https://github.com/OpenPecha/stt-documentation/blob/main/media/STT_NS_3500_chop_00001.aac)
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