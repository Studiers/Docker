# FROM
# 도커는 여러 레이어들을 겹쳐 놓아져 있는 그런 형태인 걸로 알고 있습니다
# 그렇기 때문에 기반으로 할 도커 이미지를 선택할 수 있게 하는 커맨드입니다

FROM ubuntu:latest

# LABEL
# 해당 이미지에 추가적인 정보들을 넣어주고 싶을 때 사용하는 방법..!
# 스키마 정보는 아래 사이트에서 확인!!
# http://label-schema.org/

LABEL description="This example Dockerfile installs NGINX."

# RUN
# 해당 스크립트를 실행합니다

RUN apt-get update
RUN apt-get upgrade
RUN apt-get install python3

# COPY & ADD
# 말그대로 파일을 옮깁니다

COPY files/main.py /usr/share/main.py
ADD files/main.py /usr/share/test/

# EXPOSE
# 이미지가 RUN되고 있을 동안 해당 포트를 해당 프로토콜로 열고 있습니다

EXPOSE 80/tcp

# ENTRYPOINT
# 우리가 자주 사용하는 용어다
# 이 도커 이미지가 실행시 시작할 곳, 시작점(?)을 지정해준다

# CMD
# 그리고 ENTRYPOINT에 대한 인자를 세팅해준다

ENTRYPOINT [ "python3" ]
CMD [ "/usr/share/main.py" ]

# USER
# 도커 이미지가 실행될 동안 가지고 있을 유저 형식입니다
# 이 유저네임이 존재 하지 않을 경우 실행 할 수 없을거에요..!
# 이 유저네임은 해당 이미지 안에 존재해야 합니다!! 전 그래서 root로 세팅했는데
# 각각의 OS의 root외의 시본 사용자가 있다면 그것을 사용하면 될 듯 합니다

USER root

# WORKDIR
# RUN, ENTRYPOINT, CMD 같은 것들이 실행될 기본 디렉토리를 설정합니다

# ONBUILD
# 빌드할 때 마다 호출 되는 명령어 입니다
# 예를 들어 우리가 만든 이미지가 다른 이미지의 base가 되어 빌드된다면 ONBUILD의 코드를 실행할 것입니다
# RUN과 같이 작동합니다

ONBUILD RUN echo "This is ONBUILD!!"

# ENV
# 이 도커 이미지에서 내부적으로 사용될 환경 변수들을 세팅합니다