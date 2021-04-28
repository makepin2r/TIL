# 임시로 특정 파일을 커밋 내역에서 제외하기
`.gitignore` 외에 임시로 커밋에서 제외할 파일이 있을 때 사용
```shell
    git update-index --assume-unchanged 파일명 # 워킹트리에서 파일 제외하기
    git update-index --no-assume-unchanged 파일명 # 제외한 파일 되돌리기
    git update-index --really-refresh # 제외한 모든 파일 다시 되돌리기

    git ls-files -v | grep ^h # 제외된 파일 리스트 보기
```
