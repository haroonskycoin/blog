+++
title = "개발 업데이트 #1"
tags = [
    "Development",
]
date = "2014-01-01"
description = "스카이코인 관련 최신 개발동향 소개"
aliases = [
	"/ko/development-updates/development-update-1/"
]
+++

## 개요:

- 스카이코인에서 채굴을 제거하기위한 합리적 근거가 초기 계획서에 추가되었습니다.
- 스카이코인의 2단계 post-quantum 트랜잭션 프로토콜에 대한 정보 또한 추가되었습니다.
- 스카이코인 프로토콜의 기반이 만들어졌으며 많은 커밋이 Github에 제출되었습니다.
- DHT의 스카이코인 피어 부트 스트랩(bootstrap)이 현재 작동 중입니다.
- 스카이코인 지갑 작동을위한 Webkit 임베딩
- 지갑 GUI 초안이 github에 업로드 되었습니다.

## 특징 :
- 스카이코인의 100만분의 1을 **Drop** 또는 **Droplet**이라고 합니다. Skycoins은 소수점 이하 6 자리로 나눌 수 있습니다.
- 지갑은 여러 지갑을 독립적으로 불러오기/내보내기 할 수 있습니다.
- 사용편의성을 개선하기 위해 수신 탭이 지갑에서 제거되었습니다.
- 지갑에서 스카이코인 IRC 채널에 연결하기 위한 탭이 추가되었습니다.
- 스카이코인 클라이언트는 HTML6 응용 프로그램입니다. 응용 프로그램 창에서 웹 서버 및 webkit 렌더링을 실행합니다. 그래서 그것은 HTML입니다. 하지만 원격 서버없이 실행되지 않습니다.

## 주요 일정:

- 첫 번째 스카이코인 거래가 2014 년 1 월 14 일에 이루어졌습니다. 공개 빌드는 일주일 이내에 준비됩니다.
- 지갑을 실행하려면 "go run wallet.go"를 실행하십시오.
![](/img/dev-update-1-1.png)

## 개발 진행현황 :

- 우리는 지갑을 중국어로 번역하고 있습니다.
- 지갑 팀이 JSON RPC 작업 중입니다.
- 스카이코인 주소는 전자메일주소의 역할을 하며, 메시지를 안전하게 주고받을 수 있습니다. "식별 주소" 및 "지갑 주소"RPC 작업이 진행 중입니다.
