# GIT FLOW

- 각 상황에 맞는 브랜치 모델을 제시하고 해당 브랜치에 맞게 work flow를 구성할 수 있도록 돕는다.
---

> ### branch

|branch|설명|
|--|--|
|`master`|실제 배포가 되는 브랜치 |
|`develop`|개발의 주축이 되는 브랜치 |
|`feature`|각 기능별로 생성되고 기능 구현시 삭제되는 브랜치 |
|`release`|배포를 위한 작업들을 하는 브랜치이다 |
|`hotfix`| master branch 배포후에 생기는 버그등을 급하게 수정하는 브랜치이다 |

<br/>

>  ### git flow branch merge 순서

```

feature -> develop -> release -> master 

```

>  ### git flow 명령어 및 사용 예시

1. git flow init =   master  ,  develop 2개의 브랜치가 생긴다.

2. git flow feature  start 기능명  => 기능 개발을 위한 특정브랜치가 생긴다

3. add commit push 하고 github으로 가서 pull request 생성

4. 리더가 코드리뷰후 머지  feature 브랜치 삭제 

5. 개발자는 머지 확인 후에 

6. git flow feature finish 기능명 -> 기능 개발을 마친 브랜치는 develop으로 merge되고 해당 브랜치가 삭제된다2


> ### Trouble shooting

#### 발생할 수 있는 문제들
> 1. Remote에 올라간 파일 / 폴더를 삭제
1) 서버 , 로컬 모두에서 지우고 싶은경우
```js
git rm -r 폴더명 or 파일명 
```
2) 로컬에는 남기고 서버에서만 지우고 싶은 경우
```js
git rm -r  --cached 폴더명 or 파일명 
```

2. 실수로 master 브랜치에서 작업
3. 실수로 작업중인 브랜치를 삭제
4. 특정 태그로 긴급 롤백 & 다시 hotfix



