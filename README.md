## GIT FLOW

`master`  - 실제 배포가 되는 브랜치
`develop` - 개발의 주축이 되는 브랜치
`feature`  - 각 기능별로 생성되고 기능 구현시 삭제되는 브랜치
`release`  - 배포를 위한 작업들을 하는 브랜치이다
`hotfix` - master branch 배포후에 생기는 버그등을 급하게 수정하는 브랜치이다


>  ### git flow branch merge 순서

feature -> develop -> release -> master 

>  ### git flow 명령어 및 사용 예시

1. git flow init =   master  ,  develop 2개의 브랜치가 생긴다.

2. git flow feature  start 기능명  => 기능 개발을 위한 특정브랜치가 생긴다

3. add commit push 하고 github으로 가서 pull request 생성

4. 리더가 코드리뷰후 머지  feature 브랜치 삭제 

5. 개발자는 머지 확인 후에 

6. git flow feature finish 기능명 -> 기능 개발을 마친 브랜치는 develop으로 merge되고 해당 브랜치가 삭제된다2

