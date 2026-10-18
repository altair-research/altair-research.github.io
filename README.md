# altair-research.github.io

조직의 GitHub Pages 사용자 사이트(도메인 루트). 하는 일이 둘이다 — **첫 화면(앱 허브)** 과 **`assetlinks.json`**.

- **`.well-known/assetlinks.json`** — 안드로이드 앱과 이 도메인이 같은 주인임을 증명하는 파일(Digital Asset Links).
  안드로이드는 이 파일을 **도메인 루트에서만** 찾는다. 프로젝트 저장소(`/drape/`) 안에 두면 무시된다.
  이게 없으면 TWA 앱 위에 브라우저 주소창이 뜬다.

## 지금 등록된 앱

| 앱 | 패키지 | 사이트 |
|---|---|---|
| Personal Color Mirror | `com.altairresearchlab.colormirror` | https://altair-research.github.io/drape/ |
| Sprout Frame | `com.altairresearchlab.sproutframe` | https://altair-research.github.io/sprout-frame/ |

## 지문을 고칠 때

`sha256_cert_fingerprints` 는 여러 개를 넣을 수 있고, **하나라도 맞으면** 통과한다.
넣어야 하는 값은 둘이다:

1. **업로드 키** 지문 — 내 PC 에서 서명한 apk 를 직접 설치해 볼 때 필요.
2. **Play 앱 서명 키** 지문 — Play 가 배포용으로 다시 서명하므로 **스토어로 설치한 앱에는 이게 쓰인다.**
   Play Console > 앱 > 테스트 및 출시 > 설정 > 앱 서명(App integrity) 에서 복사한다.

확인: https://altair-research.github.io/.well-known/assetlinks.json 이 JSON 으로 열려야 하고,
구글 검증기로도 볼 수 있다:

```
https://digitalassetlinks.googleapis.com/v1/statements:list?source.web.site=https://altair-research.github.io&relation=delegate_permission/common.handle_all_urls
```

절차 전체는 `altair-research/drape` 의 `PLAY-STORE.md` §4 에 있다.

## 첫 화면 (`index.html`) — 앱 허브 · 포트폴리오

2026-10-15 에 만들고 10-17 에 다시 짰다. **우리가 만든 것과, 각각 어디까지 왔는지**를 한 화면에 보여 준다.
앞으로는 앱 개발 의뢰를 받을 때 "어디까지 만들 수 있는지" 보여 주는 포트폴리오로 키운다(연락처·의뢰 안내는 아직 없음).

**구성:** 할 수 있는 것(기술 요약) → 카테고리 바로가기 → 카테고리별 카드.
카드 하나 = 화면 캡처 + 한 줄 설명 + **지금**(어디까지 왔나) + 태그(종류·테스트 여부·언어) + 그 앱이 보여 주는 기술.

**카테고리:** 🌱 식물 · 👗 스타일 · 🧠 집중·학습 · 🧭 생활 도구.
10-17 에 카테고리 → 앱을 잇는 가지 그림(SVG)을 넣었다가 **같은 날 뺐다.** 사용자가 "너무 인위적"이라 했고, 따져 보니
섹션 제목이 이미 같은 묶음을 보여 줘서 그림만의 정보는 점선 하나뿐이었다. 폰에서는 글자가 8px 로 작았다.
대신 카테고리 바로가기 한 줄을 둔다.

**한/영:** 문구마다 `data-ko` / `data-en` 이 짝으로 있고, 처음엔 브라우저 언어로 고른다. HTML 기본값은 영어(자바스크립트가 꺼져도 읽힌다).

**지켜 온 기준:**
- **넣는 것:** 공개 주소로 열리는 앱·사이트. **안 넣는 것:** 블로그(ABAD·AEE·GDS), 비공개·진행 중·접은 프로젝트.
  전체 현황은 비공개 `altair0622/control-tower` 의 `PROJECTS.md` 가 맡는다.
- **종류는 "자기 도메인의 웹사이트가 있느냐"로 가른다** (10-17 사용자 기준):
  `웹사이트 · 도메인` — FocusTone Lab(focustonelab.com) · PriceAfter(priceafter.com) · ShadeSpot(shadespot.app) · Uncommon Plant(uncommonplant.com).
  `웹 앱` — 사이트 없이 앱만 배포한 것: PeachPlay · Personal Color Mirror · Sprout Frame · WearCast (전부 이 도메인 밑 `/이름/`).
  처음엔 전부 "Web" 으로 뭉뚱그렸고, 다음엔 "주소가 곧 앱이냐"로 나눴다가 이 기준으로 다시 고쳤다.
  ShadeSpot 은 한국어 지인 테스트 안내(`/shadespot-intro/`)에 걸었었는데, 실제 사이트는 `shadespot.app`(영어)이다.
- **언어는 앱을 열어서 확인한다.** 소개 문구 언어로 짐작하지 않는다 — 처음에 FocusTone Lab·PriceAfter·Personal Color Mirror 를
  "한국어"로 잘못 달았다. 셋 다 한/영이다(Personal Color Mirror 는 브라우저 언어를 보고 자동 선택).
- **설명은 각 앱 사이트의 문구를 따른다.** 허브가 앱보다 센 주장을 하지 않는다.

**새 앱 추가:** 폰 크기(375×812)로 첫 화면을 캡처해 `assets/hub/<이름>.jpg`(가로 300px), 해당 카테고리 `<ul class="grid">` 에 카드
`<li>` 하나. 바로가기의 개수도 고친다. 문구는 `data-ko`·`data-en` 둘 다.
**`index.html` 을 고칠 때 `.well-known/` 은 건드리지 않는다.**
