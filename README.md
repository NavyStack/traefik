# [네이비스택] Traefik(트래픽) 리버스 프록시
누구나 따라할 수 있는, 그리고 이해도 필요 없는 너무나 쉬운 리버스 프록시 <br>
이것만 따라하면 추가적인 Traefik 설정을 할 일은 없으실 겁니다. (고급 사용자는.... 알아서 하세요.....) <br>
특히 제가 올리는 docker-compose는 바로 올라갑니다. <br> <br>
혹시 질문이 있다면 저의 [블로그](https://navystack.com/2023/11/%eb%9d%bc%ec%9d%b4%eb%af%b9%ec%8a%a4-%ec%98%88%ec%a0%9c%eb%a1%9c-%eb%b0%b0%ec%9a%b0%eb%8a%94-traefik-%eb%a6%ac%eb%b2%84%ec%8a%a4-%ed%94%84%eb%a1%9d%ec%8b%9c-%ec%a0%95%eb%a6%ac/) 포스트에 작성하셔도 됩니다. (별다른 로그인이 필요하지 않음.)

## Step.0 기본적인 것들 완료하기
* docker 설치
* 운영체제의 방화벽에서 80/tcp, 443/tcp, 443/udp 허용
* 클라우드 혹은 공유기에서 80/tcp, 443/tcp, 443/udp 허용

## Step.1 Git clone 하기
`git clone https://github.com/NavyStack/traefik.git && cd traefik`

## Step.2 도커 네트워크 만들기 (중요!)

`docker network create traefik-network`

## Step.3 인증서 발급을 위한 이메일 수정하기

`./traefik/etc/traefik.toml`
현재 경로에 있는 etc 폴더 내에 있는 traefik.toml에 이메일 수정

## Step.4 docker-compose.yml 파일에 있는 대시보드용 도메인 수정

`dashboard.example.com`을 원하는 도메인으로 변경하시면 됩니다. <br>
(단 http 챌린지 이므로, DNS레코드에 등록이 되어있어야 하고, 방화벽 등등 허용 해야합니다.)
(인증서 올라오기 까지 시간이 조금 걸립니다.)

## Final. docker-compose 올리기
`docker compose up -d`

이제 저의 레포지토리에 있는 traefik 파일을 숨도 안쉬고 올리면 귀찮은 것 없이 바로 올라갑니다.
(따로 링크를 걸고 명령어를 병기하겠습니다.)


수정할 것 딱 2가지
1. `./traefik/etc/traefik.toml` 이메일 수정
2. `docker-compose.toml` 파일에 있는 대시보드용 도메인 수정
