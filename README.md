
**C/C++ · Audio/Video pipeline · Embedded · Local LLM inference**
Shenzhen, China · 23 years in A/V since 2003

---

#### What I do

- **Audio/Video** — codec, streaming, player, RTC. From feature-phone TV in 2005 to 4K live streaming today.
- **Embedded / Automotive** — CarPlay, Android Auto, HiCar screen projection; Bluetooth audio; military-grade video conferencing terminals.
- **Local LLM inference** — running large MoE models on AMD AI Max+395 (128 GB unified memory), three mutually-exclusive backends under systemd.

#### Currently working on

- Regulatory video compliance integration: on-prem camera → government platform handshake → dashboard / app / backend.
- [AI-MAX-395](https://github.com/zhuxiangwei/AI-MAX-395) series — hands-on records of deploying large models on unified-memory hardware.

#### Some concrete things

- Running **Hy4-Flash SQ-128** at 256k context (host-side KV + SSD conversation
  cache) on a 128 GB unified-memory mini PC; a 125B MoE (Qwen3.8-Flash-Next,
  Q6_K_XL) previously hit **34.9–36.9 t/s** with 10+ hour sessions at 262K
  context and no throttling — that model has since been retired.
- Three inference backends share one memory pool (large MoE / 27B+MTP / video gen) —
  switching costs a full reboot, because on unified memory concurrency is a
  bandwidth problem, not a scheduling problem.
- Benchmarks lied: a draft-decoding scheme gave **+47 % on a single-point bench**
  and reversed in production A/B. Only one option stayed non-negative across
  every context band.
- Video VRAM peaks stay flat (52–53 GiB) across a 2.25× resolution range —
  the constraint is time, not memory.

