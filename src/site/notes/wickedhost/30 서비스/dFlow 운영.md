---
tags:
  - note
  - infra
  - service
  - dflow
updated: 2026-04-08
dg-publish: true
permalink: /notes/wickedhost/30 서비스/dFlow 운영/
title: dFlow 운영
---

# dFlow 운영

## 현재 상태

- 서비스 도메인: `https://devpanel1.teamwicked.me`
- 현재 운영 호스트: [[wickedhost/20 서버/ingwprox3|ingwprox3]]
- 아키텍처: `x86_64`

## 운영 포인트

- dFlow는 현재 [[wickedhost/20 서버/ingwprox3|ingwprox3]]에서 운영
- 같은 서버가 `worker-seoul-01` k3s 노드 역할도 겸함
- 장애 분석 시 앱 문제와 k3s worker 문제를 분리해서 봐야 함

## 장애 시 우선 확인

1. `https://devpanel1.teamwicked.me` 응답
2. [[wickedhost/20 서버/ingwprox3|ingwprox3]] 앱/프록시 컨테이너 상태
3. worker 노드 상태가 별도로 이상 없는지 확인

## 관련 문서

- [[wickedhost/20 서버/ingwprox3|ingwprox3]]
- [[wickedhost/30 서비스/서비스 및 도메인|서비스 및 도메인]]
- [[wickedhost/70 장애대응/장애 대응 체크리스트|장애 대응 체크리스트]]
