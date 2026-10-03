# Build and Test

**Project:** `OPENMODELICA`
**Upstream:** https://github.com/OpenModelica/OpenModelica
**License:** GPL

## Quick Start

```bash
git clone https://github.com/OpenModelica/OpenModelica
cd OpenModelica
pip install -r requirements-anticloud.txt
python anticloud_main.py --offline --pax-local
```

## Anticloud Improvements Applied

1. PAX L5 Narrow L2 General 27B local process control optimization — air-gapped plant
2. AIOSS tamper-evident batch record log (FDA/EMA 21 CFR Part 211 aligned)
3. AES-256 encryption for all formulation and process data
4. Single-binary DCS/SCADA replacement for isolated production networks
5. Zero-cloud: all ML inference, logging, and alarming runs locally
6. GPU/CPU equalizer: real-time control on CPU, simulation on GPU
7. Open OPC-UA integration replacing proprietary DCS middleware
8. Offline regulatory reporting generator: produces submission-ready documents locally

## Benchmark Targets

| Metric | Target |
| --- | --- |
| Latency | Primary inference task: <5s on CPU, <1s on GPU |
| Throughput | Batch processing: >100 items/hour on single CPU server |
| Memory | <8GB RAM for standard deployment |
| Accuracy | Task-specific accuracy within 5% of cloud-API baseline |

## Build Status

Not yet measured. Run verified build and record actual figures above.
