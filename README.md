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

## 첫 화면 (`index.html`) — 앱 허브

2026-10-15 에 만들었다. Altair Research Lab 이 만든 앱·웹사이트를 한 화면에 모은다.

- **넣는 것:** 출시됐거나 공개 주소로 열리는 앱·사이트. 이름 + 한 줄 + 태그(Web / Android · testing / 언어).
- **안 넣는 것:** 블로그(ABAD·AEE·GDS), 진행 중이거나 비공개인 프로젝트, 접은 것. 전체 현황은 비공개
  `altair0622/control-tower` 의 `PROJECTS.md` 가 맡는다 — 이 주소는 공개라서 나눴다.
- 한 줄 설명은 **각 앱 사이트의 소개 문구를 그대로** 옮긴다. 여기서 더 강한 주장을 쓰지 않는다
  (FocusTone Lab 은 "최적 주파수를 찾아준다"는 표현을 일부러 걷어냈다).
- 새 앱이 나오면 `<li>` 카드 하나를 추가한다. **`index.html` 을 고칠 때 `.well-known/` 은 건드리지 않는다.**

