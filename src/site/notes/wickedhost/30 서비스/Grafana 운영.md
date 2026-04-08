---
tags:
  - note
  - infra
  - service
  - grafana
updated: 2026-04-08
dg-publish: true
permalink: /notes/wickedhost/30 서비스/Grafana 운영/
title: Grafana 운영
---

# Grafana 운영

## 현재 상태

- 서비스 도메인: `https://dashb.teamwicked.me`
- 현재 호스트: [[wickedhost/20 서버/ingwprox1|ingwprox1]]
- 로컬 Grafana 리스너: `127.0.0.1:3001`
- 로컬 PostgreSQL 브리지: `127.0.0.1:15433`

## 운영 포인트

- Grafana는 더 이상 [[wickedhost/20 서버/Blesta 서버|Blesta 서버]]에 있지 않음
- pmacct PostgreSQL과 collector 경로가 로컬 브리지를 보도록 유지해야 함

## 장애 시 우선 확인

1. `/login` 응답
2. `127.0.0.1:15433` 리스너
3. `pmacct-postgres` 상태
4. collector/pmacctd 적재 상태

## 관련 문서

- [[wickedhost/20 서버/ingwprox1|ingwprox1]]
- [[wickedhost/70 장애대응/장애 대응 체크리스트|장애 대응 체크리스트]]
- [[wickedhost/40 운영/운영 메모|운영 메모]]
