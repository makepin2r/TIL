# git commit 취소하기
커밋 자체를 취소할 때
```shell
git reset --hard HEAD^ # commit 취소, 파일 삭제
git reset --mixed HEAD^ # commit 취소, 파일 보존, add되지 않은 상태
git reset --soft HEAD^ # commit 취소, 파일 보존, add된 상태
```