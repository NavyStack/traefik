# Traefik(트래픽) 리버스 프록시
누구나 따라할 수 있는, 그리고 이해도 필요 없는 너무나 쉬운 리버스 프록시 DNS dnsChallenge

>[!Important]
> 정리해서 https://github.com/NavyStack/traefik.git 에 merge할 예정입니다.


## Step.0 기본적인 것들 완료하기
* docker 설치
* 운영체제의 방화벽에서 80/tcp, 443/tcp, 443/udp 허용
* 클라우드 혹은 공유기에서 80/tcp, 443/tcp, 443/udp 허용

## Step.1 Git clone 하기
`git clone https://github.com/NavyStack/traefik.git && cd traefik`

## Step.2 도커 네트워크 만들기 (중요!)

`docker network create proxynet`

## Step.3 인증서 발급을 위한 이메일 수정하기

`./traefik/etc/traefik.toml`
현재 경로에 있는 etc 폴더 내에 있는 traefik.toml에 이메일 수정


## Final. docker-compose 올리기
`docker compose up -d`


수정할 것 딱 3가지
1. `./traefik/etc/traefik.toml` 이메일 수정
2. `docker-compose.toml` 파일에 있는 대시보드용 도메인 수정
3. touch ./etc/traefik/ssl/acme.json; chmod 600 ./etc/traefik/ssl/acme.json
