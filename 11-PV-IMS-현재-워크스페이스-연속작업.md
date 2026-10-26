# PV-IMS 현재 워크스페이스 — 연속 작업 안내

작성·갱신: **2026-10-22**  
목적: **다른 노트북**에서 같은 폴더를 연 뒤, 지금까지의 대화 맥락·산출물·파일 기준을 잃지 않고 이어가기.

> Cursor **채팅 기록은 PC·폴더 경로에 묶여** 다른 기기로 자동 이전되지 않는다.  
> 새 PC에서는 이 문서(또는 아래 **신규 채팅 시작 문구**)를 Agent 채팅 첫 메시지에 붙인다.

---

## 1. 지금 이 창에서 연 워크스페이스

| 항목 | 값 |
|---|---|
| **Open Folder 경로** | `D:\Desktop\서비스기획팀\커서_프로젝트\PV-IMS` |
| **예전 문서(01) 경로** | `D:\Desktop\서비스기획팀\커서활용\PV-IMS(feat.cursor)` — **더 이상 기준 아님** |
| **인수인계 묶음** | `_워크스페이스-인수인계\` (00~10 + **이 문서 11**) |

다른 노트북에서도 **위 `PV-IMS` 폴더 전체**를 복사(USB·OneDrive·git 등)한 뒤, Cursor에서 **동일하게 Open Folder** 하면 된다.  
경로 문자열이 바뀌어도 되지만, **폴더 내부 구조**는 유지하는 것이 좋다.

---

## 2. 이 워크스페이스 최상위 폴더 맵

```
PV-IMS/                          ← Cursor Open Folder (통합 작업 공간)
├── _워크스페이스-인수인계/       ← 채팅·프로젝트별 인수인계 md (00~11)
├── PV-IMS(feat.cursor)/          ← 핌스 개발 본체 + 강원TP + SLLM (예전 cursor 루트)
├── 핌스 프로토타입/              ← 기획 확정 **최종 HTML** 1개 보관
├── 핌스 디자인/                  ← 2026-06 전후 HTML·데이터 스냅샷 (참고·이력)
├── 핌스 기획 문서/               ← 기획 산출물
├── 분석모델/                     ← 분석·모델 관련 자료
├── 샘플데이터/                   ← 엑셀 등 원본 샘플
└── 주피터/                       ← 노트북 등
```

**05~10번** 인수인계 문서(rtmc-admin, 우백수, 접종차수, 자동등록, 유사성, KOI)에 적힌 프로젝트는 **이 `PV-IMS` 안에 없고** 예전 `커서활용\...` 경로에 있다. 해당 과제를 이어할 때는 그 폴더를 **별도 Open Folder** 한다.

---

## 3. 핌스 HTML — 어떤 파일이 “기준”인가

역할이 **세 갈래**로 나뉜다. 혼동하지 말 것.

| 구분 | 경로 | 용도 |
|---|---|---|
| **기획 최종본 (확정)** | `핌스 프로토타입\pv_ims_prototype_20290909.html` | 팀 기준 **최종 화면**. 이후 수정·기획 반영은 여기를 기준으로 한다. |
| **개발용 (분리 JS)** | `PV-IMS(feat.cursor)\pv_ims_prototype_cursor.html` | 같은 계열 UI. `pvims-*.js`, `vaccination-data.js` 등 **외부 파일 8개**에 의존. Cursor로 손보기 좋음. |
| **외부 전달용 (단일 파일)** | `PV-IMS(feat.cursor)\pv_ims_prototype_cursor_standalone.html` | HTML **하나만** 보내도 동작. 약 6MB. |

### 외부 JS/CSS (개발용 HTML이 참조)

`PV-IMS(feat.cursor)\` 루트에 둔다.

- `vaccine-adverse-effect-data.js` — 부작용 34종
- `vaccination-data.js` — 접종 운영DB 8000건 시드 (약 5MB)
- `pvims-real-data.js`, `pvims-charts.js`, `pvims-assistant.js`, `pvims-analytics.js`, `pvims-ui-bind.js`
- `pvims-designsys-colors.css`

**주의:** `pv_ims_prototype_20290909.html`은 `핌스 프로토타입\`에만 있고, 위 JS는 **같은 폴더에 없다**.  
그 HTML만 더블클릭하면 데이터가 비어 보일 수 있다. 로컬 확인 시:

- `PV-IMS(feat.cursor)\`에서 `pv_ims_prototype_cursor.html`을 연다, 또는
- 필요한 JS/CSS를 `핌스 프로토타입\`으로 복사해 둔다, 또는
- 아래 **번들 스크립트**로 20290909용 standalone을 따로 만든다(아직 자동화는 cursor.html 기준만).

### 화면 IA (공통)

사이드바: 종합 현황 · AI 어시스턴트 · 재고/수요 · 이상반응(현황/내역/리포트/분석 AI) · 카탈로그 · 코호트 · 안전성 비교 AI · 설정(공지/모델안내/계정/설정).

---

## 4. `PV-IMS(feat.cursor)` 하위 — 과제 분리 규칙

| 경로 | 역할 | Open Folder |
|---|---|---|
| 루트 `pv_ims_prototype_*.html`, `pvims-*.js` | 핌스 메인 | 통합 `PV-IMS` 또는 이 루트만 |
| `PV-IMS\강원TP\gangwon-tp\` | 강원 TP 자가체크·AI 브리핑 (포트 **3459**) | **가능하면 따로** → [02](./02-gw-care-ai-강원TP.md) |
| `PV-IMS\pv-ims-sllm\` | SLLM+RAG PoC (포트 **8787**) | **가능하면 따로** → [03](./03-sLLM.md) |
| `PV-IMS\강원TP\v1.0.0`, `v2.0.0` | 참고용 | **수정 금지** |

SLLM 작업 시 **루트 핌스 HTML/JS를 건드리지 않는다** (03·01 규칙).

---

## 5. 이번 채팅(2026-09~10)에서 한 일 — 대화 요약

| 순서 | 주제 | 결론·산출 |
|---|---|---|
| 1 | `_워크스페이스-인수인계` 및 `01-PV-IMS.md` 확인 | 00~10은 **2026-09-09** 기준 예전 경로(`커서활용`)가 많음. **실제 코드는** `커서_프로젝트\PV-IMS` 아래에 있음. |
| 2 | 워크스페이스 전체 파일 파악 | 상위 8개 폴더 + `PV-IMS(feat.cursor)`에 강원TP·SLLM 포함. 05~10 프로젝트는 이 워크스페이스 **밖**. |
| 3 | 최종 HTML 확정 | **`핌스 프로토타입\pv_ims_prototype_20290909.html`** = 기획 최종본. |
| 4 | `pv_ims_prototype_cursor.html` 외부 전달 | HTML만 보내면 JS/CSS 미로딩 → **standalone 번들** 생성. |
| 5 | (현재) 다른 노트북 연속 작업 | **이 문서(11)** 작성. |

---

## 6. 이번 채팅에서 생긴 산출물 (코드)

| 파일 | 설명 |
|---|---|
| `PV-IMS(feat.cursor)\scripts\bundle-pvims-standalone.mjs` | `pv_ims_prototype_cursor.html`의 외부 JS 7개 + CSS 1개를 **인라인**해 단일 HTML 생성. |
| `PV-IMS(feat.cursor)\pv_ims_prototype_cursor_standalone.html` | **전달용** 단일 파일 (~6MB). 재생성: 아래 명령. |

```bash
cd "PV-IMS(feat.cursor)"
node scripts/bundle-pvims-standalone.mjs
```

입력은 항상 `pv_ims_prototype_cursor.html`.  
**20290909 최종본**도 단일 파일로 내보내려면, 스크립트의 `inputName`/`outputName`을 바꾸거나 `핌스 프로토타입\`에 JS를 맞춰 둔 뒤 동일 방식으로 번들하면 된다.

---

## 7. 다른 노트북에서 시작하는 순서

1. **`PV-IMS` 폴더 전체**를 새 PC로 복사한다. (최소: `_워크스페이스-인수인계`, `PV-IMS(feat.cursor)`, `핌스 프로토타입`)
2. Cursor → **File → Open Folder** → 복사한 `PV-IMS`.
3. **새 Agent 채팅** → 아래 **「신규 채팅 시작 문구」** 붙여넣기 → 할 일 한 줄 추가.
4. 핌스만 손볼 때: 최종 기준이 **20290909**인지, 개발이 **cursor.html**인지 먼저 정한다.
5. 강원TP / SLLM만 손볼 때: **02·03 문서**대로 **하위 폴더만** Open Folder (채팅 분리).
6. 예전 Cursor 채팅이 필요하면 **예전 PC**의 Agents 목록 또는 `01`·`02`에 적힌 채팅 ID로 검색 (경로가 같아야 같은 스레드에 붙는 경우가 많음).

---

## 8. 인수인계 문서 색인 (00~11)

| 문서 | 내용 |
|---|---|
| [00-사용법.md](./00-사용법.md) | 채팅이 안 따라올 때 공통 절차 |
| [01-PV-IMS.md](./01-PV-IMS.md) | 핌스 개요 (경로는 **구버전** — **11번과 함께** 볼 것) |
| [02~03](./02-gw-care-ai-강원TP.md) | 강원TP, SLLM |
| [04~10](./04-ML-DL적용방안.md) | ML 목업, rtmc-admin, 우백수, 미란다, 구축형, 유사성, KOI (대부분 **다른 디스크 경로**) |
| **11 (이 문서)** | **현재 `커서_프로젝트\PV-IMS` 워크스페이스** 기준 맥락·산출물 |

---

## 9. 아직 하지 않은 일 (이어서)

- [ ] `01-PV-IMS.md` 상단 **현재 경로**를 이 워크스페이스 구조에 맞게 갱신 (선택).
- [ ] `pv_ims_prototype_20290909.html`용 **standalone** 또는 `핌스 프로토타입\`에 JS 동기화 — 전달·로컬 단일 더블클릭용.
- [ ] 20290909와 `pv_ims_prototype_cursor.html` **diff** — 어느 쪽이 최신 기능인지 주기적 확인.
- [ ] 핌스 / SLLM / 강원TP 작업 시 **폴더·채팅 분리** 유지.

---

## 10. 신규 채팅 시작 문구 (복사용)

```
이 워크스페이스는 PV-IMS(핌스) 통합 폴더다.
Open Folder: (본인 PC의) …/커서_프로젝트/PV-IMS

