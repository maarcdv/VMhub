# VMHub

Sistema de gestión centralizada de máquinas virtuales VirtualBox. Permite vincular VMs desde una interfaz web, ver su rendimiento a nivel de hardware (CPU, RAM, disco) y acceder a una terminal shell remota para ejecutar comandos.

Proyecto Intermodular — Grado Medio SMX.

## ¿Qué hace?

- Vincula máquinas virtuales de VirtualBox (de uno o varios hosts) con el servicio.
- Muestra el estado y rendimiento de cada VM en un dashboard centralizado.
- Permite acceder a una terminal interactiva de cada VM desde el navegador.

## Arquitectura

```
┌────────────┐      ┌────────────┐      ┌────────────┐
│   Agente   │ ───► │   Backend   │ ◄──► │  Frontend  │
│ (por host) │      │  (API+WS)   │      │  (web)     │
└────────────┘      └────────────┘      └────────────┘
      │
      ▼
  VirtualBox
 (VBoxManage)
```

- **agent/**: se ejecuta en cada host con VirtualBox. Reporta métricas y ejecuta comandos vía `VBoxManage`.
- **backend/**: API + WebSockets. Gestiona usuarios, VMs registradas y la comunicación en tiempo real.
- **frontend/**: dashboard web (gráficas de rendimiento + terminal integrada).
- **docs/**: documentación del proyecto (memoria, diagramas, decisiones técnicas).

## Stack técnico

| Componente | Tecnología |
|---|---|
| Agente | Python + VBoxManage/SDK VirtualBox |
| Backend | FastAPI + WebSockets |
| Frontend | React + Chart.js + xterm.js |
| Base de datos | PostgreSQL |
| Métricas históricas | InfluxDB (ampliación) |

## Estado del proyecto

🚧 En desarrollo — Proyecto Intermodular en curso.

| Fase | Contenido | Estado |
|---|---|---|
| 1r trimestre | Agente básico + registro de VMs + dashboard de métricas | ⬜ |
| 2n trimestre | Ejecución de comandos + autenticación y seguridad | ⬜ |
| 3r trimestre | Terminal interactiva completa + multi-host | ⬜ |

## Instalación

_Pendiente de documentar según avance el desarrollo._

## Licencia

MIT
