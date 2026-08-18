# ROMEO-HYDRA v0.1.0 // OFFLINE FAIL-CLOSED ECOSYSTEM

```
██████╗  ██████╗ ███╗   ███╗███████╗ ██████╗
██╔══██╗██╔═══██╗████╗ ████║██╔════╝██╔═══██╗
██████╔╝██║   ██║██╔████╔██║█████╗  ██║   ██║
██╔══██╗██║   ██║██║╚██╔╝██║██╔══╝  ██║   ██║
██║  ██║╚██████╔╝██║ ╚═╝ ██║███████╗╚██████╔╝
╚═╝  ╚═╝ ╚═════╝ ╚═╝     ╚═╝╚══════╝ ╚═════╝
        H Y D R A   ·   O F F L I N E
```

[![Release](https://img.shields.io/github/v/release/robinmacv2-ui/romeo-hydra-core?style=flat-square)](https://github.com/robinmacv2-ui/romeo-hydra-core/releases/tag/v0.1.0)
[![License: GPL-3.0](https://img.shields.io/badge/License-GPL%203.0-blue.svg?style=flat-square)](https://www.gnu.org/licenses/gpl-3.0)
[![Python 3.11+](https://img.shields.io/badge/python-3.11%2B-blue?style=flat-square)](https://www.python.org)
[![Offline](https://img.shields.io/badge/mode-OFFLINE-critical?style=flat-square)](https://github.com/robinmacv2-ui/romeo-hydra-core)
[![Fail-closed](https://img.shields.io/badge/gate-FAIL--CLOSED-black?style=flat-square)](https://github.com/robinmacv2-ui/romeo-hydra-core)

**Agente offline determinista (no LLM)** · Hecho desde Termux aarch64 · Auditable. Sin humo. Solo SHA-256.

> **Skill = capacidad · Gate = permiso · Receipt = prueba**

---

## Qué es

ROMEO-HYDRA es un agente **DFA determinista**, sin red, sin APIs, sin shell libre. Todo comando pasa por dos cerraduras:

| Fase | Comportamiento |
|------|----------------|
| **ANTE (Gate)** | parse → `verbo :: ENTIDAD k=v` → allow / deny |
| **POST (Ledger)** | ALLOW → tool + receipt + ledger · DENY → también deja receipt |

Todo queda auditado.

**Prueba mínima:**

```bash
python3 -m romeo_agent -c "echo :: hola"   # → ALLOW + receipt
python3 -m romeo_agent -c "rm :: /tmp"     # → DENY + verbo_no_admisible:rm + receipt
```

**Verbos admisibles C:** `help` · `echo` · `pwd` · `status` · `ls` · `cat` · `hash` · `hashfile` · `log` · `verify` · `score` · `audit`

**Reglas duras:** paths solo bajo ROOT (no `..`, no `/`, no `~`) · stdlib only · Python 3.11+

---

## Core

| | |
|--|--|
| **Repo** | [romeo-hydra-core](https://github.com/robinmacv2-ui/romeo-hydra-core) — agente standalone |
| **Release** | [v0.1.0](https://github.com/robinmacv2-ui/romeo-hydra-core/releases/tag/v0.1.0) · fail-closed · stdlib only |

```bash
git clone --branch v0.1.0 --depth 1 https://github.com/robinmacv2-ui/romeo-hydra-core.git
cd romeo-hydra-core && python3 -m romeo_agent -c "help ::"
```

---

## Ecosistema · 5 capas

```text
                    ┌─────────────────────────────┐
                    │   robinmacv2-ui  ·  MÉXICO  │
                    │   OFFLINE · FAIL-CLOSED     │
                    └─────────────┬───────────────┘
                                  │
         ┌────────────────────────┼────────────────────────┐
         ▼                        ▼                        ▼
   ┌───────────┐            ┌───────────┐            ┌───────────┐
   │  CAPA 0   │            │  CAPA 1   │            │  CAPA 2   │
   │ PRODUCTO  │            │  LINAJE   │            │  TEORÍA   │
   │  ██████   │            │  CÓDIGO   │            │   DOI     │
   └─────┬─────┘            └─────┬─────┘            └─────┬─────┘
         │                        │                        │
    core v0.1.0              romeo-hydra              Postulado
    master-hub               Romeo_Framework          Partícula
    (kernel+pilot+DOI)       hydra.master             Tarjeta / Manifiesto
         │
         ├──────────────┐
         ▼              ▼
   ┌───────────┐  ┌───────────┐
   │  CAPA 3   │  │  CAPA 4   │
   │ BANKING   │  │  OTROS    │
   │ explorat. │  │           │
   └───────────┘  └───────────┘
    Romeo-BANKING   LOOPER-STATION
```

```text
robinmacv2-ui
│
├── CAPA 0 · PRODUCTO (activos)
│   ├── romeo-hydra-core              → agente standalone v0.1.0
│   └── romeo-hydra-master-repository-hub → producto 0.1.2 (kernel + crypto + pilot + DOI)
│
├── CAPA 1 · LINAJE CÓDIGO
│   ├── romeo-hydra · Romeo_Framework · Romeo_Hydra_Framework · hydra.master
│
├── CAPA 2 · TEORÍA / DOI
│   ├── Postulado-invarianza-homeostatica · Part-cula-de-Luis-ngel-
│   ├── TARJETA-L-GICA-CUANTICA · MANIFIESTO-ONTOLOGICO
│
├── CAPA 3 · BANKING (exploratorio)
│   ├── Romeo-BANKING · ROMEO-HYDRA-BANKING
│
└── CAPA 4 · OTROS
    └── LOOPER-STATION
```

Índice: [`ECOSYSTEM.md`](https://github.com/robinmacv2-ui/romeo-hydra-master-repository-hub/blob/main/ECOSYSTEM.md)

---

## Evidencia

```text
# DENY (Termux)
{"gate":{"reason":"verbo_no_admisible:rm","status":"deny"},"receipt":"fec70b6e2b51a356"}

# ALLOW + hash determinista
{"gate":{"reason":"ex_ante_passed","status":"allow"},
 "result":{"sha256":"df733656293a19c54f69093ba916f0a1a2a3c151fc95c13f3a794c2631eeb3a6"},
 "receipt":"60bdfe3bc7bf600a"}

# PATH TRAVERSAL DENY
{"gate":{"reason":"path_fuera_de_envolvente_root","status":"deny"},"receipt":"dcb1ce8b0b6246e8"}
```

**Stack:** Python 3.11 stdlib only · Termux aarch64 / laptop · Offline · Fail-closed  
**Build in public:** LinkedIn · México · sin funding institucional

---

## Contacto

**Luis Angel Vazquez Martinez** — Creador de ROMEO-HYDRA

- GitHub: [@robinmacv2-ui](https://github.com/robinmacv2-ui)
- LinkedIn: [luis-angel-vazquez-martinez](https://www.linkedin.com/in/luis-angel-vazquez-martinez-066ba9422)
- Email: [robinmac.v2@gmail.com](mailto:robinmac.v2@gmail.com)
- Tel: +52 56 5015 3935

---

**Auditable. Offline. Hecho desde Termux.**
