# Speech To Text

## Task
STT for Child : 어린이(초등 1~4학년)의 음성을 Text로 변환 \
Input : 어린이의 단어/문장 발화 녹음 파일 \
Output : 발화 Text

## Dataset
| Phase | # |
| - | - |
| train | 11,340 |
| validate | 2,430 |
| test | 2,430 |


## Data Directory
```
\_data
    \_ train
        \_ xxxxxxxxxxx.pcm ..., train_label.txt
    \_ validate
        \_ xxxxxxxxxxx.pcm ..., validate_label.txt
    \_ test
        \_ xxxxxxxxxxx.pcm ..., test_label.txt

```
## Data Sample
```
sample_pcm 폴더 확인
 - 예시 pcm 데이터 제공
 - 예시 pcm 데이터를 wav 파일로 변환하여 제공
※ Meta Data for .pcm : channels=1, bit_depth=16, sampling_rate=16000
```

## Label Sample
```
# train_label.txt
./I0007_M1_OFC_105.pcm 사자
./M0193_M4_OFC_063.pcm 원숭이
./M0007_M1_OFC_043.pcm 사과
./I0129_M3_OFC_075.pcm 컴퓨터
./I0187_F4_OFC_084.pcm 저에게친절하게대해주시기때문입니다
./M0192_M4_OFC_063.pcm 주사
./M0066_M2_OFC_083.pcm 아빠
./I0010_M1_OFC_007.pcm 돌
./G0012_M1_OFC_052.pcm 선생님
./M0187_F4_OFC_036.pcm 세탁기
...

※ 발화 레이블에는 띄어쓰기 및 특수문자(., ?, ! 등) 없음

```

## Metric
```
평가를 위한 Metric : 음절단위 F1

```

## Commands
```
# train
python main.py 

# test (for submission)
python main.py --batch=4 --mode="test" --model_name 1.pth

모든 옵션은 default value가 있음
옵션은 main.py 파일 참고
```


```
!!!!!!!!!!!!!!!!!!!!! 필독!!!!!!!!!!!!!!!!!!!!!!!!!!!
** 컨테이너 내 기본 제공 폴더
- /datasets : read only 폴더 (각 태스크를 위한 데이터셋 제공)
- /tf/notebooks :  read/write 폴더 (참가자가 Wirte 용도로 사용할 폴더)
1. 참가자는 /datasets 폴더에 주어진 데이터셋을 적절한 폴더(/tf/notebooks) 내에 복사/압축해제 등을 진행한 뒤 사용해야합니다.
   예시> Jpyter Notebook 환경에서 압축 해제 예시 : !bash -c "unzip /datasets/objstrgzip/18_NLP_comments.zip -d /tf/notebooks/
   예시> Terminal(Vs Code) 환경에서 압축 해제 예시 : bash -c "unzip /datasets/objstrgzip/18_NLP_comments.zip -d /tf/notebooks/
   
2. 참가자는 각 문제별로 데이터를 로드하기 위해 적절한 path를 코드에 입력해야합니다. (main.py 참조)
3. 참가자는 모델의 결과 파일(Ex> prediction.txt)을 write가 가능한 폴더에 저장되도록 적절 한 path를 입력해야합니다. (main.py 참조)
4. 세션/컨테이너 등 재시작시 위에 명시된 폴더(datasets, notebooks) 외에는 삭제될 수 있으니 
   참가자는 적절한 폴더에 Dataset, Source code, 결과 파일 등을 저장한 뒤 활용해야합니다.
   
!!!!!!!!!!!!!!!!!!!!! 필독!!!!!!!!!!!!!!!!!!!!!!!!!!!
```
