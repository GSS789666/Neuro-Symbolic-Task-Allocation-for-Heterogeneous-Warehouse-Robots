# Versioned neuro-symbolic MRTA reproducibility package

This repository package accompanies the study by Shengshuo Gong and Oleg O. Varlamov on versioned neuro-symbolic task allocation for heterogeneous loading (LR), transport (TR), and unloading (UR) robot teams.

## Evidence boundary

- All warehouse outcomes are simulated; no physical-robot or industrial deployment is claimed.
- DeepSeek-V4-Flash outputs, service latency, and token usage were measured through the API and evaluated through frozen offline replay.
- DeepSeek is advisory. The deterministic shield, Mivar-inspired inference layer, two-stage CP-SAT allocator, and conflict-aware router retain final execution authority.
- Raw DeepSeek response caches are not included. Cache seals, request plans, derived records, and the audit chain are included so that authorized holders can verify the sealed originals.
- No API key, DPAPI secret, `.env`, `.secrets`, virtual environment, manuscript source, editorial history, or peer-review material is included.

## Contents

- `experiment/mrta`: Track A simulator, knowledge layer, allocation, routing, validation, and confirmatory analysis.
- `experiment/mrta_llm_v14`: Track G/E grounding, deterministic shield, cache-integrity, and matched simulation code.
- `experiment/tests` and `experiment/tests_llm_v14`: automated test suites.
- `experiment/runs/main_confirmatory_v1`: frozen 1,800-task Track A outputs and audits.
- `experiment/llm_track_v1_4`: frozen inputs, protocols, cache seals, and derived Track G/E records; raw model responses are absent.
- `experiment/analysis` and `experiment/figures`: publication-data derivations and reproducible figures.
- `RESULTS_SUMMARY.md`: concise findings with provenance limits.
- `MANIFEST.sha256.json`: SHA-256 digest and byte size for every payload file.

## Environment and tests

Python 3.11 was used. From the `experiment` directory:

```cmd
python -m venv .venv
.venv\Scripts\python.exe -m pip install -r requirements.txt
.venv\Scripts\python.exe -m pytest tests_llm_v14 -q
.venv\Scripts\python.exe -m pytest tests -q --ignore=tests\test_confirmatory.py
```

## Reproduce the frozen Track A checks

```cmd
set PYTHONPATH=%CD%
.venv\Scripts\python.exe -m mrta.validation run --run runs\main_confirmatory_v1 --strict-engineering --minimum-tail-sample 2000 --output runs\main_confirmatory_v1\validation_report_reproduced.json
.venv\Scripts\python.exe -m mrta.confirmatory analyze --run runs\main_confirmatory_v1 --freeze main_freeze_manifest.portable.json --protocol confirmatory_protocol.json --output runs\main_confirmatory_v1\confirmatory_analysis_reproduced.json
```

`main_freeze_manifest.json` is the byte-preserved original and contains the original workstation configuration path. `main_freeze_manifest.portable.json` changes only `config_path` to `configs/main.json`, records the original manifest hash, and preserves every frozen configuration, protocol, source, task, and result digest.

Full Track G/E raw-cache replay requires controlled access to the sealed DeepSeek response caches. The public package supports source inspection, test execution, hash comparison, and review of frozen derived records without distributing those raw responses.

## License and citation

The authors have not yet selected the public reuse license. Before making the repository public, replace `LICENSE_PENDING.md` with the approved license and update the repository URL in the article. Citation metadata is provided in `CITATION.cff`.
