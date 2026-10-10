<div align="center">

<p align="center">
  <a href="../../README.md">🇺🇸 English</a> · <a href="./ko.md">🇰🇷 한국어</a> · <a href="./zh-CN.md">🇨🇳 中文</a> · <a href="./es.md">🇪🇸 Español</a> · <a href="./hi.md">🇮🇳 हिन्दी</a><br />
  <a href="./ar.md">🇸🇦 العربية</a> · <a href="./pt-BR.md">🇧🇷 Português</a> · <strong>🇷🇺 Русский</strong> · <a href="./fr.md">🇫🇷 Français</a> · <a href="./id.md">🇮🇩 Bahasa Indonesia</a>
</p>

<p align="center">
  <a href="https://github.com/maya-thorne/batch-obfuscation-research"><img src="../assets/locales/ru/banner.svg" alt="batch-obfuscation-research banner" width="100%" /></a>
</p>

# 🛡️ batch-obfuscation-research

**Архив обфускации, деобфускации и реверс-инжиниринга пакетных файлов Windows**

[![Release](https://img.shields.io/badge/Release-v1.0.0-f43f5e.svg)](https://github.com/maya-thorne/batch-obfuscation-research/releases)
[![Ghidra RE](https://img.shields.io/badge/Ghidra_MCP-PE_Binary_Dissection-10b981.svg)](../whitepapers/BATCH_OBFUSCATION_ARCHITECTURE_AND_CODE_ANALYSIS.md)
[![References](https://img.shields.io/badge/OpenSource_Mirrors-28_Repos_%2B_HuggingFace_AI-38bdf8.svg)](../../references/batch_corpus_28)
[![Detection](https://img.shields.io/badge/Detection-Sigma_%26_YARA_Rules-a855f7.svg)](../../references/detection_rules/rules)
[![License: MT-SRL](https://img.shields.io/badge/License-MT--SRL-blue.svg)](../../LICENSE)

<sub>Engineered &amp; Audited by **[Maya Thorne](https://github.com/maya-thorne)** · Systems &amp; Reverse Engineering Research</sub>

</div>

---

## 📚 Master Technical Documentation (핵심 분석 백서 바로가기)

1. 🔬 **[BATCH_OBFUSCATION_ARCHITECTURE_AND_CODE_ANALYSIS.md](../whitepapers/BATCH_OBFUSCATION_ARCHITECTURE_AND_CODE_ANALYSIS.md)**
   - **Ghidra MCP PE Binary Reverse Engineering**: `bat2exe_12.exe` (UPX Native Stub `0x20ea0`), `BEDeCode.exe` (VB6 Native `0x1670` `ThunRTMain` & `CHRMAPSET`), `example.exe` (.NET CLR `0x337e` `_CorExeMain` & `"batch_cmd"` resource).
   - **7 Core Tools Source Code Dissection**: `Invoke-DOSfuscation`, `BatCloak`, `SomalifuscatorV2`, `0xidiz3r`, `batch_deobfuscator` (Pushdown Automaton), `Exorcism` (`cmd.exe!FindFixAndRun` API Hooking), `Bat2Exe-dehoisted`.
2. 📖 **[BATCH_OBFUSCATION_ENCYCLOPEDIA.md](../whitepapers/BATCH_OBFUSCATION_ENCYCLOPEDIA.md)**
   - `cmd.exe` 5-Stage Parser Internals, 12 Obfuscation Techniques Taxonomy, 48 Open-Source & Hugging Face Reference Matrix.
3. 🛡️ **[BATCH_OBFUSCATION_MASTER_GUIDE.md](../whitepapers/BATCH_OBFUSCATION_MASTER_GUIDE.md)**
   - 30-Year Evolution Timeline (1990s MS-DOS to 2026 AI/LLM Deobfuscation), Multi-Layer Forensic Pipeline, Sigma & YARA Rules.

---

## 🏗️ Architecture & Reverse Engineering Pipeline

<p align="center">
  <a href="https://github.com/maya-thorne/batch-obfuscation-research">
    <img src="../assets/locales/ru/architecture.svg" alt="Architecture Diagram (ru)" width="100%" />
  </a>
</p>

<p align="center">
  <a href="https://github.com/maya-thorne/batch-obfuscation-research">
    <img src="../assets/locales/ru/ast_flow.svg" alt="cmd.exe AST Engine Diagram (ru)" width="100%" />
  </a>
</p>


```mermaid
flowchart TD
    subgraph "Obfuscation & Packing Layer"
        A1["Raw Batch Script (.bat/.cmd)"] --> B1["Invoke-DOSfuscation (PowerShell)\nEnv Slicing & Reversed FOR Loop"]
        A1 --> B2["BatCloak / BEncoder (C#/Batch)\nUTF-16LE BOM (0xFF 0xFE) & X.509 Disguise"]
        A1 --> B3["SomalifuscatorV2 (Python)\nDynamic Caesar Cipher & Anti-VM"]
        A1 --> B4["0xidiz3r (Rust)\nZero-Literal 3-Seed Bootstrapping"]
        B1 & B2 & B3 & B4 --> C1["Obfuscated Batch Payload"]
        C1 --> D1["Bat2Exe Compilers (Native/C#/VB6)"]
    end

    subgraph "Ghidra MCP Binary RE & Deobfuscation Layer"
        D1 --> E1["bat2exe_12.exe (UPX 0x20ea0)"]
        D1 --> E2["BEDeCode.exe (VB6 0x1670)"]
        D1 --> E3["example.exe (.NET 0x337e)"]
        C1 --> F1["batch_deobfuscator (Static PDA AST)"]
        C1 --> F2["Exorcism (cmd.exe!FindFixAndRun 0x116B0 Hook)"]
    end
```

---

## 📂 Repository Directory Structure

- 📁 [`references/batch_corpus_28/`](../../references/batch_corpus_28) — Flattened full source code trees of 28+ open-source obfuscators, deobfuscators, runtime hookers, and compilers.
- 📁 [`references/huggingface_ai/`](../../references/huggingface_ai) — `LLM4Decompile-SFT-Deobfuscate`, `c-deobfuscate-mt`, JFrog Token Entropy Dataset (ArXiv:2510.26847), EDR Telemetry & SigmaForge datasets.
- 📁 [`references/classic_samples/`](../../references/classic_samples) — 30-Year Evolution Whitepaper, BatCloak/ScrubCrypt 3-stage forensic deep dive, and 6 PoC batch samples.
- 📁 [`references/detection_rules/`](../../references/detection_rules) — Custom Python Multi-Pass Static Deobfuscator (`deobfuscator_engine.py`), Mandiant/Unit 42 whitepaper analysis, and production Sigma/YARA rules.
