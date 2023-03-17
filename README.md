# GIT FLOW

각 상황에 맞는 브랜치 모델을 제시하고 해당 브랜치에 맞게 work flow를 구성할 수 있도록 돕는다.
 
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
> **1. Remote에 올라간 파일 / 폴더를 삭제**

1) 서버 , 로컬 모두에서 지우고 싶은경우
```js
git rm -r 폴더명 or 파일명 
```
2) 로컬에는 남기고 서버에서만 지우고 싶은 경우
```js
git rm -r  --cached 폴더명 or 파일명 
```

> **2. 실수로 master 브랜치에서 작업**
1) push는 하지 않은 경우

- 마스터에서 새로운 임시브랜치 생성
- topic(기능 개발 브랜치)에서 1번에 생성한 임시브랜치 merge
- master를 리셋하고 ( git reset --hard HEAD~) 
- 임시브랜치 삭제
<br/>

2) push까지 한 경우

- 마스터에서 새로운 임시브랜치 생성
- master를 리셋하고 ( git reset --hard HEAD~) 
- 서버에 리셋된 로컬 master를 강제로 push (git push -f origin master)
- topic(기능 개발 브랜치)에서 1번에 생성한 임시브랜치 merge

> **3. 실수로 작업중인 브랜치를 삭제**
- git reflog으로 커밋 로그에서 작업하던 브랜치 마지막 커밋시점 해쉬값  확인 
- 브랜치 다시 만들면서 해쉬값 부여하면 해당 커밋내용에 맞는 브랜치로 생성됨 (git checkout -b topic 커밋해쉬값)

> **4. 특정 태그로 긴급 롤백 & 다시 hotfix**

- 특정 tag로 리셋 ( git reset --hard 0.2.0(태그명))
- 리셋된 상태를 강제로 remote master로 push
- 새로운 핫픽스 생성 버그 수정
- develop 브랜치와 merge 
- remote로 push

```
 local tag 삭제 (git tag -d 태그명)
 로컬에서 삭제 후 remote tag 삭제 (git push origin :태그명)
```

