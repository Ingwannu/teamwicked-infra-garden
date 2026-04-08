---
tags:
  - note
  - infra
  - service
  - wickedship
updated: 2026-04-08
dg-publish: true
permalink: /notes/wickedhost/30 서비스/WickedShip 운영/
title: WickedShip 운영
---

# WickedShip 운영

## 현재 상태

- 서비스 도메인: `https://devpanel2.teamwicked.me`
- 현재 운영 호스트: [[wickedhost/20 서버/ingwprox2|ingwprox2]]
- 아키텍처: `ARM64`

## 현재 런타임

- `payload-app`
- `mongodb`
- `redis`
- `config-generator`
- `devpanel2-nginx`

## 운영 포인트

- 과거 [[wickedhost/20 서버/ingwprox4|ingwprox4]]에서 운영하다가 현재 [[wickedhost/20 서버/ingwprox2|ingwprox2]]로 이전됨
- ARM 운영 검증은 진행됐지만 이미지/배포 변경 시 첫 기동 상태를 꼭 확인
- 관련 도메인과 DNS는 [[wickedhost/30 서비스/서비스 및 도메인|서비스 및 도메인]], [[wickedhost/60 DNS/Cloudflare DNS 정리|Cloudflare DNS 정리]] 참고

## 장애 시 우선 확인

1. `https://devpanel2.teamwicked.me` 응답
2. [[wickedhost/20 서버/ingwprox2|ingwprox2]]에서 컨테이너 상태
3. 앱 내부 `3000` 리슨
4. 최근 이미지 업데이트 여부

## 관련 문서

- [[wickedhost/20 서버/ingwprox2|ingwprox2]]
- [[wickedhost/20 서버/ingwprox4|ingwprox4]]
- [[wickedhost/40 운영/운영 메모|운영 메모]]
- [[wickedhost/70 장애대응/장애 대응 체크리스트|장애 대응 체크리스트]]
