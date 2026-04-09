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

## Blueprint 익스텐션 설치 목록

현재 패널에는 Blueprint 기반 익스텐션이 다수 설치돼 있습니다. 설치 목록은 패널 로컬 파일 기준으로 확인했고, 핵심 설치 목록은 아래와 같습니다.

- `advancedmovefiles`
- `blueprint`
- `consolelogs`
- `customserversort`
- `databaseimportexport`
- `eggchanger`
- `environmentvariables`
- `filesearch`
- `loader`
- `mclogs`
- `mcmods`
- `mcplugins`
- `minecrafticonchanger`
- `minecraftplayermanager`
- `modpackinstaller`
- `nebula`
- `nightadmin`
- `pwaforblueprint`
- `resourcealerts`
- `resourcemanager`
- `simplefavicons`
- `simplefooters`
- `snowflakes`
- `sociallogin`
- `subdomainmanager`
- `sysautomation`
- `versionchanger`

## 현재 운영상 중요도가 높은 익스텐션

### `subdomainmanager`

- Cloudflare API를 사용해 서버별 서브도메인 생성
- 현재 TeamWicked 프록시 구조에 맞춰
  - alias가 도메인이면 `CNAME`
  - alias가 IP면 `A`
  로 동작하도록 조정됨
- 관련 설정 키:
  - `subdomainmanager::cloudflare_token`
  - `subdomainmanager::subdomain_limit`

### `sociallogin`

- 패널 계정 외부 로그인/연결 기능
- 계정 메뉴 쪽 `Connections` 라우트로 보임
- 관련 설정 키:
  - `sociallogin::allow_connecting`
  - `sociallogin::allow_register`

### `environmentvariables`

- 서버 단위 환경변수 UI
- 서버 라우트 `/environment-variables`
- egg별 활성 범위가 Blueprint 설정에 저장됨

### `mclogs`

- Minecraft 로그 업로드/연동 성격
- 서버 라우트 `/mclogs`

### `versionchanger`

- Minecraft 버전 전환 관련 UI
- 서버 라우트 `/minecraft/versions`
- 관련 설정 키:
  - `versionchanger::mcvapi_types_order`

### `minecraftplayermanager`

- Minecraft 플레이어 관리 UI
- 서버 라우트 `/minecraft/players`

### `mcplugins`, `mcmods`

- Minecraft 플러그인 / 모드 설치 UI
- 관련 라우트:
  - `/mcplugins`
  - `/mcmods`
- CurseForge/다운로드 관련 텍스트/설정 키가 다수 존재

### `modpackinstaller`

- 서버 라우트 `/modpacks`
- 모드팩 설치 지원용 확장

### `databaseimportexport`

- DB import/export 관련 확장
- 관련 설정 키:
  - `databaseimportexport::allow_remote_import`
  - `databaseimportexport::max_export_size`
  - `databaseimportexport::max_import_size`

### `eggchanger`

- 서버 egg 변경 관련
- 관련 설정 키:
  - `eggchanger::force_delete_files`
  - `eggchanger::force_reinstall`
  - `eggchanger::force_update_startup_command`

## UI / 테마 / 편의성 계열 익스텐션

- `nebula`
  - 패널 UI, 팔레트, 사이드바, 워터마크, 링크, wicked mode 등 설정이 매우 많음
  - 현재 패널 시각 요소에 영향을 주는 핵심 테마 확장으로 봐야 함
- `loader`
  - 로딩 화면/배경/아이콘/속도
- `simplefavicons`
  - favicon 교체
- `simplefooters`
  - footer 문구/색/크기
- `customserversort`
  - 서버 정렬 관련
- `snowflakes`
  - 시각 효과
- `nightadmin`
  - 관리자용 UI 관련 확장으로 보임
- `pwaforblueprint`
  - PWA 관련

## 리소스 / 자동화 / 파일 편의 계열

- `resourcealerts`
  - CPU/RAM 임계치 관련 설정 존재
- `resourcemanager`
  - 이름상 리소스 제어/표시용
- `sysautomation`
  - 시스템 자동화 계열
- `filesearch`
  - 파일 검색 기능
- `advancedmovefiles`
  - 파일 이동 편의 기능
- `consolelogs`
  - 콘솔 로그 관련

## 운영 메모

- Blueprint 핵심 설정은 `panel.settings` 테이블에 `blueprint::...`, `<extension>::...` 키 형태로 저장됨
- 실제 설치된 익스텐션 목록은 Blueprint 내부 `installed_extensions` 파일에도 남아 있음
- 패널 UI/동작 이상 시에는
  - 확장 자체 코드
  - DB 설정 키
  - Blueprint 캐시
  - 라우트 노출 여부
  를 같이 봐야 함
- 특히 테마/UI 이상은 `nebula`, `loader`, `simplefavicons`, `simplefooters` 쪽을 같이 의심해야 함
- 노드/서브도메인/로그인 이슈는 각각
  - `subdomainmanager`
  - `sociallogin`
  - `mclogs`
  - `environmentvariables`
  같은 개별 확장 영향 여부를 분리해서 보는 게 맞음

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
