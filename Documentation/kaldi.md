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
    

