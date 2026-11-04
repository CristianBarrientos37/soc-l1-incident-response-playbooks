# Checklist de Triaje – SOC L1

```markdown
**Ticket ID:** ________________  
**Analista:** ________________  
**Fecha/Hora inicio triaje:** ________________

---

## 1. Validación inicial de la alerta
- [ ] Abrí la alerta en Wazuh Dashboard
- [ ] Verifiqué el timestamp y el agente
- [ ] Confirmé que la regla tiene sentido en el contexto
- [ ] Revisé si hay alertas relacionadas en los últimos 30-60 minutos

## 2. Recopilación de evidencia mínima
- [ ] Host / Agente afectado identificado
- [ ] Usuario afectado (si aplica)
- [ ] IP de origen / destino
- [ ] Proceso o archivo involucrado
- [ ] Hash (si hay archivo)
- [ ] URL / Dominio (si aplica)

## 3. Evaluación de impacto
- [ ] ¿Hay evidencia de ejecución exitosa?
- [ ] ¿Hay movimiento lateral?
- [ ] ¿Hay más hosts afectados?
- [ ] ¿Se usaron credenciales?

## 4. Contención (si corresponde)
- [ ] Host aislado (si era necesario)
- [ ] Credenciales reseteadas (si aplicaba)
- [ ] IP / dominio / URL bloqueados
- [ ] Otras acciones de contención documentadas

## 5. Documentación
- [ ] Ticket creado / actualizado
- [ ] Timeline completado
- [ ] Evidencia adjunta o referenciada
- [ ] Clasificación final asignada (FP / TP / Escalado)

## 6. Decisión final
- [ ] Cerrado como False Positive
- [ ] Cerrado como True Positive – Resuelto en L1
- [ ] Escalado a L2 / IR Team (con handoff completo)

---

**Hora de finalización del triaje:** ________________  
**Tiempo total de triaje:** ________________ minutos