# Kaldi for STT


- [trial run](https://alphacephei.com/vosk/server)
- [introduction](https://kaldi-asr.org/doc/kaldi_for_dummies.html)
- [install aws](https://jrmeyer.github.io/asr/2017/10/13/Kaldi-AWS.html)
- [install official](https://kaldi-asr.org/doc/install.html)
- [install newer](https://www.assemblyai.com/blog/kaldi-install-for-dummies/)
- [amdo example](https://github.com/kaldi-asr/kaldi/tree/master/egs/xbmu_amdo31)
- [chinese example](https://en.speechocean.com/about/newsdetails/97.html#)
- [Tibetan lexicon in the word level](http://index.cslt.org/mediawiki/index.php/ASR-nsfc-data) this will be helpful in building pronunication dictionary

The audio is first transformed into phonetics using the `pronunication dictionary`. It's a (text: word) -> (text: pronunication) mapping file.
The phonimes are then used by the Language model to guess the actual characters to output. 

Kaldi does not generalize well but the model is efficient and scales well. It works on mobile. It can be used in language training to test pronunciation.

## Using the [Amdo Exmaple](https://github.com/kaldi-asr/kaldi/tree/master/egs/xbmu_amdo31)

```sh
after installing kaldi change to egs
cd /home/username/kaldi/egs/xbmu_amdo31/s5

## Change queue to run.pl

https://github.com/kaldi-asr/kaldi/blob/master/egs/xbmu_amdo31/s5/cmd.sh#L13


export train_cmd="run.pl"
export decode_cmd="run.pl"
export mkgraph_cmd="run.pl"


## Download data

mkdir /home/username/export/data

cd /home/username/export/data
wget https://www.openslr.org/resources/133/xbmu_amdo31.tar.gz
tar -xvzf xbmu_amdo31.tar.gz 
cd xbmu_amdo31/data/wav
for wav in ./*.tar.gz; do
    echo "Extracting wav from $wav"
    tar -zxf $wav && rm $wav
  done


## Update run.sh with paths
https://github.com/kaldi-asr/kaldi/blob/master/egs/xbmu_amdo31/s5/run.sh#L17
# corpus directory and download URL
data=home/username/export/data

## Prepare dict
./local/xbmu_amdo31_prepare_dict.sh /home/username/export/data/xbmu_amdo31/resource/

## Prepare data
./local/xbmu_amdo31_data_prep.sh /home/username/export/data/xbmu_amdo31/data/wav/ /home/username/export/data/xbmu_amdo31/data/transcript/
```
    
this is example of the proncuniation disctionary
data/local/dict/lexicon.txt

```tsv
ཀ k a
ཀག k a k
ཀང k a ng
ཀད k ecb
ཀན k ec
ཀབ k a p
ཀམ k a m
ཀར k aw
ཀས k ecb
ཀི k i
ཀིང k i ng
ཀིན k ii
ཀིམ k i m
ཀིམས k i m
ཀིར k iw
ཀུག k u k
ཀུང k u ng
ཀུན k yy
ཀུམ k u m
ཀུར k uw
```

and this is example of the transcript for training
data/test/text
```tsv
a_0_cacm-A70_31050 ཁྱོད ཚོ འབྲོག པ ས ཆ གི མྱིས གོན ན ད ངེས ངེས འེབ དེ ཡིན
a_0_cacm-A70_31051 རྒྱལ ཁ ཡང ནས ཡང དུ བླངས པ རེད
a_0_cacm-A70_31052 སློབ སྦྱོང ལ ཤུགས སྣོན རྒྱག དགོས པའི གནད དོན
a_0_cacm-A70_31053 ཐུག པ ཞལ ལུ གང བསྐོལ ནས ལྷ གཅིག ཀོང ཇོ ལ འདྲེན པ
a_0_cacm-A70_31054 འདི ལོ ནམ ཐང ནས ལོ ཏོག ལ སྐྱོན ཆེན པོ ཤོར སོང
a_0_cacm-A70_31055 དམངས གཙོ རང དབང གི སྲུང དམག ཏུ རྒྱན སྤྲོས བྱས ཤིང
a_0_cacm-A70_31056 ཁྱོད ཀྱིས འདི ལྟར རང ལུས ང ལ སྟེར བ བཞིན དུ གཞན ལའང འདི ལྟར སྟེར ངེས རེད སྙམ སྲིད
a_0_cacm-A70_31057 དེའི ནང ནས ཆོས ཉིད ལྡན པའི རིགས བཙལ དགོས
a_0_cacm-A70_31058 འདི ནི སྲིད འཛིན དོ དམ སྒྲིག སྲོལ བསྒྱུར བཅོས གཏིང ཟབ ཏུ སྤེལ བའི ལྟེ གནད ཡིན
a_0_cacm-A70_31059 དིམ བསགས དངོས པོ ནི ཅིས ཀྱང ཤིན ཏུ མཐུག ཅིང མཁྲེགས པ
a_0_cacm-A70_31060 ཡིད རྩེ གཅིག གི སྒོ ནས ཟོལ སྦྱོར གྱི བྱ སྤྱོད སྤངས པ
a_0_cacm-A70_31061 རང རྒྱལ སྤྱི ཚོགས རིང ལུགས ཀྱི ལོ རྒྱུས ཆ རྐྱེན འོག
a_0_cacm-A70_31062 དེ དངོས གནས དང ལེན བྱ མིན ལ གལ མི ཆེ བ ཡིན
a_0_cacm-A70_31063 ཧུར བརྩོན གྱིས དགོན པའི རང གསོའི ནུས པ མཐོ རུ གཏོང དགོས
a_0_cacm-A70_31064 ཁོང གིས ལས ཀར རྩ བ ནས ཕམ ཁ འབྱུང བ རེད
a_0_cacm-A70_31065 གལ ཏེ ཤིང རྟ མོ ལྗང ཁུ འབའ ཞིག འཚོ བ ཡིན ན
a_0_cacm-A70_31066 གཅིག ནི བཞད པ དང གྲུབ ཚུལ དཀྱུས མའི མེ ཏོག ཡིན ལ
a_0_cacm-A70_31067 ང ཚོས རིགས འབྱེད པ ཡིས ཆ ཤས རེ རེ བྱས ནས ཐེར འདོན བྱས ཡོད
```