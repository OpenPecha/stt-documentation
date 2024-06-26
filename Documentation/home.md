# Welcome to stt-documentation :)

One stop location for all STT/TTS documentations

Repositories related to STT/TTS are 
- [stt-split-audio](https://github.com/OpenPecha/stt-split-audio)
    - Download audio from links in catalog google sheets and split the audio, run inference and create csv to be uploaded in stt.pecha.tools DB.
        - [STT_NS Catalog | Natural Speech](https://docs.google.com/spreadsheets/d/107pF1LcHgbJtCGCdGwffqIyM70eImBmgPOjUuHQfZ7g/edit?usp=sharing)
        - [STT_TT Catalog | Tibetan Teachings](https://docs.google.com/spreadsheets/d/1zX1JEUigHX5gSwfJKqeerhs_5Xxkq8wFbpVUBjrKEnc/edit?usp=sharing)
        - [STT_CS Catalog | Children Speech](https://docs.google.com/spreadsheets/d/1-WuaaWKIHJfGQhDXVSwG-v2qGqxQYVqqk7lFeHyxEzk/edit?usp=sharing)
        - [STT_MV Catalog | Tibetan Movies](https://docs.google.com/spreadsheets/d/1UOhU5Jcge89URmfagDf7Imm_QP74opOx6QsS2LaOSd0/edit?usp=sharing)
        - [STT_AB Catalog | Audio Book](https://docs.google.com/spreadsheets/d/1yKSzConuVWo8BuMDs2mabF5iiBKUz2wF--LIabFN6QE/edit?usp=sharing)
        - [STT_PC Catalog | Podcast](https://docs.google.com/spreadsheets/d/1wJ2tPcTec_KnIaN0qcn5fOhBGMzYSHBXmv3kgHYVPlg/edit?usp=sharing)
        - [STT_HS Catalog | History](https://docs.google.com/spreadsheets/d/1SjlnWsr6YVhBIW6EaS0ITmboDmEuj2VnxGRNL50OPx4/edit?usp=sharing)   
        - [STT_NV Catalog | News](https://docs.google.com/spreadsheets/d/1iKV46XlcFAWXOMq-I2dZXGZ7CttC2eW3/edit?usp=sharing&ouid=113331048033531729878&rtpof=true&sd=true)
- [pecha-tools-for-stt](https://github.com/OpenPecha/pecha-tools-for-stt)
    - The Next.js web app for annotation and reports
- [saymore-report-generator](https://github.com/OpenPecha/saymore-report-generator)
    - STT_MV and STT_NW are annotated on Saymore and uploaded on [MonlamAI GitHub](https://github.com/monlamai) while others are working in stt.pecha.tools
- [elan_parser](https://github.com/OpenPecha/elan_parser)
    - Used to generate reports for STT_MV and STT_NW
- [stt-combine-datasets](https://github.com/OpenPecha/stt-combine-datasets)
    - Combine all the STT/TTS datasets and create dataset for training and benchmark. This repo has information about where all the data are located.
- [stt-wav2vec2](https://github.com/OpenPecha/stt-wav2vec2)
    - Wav2Vec2 model training notebook
- [stt-whisper](https://github.com/OpenPecha/stt-whisper)
    - Whisper model training notebook
- [stt-model-evaluation](https://github.com/OpenPecha/stt-model-evaluation)
    - Evaluation of medel performance on benchmark
- [stt-sagemaker-endpoint](https://github.com/OpenPecha/stt-sagemaker-endpoint)
    - Deploy model on SageMaker Endpoint
- [stt-inference-api](https://github.com/OpenPecha/stt-inference-api)
    - FastAPI inference for STT/TTS. Not used currently.