# PB-02: Alerta de Ransomware en Endpoint

**Nivel:** SOC L1  
**Severidad:** Crítica  
**SLA triaje:** ≤ 5 minutos  
**MITRE ATT&CK:**
- T1486 – Data Encrypted for Impact
- T1490 – Inhibit System Recovery
- T1083 – File and Directory Discovery
- T1059 – Command and Scripting Interpreter

## 1. Detección / Trigger
- Regla Wazuh: “Ransomware behavior detected”, “Multiple file modifications”, “Suspicious process creating .encrypted files”
- Alerta de File Integrity Monitoring (FIM) masiva
- Usuario reporta archivos bloqueados / mensaje de rescate

## 2. Triaje Inicial (L1) – ACCIONES RÁPIDAS

1. **Confirmar la alerta** (máximo 2-3 minutos)
   - Ver proceso sospechoso en Wazuh
   - Revisar extensiones de archivos modificados
   - Verificar si hay mensaje de ransom note

2. **Contención inmediata (prioridad #1)**
   - **Aislar el endpoint** → Wazuh Active Response o desconectar de red
   - No apagar el equipo (preservar memoria volátil si es posible)

3. **Identificar alcance**
   - ¿Hay más endpoints con la misma alerta?
   - ¿Hay shares de red montados?

## 3. Acciones L1

| Acción | Prioridad | Herramienta |
|--------|-----------|-------------|
| Aislar host | Crítica | Wazuh Active Response / EDR / switch |
| Identificar proceso padre | Alta | Wazuh / Sysmon |
| Recopilar ransom note (si existe) | Alta | Acceso remoto controlado |
| Verificar backups (no restaurar aún) | Media | Solicitar a Infrastructure |
| Notificar a L2 e Incident Commander | Crítica | Ticket + llamada |

## 4. Diagrama de flujo

```mermaid
flowchart TD
    A[Alerta de Ransomware<br/>o comportamiento sospechoso] --> B{Confirmación rápida<br/>≤ 2-3 minutos}
    
    B --> B1[Revisar proceso sospechoso]
    B --> B2[Extensiones de archivos modificados]
    B --> B3[¿Existe ransom note?]
    
    B1 & B2 & B3 --> C{¿Es ransomware<br/>confirmado o altamente sospechoso?}
    
    C -->|No - Falso positivo| D[Cerrar como FP<br/>Documentar]
    C -->|Sí| E[CONTENCIÓN INMEDIATA]
    
    E --> E1[Aislar el endpoint<br/>Wazuh Active Response / EDR / Red]
    E --> E2[NO apagar el equipo<br/>Preservar evidencia volátil]
    
    E1 & E2 --> F[Identificar alcance]
    F --> F1[¿Más endpoints afectados?]
    F --> F2[¿Shares de red montados?]
    F --> F3[Identificar proceso padre]
    
    F1 & F2 & F3 --> G[Notificar y Escalar]
    G --> G1[Crear ticket Crítico]
    G --> G2[Notificar a L2 + Incident Commander]
    G --> G3[Adjuntar timeline + evidencia]
    
    G1 & G2 & G3 --> H[Handoff a IR Team]
    
    style A fill:#8b0000,stroke:#333,color:#fff
    style C fill:#2d5a27,stroke:#333,color:#fff
    style E fill:#8b0000,stroke:#333,color:#fff
    style E1 fill:#8b0000,stroke:#333,color:#fff
    style G fill:#8b0000,stroke:#333,color:#fff
    style H fill:#8b0000,stroke:#333,color:#fff
    style D fill:#555,stroke:#333,color:#fff
```

## 5. Escalamiento inmediato
Siempre escalar a L2/IR Team en casos de ransomware confirmado o altamente sospechoso.

## 6. Documentación
Usar plantilla de ticket + checklist de ransomware.