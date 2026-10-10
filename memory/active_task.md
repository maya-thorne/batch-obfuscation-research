# 📋 Worker 1 액티브 태스크 체크리스트 (batch-obfuscation-research)

## 📌 6대 필수 품질 과업

- [x] **1. 실제 깃허브 웹페이지 접속 및 인간 관점 UI/UX 실측 검증**:
  - Chrome CDP(포트 9227) 격리 탭으로 `https://github.com/maya-thorne/batch-obfuscation-research` 접속.
  - 배너 크기, 폰트 가독성, 여백, SVG 네온 배너 렌더링 무결성 스크린샷 캡처 및 시각 검증 완료 (4종 실측 캡처 자산 생성).
  - 모든 이미지는 클릭 시 raw 미디어 뷰어로 튕기지 않도록 `<a href="...">` 래핑 유지.

- [x] **2. 10개국어 다국어 네비게이션 및 시각 자료 현지화**:
  - 10개국어 문서(`docs/locales/*.md`) 링크 100% 정상 작동 검증 완료.
  - 각 언어별 마크다운 내 아키텍처 다이어그램 및 파서 흐름도(`architecture.svg`, `ast_flow.svg`) 20종 전용 렌더링 및 1:1 매핑 완료.

- [x] **3. 시각적 에셋(Mermaid, SVG, GIF) 고도화**:
  - 다계층 아키텍처 및 파서 5단계 전개 흐름을 나타내는 고해상도 SVG 다이어그램 20종 완비.
  - 다크 터미널 네온 테마 기반의 벡터 그래픽 렌더링 검증 완료.

- [x] **4. GitHub 공식 Release 및 Git Tag (`v1.0.0`) 발행**:
  - `v1.0.0` 태그 생성 및 원격 푸시 완료.
  - GitHub REST API를 통한 공식 릴리즈(ID: 409142764) 발행 및 릴리즈 노트 등록 완료.
  - README 상단에 Release 뱃지 1:1 연결 완료.

- [x] **5. 라이선스(LICENSE) 규격화 및 오픈소스 크레딧**:
  - 공식 LICENSE (Maya Thorne Systems & Security Research License - MT-SRL, Copyright 2026 Maya Thorne) 완비.
  - 공개 연구 자료에 대한 라이선스 크레딧 표기 및 방어적 학술 연구 목적 면책 조항 명시.

- [x] **6. 전역 규칙 준수 (AI 도구명/워터마크 0건)**:
  - 코드, 주석, 문서 전수 감사 및 무결성 확인 (Engineered & Audited by Maya Thorne 유지).

---

## 🚀 실행 모드 & 협업 도구 지침 (Teamwork & Quality Invariants)
- 🤖 **/teamwork-preview 및 멀티 에이전트 협업 허용**: 필요 시 /teamwork-preview 및 서브에이전트 병렬 디스패치(invoke_subagent)를 적극 활용하여 작업 생산성 및 리서치/검증 품질을 극대화할 수 있습니다.
- 💎 **토큰 제한 없음 (Uncapped Token Mode)**: 토큰을 아끼기 위해 코드를 축약하거나 문서를 요약하지 마십시오. 완전한 코드, 완전한 다국어 문서, 고해상도 시각 에셋을 타협 없이 완성하십시오.
- 🔥 **/goal 완주 철칙**: **대충 X · 토큰제한X · 오래 걸린다고 품질 저하X**. 6대 품질 과업(브라우저 실측 검증, 10개국어 다이어그램 현지화, SVG/GIF 에셋, v1.0.0 릴리즈/태그, LICENSE)을 기계적/시각적으로 100% 입증될 때까지 완주하십시오.

---

## 🔍 피드백 리팩토링 & 키워드 기억 리트리벌 (Memory Recall Protocol)
> **[전담 피드백 체크리스트]**: `memory/feedback_audit.md` (상위: `_BY_PASSS/WORKER_FEEDBACK_GUIDE.md`)
> **[기억 소환 키워드]**: 프롬프트나 태스크에서 아래 키워드가 언급되면 즉시 해당 규칙을 엄격히 소환하여 실행합니다:
- **`@clean-root`**: 루트 항목을 6~7개로 극도 슬림화 (백서는 `docs/whitepapers/`, 레퍼런스는 `references/`로 이동하여 첫 뷰포트 배너 노출 보장).
- **`@english-naming`**: 한글 폴더/파일명 전면 금지, 100% 영문 표준 네이밍 치환.
- **`@semantic-commit`**: 일괄 커밋 도배 금지, 파일/모듈별 개별 맥락 커밋 메시지 적용.
- **`@security-audit`**: `.env`, 캐시, 불필요 바이너리 등 배제 및 클린 커밋 검증.
- **`@custom-license`**: Maya Thorne 전용 연구 라이선스(MT-SRL) 적용.
- **`@feedback`**: 사용자 3대 시각 피드백 종합 반영 체크리스트 완수.
