---
tags:
  - note
  - infra
  - server
  - oracle
updated: 2026-04-08
name: ingwprox1
role: management, fanout, grafana
architecture: ARM64
shape: VM.Standard.A1.Flex
public_ip: 64.110.90.243
private_ip: 10.0.0.30
dg-publish: true
permalink: /notes/wickedhost/20 서버/ingwprox1/
title: ingwprox1
---

# ingwprox1

## 역할

- Oracle 관리 서버
- WireGuard 팬아웃 허브
- [[wickedhost/30 서비스/Grafana 운영|Grafana 운영]] 호스트
- `garden.teamwicked.me` 직접 호스팅 서버

## 주요 정보

- 공인 IP: `64.110.90.243`
- 사설 IP: `10.0.0.30`
- 아키텍처: `ARM64`
- Shape: `VM.Standard.A1.Flex`
- 리눅스 표시 자원: `8 vCPU`, `약 24GB RAM`

## 운영 중인 핵심 기능

- WireGuard 팬아웃 NAT 및 프론트 허브
- Grafana 로컬 리스너: `127.0.0.1:3001`
- Grafana/pmacct PostgreSQL 브리지: `127.0.0.1:15433`
- Obsidian Digital Garden 정적 호스팅 + Cloudflare Tunnel

## 같이 연결되는 문서

- [[wickedhost/10 인프라/인프라 개요|인프라 개요]]
- [[wickedhost/30 서비스/서비스 및 도메인|서비스 및 도메인]]
- [[wickedhost/30 서비스/Grafana 운영|Grafana 운영]]
- [[wickedhost/40 운영/운영 메모|운영 메모]]
- [[wickedhost/70 장애대응/장애 대응 체크리스트|장애 대응 체크리스트]]
