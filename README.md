# chainflix-storage-update

root@chainflix:/home# sudo su -
```
비밀번호 입력
```
root@chainflix:/home# sudo apt-get install vim
```
```
root@chainflix:/home# mkdir /home/chainflix
```
```
root@chainflix:/home# cd /home/chainflix
```
```
root@chainflix:/home# sudo wget https://github.com/jampick-kr/chainflix-storage-update/releases/latest/download/chainflix.linux.tar.gz
```
Resolving github.com (github.com)... 15.164.81.167
HTTP request sent, awaiting response... 200 OK
Length: 20507613 (20M) [application/octet-stream]
Saving to: ‘chainflix.linux.tar.gz’

chainflix.linux.tar.gz                          100%[==========================================>]  19.56M  7.70MB/s    in 2.5s
```
root@chainflix:/home/chainflix# tar xvfzp chainflix.linux.tar.gz
```
chainflix
lib/
lib/node_sqlite3.node
lib/core.bin
```
root@chainflix:/home/chainflix# rm -rf chainflix.linux.tar.gz
```
```
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
컨트롤-x 또는 컨트롤-c 눌러 빠져나온다.
```

root@chainflix:/home/chainflix# vi ./conf/config.json
```
{
  "stream": {
    "rootPath": "",
    "rootFolder": "./videos/",
    "throttle": 100000000
  },
  "storage": {
    "controller_url": "http://beta-controller.chainflix.net:3002",
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
* 위 storage_id와 api_key를 입력합니다. Size_max : 100이면 100G / 3000G = 3테라

root@chainflix:/home/chainflix# sudo ./chainflix start
```
2020-06-09 14:46:58 info: Daemon Starts ..................
2020-06-09 14:46:58 info: Content Count: 0
2020-06-09 14:46:58 info: Size Available: 100.00GB
2020-06-09 14:46:58 info: VidStreamer up and running on http port : 3001
2020-06-09 14:46:59 info: VidStreamer up and running on https port : 3002
2020-06-09 14:46:59 info: connected the storage controller.
```
