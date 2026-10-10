# 🔍 전담 작업자 피드백 감사 및 리팩토링 체크리스트 (feedback_audit.md)

> **[상위 지침 연동]**: `_BY_PASSS/WORKER_FEEDBACK_GUIDE.md`
> **[기억 리트리벌 키워드]**: `@feedback`, `@clean-root`, `@english-naming`, `@semantic-commit`, `@security-audit`, `@custom-license`

---

## 📌 본 저장소 필수 개선 액션 플랜

- [x] **1. [@clean-root] 루트 디렉터리 슬림화 (최대 6~7개 항목 유지)**:
  - 첫 접속 시 화면에 README.md와 히어로 배너가 가려지지 않도록 루트를 슬림화 완료.
  - 모든 백서 및 마크다운 문서는 `docs/whitepapers/`로 이동 완료.
  - 모든 레퍼런스 폴더는 `references/` 하위로 단일화 완료.
  - 루트에는 오직 `.gitignore`, `LICENSE`, `README.md`, `docs/`, `memory/`, `references/`, `src/` 총 7개 항목만 유지.

- [x] **2. [@english-naming] 100% 영문 디렉터리 및 파일명 표준화**:
  - `01_배치난독화_GitHub_28종` -> `references/batch_corpus_28` 치환 완료.
  - `02_HuggingFace_AI_자원` -> `references/huggingface_ai` 치환 완료.
  - `03_고전_및_실전_연구샘플` -> `references/classic_samples` 치환 완료.
  - `04_탐지규칙_및_자체엔진` -> `references/detection_rules` 치환 완료.
  - 저장소 내 모든 폴더 및 파일명에서 한글을 100% 배제하고 영문 표준 적용 완료.

- [x] **3. [@semantic-commit] 파일/모듈별 맥락 커밋 메시지 분리**:
  - 일괄 커밋 도배 방지, 변경된 파일/기능 단위로 커밋 분리 적용:
    - `refactor(naming): convert reference directories to pure english naming in references/`
    - `docs(whitepaper): relocate core research whitepapers to docs/whitepapers/`
    - `chore(license): apply dedicated Maya Thorne Systems & Security Research License (MT-SRL)`
    - `docs(readme): update navigation links and slim root layout for instant banner visibility`
    - `style(ui): finalize clean-root architecture maintaining 7 root items`

- [x] **4. [@security-audit] 전수 보안 감사 (Zero-Leak Audit)**:
  - `.env`, 임시 캐시(`.cache`, `__pycache__`), 디버그 로그, 불필요한 대용량 바이너리 배제 완료.
  - `.gitignore` 파일에 민감 파일 및 불필요 아티팩트 차단 룰 추가 완료.

- [x] **5. [@custom-license] Maya Thorne 전용 라이선스 적용**:
  - 루트의 `LICENSE` 파일을 Maya Thorne Systems & Security Research License (MT-SRL)로 교체 완료.
