# 02 - Roles y Responsabilidades en el SOC

Este documento define los roles típicos dentro de un Security Operations Center (SOC) y detalla específicamente las responsabilidades del **Analista SOC L1**, que es el perfil al que está orientado este repositorio de portafolio.

---

## 1. Estructura típica de un SOC

| Nivel | Rol | Enfoque principal |
|-------|-----|-------------------|
| **L1** | Security Analyst / Triage Analyst | Triaje, validación de alertas, contención inicial, documentación |
| **L2** | Incident Responder / Senior Analyst | Investigación profunda, análisis forense básico, contención avanzada |
| **L3** | Threat Hunter / Malware Analyst / IR Lead | Hunting, análisis de malware, respuesta a incidentes complejos |
| **IR Team** | Incident Response Team | Manejo de incidentes mayores (ransomware, APT, etc.) |
| **SOC Manager** | Gestión del equipo y métricas | Supervisión, reporting, mejora continua |

---

## 2. Responsabilidades del Analista SOC L1

### 2.1 Responsabilidades principales

- Monitorear el SIEM (en este laboratorio: **Wazuh Dashboard**)
- Realizar el **triaje** de alertas según los playbooks definidos
- Validar si una alerta es **True Positive** o **False Positive**
- Recopilar evidencia mínima necesaria
- Ejecutar acciones de **contención inicial** (cuando tenga permisos y según playbook)
- Documentar correctamente el incidente usando las plantillas de tickets
- Escalar de forma oportuna y con información completa a L2 / IR Team
- Mantener el timeline actualizado en tiempo real

### 2.2 Responsabilidades que **NO** corresponden normalmente al L1

- Análisis forense profundo de memoria o disco
- Ingeniería inversa de malware
- Decisiones de negocio sobre comunicación externa o legal
- Restauración de sistemas productivos
- Modificaciones permanentes de reglas del SIEM (salvo aprobación)

---

## 3. Matriz RACI simplificada (ejemplo)

| Actividad                        | L1     | L2     | IR Team | SOC Manager |
|----------------------------------|--------|--------|---------|-------------|
| Monitoreo de alertas             | R/A    | C      | I       | I           |
| Triaje inicial                   | R/A    | C      | I       | I           |
| Contención inicial (host/IP)     | R      | A/C    | C       | I           |
| Investigación profunda           | C/I    | R/A    | C       | I           |
| Análisis de malware              | I      | C      | R/A     | I           |
| Comunicación a stakeholders      | I      | C      | R       | A           |
| Lecciones aprendidas             | C      | R      | R/A     | A           |

**Leyenda RACI:**
- **R** = Responsible (hace el trabajo)
- **A** = Accountable (responsable final)
- **C** = Consulted (se le consulta)
- **I** = Informed (se le informa)

---

## 4. Criterios de Escalamiento (cuándo pasar de L1 a L2)

El Analista L1 **debe escalar** cuando se cumpla cualquiera de estas condiciones:

- Evidencia clara de compromiso exitoso (ransomware, C2, movimiento lateral)
- Afectación a múltiples hosts o usuarios
- Credenciales de cuentas privilegiadas comprometidas
- Necesidad de análisis forense o de malware
- El playbook indica explícitamente escalar
- Duda razonable sobre el alcance del incidente
- El tiempo de investigación supera el SLA de L1

**Principio clave**:  
> “Si tienes duda de si debes escalar… escala.”

---

## 5. Handoff de calidad (qué debe entregar el L1)

Cuando se escala un caso, el ticket debe incluir como mínimo:

1. Resumen claro del incidente (2-4 líneas)
2. Timeline completo de acciones realizadas
3. Evidencia recopilada (IPs, hashes, usuarios, hosts, capturas)
4. Acciones de contención ya ejecutadas
5. Hipótesis actual del analista L1
6. Mapeo a MITRE ATT&CK (si aplica)
7. Qué se necesita específicamente de L2

Usar siempre la plantilla de ticket disponible en `templates/ticket-incident-response.md`.

---

## 6. Habilidades esperadas en un Analista SOC L1

- Comprensión de redes y protocolos (TCP/IP, DNS, HTTP, etc.)
- Lectura básica de logs (Windows Event Log, Sysmon, Linux auth.log, etc.)
- Uso de SIEM (Wazuh en este laboratorio)
- Conocimiento de MITRE ATT&CK
- Capacidad de seguir playbooks bajo presión
- Buena documentación y comunicación escrita
- Mentalidad de “asumir compromiso hasta demostrar lo contrario”

---

## 7. Relación con este repositorio

Este repositorio está diseñado específicamente para demostrar las competencias de un **Analista SOC L1**:

- Playbooks de triaje y contención inicial
- Plantillas de documentación profesional
- Diagramas de flujo de decisión
- Mapeo a MITRE ATT&CK
- Uso práctico de un laboratorio real con Wazuh