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

이 문서는 Oracle Cloud 비용 확인 결과를 요약합니다. 현재 서버 구성과 역할은 [[wickedhost/20 서버/서버 인벤토리|서버 인벤토리]] 및 [[wickedhost/10 인프라/인프라 개요|인프라 개요]]를 함께 봅니다.

## 최근 확인 기준

- 4월 누적 총액: `16.9907 SGD`
- 조회 범위: `2026-04-01 00:00 UTC ~ 2026-04-09 00:00 UTC`

## 서비스별

- Compute: `12.8402 SGD`
- Block Storage: `4.1422 SGD`
- API Gateway: `0.0083 SGD`

## 인스턴스별

### [[wickedhost/20 서버/ingwprox1|ingwprox1]]

- Compute: `0.0000 SGD`
- Boot volume: `2.6344 SGD`
- 합계: `2.6344 SGD`
- 메모:
  - A1 Always Free 성격 때문에 compute가 0으로 잡힘
  - 그래도 boot volume은 계속 비용에 반영

### [[wickedhost/20 서버/ingwprox3|ingwprox3]]

- Compute: `7.0042 SGD`
- Boot volume: `0.3237 SGD`
- 합계: `7.3279 SGD`
- 메모:
  - 현재 가장 비용이 큰 서버
  - dFlow 운영 및 x86 과금 영향

### [[wickedhost/20 서버/ingwprox4|ingwprox4]]

- Compute: `5.8276 SGD`
- Boot volume: `0.5380 SGD`
- 합계: `6.3656 SGD`
- 메모:
  - 현재 `STOPPED`지만 4월 누적 비용엔 이전 사용분이 반영됨

## 추가 메모

- [[wickedhost/20 서버/ingwprox2|ingwprox2]] 잔여 스토리지는 현재 없음
- 최근 기준으로 비용이 가장 큰 서버는 [[wickedhost/20 서버/ingwprox3|ingwprox3]], 다음이 [[wickedhost/20 서버/ingwprox4|ingwprox4]]
- 앱 이전/정지 여부와 과금 반영 시점은 완전히 일치하지 않을 수 있음

## 같이 봐야 하는 문서

- [[wickedhost/20 서버/서버 인벤토리|서버 인벤토리]]
- [[wickedhost/10 인프라/인프라 개요|인프라 개요]]
- [[wickedhost/40 운영/운영 메모|운영 메모]]
