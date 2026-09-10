# Finanzas Sommos — Operative incomes

## Propósito

Documentar la lógica de ingresos devengados y forecast comercial de Sommos.

Esta referencia pertenece a:

`finanzas-devengo-operativo`

La pestaña principal es:

`Operative incomes`

---

# Principio fundamental

`Operative incomes` representa principalmente:

- ingreso devengado por periodo;
- ingreso programado;
- forecast comercial;
- monto a facturar;
- grants cuando corresponda a la estructura del modelo.

No representa necesariamente:

- cash recibido;
- saldo bancario;
- cobro del mes.

La regla central es:

`Ingreso devengado ≠ Cobro`

---

# Relación con el modelo

La dirección principal es:

`Operative incomes`
→ `CxC Mensual`
→ `Real P&L`

Mientras que:

`Transacciones`
→ cobros reales
→ `CxC Mensual`
→ `Cash Flow`

No invertir estas dependencias.

---

# Fuente de Monto a facturar

En `CxC Mensual`, el:

`Monto a facturar`

debe provenir principalmente de:

`Operative incomes`

Por lo tanto, no calcular el monto a facturar desde los movimientos bancarios.

---

# Fuente de ingresos del P&L

`Real P&L` utiliza `Operative incomes` para sus líneas de ingreso.

Entre las líneas conocidas pueden aparecer:

- Full new integration incomes
- Full Integration monthly maintenance fee
- Proof of concept incomes
- Transactions Fee
- Extra features development income
- Others

La estructura viva del Sheet prevalece.

---

# Clientes y conceptos

`Operative incomes` puede organizar ingresos por:

- cliente;
- proyecto;
- concepto;
- categoría de ingreso;
- mes.

No eliminar una cuenta histórica solo porque un mes tenga valor cero.

---

# Histórico

Los periodos ya ocurridos y reconciliados deben conservar los importes validados.

El histórico hasta agosto de 2026 fue utilizado para reconciliar:

- CxC Mensual;
- Real P&L;
- Cash Flow;
- Balance Sheet.

No modificarlo silenciosamente.

---

# Forecast

Los meses futuros representan expectativas, no cash confirmado.

El forecast puede basarse en:

- contrato;
- mantenimiento recurrente;
- proyecto esperado;
- calendario comercial;
- grant;
- presupuesto aprobado;
- Control financiero vigente.

No inventar crecimiento o nuevos ingresos sin una fuente.

---

# Forecast Sep–Dic 2026

El forecast Sep–Dic 2026 fue reconstruido y validado contra el Control antiguo.

Antes de modificarlo:

1. identificar qué cliente/concepto cambia;
2. identificar el nuevo supuesto;
3. cuantificar el impacto;
4. revisar CxC;
5. revisar P&L;
6. revisar Cash Flow y Runway si es material.

---

# Grants

Los grants deben mantenerse conceptualmente separados del revenue operativo ordinario.

Programas conocidos:

- INNOVATECH
- Startup Perú
- INCOFIN
- FIID Guatemala

No clasificar automáticamente un desembolso como venta.

---

# Programación de grants

Distinguir:

- monto aprobado;
- monto programado;
- monto exigible;
- cobro realizado;
- saldo.

El monto aprobado total no debe convertirse automáticamente en ingreso/devengo del mes.

---

# Startup Perú

Existe un caso validado en el forecast de septiembre de 2026 por aproximadamente:

`USD 934`

Este valor tiene impacto en:

- CxC;
- Cash Flow;
- Balance Sheet;
- Runway.

No eliminarlo sin revisar el modelo completo.

---

# Cobros

Un cobro real debe validarse principalmente desde:

`Transacciones`

El cobro no redefine el periodo de ingreso.

Ejemplo:

Servicio de julio cobrado en agosto:

`Operative incomes julio`
→ ingreso julio

`Transacciones agosto`
→ cash agosto

---

# Vencimientos

El vencimiento puede utilizarse para planificar:

- cobros;
- CxC;
- próximos 30 días.

No determina el periodo del ingreso.

---

# Budget vs Forecast

No confundir:

`Presupuesto`

con:

`Operative incomes`

El presupuesto es una referencia de planificación.

`Operative incomes` puede representar el forecast/actual devengado vivo.

Las diferencias entre ambos son válidas y necesarias para análisis de variaciones.

---

# Nuevos clientes o ingresos

Antes de añadir un nuevo concepto:

- revisar si el cliente ya existe;
- revisar la categoría;
- revisar el mes;
- revisar contrato/soporte;
- revisar si es operativo o financiamiento.

No crear una nueva categoría si puede utilizarse una existente.

---

# Modificación histórica

Si se modifica un mes cerrado:

revisar inmediatamente:

- `CxC Mensual`
- `Real P&L`
- `Cash Flow`
- `Balance Sheet`
- `Dashboard`

No considerar correcto un cambio únicamente porque el total anual no varíe.

---

# QA

Después de modificar:

- releer la celda;
- comprobar cliente;
- comprobar mes;
- comprobar concepto;
- comprobar total mensual;
- comprobar CxC;
- comprobar P&L;
- comprobar checks.

Buscar:

- `#REF!`
- `#VALUE!`
- `#N/A`
- `#DIV/0!`
- `#ERROR!`

---

# Guardrails

- No usar cash como devengo.
- No mover ingresos al mes del cobro.
- No inventar forecast.
- No reconocer todo un grant aprobado de una vez.
- No hardcodear para cuadrar CxC.
- No cambiar históricos cerrados sin revisar impacto.
- No usar presupuesto como sustituto automático del forecast.

---

# Regla final

`Operative incomes` debe responder:

**¿qué ingreso corresponde económicamente a este mes?**

No:

**¿cuánto dinero entró al banco este mes?**
