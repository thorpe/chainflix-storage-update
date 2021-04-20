# 체인플릭스 프로그램 설치하기
<hr>

```
리눅스 시스템의 경우 보안이슈로 일반 유저의 권한과 슈퍼유저의 권한이 있습니다.
슈퍼유저의 권한이 필요할때 비밀번호를 입력하게 받으며, 리눅스 설치한 비밀번호를 입력하시면 됩니다.
```

<hr>

### Step-01 첫번째 리눅스의 슈퍼권환을 가집니다.
root@chainflix:/home# sudo su -
```
비밀번호 입력
```
##### 알림1 : 비밀번호를 입력하지만 모니터 화면에는 아무것도 안쳐지는것 처럼 보이지만 실제로는 비밀번호가 입력되어집니다.
##### 알림2 : 리눅스 설치때 입력하였던 비밀번호를 넣어주세요. 체인플릭스 앱의 비밀번호와는 상관이 없습니다.

<hr>

### Step-02 필수 프로그램 설치 - 필요한 프로그램을 설치합니다.
root@chainflix:/home# sudo apt-get install vim
```
설치되는 과정이 보여집니다.
```

<hr>

### Step-03 폴더생성 - 체인 플릭스 설치할 폴더를 만듭니다.
root@chainflix:/home# mkdir /home/chainflix
```
화면에 아무런 표시가 되지 않습니다.
```

<hr>

### Step-04 설치할 폴더에 들어가기를 진행합니다.
root@chainflix:/home# cd /home/chainflix
```
화면에 아무런 표시가 되지 않습니다.
```

<hr>

### Step-05 체인플릭스 프로그램 다운받기를 진행합니다.
root@chainflix:/home# sudo wget https://github.com/jampick-kr/chainflix-storage-update/releases/latest/download/chainflix.linux.tar.gz
```
Resolving github.com (github.com)... 15.164.81.167
HTTP request sent, awaiting response... 200 OK
Length: 20507613 (20M) [application/octet-stream]
Saving to: ‘chainflix.linux.tar.gz’

chainflix.linux.tar.gz  100%[==========================================>]  19.56M  7.70MB/s    in 2.5s
```

<hr>

### Step-06 다운받은 체인플릭스 압축 풀기를 진행합니다.
root@chainflix:/home/chainflix# tar xvfzp chainflix.linux.tar.gz
```
chainflix
lib/
lib/node_sqlite3.node
lib/core.bin
```
<hr>

### Step-07 압축을 풀었기때문에 다운받은 파일 삭제하기 - 필수아님
root@chainflix:/home/chainflix# rm -rf chainflix.linux.tar.gz
```
화면에 아무런 표시가 되지 않습니다.
```
<hr>

### Step-08 체인플릭스 프로그램 실행하기
root@chainflix:/home/chainflix# ./chainflix start
```
[LAUNCHER] task run
[LAUNCHER] [APP] CHAINFLIX STORAGE START v1.1.8

[LAUNCHER] [SERVER] HTTP SERVER START http://192.168.0.2:3001

[LAUNCHER] [ST] Init Storage System
[ST] File verification is Starting

[LAUNCHER] [ST] File verification complete!

[LAUNCHER] [ST] Video Count: 0
[ST] Size Available 100.00 GB

[LAUNCHER] [SOCKET] Connected a Storage Controller https://sc-socket.chainflix.net

[LAUNCHER] [SOCKET] Storage Id

[LAUNCHER] [SOCKET] login fail Required parameters: storage_id,api_key

[LAUNCHER] [SOCKET] Storage Disconnect undefined
.
```
##### 알림1 : 컨트롤-x 또는 컨트롤-c 눌러 빠져나옵니다..
##### 알림2 : 설치 폴더아래 conf 폴더 생성, config.json 파일이 생성되어 있어야 합니다.

<hr>

### Step-09 체인플릭스 환경 설정하기
root@chainflix:/home/chainflix# vi ./conf/config.json
```
{
  "stream": {
    "rootPath": "",
    "rootFolder": "./videos/",
    "throttle": 100000000
  },
  "storage": {
    "controller_url": "https://beta-controller.chainflix.net:3002",
    "storage_id": "",
    "api_key": "",
    "size_max": 100,
    "http_port": 3001,
    "https_port": 3002,
    "uploadPath": "./uploads/",
    "max_traffic": 1000
  }
}
```
##### 알림1 : 간혹 vi 입력시에 모드(읽기모드, 수정모드등등)을 요청하는 화면이 보이시면 수정모드(E)를 눌러 진입해주세요.
##### 알림2 : vi로 진입하셨으면 i = 쓰기모드(설정값을 넣을수 있는 상태) / :wq = 저장후 종료하기 입니다.
##### 알림3 : i를 눌러 설정값을 수정할수 있는 상태이면 storage_id와 api_key는 chainflix.net 홈페이지에서 확인후 입력해주세요.
##### 알림4 : Size_max : 100이면 100G / 3000G = 3테라 입니다.
##### 알림5 : 하드디스크 2개로 서비스하실때 체인플릭스 저장위치를 다르게 하실경우 rootFolder / uploadPath 경로를 절대 경로로 잡아주세요.

<hr>

### Step-10 마지막단계 - 체인플릭스 실행하기
root@chainflix:/home/chainflix# sudo ./chainflix start
```
2020-06-09 14:46:58 info: Daemon Starts ..................
2020-06-09 14:46:58 info: Content Count: 0
2020-06-09 14:46:58 info: Size Available: 100.00GB
2020-06-09 14:46:58 info: VidStreamer up and running on http port : 3001
2020-06-09 14:46:59 info: VidStreamer up and running on https port : 3002
2020-06-09 14:46:59 info: connected the storage controller.
```
##### 알림1 : 실행을 성공적으로 하셨다면 포트포워딩 부분을 진행해주세요.


<hr>
