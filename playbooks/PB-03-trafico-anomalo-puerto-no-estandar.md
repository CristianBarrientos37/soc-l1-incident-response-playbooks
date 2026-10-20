# PB-03: Tráfico Anómalo hacia Puerto No Estándar

**Nivel:** SOC L1  
**Severidad:** Baja → Media  
**SLA triaje:** ≤ 20 minutos  
**MITRE ATT&CK:**
- T1048 – Exfiltration Over Alternative Protocol
- T1071 – Application Layer Protocol
- T1571 – Non-Standard Port
- T1090 – Proxy

## 1. Detección
- Alerta Wazuh: “Connection to non-standard port”, “Suspicious outbound connection”
- Reglas de firewall / Suricata / Zeek
- Netflow anómalo

## 2. Triaje

1. Validar:
   - IP origen (agente)
   - IP destino + puerto
   - Protocolo (TCP/UDP)
   - Volumen de datos
   - Proceso que inicia la conexión (Sysmon / auditd)

2. Clasificar:
   - ¿Es un servicio legítimo mal documentado?
   - ¿Es C2 conocido? (consultar Threat Intel)
   - ¿Hay DNS tunneling o beaconing?

## Diagrama de flujo

```mermaid
flowchart TD
    A[Alerta: Tráfico anómalo<br/>Puerto no estándar] --> B[Validar la alerta]
    
    B --> B1[IP origen - Agente]
    B --> B2[IP destino + Puerto]
    B --> B3[Protocolo TCP/UDP]
    B --> B4[Volumen de datos]
    B --> B5[Proceso que inicia la conexión<br/>Sysmon / auditd]
    
    B1 & B2 & B3 & B4 & B5 --> C{Clasificar el tráfico}
    
    C -->|Servicio legítimo<br/>mal documentado| D[Documentar excepción<br/>Cerrar como FP / Accepted Risk]
    
    C -->|Sospechoso| E[Análisis adicional]
    E --> E1[Consultar Threat Intelligence<br/>VirusTotal / AbuseIPDB]
    E --> E2[Verificar reputación IP/dominio]
    E --> E3[Buscar patrones de beaconing<br/>o DNS tunneling]
    
    E1 & E2 & E3 --> F{¿Evidencia de C2<br/>o exfiltración?}
    
    F -->|No| G[Monitoreo adicional<br/>Documentar y cerrar]
    
    F -->|Sí| H[Contención L1]
    H --> H1[Bloquear IP destino temporalmente]
    H --> H2[Solicitar captura de tráfico pcap]
    H --> H3[Aislar endpoint si es necesario]
    
    H1 & H2 & H3 --> I{¿Requiere investigación<br/>profunda o forense?}
    
    I -->|No| J[Resolver en L1<br/>Documentar]
    I -->|Sí| K[Escalar a L2<br/>Handoff con evidencia]
    
    style A fill:#1e3a5f,stroke:#333,color:#fff
    style C fill:#2d5a27,stroke:#333,color:#fff
    style F fill:#2d5a27,stroke:#333,color:#fff
    style I fill:#2d5a27,stroke:#333,color:#fff
    style H fill:#8b0000,stroke:#333,color:#fff
    style K fill:#8b0000,stroke:#333,color:#fff
    style D fill:#555,stroke:#333,color:#fff
    style G fill:#555,stroke:#333,color:#fff
    style J fill:#555,stroke:#333,color:#fff
```

## 3. Acciones

- Bloquear IP destino temporalmente (si es claramente maliciosa)
- Solicitar captura de tráfico (pcap) al endpoint
- Verificar reputación de IP/dominio (VirusTotal, AbuseIPDB, etc.)
- Escalar si hay evidencia de exfiltración o C2 confirmado