먼저 읽을 문서:
- _워크스페이스-인수인계/11-PV-IMS-현재-워크스페이스-연속작업.md

파일 기준:
- 기획 최종 HTML: 핌스 프로토타입/pv_ims_prototype_20290909.html
- 개발용(분리 JS): PV-IMS(feat.cursor)/pv_ims_prototype_cursor.html
- 외부 전달용 단일 HTML: PV-IMS(feat.cursor)/pv_ims_prototype_cursor_standalone.html
- 번들 재생성: PV-IMS(feat.cursor)에서 node scripts/bundle-pvims-standalone.mjs

규칙:
- SLLM은 PV-IMS(feat.cursor)/PV-IMS/pv-ims-sllm 만. 루트 핌스 HTML/JS는 SLLM 작업 시 수정하지 마라.
- 강원 TP는 PV-IMS(feat.cursor)/PV-IMS/강원TP/gangwon-tp (3459). v1.0.0·v2.0.0 참고만.
- 05~10번 과제(rtmc-admin, 우백수 등)는 이 워크스페이스 밖 — 해당 폴더를 따로 연다.

지금 할 일:
(여기에 요청을 한 줄로 적는다)
```

---

## 11. 한 줄 요약

**`커서_프로젝트\PV-IMS`를 통째로 옮기고, 새 채팅에 이 문서(11)를 붙이면 된다. 최종 화면은 `20290909.html`, 개발·번들은 `PV-IMS(feat.cursor)`, 외부엔 `*_standalone.html`을 쓴다.**
