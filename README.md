# NestJS에서 간단한 앱 도커라이징

### Docker 사용 방법

```
1. Dockerfile과 .dockerignore 파일 생성
2. docker build . -t nestjs-docker-study
3. docker container run -d -p 3000:3000 nestjs-docker-study
4. docker stop <docker_names>
```

### Dockerfile의 속성들 분석

- `FROM`: image를 생성할 때 DockerHub에 있는 특정 이미지를 기반으로 이미지를 생성하겠다는 선언을 해주는 부분이다. 여기서 선언한 이미지는 `Base Image`라고 부른다. 이 프로젝트에서는 NestJS 기반이기 때문에 node를 베이스 이미지로 선언했다.

- `WORKDIR`: RUN, CMD 명령어가 실행될 디렉토리를 설정하는 부분이다. Dockerfile에서 정의한 명령어를 실행하기 위해서 작업용 디렉토리를 미리 선언해준다고 생각하자.

- `COPY`: 특정 파일을 도커 이미지에 추가한다. `COPY . .`가 의미하는 것은 WORKDIR로 지정한 위치에 현재 Dockerfile이 위치한 곳의 모든 파일을 복사한다는 의미이다.

- `RUN`: 베이스로 선언했던 이미지 위에 환경을 구축하기 위한 명령을 실행하는 것이다.

- `EXPOSE`: 포트 설정 (이 도커이미지는 EXPOSE 포트를 외부에 공개할 예정이다 라는 뜻!)

- `CMD`: 최종적으로 생성된 이미지에서 명령을 실행시킬 때 사용한다. Dockerfile 내에서는 1개의 CMD 속성만 사용할 수 있다.
