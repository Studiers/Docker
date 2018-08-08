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
docker container commit <container_name> <repo>:<tag>
```

## .dockerignore