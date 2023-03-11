```
fetch 를 필요로하는 정교한 상황이 있을 수 있음

일단 pull하게 되면 두 브랜치가 같은 곳을 보게됨
git fetch origin main 을 하게되면 origin main이 main 을 앞서게 됨
(다운로드한 최신 커밋이 원격저장소의 몇번인지 적어두고 로컬엔 반영을 안한다는 말)

=> 이때 git diff HEAD origin HEAD를 하게되면 그 차이를 확인하고 
=> 합칠 수 있음(git merge origin/main)
```

[생활코딩-지옥에서 온 Git - pull VS fetch의 원리](https://www.youtube.com/watch?v=V6R96Hzm8hY&list=PLuHgQVnccGMA8iwZwrGyNXCGy2LAAsTXk&index=43)
