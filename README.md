# Guía de Respuestas a Incidentes y Playbooks de Triaje – SOC L1

> Repositorio de portafolio que demuestra la metodología de trabajo de un Analista de Seguridad de Nivel 1 (SOC L1) mediante playbooks operativos, diagramas de flujo, plantillas de tickets y mapeo a MITRE ATT&CK.

## Objetivo

Este repositorio actúa como un **Manual de Procedimientos (SOP)** y colección de **Playbooks** para escenarios comunes que enfrenta un analista SOC L1. El objetivo es mostrar:

- Comprensión del ciclo de vida de un incidente (basado en NIST SP 800-61 y SANS PICERL)
- Capacidad de triaje rápido y documentación profesional
- Uso práctico de un SIEM (Wazuh) en un laboratorio real de 4 máquinas virtuales
- Mapeo consistente a MITRE ATT&CK

## Laboratorio utilizado

Se utilizó un laboratorio casero con **4 máquinas virtuales** configuradas según la guía de laboratorio SOC + Wazuh:

| Rol                    | Sistema Operativo      | Función principal                          |
|------------------------|------------------------|--------------------------------------------|
| Wazuh Manager + Dashboard | Ubuntu 22.04         | SIEM, reglas, alertas, visualización       |
| Endpoint Windows       | Windows 10/11          | Agente Wazuh + Sysmon                      |
| Endpoint Linux         | Ubuntu 22.04           | Agente Wazuh + auditd + FIM                |
| Máquina Atacante       | Kali Linux             | Simulación de ataques controlados          |

## Estructura del repositorio

```text
├── docs/                  # Metodología y contexto del laboratorio
├── playbooks/             # Playbooks operativos L1
├── diagrams/              # Diagramas de flujo (Mermaid)
├── templates/             # Plantillas de tickets y checklists
├── mitre/                 # Mapeo de técnicas ATT&CK
└── examples/              # Ejemplos rellenados de tickets reales del lab
```

## Playbooks incluidos

| ID     | Escenario                                      | Severidad típica | SLA triaje |
|--------|------------------------------------------------|------------------|------------|
| PB-01  | Phishing con credenciales comprometidas        | Media-Alta       | ≤ 15 min   |
| PB-02  | Alerta de Ransomware en Endpoint               | Crítica          | ≤ 5 min    |
| PB-03  | Tráfico anómalo hacia puerto no estándar       | Baja-Media       | ≤ 20 min   |

## Metodología de respuesta a incidentes

Se sigue el ciclo **PICERL** (SANS) / **NIST SP 800-61**:

1. **Preparation**
2. **Identification** (Triaje)
3. **Containment**
4. **Eradication**
5. **Recovery**
6. **Lessons Learned**

El analista L1 se enfoca principalmente en **Identification** y **Containment** inicial, documentando todo para un handoff limpio a L2/IR Team.

## Cómo usar este repositorio

1. Leer `docs/01-metodologia-ir.md`
2. Revisar los playbooks según el tipo de alerta
3. Usar las plantillas de `templates/` para documentar
4. Consultar los diagramas Mermaid para seguir el flujo lógico

## Mapeo a MITRE ATT&CK

Todos los playbooks incluyen las técnicas relevantes. Ver carpeta `mitre/` para el mapeo completo.

## Autor

Cristian Barrientos 
Analista SOC L1 en formación  
Laboratorio personal con Wazuh  

---

**Nota de seguridad:** Este repositorio no contiene credenciales, tokens, logs reales ni información sensible del laboratorio.