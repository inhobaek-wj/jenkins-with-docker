## Installation

- 최초 설치 시 log에 admin init password가 나오는데 이를 확인하기 위해서 detach mode(-d)로 실행하지 않는다.
(나중에 확인할 순 있음)

  ``` shell
  docker-compose up
  ```

- init password를 입력하여 로그인을 하면 plugin 설치 화면이 나오고 추천하는 것을 다 설치.

- 그 뒤 새 어드민 계정을 생성하면 끝.

## Project setup

1. Multibranch Pipeline으로 새 item을 만든다.
    - item 이름은 project repo 이름으로.
    - Pipeline과 Multiline pipeline의 차이
      - Pipeline: whole delivery cycle e.g. test | build | .. for a single branch.
      - Multiline pipeline: like pipeline for multiple branches.
    - Branch sources -> git -> git repo 주소 입력.
    - Behaviors: Filter by name (with regular expression)으로 master|dev를 설정.

2. Credentials 설정.
    - 3종류의 Credential Scopes
      - System: Only available on jenkins server NOT for jenkins jobs.
      - Global: Everywhere accessible.
      - Project: Limited to project, ONLY with multibranch pipeline, folder -> enables to organize build jobs in folders.

3. Jenkinsfile을 생성. (Jenkinsfile-sample 참고)
  
## Reference
https://youtube.com/playlist?list=PLy7NrYWoggjw_LIiDK1LXdNN82uYuuuiC
