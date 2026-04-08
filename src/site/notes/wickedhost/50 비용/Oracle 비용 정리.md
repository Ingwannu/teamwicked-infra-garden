---
tags:
  - note
  - infra
  - cost
  - oracle
updated: 2026-04-08
dg-publish: true
permalink: /notes/wickedhost/50 비용/Oracle 비용 정리/
title: Oracle 비용 정리
---

# Oracle 비용 정리

## 최근 확인 기준

- 4월 누적 총액: `16.9907 SGD`
- 범위: `2026-04-01 00:00 UTC ~ 2026-04-09 00:00 UTC`

## 서비스별

- Compute: `12.8402 SGD`
- Block Storage: `4.1422 SGD`
- API Gateway: `0.0083 SGD`

## 인스턴스별

### ingwprox1

- Compute: `0.0000 SGD`
- Boot volume: `2.6344 SGD`
- 합계: `2.6344 SGD`

### ingwprox3

- Compute: `7.0042 SGD`
- Boot volume: `0.3237 SGD`
- 합계: `7.3279 SGD`

### ingwprox4

- Compute: `5.8276 SGD`
- Boot volume: `0.5380 SGD`
- 합계: `6.3656 SGD`

## 메모

- `ingwprox2` 잔여 스토리지는 현재 없음
- 가장 비용이 큰 서버는 최근 기준 `ingwprox3`, 다음이 `ingwprox4`
