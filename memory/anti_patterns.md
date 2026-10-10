# 🚫 Worker 1 중복 방지 규칙 (Anti-Patterns)

1. **도구 개발 중복 금지**:
   - `batch-obfuscation-research`는 이론 연구와 백서 전담이므로, 실제 파이썬/러스트 기반 CLI 탈난독화 패키지를 구현하지 않는다. (해당 기능은 Worker 2의 `batch-deobfuscator-re`에 위임)

2. **바이너리 역공학 중복 금지**:
   - Ghidra 역공학, PE 언패킹, 어셈블리 분석은 다루지 않는다. (해당 기능은 Worker 5의 `bat2exe-ghidra-forensics`에 위임)

3. **탐지 룰셋 중복 금지**:
   - Sigma 규칙이나 YARA 룰을 자체 제작하여 저장소의 메인 피처로 내세우지 않는다. (해당 기능은 Worker 3의 `batch-forensics-and-ghidra-re`에 위임)

4. **순수 파서 공학 중복 금지**:
   - `cmd.exe` AST 구문 파서 트리를 자체 구현하지 않는다. (해당 기능은 Worker 4의 `cmd-ast-deobfuscator`에 위임)
