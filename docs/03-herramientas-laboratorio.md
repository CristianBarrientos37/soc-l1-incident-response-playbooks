# Laboratorio SOC – Wazuh (4 VMs)

| Máquina | Rol | SO | IP (ejemplo) | Función principal |
|---------|-----|----|--------------|-------------------|
| VM1 | Wazuh Manager + Dashboard | Ubuntu 22.04 | 192.168.56.10 | SIEM, reglas, alertas, Dashboard |
| VM2 | Endpoint Windows | Windows 10/11 | 192.168.56.20 | Agente Wazuh, Sysmon, PowerShell logging |
| VM3 | Endpoint Linux | Ubuntu 22.04 | 192.168.56.30 | Agente Wazuh, auditd, file integrity |
| VM4 | Atacante / Cliente | Kali / Ubuntu | 192.168.56.40 | Generación de tráfico malicioso, phishing simulado |

**Herramientas utilizadas en el laboratorio:**
- Wazuh Manager + Dashboard
- Sysmon (Windows)
- auditd + File Integrity Monitoring (Linux)
- TheHive / Shuffle (opcional para ticketing)
- Wireshark / tcpdump para análisis de tráfico