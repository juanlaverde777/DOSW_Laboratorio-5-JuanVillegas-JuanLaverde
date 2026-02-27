# DOSW_Laboratorio-5-JuanVillegas-JuanLaverde

### PARTE 2
#### Roles del equipo (Scrum)

- Product Owner: Juan Manuel Villegas
- Scrum Master: Juan José Laverde
- Desarrollador: Villegas-Laverde

  # Desglose de trabajo (Scrum) — Realizar Consignación

 
**Requerimiento seleccionado:** RF-03 — Realizar consignación

---

## Épica (SCRUM-5)

| Campo | Descripción |
|---|---|
| **ID** | EP-01 |
| **Título** | Gestión de consignaciones desde bancos externos |
| **Descripción** | Permitir que clientes y cajeros realicen consignaciones a cuentas Bankify provenientes de bancos externos (p. ej. Bancolombia, Davivienda o PSE), validando origen y actualizando saldos de forma segura y registrada. |
| **Stakeholder** | Gerente de Operaciones / Product Owner |

---

## Historias de usuario 

| ID | Título |
|---:|---|
| **SCRUM-6: HU-01** | Como cliente quiero consignar dinero a una cuenta Bankify para que mi saldo se actualice y quede registrado. |
| **SCRUM-7: HU-02** | Como cajero quiero ingresar consignaciones en nombre de clientes para que puedan recibir fondos desde bancos externos. |
| **SCRUM-8: HU-03** | Como sistema quiero validar que el banco origen esté permitido (p. ej. Bancolombia/Davivienda) para prevenir consignaciones desde bancos no soportados. |
| **SCRUM-9: HU-04** | Como cliente quiero recibir un comprobante/recibo tras una consignación para tener evidencia de la transacción. |

**Descripción detallada / aceptación :**
- **SCRUM-6: HU-01:** El cliente introduce número de cuenta destino y monto; el sistema registra la transacción y actualiza saldo.
- **SCRUM-7: HU-02:** El cajero ingresa datos de la consignación en una interfaz operativa; el sistema valida y procede igual que HU-01.
- **SCRUM-8: HU-03:** Antes de registrar la transacción, el sistema consulta la lista de bancos permitidos y, si aplica, procede; si no, rechaza la consignación con mensaje.
- **SCRUM-9: HU-04:** Tras registro exitoso, el sistema genera un comprobante (PDF o JSON en API) con identificador de transacción, banco origen y monto.

---

## Tareas por historia de usuario

**SCRUM-6: HU-01 (cliente) — tareas**
- SCRUM-22: TR-01: Diseñar UI de consignación para cliente (formulario cuenta + monto).
- SCRUM-23: TR-02: Implementar endpoint backend para crear consignación.
- SCRUM-24: TR-03: Actualizar lógica de saldo y registro de transacción en la base de datos.

**SCRUM-7 HU-02 (cajero) — tareas**
- SCRUM-25: TR-04: Diseñar UI operativa para cajero (campos adicionales, validaciones).
- SCRUM-26: TR-05: Implementar permisos/roles para permitir acción de cajero.
- SCRUM-27: TR-06: Registrar transacciones con meta-datos (usuario operador).

**SCRUM-8 HU-03 (validación banco origen) — tareas**
- SCRUM-28: TR-07: Definir y persistir lista de bancos permitidos (código banco → nombre).
- SCRUM-29: TR-08: Implementar validación en backend para origen de fondos.
- SCRUM-30: TR-09: Crear pruebas unitarias e integración para la validación.

**SCRUM 9 HU-04 (comprobante) — tareas**
- SCRUM-31: TR-10: Definir formato de comprobante (PDF/JSON) y campos requeridos.
- SCRUM-32: TR-11: Implementar generación de comprobante y su almacenamiento.
- SCRUM-33: TR-12: Exponer endpoint/descarga del comprobante para el usuario.

---

## Relación épica ↔ historias
- EP-01 → HU-01, HU-02, HU-03, HU-04

---

## Prioridad 

- **HU-01 — Alto.** Justificación: Es la funcionalidad core (cliente debe poder recibir consignaciones) y permite comprobar flujo de negocio.
- **HU-03 — Alto.** Justificación: Si no validamos bancos origen, el sistema podría aceptar transacciones inválidas; seguridad y reglas de negocio primero.
- **HU-02 — Medio.** Justificación: Importante para operaciones presenciales, pero la interfaz de cajero se puede desplegar en iteración posterior.
- **HU-04 — Medio.** Justificación: El comprobante es necesario para auditoría y confianza, pero puede generarse una vez el flujo principal esté estable.

---

## Parte 4 

Se agrega el link con el video de la votacion mediante Planning Poker 

https://pruebacorreoescuelaingeduco-my.sharepoint.com/:v:/g/personal/juan_laverde-r_mail_escuelaing_edu_co/IQCMF2XUzsN-SLA1Z0SbGi2CAX7ivID3yT5A5XL2Anfvj8o?e=UqH9zu&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D


a. ¿Cuál fue la mayor dificultad a la hora de estimar?

La mayor dificultad que enfrentamos fue cuantificar el equilibrio entre la lógica de negocio y los requisitos no funcionales, especialmente en temas de seguridad y validación de datos. Tuvimos que analizar cuidadosamente cómo procesos que parecen sencillos desde la perspectiva del usuario implican una complejidad técnica mayor en el backend para garantizar que todas las transacciones se realicen de forma íntegra y sin errores de persistencia.

b. ¿Fue fácil llegar a un consenso?

Sí, logramos alcanzar el consenso de manera eficiente gracias a que mantuvimos una comunicación constante y directa durante toda la sesión. El uso de la técnica de Planning Poker fue clave en este proceso, ya que nos permitió identificar rápidamente los puntos donde nuestras percepciones sobre el esfuerzo diferían, obligándonos a discutir los detalles técnicos de cada historia antes de asignar un valor definitivo.

c. ¿Cómo resolvieron los escenarios donde las estimaciones para la misma historia de usuario no fueron cercanas?

En los casos donde hubo disparidad en las cifras, aplicamos el principio de debate técnico. Cada integrante expuso los argumentos detrás de su elección; por lo general, la estimación más alta se debía a la identificación de riesgos o tareas adicionales, como pruebas de integración o validaciones de seguridad, que el otro integrante no había contemplado. Al final, optamos por la estimación que garantizara una cobertura completa del desarrollo y la calidad del producto, evitando subestimar el trabajo necesario.

