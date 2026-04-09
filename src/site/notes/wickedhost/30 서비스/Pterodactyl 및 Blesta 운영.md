---
tags:
  - note
  - infra
  - service
  - pterodactyl
  - blesta
updated: 2026-04-08
dg-publish: true
permalink: /notes/wickedhost/30 서비스/Pterodactyl 및 Blesta 운영/
title: Pterodactyl 및 Blesta 운영
---

# Pterodactyl 및 Blesta 운영

## 현재 상태

- Pterodactyl Panel: `https://panel.teamwicked.me`
- Blesta: [[wickedhost/20 서버/Blesta 서버|Blesta 서버]]

## 패널과 Wings 노드 구조

- Panel 웹 호스트는 Oracle 경로로 분리되어 있음
- Blesta는 [[wickedhost/20 서버/Blesta 서버|Blesta 서버]]에 따로 있고, 같은 머신으로 보면 안 됨
- 현재 주요 Wings 노드는 아래와 같이 운영
  - `kr.node.wicked.1`
    - FQDN: `snode1.teamwicked.me`
    - scheme: `https`
  - `kr.node.wicked.2`
    - FQDN: `snode2.teamwicked.me`
    - scheme: `https`
  - `kr.node.wicked.3`
    - FQDN: `snode3.teamwicked.me`
    - scheme: `https`
  - `kr.maxnode.wicked.1`
    - FQDN: `smaxnode1.teamwicked.me`
    - scheme: `https`

## 프록시 환경 기준 노드 원칙

- `node*`, `snode*` 도메인은 Cloudflare에서 Oracle fanout 공인 IP에 고정
- 백엔드 실IP 변경은 `theireal*`만 갱신해야 함
- Wings FQDN은 실IP가 아니라 운영용 고정 도메인 기준으로 유지하는 것이 원칙
- 노드가 프록시 뒤에 있더라도 패널에서 보는 FQDN과 인증서 SAN/CN이 맞아야 자동 설정 반영이 동작
- 노드 FQDN을 바꾼 뒤 패널이 자동 `config.yml` 갱신에 실패하면, 대개 인증서 이름 불일치나 proxy/origin mismatch부터 봐야 함

## 운영 포인트

- Panel과 Blesta는 현재 같은 호스트가 아님
- Panel은 Oracle 경로, Blesta는 별도 외부 호스트로 분리
- Wings API 헬스체크는 경우에 따라 `401`이 정상 응답 기준이 될 수 있음
- `https://<node-fqdn>/api/system`
  - `401 Unauthorized`면 Wings 웹/API는 살아 있는 경우가 많음
- 패널이 느릴 때는 Panel 웹이 아니라 특정 노드 API timeout 때문에 체감이 느려질 수 있음
- `snode*` 응답 지연과 `node*` 응답 지연을 분리해서 봐야 함

## Blueprint Subdomains 메모

- `subdomainmanager` 확장이 설치돼 있음
- Cloudflare 레코드 생성은 allocation의 `ip_alias`를 기준으로 동작
- 현재는 기존처럼 alias를 강제로 A로 해석해 박는 방식이 아니라
  - alias가 도메인이면 `CNAME`
  - alias가 IP면 `A`
  로 동작하도록 맞춤
- 따라서 `node3.teamwicked.me` 같은 alias를 쓰는 서버는, 이후 생성되는 하위 도메인도 프록시 IP 변화를 따라갈 수 있음
- 과거에 생성된 일부 서브도메인은 real IP가 박혀 있었고, 이 부분은 한 차례 Cloudflare 레코드를 재생성해서 교정함

## 장애 시 우선 확인

1. `panel.teamwicked.me` 응답
2. 노드 Wings API 응답
3. Blesta는 [[wickedhost/20 서버/Blesta 서버|Blesta 서버]] 기준으로 분리 확인
4. `snode*` / `node*` 실제 DNS가 팬아웃 공인 IP로 유지되는지 확인
5. 노드 FQDN 변경 직후라면 인증서 이름과 패널 저장값이 일치하는지 확인
6. subdomain 관련 이슈면 Cloudflare에서 실제 생성된 레코드가 `A real-ip`인지 `CNAME node*`인지 확인

## 관련 문서

- [[wickedhost/30 서비스/서비스 및 도메인|서비스 및 도메인]]
- [[wickedhost/20 서버/Blesta 서버|Blesta 서버]]
- [[wickedhost/70 장애대응/장애 대응 체크리스트|장애 대응 체크리스트]]
- [[wickedhost/60 DNS/Cloudflare DNS 정리|Cloudflare DNS 정리]]
- [[wickedhost/40 운영/운영 메모|운영 메모]]
