# ROMEO-HYDRA · Offline fail-closed ecosystem

**Luis Angel Vazquez Martinez** · México  
ORCID [0009-0006-8163-3759](https://orcid.org/0009-0006-8163-3759)

[![Offline](https://img.shields.io/badge/mode-OFFLINE-critical?style=flat-square)](#)
[![Fail-closed](https://img.shields.io/badge/gate-FAIL--CLOSED-black?style=flat-square)](#)
[![Python 3.11+](https://img.shields.io/badge/python-3.11%2B-blue?style=flat-square)](https://www.python.org)
[![Stdlib core](https://img.shields.io/badge/core-stdlib%20only-success?style=flat-square)](#)

**Deterministic agent (not an LLM)** · Built from Termux aarch64 · Auditable · SHA-256 evidence

> **Skill = capability · Gate = permission · Receipt = proof**

---

## Public evaluation surface (start here)

| Repo | Role | Jury command |
|------|------|----------------|
| **[romeo-hydra-quantik](https://github.com/robinmacv2-ui/romeo-hydra-quantik)** | Public door | `python3 main.py` |
| **[romeo-hydra-master-repository-hub](https://github.com/robinmacv2-ui/romeo-hydra-master-repository-hub)** | Product surface + pilot + DOI | `pip install -e .` then `python -m romeo_agent -c "status ::"` |
| **[hydra-genesis-zero](https://github.com/robinmacv2-ui/hydra-genesis-zero)** | Pure kernel MRU (no pip) | `python3 main.py` |

### 3-minute reproduce (hub)

```bash
git clone --depth 1 https://github.com/robinmacv2-ui/romeo-hydra-master-repository-hub.git
cd romeo-hydra-master-repository-hub
python3 -m venv .venv && source .venv/bin/activate
pip install -e .          # ZERO third-party packages
python -m romeo_agent -c "status ::"
python -m romeo_agent -c "help ::"
```

Checklist: [JURY_CHECKLIST.md](https://github.com/robinmacv2-ui/romeo-hydra-master-repository-hub/blob/main/JURY_CHECKLIST.md)

---

## How the gate works

| Phase | Behavior |
|-------|----------|
| **ANTE (Gate)** | parse → `verb :: ENTITY k=v` → allow / deny |
| **POST (Ledger)** | ALLOW → tool + receipt + ledger · DENY → receipt still written |

```bash
python -m romeo_agent -c "echo :: hola"   # → ALLOW + receipt
python -m romeo_agent -c "rm :: /tmp"     # → DENY + receipt (fail-closed)
```

Hard rules: paths only under ROOT · stdlib only on product surface · offline.

---

## Non-claims (read before scoring)

- Not CNBV-certified  
- Not a production banking system  
- Not an LLM  
- Laboratory code under `lab/` is **out of product evaluation scope**

---

## Evidence sample

```text
ALLOW → gate.status=allow · lineage · receipt
DENY  → gate.status=deny  · reason · receipt  (no crash)
```

Concept DOI: [10.5281/zenodo.21744014](https://doi.org/10.5281/zenodo.21744014)

---

## Contact

**Luis Angel Vazquez Martinez** — ROMEO-HYDRA

- GitHub: [@robinmacv2-ui](https://github.com/robinmacv2-ui)
- Email: [robinmac.v2@gmail.com](mailto:robinmac.v2@gmail.com)
- Commercial: emmororromeohydra@gmail.com

**Auditable. Offline. Built from Termux.**
