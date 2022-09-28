# chapter5

## 5.1 서버 저장소 <br>
원격(remote) 저장소나, 로컬 저장소의 코드를 복제한 복사본이라고도 함 <br>
장점: 코드의 안전한 보관, 소스 코드를 다른 사람들과 공유, 협업하여 개발 진행 가능

### 5.1.1 협업 저장소 <br>
여러 명의 개발자가 규모가 큰 프로젝트를 효율적이고 좋은 품질로 개발하기 위한 협업 도구 <br>
유연한 개발을 위해 분산형 모델 선택

### 5.1.2 연속된 작업 <br>
장점: 원격 저장소에 개발 중인 코드의 서버를 저장한다면 어디서든 동기화 가능해 연속된 작업이 가능 <br>
분산된 저장소 통일, 최신 코드 배포, 여러 컴퓨터에 동기화, 결과물을 다시 서버로 통합

### 5.1.3 새 멤버 <br>
새로운 멤버와의 협업에서는 복잡한 단계를 거치지 않아도 깃의 원격 저장소 주소를 알려주어 쉽게 <br>
버전을 공유하는 것이 가능


## 5.2 깃허브 서버 준비 <br>
호스팅을 받아 쉽게 원격 저장소 운영 가능

### 5.2.1 깃허브 <br>
대표적인 깃호스팅 서비스이며 무료 <br>
:pushpin:http://github.com/사용자이름

### 5.2.2 저장소 생성 <br>
공개용 저장소와 비공개용 저장소(일부 유료 서비스) 두 개가 존재
1. New repository를 선택하여 저장소 생성 
2. 소유자(owner)를 확인, Repository name에 저장소 이름 입력(대소문자, 숫자, 하이픈, 밑줄 가능)
3. 저장소 URL은 http://github.com/소유자/저장소 <br>
한 소유자 안에 같은 저장소 이름은 중복 불가능


## 5.3 깃허브 연동 및 원격 등록 <br>
저장소와 로컬 저장소의 연결

### :pushpin:5.3.1로컬 저장소 <br>
README 파일을 체크하지 않은 상태에서 로컬 저장소와 원격 저장소를 연결하는 두 가지 방법 
1. 새로운 로컬 저장소를 생성하고 원격 저장소 연결
> $ mkdir 새 폴더 이름 <br>
> $ cd 새 폴더 이름 <br>
> $ git init <br>
> $ echo "# 파일 이름" >> REAM.md <br>
> $ git add README.md <br>
> $ git commit -m "커밋 내용"

2. 기존 저장소 연결

### 5.3.2 프로토콜 <br>
깃이 서버와 통신할 수 있도록 함, Local, HTTP, SSH, Git 네 종류

1. Local: 원격 저장소를 생성, 자시의 컴퓨터를 Network File Syster 등 서버로 이용할 때 편리 <br> 
$ git remote add 원격저장소별칭 폴더경로 <br>
폴더 경로만 입력하면됨, 간단한 서버 구축, 빠른 동작 가능 <br>
모든 자료가 자신의 컴퓨터에 집중되는 위험

2. HTTP <br>
서버에 접속하려면 로그인 절차 필요, 익명 혹은 계정을 이용하여 처리 가능

3. SSH <br>
깃에서 권장하는 프로토콜, 높은 수준의 보안 통신 처리로 안전 <br>
'ssh://계정@주소'처럼 프로토콜 타입 지정, 현재 로그인된 사용자로 대체 가능 <br>
접속 시 인증서가 만들어지는데 별도의 로그인이 필요없음 <br>
인증서는 공개키(서버에 등록), 개인키(로컬에 저장) 두 개 존재 <br>
익명 접속 불가능, 그래서 깃 서버 운영에 적합

4. Git <br>
깃의 데몬 서비스를 위한 전용 프로토콜 방식 <br>
SSH와 유사하지만 인증 시스템이 없어 보안에 취약 <br>
잘 사용하지 않음

### :pushpin:5.3.3 원격 저장소의 리모트 목록 관리 <br>
깃은 원격 저장소(서버)를  관리할 때 remote 명령어를 사용 <br>
현재 연결된 원격 저장소 목록 확인 가능, 등록과 취소 등 장업 가능 <br>
-help옵션으로 다양한 기능을 확인 가능
 
$ git remote: 원격 저장소의 이름(별칭) 출력, 원격 저장소 목록 확인할 때 편리 <br>
$ git remote -v: 원격 저장소의 별칭 이름과 URL확인 가능

