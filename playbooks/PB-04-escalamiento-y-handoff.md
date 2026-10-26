# PB-04: Escalamiento y Handoff a L2 / IR Team

**Nivel:** SOC L1  
**Severidad:** Según el incidente original  
**Objetivo:** Realizar un escalamiento limpio, completo y profesional para que L2 o el Incident Response Team puedan continuar sin pérdida de información.

---

## 1. ¿Cuándo escalar?

El Analista L1 **debe escalar** cuando se cumpla **cualquiera** de estas condiciones:

- Evidencia clara de compromiso exitoso (ransomware, C2, movimiento lateral, etc.)
- Afectación a múltiples hosts o usuarios
- Credenciales de cuentas privilegiadas comprometidas
- Necesidad de análisis forense, de malware o de memoria
- El playbook específico indica escalar
- El tiempo de investigación supera el SLA de L1
- Existe duda razonable sobre el alcance real del incidente

> **Principio clave:** Si tienes duda de si debes escalar… **escala**.

---

## 2. Proceso de Escalamiento (paso a paso)

1. **Completar el ticket** con toda la información disponible (usar plantilla de ticket).
2. **Actualizar el timeline** hasta el momento exacto del handoff.
3. **Clasificar la severidad** final (Crítica / Alta / Media).
4. **Notificar** según el canal definido (ticket + mención / llamada / chat de incidentes).
5. **Entregar el handoff** de forma estructurada (ver sección 3).
6. **Quedar disponible** para aclaraciones durante los siguientes 15-30 minutos.

---

## 3. Contenido mínimo del Handoff

El ticket o mensaje de escalamiento debe incluir **obligatoriamente**:

| Sección | Contenido requerido |
|---------|---------------------|
| **Resumen** | 2-4 líneas claras de qué ocurrió |
| **Timeline** | Lista cronológica de todas las acciones realizadas |
| **Evidencia** | IPs, hashes, usuarios, hosts, URLs, procesos, capturas |
| **Acciones de contención ya realizadas** | Qué se aisló, bloqueó o reseteó |
| **Hipótesis actual del L1** | Qué cree el analista que está pasando |
| **MITRE ATT&CK** | Tácticas y técnicas identificadas |
| **Qué se necesita de L2** | Análisis forense, malware, alcance, etc. |
| **Estado actual** | Hosts aislados, usuarios bloqueados, etc. |

---

## 4. Plantilla rápida de mensaje de escalamiento

```text
[ESCALAMIENTO] INC-YYYYMMDD-XXX – [Título corto del incidente]

Severidad: Crítica / Alta
Analista L1: [Tu nombre]
Hora de escalamiento: [HH:MM]

Resumen:
[2-4 líneas]

Acciones de contención ya realizadas:
- ...

Evidencia clave:
- Hosts: ...
- Usuarios: ...
- IPs: ...
- Hashes: ...

Hipótesis L1:
...

Se necesita de L2:
- Análisis de ...
- Confirmación de alcance
- etc.

Ticket completo: [enlace]