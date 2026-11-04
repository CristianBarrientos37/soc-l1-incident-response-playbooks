# Mapeo a MITRE ATT&CK – Playbooks SOC L1

Este documento resume las **tácticas y técnicas de MITRE ATT&CK** asociadas a los playbooks de este repositorio.

---

## PB-01: Phishing con Credenciales Comprometidas

| Técnica ID | Nombre | Descripción en el contexto del playbook |
|------------|--------|-----------------------------------------|
| T1566     | Phishing | Vector inicial de ataque |
| T1566.001 | Spearphishing Attachment | Correo con adjunto malicioso |
| T1566.002 | Spearphishing Link | Correo con enlace malicioso |
| T1078     | Valid Accounts | Uso de credenciales robadas |
| T1110     | Brute Force | Posibles intentos posteriores de fuerza bruta |

**Tácticas principales:** Initial Access, Credential Access

---

## PB-02: Alerta de Ransomware en Endpoint

| Técnica ID | Nombre | Descripción en el contexto del playbook |
|------------|--------|-----------------------------------------|
| T1486     | Data Encrypted for Impact | Cifrado de archivos |
| T1490     | Inhibit System Recovery | Eliminación de shadow copies / backups |
| T1083     | File and Directory Discovery | Enumeración de archivos antes de cifrar |
| T1059     | Command and Scripting Interpreter | Ejecución de scripts o binarios |
| T1204     | User Execution | Ejecución iniciada por el usuario |

**Tácticas principales:** Execution, Impact

---

## PB-03: Tráfico Anómalo hacia Puerto No Estándar

| Técnica ID | Nombre | Descripción en el contexto del playbook |
|------------|--------|-----------------------------------------|
| T1571     | Non-Standard Port | Comunicación por puertos no habituales |
| T1071     | Application Layer Protocol | Uso de protocolos legítimos para C2 |
| T1048     | Exfiltration Over Alternative Protocol | Posible exfiltración |
| T1090     | Proxy | Uso de proxies o tunnels |
| T1572     | Protocol Tunneling | Túneles (DNS, ICMP, etc.) |

**Tácticas principales:** Command and Control, Exfiltration

---

## Resumen visual de tácticas cubiertas

- **Initial Access**
- **Execution**
- **Credential Access**
- **Command and Control**
- **Exfiltration**
- **Impact**

---
