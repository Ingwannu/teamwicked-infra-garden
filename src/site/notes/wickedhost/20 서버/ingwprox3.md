---
tags:
  - note
  - infra
  - server
  - oracle
updated: 2026-04-08
name: ingwprox3
role: dflow, k3s-worker
architecture: x86_64
shape: VM.Standard.E3.Flex
public_ip: 146.56.138.101
private_ip: 10.0.0.192
dg-publish: true
permalink: /notes/wickedhost/20 서버/ingwprox3/
title: ingwprox3
---

# ingwprox3

## 역할

- [[wickedhost/30 서비스/dFlow 운영|dFlow 운영]] 서버
- `devpanel1.teamwicked.me`
- k3s worker 노드

## 주요 정보

- 공인 IP: `146.56.138.101`
- 사설 IP: `10.0.0.192`
- 아키텍처: `x86_64`
- Shape: `VM.Standard.E3.Flex`
- 자원: `1 OCPU / 4GB`

## 운영 메모

- k3s worker 이름: `worker-seoul-01`
- dFlow 운영과 노드 역할이 함께 있어 장애 분석 시 앱 문제와 노드 문제를 분리해야 함

## 같이 연결되는 문서

- [[wickedhost/30 서비스/dFlow 운영|dFlow 운영]]
- [[wickedhost/30 서비스/서비스 및 도메인|서비스 및 도메인]]
- [[wickedhost/10 인프라/인프라 개요|인프라 개요]]
- [[wickedhost/70 장애대응/장애 대응 체크리스트|장애 대응 체크리스트]]
