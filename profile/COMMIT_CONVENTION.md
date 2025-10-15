# Commit Message Convention

## 커밋 메시지 구조

```
<type>(<scope>): <subject>

<body>

<footer>
```

## Type

커밋의 타입을 나타냅니다:

- `feat`: 새로운 기능 추가
- `fix`: 버그 수정
- `docs`: 문서 수정
- `style`: 코드 포맷팅, 세미콜론 누락 등 (코드 변경 없음)
- `refactor`: 코드 리팩토링
- `test`: 테스트 코드 추가 또는 수정
- `chore`: 빌드 업무, 패키지 매니저 설정 등
- `perf`: 성능 개선
- `ci`: CI/CD 설정 변경
- `build`: 빌드 시스템 또는 외부 의존성 변경

## Scope (선택사항)

변경 사항이 영향을 미치는 범위:

- `api`: API 관련
- `ui`: UI 컴포넌트
- `auth`: 인증/인가
- `db`: 데이터베이스
- `config`: 설정 파일
- 프로젝트별 모듈명 등

## Subject

- 50자 이내로 작성
- 명령형으로 작성 (예: "추가한다" ❌, "추가" ✅)
- 마침표를 붙이지 않음
- 첫 글자는 소문자로 시작 (영문인 경우)

## Body (선택사항)

- 72자마다 줄바꿈
- 무엇을, 왜 변경했는지 작성 (어떻게는 코드에서 확인 가능)
- Subject와 한 줄 띄어쓰기

## Footer (선택사항)

- 이슈 트래커 ID 참조
- Breaking changes 명시

**형식:**
```
Fixes: #123
Refs: #456
BREAKING CHANGE: 변경 사항 설명
```

## 예시

### 기본 예시

```
feat(auth): 소셜 로그인 기능 추가

카카오, 네이버 소셜 로그인 기능을 구현했습니다.
OAuth 2.0 프로토콜을 사용하여 안전하게 인증을 처리합니다.

Refs: #123
```

### 간단한 예시

```
fix: 주차 정보 시스템 데이터 조회 오류 수정
```

```
docs: README에 설치 가이드 추가
```

```
refactor(ui): 버스정류장 컴포넌트 구조 개선
```

## 주의사항

- 하나의 커밋에는 하나의 논리적 변경사항만 포함
- WIP(Work In Progress) 커밋은 최종 PR 전에 정리
- 커밋 메시지는 한글 또는 영문 일관성 있게 작성
- 팀 내 합의된 컨벤션을 우선적으로 따를 것

## 참고

- [Conventional Commits](https://www.conventionalcommits.org/)
- [Angular Commit Guidelines](https://github.com/angular/angular/blob/master/CONTRIBUTING.md#commit)