<div align="center">

# draxo

**kernel internals · reverse engineering · hooking engines**

</div>

---

### what i do

windows internals and reverse engineering. i spend most of my time below the
line — auditing kernel drivers for vulnerabilities, building hooking
infrastructure, and understanding how compiled code actually behaves on
silicon.

recent work includes a full length-decoder rewrite (legacy/REX/VEX/EVEX),
a hooking engine with two independent backends, and documented vulnerability
research on signed kernel drivers shipping to millions of machines.

---

### projects

| repo | what it is |
|---|---|
| [**Amnesia-Hook**](https://github.com/DaddyZyn/Amnesia-Hook) | x64 hooking engine — inline (trampoline) + VEH (hardware breakpoint) backends. custom length decoder covering legacy/REX/VEX/EVEX. D3D9/11/12 + OpenGL vtable hooks. zero dependencies. |
| [**Windows-Vuln-drivers**](https://github.com/DaddyZyn/Windows-Vuln-drivers) | documented vulnerability research on signed Windows kernel drivers not on Microsoft's blocklist. full analysis with assembly-level evidence, reversed interface headers, non-destructive PoCs. |

---

### toolset

`C++20` `C` `Rust` `Python` `x86/x64 asm`

`IDA Pro` `x64dbg` `ReClass` `Ghidra` `HDE64/AmLDE` `capstone` `keystone`

`WDK / KMDF / WDM` `ImGui` `D3D9/11/12` `Git`

---

### focus areas

<details>
<summary><b>expand</b></summary>
<br>

- driver vulnerability research — length decoders, relocation engines, protocol reconstruction from raw disassembly
- inline hooking — prologue relocation, rip-relative fixups, branch widening, trampoline allocation strategies
- hardware breakpoint hooking — DR register management, VEH dispatch, thread-local state isolation
- graphics API interception — D3D9/11/12 vtable resolution, swapchain capture, ImGui overlay integration
- windows internals — PE format, SEH/VEH dispatch, loader internals, session-bound kernel command interfaces

</details>

---

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=DaddyZyn&show_icons=true&theme=github_dark&hide_border=true&bg_color=00000000&hide_rank=false" alt="stats" width="420">

</div>
