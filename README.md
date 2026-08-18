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

---

### Quién soy

**Luis Angel Vazquez Martinez** — fundador de ROMEO-HYDRA.  
Arquitectura de agentes offline con gate ex-ante y evidencia SHA-256, construida desde Termux (México), sin equipo ni funding institucional.  
Un mes de build-in-public: de cero a runtime determinista fail-closed.

### Qué es ROMEO-HYDRA

Runtime offline para gobernanza de acciones: **Skill = capacidad · Gate = permiso · Receipt = prueba**.  
El circuito es dual: **ANTE** (el predicado de admisibilidad decide allow/deny antes de ejecutar) y **POST** (toda decisión deja receipt SHA-256[:16] en ledger append-only).

Ejemplo real:

```text
python3 -m romeo_agent -c "rm :: /tmp"
→ gate.status = "deny" | reason = "verbo_no_admisible:rm" | receipt = fec70b6e2b51a356

python3 -m romeo_agent -c "echo :: hola"
→ gate.status = "allow" | reason = "ex_ante_passed" | receipt = 60bdfe3bc7bf600a
```

No hay shell libre. No hay red. No hay APIs externas. Solo Python stdlib.

---

### Ecosistema (señal, no ruido)

| Repo | Rol | Status |
|------|-----|--------|
| [romeo-hydra-core](https://github.com/robinmacv2-ui/romeo-hydra-core) | Agente DFA offline · release v0.1.0 | ![Active](https://img.shields.io/badge/status-Active-success?style=flat-square) |
| [romeo-hydra-master-repository-hub](https://github.com/robinmacv2-ui/romeo-hydra-master-repository-hub) | Producto completo · kernel + pilot + tests + DOI | ![Active](https://img.shields.io/badge/status-Active-success?style=flat-square) |
| [romeo-hydra](https://github.com/robinmacv2-ui/romeo-hydra) | Núcleo histórico · linaje técnico | ![Linaje](https://img.shields.io/badge/status-Linaje-lightgrey?style=flat-square) |
| [Romeo_Framework](https://github.com/robinmacv2-ui/Romeo_Framework) | Metodología reproducible (ROMEO) | ![Beta](https://img.shields.io/badge/status-Beta-yellow?style=flat-square) |
| [Romeo-BANKING](https://github.com/robinmacv2-ui/Romeo-BANKING) | Gobernanza auditable · exploratorio | ![Beta](https://img.shields.io/badge/status-Exploratorio-yellow?style=flat-square) |
| [Postulado-invarianza-homeostatica](https://github.com/robinmacv2-ui/Postulado-invarianza-homeostatica) | Formalismo DOI · no producto | ![Theory](https://img.shields.io/badge/status-Theory-blue?style=flat-square) |

Índice completo: [`ECOSYSTEM.md`](https://github.com/robinmacv2-ui/romeo-hydra-master-repository-hub/blob/main/ECOSYSTEM.md)

---

### Evidencia (Termux · 2026-08-18)

```text
# DENY
{"gate":{"reason":"verbo_no_admisible:rm","status":"deny"},"receipt":"fec70b6e2b51a356"}

# ALLOW + determinismo hash
{"gate":{"reason":"ex_ante_passed","status":"allow"},
 "result":{"sha256":"df733656293a19c54f69093ba916f0a1a2a3c151fc95c13f3a794c2631eeb3a6"},
 "receipt":"60bdfe3bc7bf600a"}

# PATH TRAVERSAL DENY
{"gate":{"reason":"path_fuera_de_envolvente_root","status":"deny"},"receipt":"dcb1ce8b0b6246e8"}
```

Receipts verificables con `verify :: <receipt>` sobre el ledger local.

---

### Stack

- Python 3.11+ · **stdlib only** en el core  
- Offline · fail-closed · sin shell libre · Termux aarch64 / laptop  
- Sintaxis: `verbo :: ENTIDAD k=v`  
- Verbos C: help · pwd · ls · cat · hash · hashfile · echo · status · log · verify · score · audit

```bash
git clone --branch v0.1.0 --depth 1 https://github.com/robinmacv2-ui/romeo-hydra-core.git
cd romeo-hydra-core && python3 -m romeo_agent -c "help ::"
```

---

### Contacto

- GitHub: [robinmacv2-ui](https://github.com/robinmacv2-ui)
- LinkedIn: [luis-angel-vazquez-martinez](https://www.linkedin.com/in/luis-angel-vazquez-martinez-066ba9422)
- Email: [robinmac.v2@gmail.com](mailto:robinmac.v2@gmail.com)
- Tel: +52 56 5015 3935

---

**Auditable. Sin humo. Hecho desde Termux.**  
Luis Angel Vazquez Martinez · México · 2026
