# Basic of Docker
## How to build
아래의 명령어를 수행하면 docker는 Dockerfile을 찾아 그 내용을 수행할 것입니다
```bash
docker image build -t <repo>:<tag> -f <dockerfile_path>
```

그리고 아래의 명령어로 도커 이미지가 제대로 등록이 되었는지를 확인 할 수 있습니다
```bash
docker image ls
```

## Managing Image & Container
이미 있는 이미지들과 컨테이너들을 관리하는 과정에 대해서 적고자 한다

```bash
docker container run -it --name <container_name> <image_name>
```

위를 명령어를 사용해서 interact 모드로 해당 이미로 부터 생겨난 컨테이너에 하고 싶은 작업을 하고  
exit명령어를 통해서 밖으로 나온다

그리고 아래의 명령어를 통해서 해당 컨테이너의 상태를 커밋하여 하나의 이미지로 만든다

```bash
docker container commit <container_name> <repo>:<tag>
```

위의 과정을 통해서 python3 가 설치되어 있는 이미지를 생성했다


## Image export
이미지들을 바깥에 파일로 빼올수도 있다
```bash
docker image save -o <tar_file_name> <repo>:<tag>
```

해당 tar의 구조는 아래와 같이 나온다

```
$ tree
.
├── 4d5ca7679a732942bf7c0626abb6f77d138d75e3c4328f3cdf54aef5b49c7f09.json
├── 4dd0edbc2ef4322bca6c484f723afec9d3b4985b6d0276a433d729b198658f87
│   ├── json
│   ├── layer.tar
│   └── VERSION
├── 6dac129f6e5be56954ee2806784df939c5184cc31494269518bb09dc0ca15099
│   ├── json
│   ├── layer.tar
│   └── VERSION
├── 77a21da8dfd12031491b0adaca60a4172872dcc5723426a2a5c864ffbd624c5e
│   ├── json
│   ├── layer.tar
│   └── VERSION
├── 9dbc2dec25a596653aff8c2990cb6aad78dfae58a5c1a400458effc0cc749c22
│   ├── json
│   ├── layer.tar
│   └── VERSION
├── b59e769a506b7a11e6d54b24ff5e3b3eee73833f41366da125c6e1b9136d732f
│   ├── json
│   ├── layer.tar
│   └── VERSION
├── c96dd4835f36f3dbb003c2ed69dba61aa4ba60203656e582a2f4f24a7d0816d7
│   ├── json
│   ├── layer.tar
│   └── VERSION
├── fb35dc9d7921e1de82c9c6b6f80372cdc38bad76bc4875a80e7e90a9a596ac4a
│   ├── json
│   ├── layer.tar
│   └── VERSION
├── manifest.json
├── repositories
└── test.tar

7 directories, 25 files
```

각각의 레이어들을 포함하고 있고 그 구조들과 버전을 json과 VERSION으로 관리하는 듯하다