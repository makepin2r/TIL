# 브랜치 삭제하기

## local branch 삭제
```shell   
    git branch -d [브랜치명]

    # 충돌사항이 남아 삭제가 불가능하다는 에러가 뜰 경우
    git branch -D [브랜치명]
```

## remote branch 삭제
```shell   
    git push origin --delete  [브랜치명]
```

---
### 참고
https://ifuwanna.tistory.com/284

