Video 대상으로 VQA를 수행한 과정을 기록한 문서입니다.   
github: https://github.com/seo3650/video-question-answering

# Dataset
1. [MSVD-QA dataset](https://mega.nz/#!QmxFwBTK!Cs7cByu_Qo42XJOsv0DjiEDMiEm8m69h60caDYnT_PQ)와 [YoutubeClips](http://www.cs.utexas.edu/users/ml/clamp/videoDescription/)을 사용하였습니다. MSVD-QA는 `MSVD-QA`, YoutubeClips는 `MSVD-QA/video`에 저장하였습니다.
2. Youtube clip video의 이름을 수정하기 위해 [매핑 데이터](https://mega.nz/#!QrowUADZ!oFfW_M5wAFsfuFDEJAIa2BeFVHYO0vxit3CMkHFOSfw)를 사용하였습니다.
3. MSVD-QA dataset에서 **test_qa.json, val_qa.json, train_qa.json** 등을 적절히 수정하여, 1번부터 100번까지의 video만 사용하였습니다.

# Pretrained model
1. Video 처리를 위해 [VGG16 checkpoint](https://mega.nz/#!YU1FWJrA!O1ywiCS2IiOlUCtCpI6HTJOMrneN-Qdv3ywQP5poecM) 와 [C3D checkpoint](https://www.dropbox.com/sh/8wcjrcadx4r31ux/AAAkz3dQ706pPO8ZavrztRCca?dl=0)를 사용하였습니다. `util`에 저장하였습니다.
2. word embedding을 위해 [glove.6B.zip](https://nlp.stanford.edu/projects/glove/)를 사용하였습니다. **glove.6B.300d.txt**를 `util`에 저장하였습니다.

# Preprocess
1. **preprocess_msvdqa.py**에 있는 2개의 for 문에서 dataset의 개수를 확인하고 다음과 같이 전처리를 합니다.
```
python preprocess_msvdqa.py MSVD-QA
```

# Training & Test
1. 다음과 같이 training 및 test를 하였습니다.
```
python run_gra.py --mode [train/test] --gpu 0 --log log/evqa --dataset msvd_qa --config 0
```

# Result & Example
acc: 28.06% (Only 5% of the entire dataset was used.)   
   
`Question: "how many cats are walking up to a fence in a door frame?"`   
![Sample_video](./sample.gif)   
`Answer: two`
## Reference
https://github.com/ssemenova/RT-VQA
