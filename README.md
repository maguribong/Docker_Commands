#Install Docker (in Linux)
***
#### download & install

    curl -s https://get.docker.com/ | sudo sh

#### user권한 추가
    sudo usermod -aG docker [username]

#### docker service start
    sudo service docker start 
***
# Install Docker-Compose (in Linux)
    sudo curl -L "https://github.com/docker/compose/releases/download/2.6.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

    sudo chmod +x /usr/local/bin/docker-compose
    
    docker-compose --version
***
#Commands
####docker service 시작 
    sudo service docker start

####동작중인 컨테이너 확인
    docker ps

####정지된 컨테이너 확인
    docker ps -a

####컨테이너 삭제
    docker rm [container id]

####복수의 컨테이너 삭제
    docker rm [container id], [container id], ...

####도커 이미지 확인
    docker images

####이미지 삭제
    docker rmi [image id]

####이미지 강제 삭제
    docker rmi -f [image id]

####모든 도커 컨테이너 중지&삭제
    docker stop $(docker ps -aq)

    docker rm $(docker ps -aq)

####모든 도커 이미지 삭제
    docker rmi $(docker images -q)

####컨테이너 cli
    docker exec -it [container id] /bin/sh

***
# Docker build
> docker build -t [이름공간]/[이미지 이름]:[태그] 
    
    example 
    docker build -t maguribong -f ./loadtest_v1/Maguribong.dockerfile .

***
# Docker run
> docker run -d -p [포트번호]:[포트번호][이미지]

    example
    docker run -d -p 8095:8095 flask-api/text-generater:v1
***

# Docker hub에 image push / pull
1. docker hub에 올릴 image 생성
> docker tag [local-image]:[tagname][username]/[new-repo]:[tagname]

    example
    docker tag lars:latest 123513134.dkr.ecr.us.amazonaws.com/lars:latest
2. image push
> docker push [username]/[new-repo]:[tagname]

    example
    docker push 123513134.dkr.ecr.us.amazonaws.com/lars:latest
3. image pull
> docker pull [username]/[new-repo]:[tagname]

    example
    docker pull 123513134.dkr.ecr.us.amazonaws.com/lars:latest
***
