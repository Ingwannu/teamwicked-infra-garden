---
tags:
  - note
  - infra
  - service
  - pterodactyl
  - blesta
updated: 2026-04-08
dg-publish: true
permalink: /notes/wickedhost/30 서비스/Pterodactyl 및 Blesta 운영/
title: Pterodactyl 및 Blesta 운영
---

# Pterodactyl 및 Blesta 운영

## 현재 상태

- Pterodactyl Panel: `https://panel.teamwicked.me`
- Blesta: [[wickedhost/20 서버/Blesta 서버|Blesta 서버]]

## 운영 포인트

- Panel과 Blesta는 현재 같은 호스트가 아님
- Panel은 Oracle 경로, Blesta는 별도 외부 호스트로 분리
- Wings API 헬스체크는 경우에 따라 `401`이 정상 응답 기준이 될 수 있음

## 장애 시 우선 확인

1. `panel.teamwicked.me` 응답
2. 노드 Wings API 응답
3. Blesta는 [[wickedhost/20 서버/Blesta 서버|Blesta 서버]] 기준으로 분리 확인

## 관련 문서

- [[wickedhost/30 서비스/서비스 및 도메인|서비스 및 도메인]]
- [[wickedhost/20 서버/Blesta 서버|Blesta 서버]]
- [[wickedhost/70 장애대응/장애 대응 체크리스트|장애 대응 체크리스트]]
