# 절대경로와 상대경로
> ⭐️ 절대경로란?
* 최상위 디렉토리까지 모두 표시된 경로
* ex) 우리집은 서울지 광진구 OO길 25 1001호야
``` ruby
C:\USERS\BETTERTOSPEAK\PART4\BREWERY.txt
```
> 💫 상대경로란?
* 현재 디렉토리를 비교 대상으로 삼아 작성된 경로
* ex) 지금 서있는 위치에서 버스타고 2블럭 가서 OO상가 밀집지구 안으로 들어가면 보이는 건물 1001호야
``` ruby
아래와 같은 상황에서

/home/user/project/
├── data/
│   └── data.csv
├── script/
│   └── analysis.py   # 출발점
└── README.md

현재 절대경로 : /home/user/project/analysis.py

만약 목적지가 /home/user/project/data/data.csv라면,
../data/data/csv 라고 작성

(.. : 상위 디렉토리로 이동)
```

# Git의 branch
> 📌 Git
* 깃은 **버전 관리 시스템(Version Control System)** 으로, 프로젝트를 진행하는 과정에서 업데이트 내용을 따로 저장하는 것이 아니라 분산시켜 각 버전을 관리함
* 브랜치를 활용해 여러 개발자들이 비선형적인 개발을 수행(= 병렬적으로 수행)하는 것을 가능하게 함
> 🕊️ Git에서의 branch
* branch : commit 단위로 구분된 소스 코드 타임라인에서의 분기점, 즉 주된 개발 경로(master/main)에서 분리된 독립적인 개발 경로
  * branch에서 작업을 완료하면 merge 작업 수행 가능
    
    ![Image](https://github.com/user-attachments/assets/4942dbc4-e857-4054-908d-f16f39469341)  </br> 
    위 그림처럼main이 아니라 branch에서 branch로 합쳐서 진행하는 경우도 존재함
