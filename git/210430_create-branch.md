# 브랜치 추가하기

## 1. local branch 생성
```shell
    git branch [브랜치명]
```

## 2. remote branch 생성
- 생성한 로컬 브랜치로 이동한 뒤(`git checkout [브랜치명]`), 다음 명령 입력
```shell
    git push [리모트명] [브랜치명]
```

## 3. local branch 와 remote branch 연동
- 생성한 로컬 브랜치에서 다음 명령 입력
```shell
    git branch --set-upstream-to [리모트명]/[브랜치명]
```
- 1과 2 방식대로 브랜치를 푸쉬한 경우 3을 하지 않아도 잘 작동하긴 한다. (로컬 브랜치 생성 후 -> 리모트에 바로 푸쉬) 그러나 로컬과 리모트가 따로 생성되었을 경우 꼭 연동해주어야 한다.