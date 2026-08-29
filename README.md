<div align="center">

# draxo

**kernel internals · reverse engineering · hooking engines**

[![typedef](https://img.shields.io/badge/typedef-struct_draxo-1c2029?style=for-the-badge&labelColor=0d1117)](#)

</div>

---

windows internals and reverse engineering. i spend most of my time below the
line — auditing kernel drivers for vulnerabilities, building hooking engines,
writing length decoders from scratch, and understanding how compiled code
actually behaves on silicon.

recent work: a full x64 length decoder covering legacy/REX/VEX/EVEX
(AVX through AVX-512), a dual-backend hooking engine, documented
vulnerability research on signed kernel drivers, and low-level GPU API
interception across three graphics generations.

---

## languages

<div align="left">
  <img src="https://skillicons.dev/icons?i=cpp,c,rust,asm,cs,python,lua,go,java,js,ts,html,css,react,nodejs,bash,powershell&theme=dark" alt="languages" />
</div>

---

## projects

| repo | what it is |
|---|---|
| [**Amnesia-Hook**](https://github.com/DaddyZyn/Amnesia-Hook) | x64 hooking engine. two independent backends — inline (trampoline + custom length decoder covering legacy/REX/VEX/EVEX) and VEH (hardware breakpoint, lock-free handler, thread-local state). D3D9/11/12 + OpenGL vtable hooks. zero dependencies. |
| [**Windows-Vuln-drivers**](https://github.com/DaddyZyn/Windows-Vuln-drivers) | documented vulnerability research on signed kernel drivers not on Microsoft's blocklist. full analysis with assembly-level evidence, reversed interface headers, non-destructive PoCs, live validation matrices. |

---

## what i actually do

<details>
<summary><b>kernel / driver research</b></summary>
<br>

- driver vulnerability auditing — signed kernel drivers not on Microsoft's blocklist, protocol reconstruction from raw disassembly, live validation matrices
- length decoders — table-driven x64 instruction decoding from scratch, VEX/EVEX map handling, rip-relative displacement tracking, branch classification
- relocation engines — prologue instruction relocation, Jcc widening, far-call return address preservation, rip-relative displacement recomputation
- trampoline allocation — bounded ±2 GB outward search, 64K-granularity stepping, page-level VirtualAlloc strategies
- caller-gate analysis — process-notify callback whitelists, module-base validation, session-bound kernel command interfaces
- BYOVD documentation — stripped-hardening forks, loader fallback paths, unrestricted device variants

</details>

<details>
<summary><b>hooking infrastructure</b></summary>
<br>

- inline hooking — 14-byte absolute jump patching, prologue relocation with instruction widening, inverted-branch abs-jump construction
- hardware breakpoint hooking — DR0-DR3 management, VEH dispatch, single-step handoff, thread-local state isolation, per-thread re-arm
- detour chaining — ordered detour stacks on live hooks, forward-only chain rewriting, trampoline sharing
- vtable interception — per-object and per-class swap, COM interface navigation, throwaway device resolution for D3D9/11/12
- batch operations — single freeze window for N hooks, deferred enable queues, thread-count bounded suspension
- hot-patch detection — MSVC /hotpatch layout recognition, int3/nop padding validation, 5-byte pre-function jump insertion

</details>

<details>
<summary><b>low level</b></summary>
<br>

- x86-64 instruction encoding — legacy prefixes, REX, VEX 2/3-byte, EVEX 4-byte, modrm/sib/disp/imm sizing, opcode map tables (primary/0F/0F38/0F3A)
- PE format — section walking, vtable resolution, IAT/EAT parsing, import forwarding, export enumeration
- SEH/VEH dispatch — vectored exception handler registration, single-step trap flag management, context record manipulation
- windows internals — loader lock, session-bound kernel interfaces, process-notify callbacks, registry-fed configuration gates
- memory management — VirtualAlloc strategies, page protection transitions, secure/unsecure virtual memory, MDL construction and mapping
- graphics API internals — COM vtable navigation, feature-level negotiation, swapchain creation for vtable capture, factory/adapter enumeration

</details>

<details>
<summary><b>tooling + workflow</b></summary>
<br>

- IDA Pro — headless scripting, .pdata-driven function enumeration, Hex-Rays decompilation pipelines, vtable reconstruction, cross-reference analysis
- capstone / keystone — instruction-length cross-validation, test-vector generation, brute-force encoding fuzzing
- x64dbg / ReClass — runtime structure mapping, live memory inspection, vtable walking
- CMake / MSVC — multi-target builds, /W4 clean compilation, static analysis integration
- Python tooling — keystone assembly pipelines, capstone cross-verification, automated test-vector generation, registry/system introspection
- git — multi-repo workflows, rebase conflict resolution, subtree management

</details>

---

## stack

<div align="left">
  <img src="https://skillicons.dev/icons?i=cpp,c,rust,asm,cs,py,go,java,lua,js,ts,html,css,react,nodejs,bash,md&theme=dark" alt="languages" />
</div>

<div align="left">
  <img src="https://skillicons.dev/icons?i=windows,linux,git,github,cmake,vscode,visualstudio,idea,figma,react,nodejs,express,vercel,md&theme=dark" alt="tools" />
</div>

---