저장소의 권한 정보까지는 알 수 없지만 복수의 원격 저장소를 연결해 사용 가능하면 목록을 모두 출력 가능

### 5.3.4 주소와 별칭 <br>
로컬 저장소에 원격 저장소(서버)를 등록하려면 서버 주소 필요 <br>
깃허브 같은 저장소는 프로토콜+도메인 주소, 로컬에 서버 저장소 생성에는 폴더 경로 사용

- 별칭: 원격 서버의 주소는 긴 문자열 형태이기 때문에 긴 서버 URL 문자열을 별칭으로 만들어 사용 가능
- origin: 대표적으로 사용하는 별칭, 원격 서버와 연결할 때 별칭으로 많이 사용

### 5.3.5 원격 저장소에 연결 <br>
원격 저장소를 연결할 때, **add 옵션** 사용
> $ git remote add 원격저장소별칭 원격저장소URL
>> $ git remove -v <br>
>> 원격저장소별칭 원격저장소URL (fetch) <br>
>> 원격저장소별칭 원격저장소URL (push)

- fetch : 서버에서 가지고 오는 동작
- push : 서버로 전송하는 동작
 별칭은 중복하여 선택 불가
 
 ### 5.3.6 소스트리에서 원격 브랜치 <br>
 원격 저장소를 등록하면 기존 master 브랜치와 달리 또 하나의 브랜치가 표시됨
 
 **별칭/브랜치**는 원격 저장소의 브랜치를 의미
 
 ### 5.3.7 별칭 이름 변경과 정보 <br>
 별칭은 긴 문자열의 서버 주소를 대체, <br>
 등록된 서버의 별칭 이름은 다시 변경 가능 **rename 옵션** 사용
 > $ git remote rename 변경전 변경후
  
 remote 명령어는 간략한 원격 저장소 정보만 출력 <br>
 원경 저장소의 상세한 정보를 확인하려면 **show 옵션** 사용
 > $ git remote show 원격저장소별칭
 
 ### 5.3.8 원격 서버 삭제 <br>
 로컬 저장소는 복수의 원격 저장소와 연결 가능 <br>
 풀 리퀘스트, 테스트 등의 목적으로 임시 등록된 원격 저장소가 있으며, 등록된 원격 저장소는 **rm 옵션**으로 삭제 
 > $ git remote rm 원격저장소별칭
 
 
 ## 5.4 서버 전송 <br>
 원격 저장소가 연결되면 로컬 저장소의 커밋 업로드 가능
 
 ### :pushpin:5.4.1 push : 서버에 전송 <br>
 원격 저장소로 커밋된 파일을 업로드하는 동작 <br>
 원격 저장소로 로컬 깃 저장소의 내용을 전송할 때 **push 명령어** 사용
 > $ git push 원격저장소별칭 브랜치이름
 별칭 이름을 가지는 서버의 master 브랜치에 현재 브랜치를 업로드
 
 처음 푸시하면 서버에 새로운 master 브랜치 생성 <br>
 로컬의 master 브랜치 안에 있는 소스 코드를 서버의 master 브랜치로 업로드
 
 원격 저장소에 푸시하면 master 브랜치가 총 2개 생성
  1. 로컬 저장소의 master 브랜치
  2. 서버의 master 브랜치
 전송은 두 브랜치 간에 전송과 수신을 동기화
 
 자신의 로컬 저장소를 **백업**하는 용도로 원격 저장소 사용 가능
 
 
 ## 5.5 자동으로 내려받기 <br>
 원격 저장소에서 커밋된 코드를 내려받는 방법
 
 ### :pushpin:5.5.1 clone : 복제 <br>
 기존 저장소를 이용하여 새로운 저장소를 생성하는 방법 중 하나 <br>
 일반적인 복제와 원격 저장소를 복제하는 방법에 차이가 있음
 + 복제할 때, **clone 명령어** 사용
  + clone 명령어는 초기화 init 명령어 외에 원격 서버 접속에 필요한 추가 설정 자동으로 수행
  + 서버의 연결 설정을 마친 후 서버 안에 있는 모든 커밋된 코드 이력을 한 번에 내려받음
   > $ git clone 원격저장소URL
   
 ### :pushpin:5.5.2 pull : 서버에서 내려받기 <br>
 복제 후 원격 저장소의 개인된 내용을 추가로 내려받으려면 **pull 명령어** 사용
  + pull 명령어는 로컬 저장소보다 최신인 갱신된 원격 저장소의 커밋 정보를 현재 로컬 저장소로 내려받음
  + 주기적으로 사용하면 최신 커밋 정보로 로컬 저장소 유지 가능
   > $ git pull
  + 원격 저장소와 로컬 저장소 간 커밋 반영 가능
 
 
 ## 5.6 수동으로 내려받기 <br>
 원격 저장소 내용을 내려받는 방법
 
 ### 5.6.1 자동 병합 <br>
 pull은 원격 서버에서 현재 커밋보다 더 최신 정보가 있을때 내려받아 임시 영역에 저장 <br>
 스테이지 영역이 아닌 원격 저장소를 위한 전용 임시 브랜치가 따로 있음 <br>
 내려받은 최신 커밋을 현재 브랜치로 자동 병합 처리 <br>
 - 병합: 원격 서버 파일과 로컬 파일을 하나로 합치는 과정 
  + 혼자 개발하는 프로젝트에 사용하기 좋음
  + 여러 개발자와 협업 할 때 오류가 발생할 수 있음
 
 ### 5.6.2 fetch: 가져오기 <br>
 원격 저장소에서 코드를 수동으로 내려받는 작업 수행 <br>
 커밋된 코드를 임시 브랜치로 내려받은 후 현재 브랜치와 자동 병합하지 않음 <br>
 > $ git fetch 원격저장소URL <br>
 <br> pull 명령어와 달리 fetch 명령어를 실행한 후 커밋이 추가된 것을 확인할 수 없음
  + 원격 저장소의 커밋들만 가지고 올 뿐 로컬 저장소에서 어떤 작업도 하지 않음
 
 ### 5.6.3 merge 명령어로 수동 병합 <br>
 fetch로 내려받은 커밋을 로컬 저장소에 적용하려면 병합 명령인 **merge 명령어** 사용
 > $ git merge 원격저장소별칭/브랜치이름
  fetch 명령어로 내려받은 커밋들이 추가된 것을 확인할 수 있음


 ## 5.7 순서 <br>
 원격 저장소에서는 다수의 개발자가 동시에 커밋을 푸시할 수 없음, 순차적으로 푸시해야 함
 
 ### 5.7.1 최신 상태 <br>
 원격 저장소에 푸시하려면 로컬 저장소를 최신 상태로 유지해야 함 <br>
 커밋이 순차적이지 않을 때 깃은 푸시 동작을 거부 <br>
 푸시 동작이 거부되면 pull 또는 fetch 작업으로 로컬 저장소를 갱신하고 다시 푸시해야 함
 
 ### 5.7.2 충돌 방지 <br>
 깃이 최신 상태에서만 푸시를 허용하는 것은 충돌을 방지하기 위함 <br>
 pull 작업은 내려받은 커밋들을 현재 브랜치로 자동 병합하는데, 이때 커밋 내용이 순차적이지 않으면 병합 과정에서 충돌 발생 <br>
 깃은 이러한 충돌을 쉽게 해결하기 위해 푸시할 때 커밋의 순차적 기록을 확인 <br>
 push 명령어를 사용할 때 충돌을 최소화하기 위해 미리 원격 저장소를 확인 <br>
 pull 명령어를 사용해 새로운 커밋 갱신이 없는지 지속적으로 확인하는 것이 좋음 <br>
  + 권장 순서: pull -> coding -> commit -> pull -> push <br>
 소스트리의 push 위에 현재 로컬 저장소와 원격 저장소 간 커밋 차이점을 출력하는 작은 숫자가 표시됨
 
 
 ## 5.8 정리:bulb:
 1. 깃은 코드 이력을 관리해주고 다른 개발자와 협업 도구로도 많이 사용
    + 다른 개발자와 협업하려면 공유 매개체의 역할을 수행할 서버가 필요
 2. 다양한 종류의 서버 지원
    + 깃 서버를 직접 만들 수 있음
    + 인기 있는 깃 호스팅 서비스를 이용할 수 있음
 3. 서버 역할을 수행하는 원격 저장소와 커밋 정보들을 주고 받음
    + 로컬 컴퓨터는 원격 저장소에 커밋 코드를 전송하거나 추가된 커밋을 내려받을 수 있음
 4. 원격 저장소를 불특정 다수를 대상으로 공유 가능
 5. 오픈 소스를 활성화 하는 데 가장 많은 기여를 하는 협업 툴
