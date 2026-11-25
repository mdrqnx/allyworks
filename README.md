# Allyworks 웹사이트 (리뉴얼)

주식회사 앨리웍스(Allyworks Co., Ltd.) 기업 웹사이트 리뉴얼 버전입니다.
빌드 도구 없이 동작하는 정적 사이트(HTML · CSS · 바닐라 JS)로, 어떤 웹 서버/정적 호스팅에도 그대로 올릴 수 있습니다.

## 페이지 구성

| 파일 | 내용 |
| --- | --- |
| `index.html` | 메인 — 히어로, 고객사, 사업분야, Java 플랫폼, Oracle 대비 비용, 진행 방식, 시스템 통합, 파트너, 문의 |
| `company.html` | 회사소개 — 인사말, 핵심가치, 비전·전략·핵심 경쟁력(`#vision`), 사업분야, Azul 파트너십, 회사 개요 |
| `platform.html` | Java 플랫폼(Azul) — Core(`#core`), Prime(`#prime`), Runtime Intelligence(`#runtime-intelligence`), Payara(`#payara`), Oracle Java 전환(`#migration`), FAQ |
| `herodevs.html` | 오픈소스 EOL 지원(HeroDevs) — Never-Ending Support(`#nes`), 지원 기술(`#coverage`), 도입 방식(`#how-it-works`), 보안·규제 대응(`#security`), Azul과 함께(`#with-azul`), FAQ |
| `services.html` | 시스템 통합 — 공공기관 SI 구축(`#build`), 시스템 통합 유지보수(`#maintenance`), 수행 프로세스 |
| `partners.html` | 파트너 — 글로벌 파트너(Azul Systems, HeroDevs), 국내 사업 파트너, 주요 고객사 |
| `contact.html` | 문의하기 — 연락처, 문의 폼(메일 앱 연동), 오시는 길(`#location`) |

## 폴더 구조

```
assets/
  css/style.css          공통 디자인 시스템 (색상·타이포 토큰, 헤더/푸터, 버튼, 카드 등 컴포넌트)
  css/pages/*.css        페이지별 스타일
  js/main.js             헤더 스크롤, 모바일 메뉴, 스크롤 등장 애니메이션, 숫자 카운트업, 문의 폼(mailto)
  img/brand/             공식 로고(SVG, 기존 홈페이지 로고를 벡터화)·파비콘·원본 PNG
  img/partners/          해외/국내 사업 파트너 로고 (HeroDevs 로고는 공식 미디어 키트 SVG, 색상·비율 변경 금지)
  img/clients/           주요 고객사 로고
```

## 로컬에서 보기

```bash
python3 -m http.server 8000
# 브라우저에서 http://localhost:8000
```

## 외부 리소스

- 폰트: Pretendard (jsDelivr), JetBrains Mono (Google Fonts)
- 아이콘: Lucide 0.460.0 (jsDelivr) — `<i data-lucide="아이콘-이름"></i>` 형태로 사용

## 수정 가이드

- **색상/폰트/간격**: `assets/css/style.css` 상단 `:root` 토큰만 바꾸면 전체에 반영됩니다.
- **연락처**: 이메일·전화·주소는 각 페이지 헤더(모바일 메뉴)와 푸터, `contact.html`에 있습니다. 변경 시 전체 검색(`joon@allyworks.co.kr`, `070-4099-2232`)으로 함께 바꿔 주세요.
- **문의 폼**: 서버 없이 방문자의 메일 앱을 여는 방식(`<form data-mailto="...">`)입니다. 폼 전송 서비스(예: 자체 API, Formspree 등)를 쓰려면 `contact.html`의 폼 `action`을 지정하고 `data-mailto` 속성을 제거하면 됩니다.
- **Azul·HeroDevs 관련 수치**(최대 70% 절감, 1,000+ 고객사 등)와 지원 기술 목록은 각 사 공개 자료 기준이며, 페이지에 각주로 표기되어 있습니다. 벤더 자료가 바뀌면 함께 갱신해 주세요.

## 참고

- 파트너·고객사 로고는 각 사의 상표이며, 기존 앨리웍스 홈페이지에 게시된 이미지를 그대로 사용했습니다.

## 영어 버전 (English)

- 영어 페이지는 `en/` 폴더에 있습니다: `en/index.html`, `en/company.html`, `en/platform.html`, `en/herodevs.html`,
  `en/services.html`, `en/partners.html`, `en/contact.html` — 한국어 페이지와 같은 구조·같은 CSS/JS/이미지를 씁니다(`../assets/`).
- 모든 페이지 헤더의 **KO / EN** 전환 버튼은 같은 페이지의 다른 언어 버전으로 이동합니다.
- `assets/js/main.js`는 `<html lang>` 값에 따라 메뉴·문의 양식 문구를 한국어/영어로 바꿉니다.
- 영어 전용 레이아웃 보정이 필요한 경우 각 페이지 CSS에 `html[lang="en"]` 범위로만 넣었습니다(한국어 화면에는 영향 없음).
- 한국어 문구를 바꾸면 `en/` 의 같은 페이지도 함께 고쳐 주세요.
