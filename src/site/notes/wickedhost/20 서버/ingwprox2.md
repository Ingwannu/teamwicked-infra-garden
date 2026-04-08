---
tags:
  - note
  - infra
  - server
  - oracle
updated: 2026-04-08
name: ingwprox2
role: wickedship
architecture: ARM64
shape: VM.Standard.A1.Flex
public_ip: 217.142.142.202
private_ip: 10.0.0.168
dg-publish: true
permalink: /notes/wickedhost/20 서버/ingwprox2/
title: ingwprox2
---

# ingwprox2

## 역할

- 현재 [[wickedhost/30 서비스/WickedShip 운영|WickedShip 운영]] 서버
- `devpanel2.teamwicked.me` 호스트
- ARM 전환 후 현재 앱 운영 기준 서버

## 주요 정보

- 공인 IP: `217.142.142.202`
- 사설 IP: `10.0.0.168`
- 아키텍처: `ARM64`
- Shape: `VM.Standard.A1.Flex`
- 자원: `2 OCPU / 4GB`

## 현재 런타임

- `payload-app`
- `mongodb`
- `redis`
- `config-generator`
- `devpanel2-nginx`

## 운영 메모

- 기존 [[wickedhost/20 서버/ingwprox4|ingwprox4]]에서 ARM으로 이전 완료
- 현재 `devpanel2.teamwicked.me`는 이 서버를 가리킴
- 서버 증설/ARM 검증 관련 메모는 [[wickedhost/40 운영/운영 메모|운영 메모]] 참고

## 같이 연결되는 문서

- [[wickedhost/30 서비스/WickedShip 운영|WickedShip 운영]]
- [[wickedhost/30 서비스/서비스 및 도메인|서비스 및 도메인]]
- [[wickedhost/10 인프라/인프라 개요|인프라 개요]]
- [[wickedhost/70 장애대응/장애 대응 체크리스트|장애 대응 체크리스트]]
