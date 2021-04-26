# 로컬저장소 푸쉬

1. git 계정 초기설정

2. git inite

3. git remote add origin 주소

4. git add * (*=all)

5. git status 로 상태확인

6.   git remote -v 로 주소 확인

7. git commit -m "" 커밋 필수

8. ```javascript
   git push -u origin master
   ```

* 연동 주소 삭제 git remote remove origin
* refspec master does not match any 오류는 저장소에 올려져있는 데이터랑 일치 않아서 덮여 씌울수 있기 때문에 뜨는 경고 풀후 푸쉬하자git remote set-url origin https://heckevil@github.com/heckevil/MarkDown.git

git pull origin main(브런치 이름)

이후 푸쉬