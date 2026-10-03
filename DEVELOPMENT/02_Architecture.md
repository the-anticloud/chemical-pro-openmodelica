# Technical Architecture — OPENMODELICA

**Upstream:** [https://github.com/OpenModelica/OpenModelica](https://github.com/OpenModelica/OpenModelica)
**License:** GPL
**Category:** CHEMICAL_PRODUCTION
**Anticloud Integration:** PAX L5 Narrow L2 General 27B + AIOSS + Offline-First

## Upstream Description

Chemical process modeling

## Anticloud Architectural Changes

1. PAX L5 Narrow L2 General 27B local process control optimization — air-gapped plant
2. AIOSS tamper-evident batch record log (FDA/EMA 21 CFR Part 211 aligned)
3. AES-256 encryption for all formulation and process data
4. Single-binary DCS/SCADA replacement for isolated production networks
5. Zero-cloud: all ML inference, logging, and alarming runs locally
6. GPU/CPU equalizer: real-time control on CPU, simulation on GPU
7. Open OPC-UA integration replacing proprietary DCS middleware
8. Offline regulatory reporting generator: produces submission-ready documents locally

## Integration Points

- **PAX Inference Socket:** Local HTTP endpoint at `127.0.0.1:11434/v1/chat` — same OpenAI-compatible API, zero cloud
- **AIOSS Hook:** Every write operation calls `aioss_append(event, payload)` before commit
- **Encryption Layer:** All file I/O routed through `anticloud_crypto.encrypt_at_rest()`
- **Single Binary Build:** `pyinstaller anticloud_openmodelica.spec` or `go build -o openmodelica`

## Deployment Modes

| Mode | Hardware | Notes |
| --- | --- | --- |
| Edge CPU | Raspberry Pi 4 / Intel NUC | Full feature set, PAX on CPU |
| Desktop GPU | RTX 3060 / A10 | PAX GPU inference, <1s latency |
| Server | 2× A100 | Full batch throughput |
| Air-gapped | Any x86/ARM | Zero network dependency |