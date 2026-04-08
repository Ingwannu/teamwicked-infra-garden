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

## 관리 및 앱 도메인

- `devpanel2.teamwicked.me -> 217.142.142.202`
- `devpanel1.teamwicked.me -> 146.56.138.101`
- `dashb.teamwicked.me -> ingwprox1`
- `panel.teamwicked.me -> Oracle panel 경로`

## 팬아웃 고정 도메인

- `node.teamwicked.me -> 152.70.94.228`
- `node2.teamwicked.me -> 146.56.153.18`
- `node3.teamwicked.me -> 146.56.157.95`
- `snode1.teamwicked.me -> 152.70.94.228`
- `snode2.teamwicked.me -> 146.56.153.18`
- `snode3.teamwicked.me -> 146.56.157.95`

## 백엔드 DDNS

- `theireal1.teamwicked.me`
- `theireal2.teamwicked.me`
- `theireal3.teamwicked.me`

## 운영 규칙

- `node*`, `snode*`는 백엔드 DDNS 대상이 아님
- 백엔드 실IP 변경 시 `theireal*`만 갱신
- 앱 도메인 이전 시 Cloudflare 프록시 여부와 origin 인증서를 함께 확인할 것
