---
tags:
  - gardenEntry
  - infra
  - teamwicked
  - overview
updated: 2026-04-08
dg-home: true
dg-publish: true
title: TeamWicked 인프라 홈
---

# TeamWicked 인프라 홈

이 문서는 현재 TeamWicked의 Oracle 서버 구조, 앱 패널 배치, WireGuard 팬아웃, Grafana, Digital Garden 운영 상태를 한 번에 보는 시작 문서입니다.

## 빠른 이동

- 전체 구조: [[wickedhost/10 인프라/인프라 개요|인프라 개요]]
- 서버별 상세: [[wickedhost/20 서버/서버 인벤토리|서버 인벤토리]]
- 서비스 및 도메인: [[wickedhost/30 서비스/서비스 및 도메인|서비스 및 도메인]]
- 운영 규칙: [[wickedhost/40 운영/운영 메모|운영 메모]]
- 비용: [[wickedhost/50 비용/Oracle 비용 정리|Oracle 비용 정리]]
- DNS: [[wickedhost/60 DNS/Cloudflare DNS 정리|Cloudflare DNS 정리]]
- 장애 대응: [[wickedhost/70 장애대응/장애 대응 체크리스트|장애 대응 체크리스트]]

## 현재 핵심 상태

- 운영 WireGuard 팬아웃 허브: [[wickedhost/20 서버/ingwprox1|ingwprox1]]
- WickedShip 운영 호스트: [[wickedhost/20 서버/ingwprox2|ingwprox2]]
- dFlow 운영 호스트 및 k3s 워커: [[wickedhost/20 서버/ingwprox3|ingwprox3]]
- 이전 WickedShip 호스트: [[wickedhost/20 서버/ingwprox4|ingwprox4]]
- 별도 과금/고객 관리 서버: [[wickedhost/20 서버/Blesta 서버|Blesta 서버]]

## 현재 운영 엔드포인트

- WickedShip: `https://devpanel2.teamwicked.me`
- dFlow: `https://devpanel1.teamwicked.me`
- Grafana: `https://dashb.teamwicked.me`
- Pterodactyl Panel: `https://panel.teamwicked.me`
- Garden: `https://garden.teamwicked.me`

## 읽는 순서 추천

1. [[wickedhost/10 인프라/인프라 개요|인프라 개요]]
2. [[wickedhost/20 서버/서버 인벤토리|서버 인벤토리]]
3. [[wickedhost/30 서비스/서비스 및 도메인|서비스 및 도메인]]
4. [[wickedhost/40 운영/운영 메모|운영 메모]]
5. [[wickedhost/70 장애대응/장애 대응 체크리스트|장애 대응 체크리스트]]

## 관련 개별 문서

- 서버:
  - [[wickedhost/20 서버/ingwprox1|ingwprox1]]
  - [[wickedhost/20 서버/ingwprox2|ingwprox2]]
  - [[wickedhost/20 서버/ingwprox3|ingwprox3]]
  - [[wickedhost/20 서버/ingwprox4|ingwprox4]]
  - [[wickedhost/20 서버/Blesta 서버|Blesta 서버]]
- 서비스:
  - [[wickedhost/30 서비스/WickedShip 운영|WickedShip 운영]]
  - [[wickedhost/30 서비스/dFlow 운영|dFlow 운영]]
  - [[wickedhost/30 서비스/Grafana 운영|Grafana 운영]]
  - [[wickedhost/30 서비스/Pterodactyl 및 Blesta 운영|Pterodactyl 및 Blesta 운영]]

## 메모

- 이 vault는 중복 요약보다 문서 간 연결을 우선합니다.
- 서버/서비스 문서 간 위키링크를 명시적으로 걸어 백링크가 잘 생기도록 유지합니다.
- 퍼블리시 대상은 현재 `wickedhost` 아래의 모든 `.md` 문서입니다.
