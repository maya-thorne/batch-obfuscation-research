<div align="center">

<p align="center">
  <a href="../../README.md">🇺🇸 English</a> · <strong>🇰🇷 한국어</strong> · <a href="./zh-CN.md">🇨🇳 中文</a> · <a href="./es.md">🇪🇸 Español</a> · <a href="./hi.md">🇮🇳 हिन्दी</a><br />
  <a href="./ar.md">🇸🇦 العربية</a> · <a href="./pt-BR.md">🇧🇷 Português</a> · <a href="./ru.md">🇷🇺 Русский</a> · <a href="./fr.md">🇫🇷 Français</a> · <a href="./id.md">🇮🇩 Bahasa Indonesia</a>
</p>

<p align="center">
  <a href="https://github.com/maya-thorne/batch-obfuscation-research"><img src="../assets/locales/ko/banner.svg" alt="batch-obfuscation-research banner" width="100%" /></a>
</p>

# 🛡️ batch-obfuscation-research

**Windows 배치 파일(`cmd.exe`) 난독화·디옵퓨스케이션 원리 및 원본 소스코드 심층 역공학 아카이브 (1990s–2026)**

[![Release](https://img.shields.io/badge/Release-v1.0.0-f43f5e.svg)](https://github.com/maya-thorne/batch-obfuscation-research/releases)
[![Ghidra RE](https://img.shields.io/badge/Ghidra_MCP-PE_Binary_Dissection-10b981.svg)](../whitepapers/BATCH_OBFUSCATION_ARCHITECTURE_AND_CODE_ANALYSIS.md)
[![References](https://img.shields.io/badge/OpenSource_Mirrors-48_Repos_%2B_HuggingFace_AI-38bdf8.svg)](../../references/batch_corpus_28)
[![Detection](https://img.shields.io/badge/Detection-Sigma_%26_YARA_Rules-a855f7.svg)](../../references/detection_rules/rules)
[![License: MT-SRL](https://img.shields.io/badge/License-MT--SRL-blue.svg)](../../LICENSE)

<sub>설계 및 역공학 감사: **[Maya Thorne](https://github.com/maya-thorne)** · 시스템 &amp; 리버스 엔지니어링 아키텍트</sub>

</div>

---

## 📌 아카이브 개요 및 3대 핵심 마스터 백서

본 저장소는 지난 30년간 진화해 온 **Windows `cmd.exe` 배치 스크립트 난독화, 실행 파일 패킹(`Bat2Exe`), 정적 푸시다운 오토마타(PDA) 에뮬레이션, 런타임 API 후킹(`Exorcism`), 그리고 Hugging Face 트랜스포머 신경망 역난독화 기법**을 원본 소스코드와 어셈블리 레벨에서 전수 해부한 통합 연구 아카이브입니다.

| 마스터 문서 | 수록 내용 및 기술적 깊이 |
| :--- | :--- |
| 🔬 **[`BATCH_OBFUSCATION_ARCHITECTURE_AND_CODE_ANALYSIS.md`](../whitepapers/BATCH_OBFUSCATION_ARCHITECTURE_AND_CODE_ANALYSIS.md)** | **기드라 MCP 바이너리 역공학 & 7대 핵심 도구 원본 소스코드 분해 백서**:<br>• `bat2exe_12.exe` (UPX 스텁 `0x20ea0`), `BEDeCode.exe` (VB6 네이티브 `0x1670` `ThunRTMain` & `CHRMAPSET`), `example.exe` (.NET CLR `0x337e` `_CorExeMain` & `"batch_cmd"` 리소스) 실측 디스어셈블리.<br>• `Invoke-DOSfuscation`, `BatCloak`, `SomalifuscatorV2`, `0xidiz3r`, `batch_deobfuscator`, `Exorcism`, `Bat2Exe-dehoisted` 원본 코드 라인별 분해. |
| 📖 **[`BATCH_OBFUSCATION_ENCYCLOPEDIA.md`](../whitepapers/BATCH_OBFUSCATION_ENCYCLOPEDIA.md)** | **배치 난독화 종합 대백과사전 (v2.0)**:<br>• `cmd.exe` 5단계 파싱 파이프라인(`%VAR%` ➔ `^` 이스케이프 ➔ `!VAR!` 지연 확장 ➔ 구분자 정규화 ➔ `CmdNode` 실행) 완벽 도식화.<br>• 12대 핵심 난독화 기법 택소노미 및 48개 오픈소스/AI 데이터셋 전수 카탈로그. |
| 🛡️ **[`BATCH_OBFUSCATION_MASTER_GUIDE.md`](../whitepapers/BATCH_OBFUSCATION_MASTER_GUIDE.md)** | **30년 진화사 및 탐지 엔지니어링 마스터 가이드**:<br>• 1990년대 고전 MS-DOS 기법부터 2026년 최신 AI 역난독화까지의 연대기.<br>• 정적 ➔ 동적 ➔ AI 다계층 포렌식 파이프라인 및 프로덕션급 **Sigma / YARA** 탐지 룰셋. |

---

## 🏗️ 전체 아키텍처 및 역공학 파이프라인

<p align="center">
  <a href="https://github.com/maya-thorne/batch-obfuscation-research">
    <img src="../assets/locales/ko/architecture.svg" alt="Architecture Diagram (ko)" width="100%" />
  </a>
</p>

<p align="center">
  <a href="https://github.com/maya-thorne/batch-obfuscation-research">
    <img src="../assets/locales/ko/ast_flow.svg" alt="cmd.exe AST Engine Diagram (ko)" width="100%" />
  </a>
</p>


```mermaid
flowchart TD
    subgraph "1. Obfuscation & Packing Layer (난독화 및 패커 계층)"
        A1["원본 배치 스크립트 (.bat/.cmd)"] --> B1["Invoke-DOSfuscation (PowerShell)\n환경변수 슬라이싱 & 역순 FOR 루프"]
        A1 --> B2["BatCloak / BEncoder (C#/Batch)\nUTF-16LE BOM (0xFF 0xFE) & X.509 위장"]
        A1 --> B3["SomalifuscatorV2 (Python)\n동적 카이사르 암호 & Anti-VM/Echo Trap"]
        A1 --> B4["0xidiz3r (Rust)\nZero-Literal 3-Seed 부트스트랩"]
        B1 & B2 & B3 & B4 --> C1["고도 난독화된 배치 스크립트"]
        C1 --> D1["Bat2Exe Packers (Native/C#/VB6)\nPE 리소스 임베딩 & 오버레이 패킹"]
    end

    subgraph "2. Ghidra MCP Binary RE Layer (기드라 MCP 실측 역공학)"
        D1 --> E1["bat2exe_12.exe (x86 Native UPX)\nEP: 0x20ea0 (pushal / mov esi, 0x414000)"]
        D1 --> E2["BEDeCode.exe (x86 VB6 Native)\nEP: 0x1670 -> 0x1668 (ThunRTMain IAT)"]
        D1 --> E3["example.exe (x86 .NET CLR)\nEP: 0x337e (jmp _CorExeMain / 'batch_cmd')"]
    end

    subgraph "3. Deobfuscation & Detection Layer (역난독화 및 방어 공학)"
        C1 --> F1["batch_deobfuscator (Python)\n푸시다운 오토마타(PDA) & 슬라이싱 에뮬레이터"]
        C1 --> F2["Exorcism (Rust + Python)\ncmd.exe!FindFixAndRun (0x116B0) API 후킹"]
        E1 & E2 & E3 --> G1["Hugging Face AI & EDR Telemetry\nLLM4Decompile + 엔트로피/Sigma/YARA 룰셋"]
    end
```

---

## 📂 디렉터리 구성 (Repository Layout)

- 📁 **[`references/batch_corpus_28/`](../../references/batch_corpus_28)** — 중첩 `.git`이 평탄화(Flatten)되어 GitHub 웹에서 즉시 열람 가능한 41개 오픈소스 난독화기·디옵퓨스케이터·패커 원본 코드 트리.
- 📁 **[`references/huggingface_ai/`](../../references/huggingface_ai)** — `LLM4Decompile-SFT-Deobfuscate`, `c-deobfuscate-mt`, JFrog 토큰 엔트로피 식별 데이터셋(ArXiv:2510.26847), EDR 텔레메트리 및 SigmaForge 룰셋.
- 📁 **[`references/classic_samples/`](../../references/classic_samples)** — 30년 진화사 백서(`CLASSIC_TO_MODERN_EVOLUTION.md`), BatCloak/ScrubCrypt 3단계 메모리 복호화 심층 분석서 및 6종 실증 샘플.
- 📁 **[`references/detection_rules/`](../../references/detection_rules)** — 자체 개발 파이썬 다중 패스 정적 디옵퓨스케이터(`deobfuscator_engine.py`), Mandiant/Unit 42 위협 인텔리전스 백서, Sigma 및 YARA 탐지 룰.

---

## 📄 라이선스

본 프로젝트는 **Maya Thorne Systems & Security Research License (MT-SRL)** 하에 배포됩니다. 자세한 내용은 [`LICENSE`](../../LICENSE) 파일을 참조하십시오.
