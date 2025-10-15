# 커밋 메시지 컨벤션

## 📋 기본 구조

```
<type>(<scope>): <subject>

<body>

<footer>
```

### 구성 요소

- **type**: 커밋의 타입 (필수)
- **scope**: 변경 범위 (선택)
- **subject**: 커밋 제목 (필수)
- **body**: 상세 설명 (선택)
- **footer**: 이슈 참조 및 주요 변경사항 (선택)

---

## 🏷️ Type (커밋 타입)

| Type | 설명 | 예시                          |
|------|------|-----------------------------|
| `feat` | 새로운 기능 추가 | 주차 정보 실시간 알림 기능             |
| `fix` | 버그 수정 | 이륜차 감지 오류 수정                |
| `perf` | 성능 개선 | 쿼리 최적화로 응답속도 개선             |
| `refactor` | 코드 리팩토링 (동작 변화 없음) | 컴포넌트 구조 개선                  |
| `style` | 코드 포맷팅, 세미콜론 등 | 들여쓰기 수정                     |
| `docs` | 문서 작성 및 수정 | API 문서 업데이트                 |
| `test` | 테스트 코드 추가/수정 | 단위 테스트 추가                   |
| `build` | 빌드 시스템, 외부 의존성 변경 | webpack 설정 변경               |
| `ci` | CI/CD 설정 변경 | GitHub Actions 워크플로우 수정     |
| `chore` | 기타 변경사항 | 기타 (의존성 업데이트는 가능하면 build:로) |
| `revert` | 이전 커밋 되돌림 | Revert "feat: 알림 기능"        |

---

## 🎯 Scope (변경 범위)

프로젝트 특성에 따라 적절한 scope를 선택합니다.

### 프론트엔드 (FE)

```
ui, ux, a11y, i18n, state, routing, forms, theme, assets, build, lint, deps, tests, storybook, bundle, monitoring
```

**예시:**
- `feat(ui): 다크모드 토글 추가`
- `fix(a11y): 키보드 네비게이션 개선`
- `perf(bundle): 관리자 페이지 코드 스플리팅`

### 백엔드 (BE)

```
api, domain, service, repository, db, migration, security, auth, cache, queue, scheduler, observability, infra, build, deps, tests
```

**예시:**
- `feat(api): 사용자 세션 조회 엔드포인트 추가`
- `fix(db): sessions 테이블 인덱스 추가`
- `refactor(service): 주차장 검색 로직 개선`

---

## ✍️ Subject (제목) 작성 규칙

1. **50자 이내**로 작성
2. **명령형**으로 작성
   - ✅ `주차 정보 API 추가`
   - ❌ `주차 정보 API를 추가했습니다`
3. **마침표(.)를 붙이지 않음**

---

## 📝 Body (본문) 작성 가이드

본문은 선택사항이지만, 다음과 같은 경우 작성합니다:

### 작성이 필요한 경우

- 변경 사항이 복잡하거나 여러 부분에 영향을 미칠 때
- 성능 개선 수치가 있을 때
- API/DB 스키마 변경이 있을 때
- 사용자에게 영향을 주는 변경일 때

### 작성 규칙

- **72자마다 줄바꿈**
- **제목과 한 줄 띄어쓰기**
- **무엇을, 왜 변경했는지** 중심으로 작성

### 본문 템플릿

```
왜 변경했는가? (문제 상황 또는 의도)
무엇을 어떻게 변경했는가? (핵심 변경사항 2-4개)
영향 범위는? (사용자/시스템, 성능, 계약, 마이그레이션)
고려한 대안은? (선택사항)
```

### FE 본문 작성 포인트

- **사용자 영향**: UI 변화, 접근성, 상호작용 변경
- **번들 영향**: 번들 사이즈, 로딩 속도 변화 (±KB, LCP 등)
- **시각 자료**: 가능하면 스크린샷 링크 첨부

### BE 본문 작성 포인트

- **계약 변경**: API 요청/응답, DB 스키마 변경 명시
- **마이그레이션**: DDL/데이터 마이그레이션 적용/롤백 방법
- **성능 지표**: TPS, latency, 쿼리 실행 계획 변화 등 수치

---

## 🔖 Footer (푸터)

### ~~이슈 참조~~

추후 이슈 트래커 연동시 사용

```
Refs: #123
Fixes: #456
Closes: #789
```

### Breaking Changes (주요 변경사항)

API나 동작 방식의 변경으로 하위 호환성이 깨지는 경우:

```
BREAKING CHANGE: Order.status 필드가 Order.state로 변경됨
```

또는 제목에 `!` 추가:

```
feat(domain)!: Order.status를 Order.state로 변경
```

---

## 💡 커밋 메시지 예시

### 기본 예시

```
feat(auth): 소셜 로그인 기능 추가

카카오, 네이버 OAuth 2.0 기반 소셜 로그인을 구현
- 시스템 설정에 따른 자동 테마 감지
- localStorage에 사용자 선택 저장
- 디자인 v3 가이드에 맞춰 눈의 피로 감소

Refs: #123
```

### 성능 개선 예시

```
perf(db): sessions 테이블 인덱스 추가

sessions(user_id, last_seen)에 복합 인덱스 추가
- 쿼리 P95: 420ms → 38ms 개선
- Seq Scan → Index-Only Scan으로 실행 계획 변경
```

### Breaking Change 예시

```
feat(api)!: 주문 상태 필드명 변경

Order.status를 Order.state로 변경
- 이유: 도메인 용어 통일 및 명확성 향상
- 마이그레이션: V45__rename_status_to_state.sql 실행
- 롤백: V45_down__rename_state_to_status.sql 실행

BREAKING CHANGE: API 응답의 status 필드가 state로 변경
Refs: #234
```

### 간단한 수정 예시

```
fix: 주차 정보 시스템 데이터 조회 오류 수정
```

```
docs: README에 설치 가이드 추가
```

```
refactor(ui): 버스정류장 컴포넌트 구조 개선
```

---

## ✅ Do / ❌ Don't

### ✅ Do (좋은 예)

- **명령형 사용**: `추가`, `수정`, `개선`
- **구체적 작성**: `로그인 API 응답 속도 개선`
- **수치 포함**: `번들 크기 120KB 감소`, `응답시간 90ms 개선`
- **영향 범위 명시**: 사용자/시스템, 성능, API 변경 등
- **Breaking Change 명확히**: `!` 또는 `BREAKING CHANGE` 사용
- **한 커밋 = 한 의도**: 작게, 자주 커밋

### ❌ Don't (나쁜 예)

- **모호한 표현**: `수정함`, `변경`, `업데이트`
- **과거형 사용**: `추가했음`, `수정했습니다`
- **너무 큰 커밋**: UI·API·DB를 한 커밋에 섞음
- **맥락 생략**: 본문 없이 복잡한 변경사항 커밋
- **의미 불명**: `기타 수정`, `misc`, `update stuff`

---

## 📌 주의사항

1. **하나의 커밋에는 하나의 논리적 변경사항만** 포함
2. **커밋 메시지는 한글로 일관성** 있게 작성
3. **팀 내 합의된 컨벤션을 우선**적으로 따를 것
4. **민감 정보 절대 포함 금지** (비밀번호, API 키 등)

---

## 📚 참고 자료

- [Conventional Commits](https://www.conventionalcommits.org/)
- [Angular Commit Guidelines](https://github.com/angular/angular/blob/master/CONTRIBUTING.md#commit)