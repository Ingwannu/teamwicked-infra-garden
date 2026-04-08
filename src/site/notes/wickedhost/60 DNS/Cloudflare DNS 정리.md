---
tags:
  - note
  - infra
  - dns
  - cloudflare
updated: 2026-04-08
dg-publish: true
permalink: /notes/wickedhost/60 DNS/Cloudflare DNS 정리/
title: Cloudflare DNS 정리
---

# Cloudflare DNS 정리

이 문서는 Cloudflare에서 관리하는 핵심 도메인과 운영 규칙을 정리합니다. 서비스 연결은 [[wickedhost/30 서비스/서비스 및 도메인|서비스 및 도메인]], 팬아웃 원칙은 [[wickedhost/40 운영/운영 메모|운영 메모]], 인프라 전체 구조는 [[wickedhost/10 인프라/인프라 개요|인프라 개요]]를 참고합니다.

## 관리 및 앱 도메인

- `devpanel2.teamwicked.me -> 217.142.142.202`
  - 서비스: [[wickedhost/30 서비스/WickedShip 운영|WickedShip 운영]]
  - 호스트: [[wickedhost/20 서버/ingwprox2|ingwprox2]]
- `devpanel1.teamwicked.me -> 146.56.138.101`
  - 서비스: [[wickedhost/30 서비스/dFlow 운영|dFlow 운영]]
  - 호스트: [[wickedhost/20 서버/ingwprox3|ingwprox3]]
- `dashb.teamwicked.me`
  - 서비스: [[wickedhost/30 서비스/Grafana 운영|Grafana 운영]]
  - 호스트: [[wickedhost/20 서버/ingwprox1|ingwprox1]]
- `panel.teamwicked.me`
  - 서비스: [[wickedhost/30 서비스/Pterodactyl 및 Blesta 운영|Pterodactyl 및 Blesta 운영]]
- `garden.teamwicked.me`
  - 서비스: TeamWicked Infra Garden
  - 호스트: [[wickedhost/20 서버/ingwprox1|ingwprox1]]
  - Cloudflare Tunnel 경유

## 팬아웃 고정 도메인

- `node.teamwicked.me -> 152.70.94.228`
- `node2.teamwicked.me -> 146.56.153.18`
- `node3.teamwicked.me -> 146.56.157.95`
- `snode1.teamwicked.me -> 152.70.94.228`
- `snode2.teamwicked.me -> 146.56.153.18`
- `snode3.teamwicked.me -> 146.56.157.95`

이 도메인들은 팬아웃 공인 IP 고정용이며, 백엔드 실IP 변경과 무관합니다.

## 백엔드 DDNS 대상

- `theireal1.teamwicked.me`
- `theireal2.teamwicked.me`
- `theireal3.teamwicked.me`

## 운영 규칙

- `node*`, `snode*`는 백엔드 DDNS 대상이 아님
- 백엔드 실IP 변경 시 `theireal*`만 갱신
- 앱 도메인 이전 시:
  - Cloudflare 프록시 여부
  - 원본 HTTPS 인증서
  - 실제 origin 호스트
  를 함께 확인

## 같이 보면 좋은 문서

- [[wickedhost/30 서비스/서비스 및 도메인|서비스 및 도메인]]
- [[wickedhost/40 운영/운영 메모|운영 메모]]
- [[wickedhost/70 장애대응/장애 대응 체크리스트|장애 대응 체크리스트]]
