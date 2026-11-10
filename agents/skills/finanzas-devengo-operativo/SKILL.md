---
name: finanzas-devengo-operativo
description: Gestiona y audita el devengo operativo mensual de Sommos mediante Operative incomes, Real S&A y Sueldos 2026, separando correctamente reconocimiento contable de cobros y pagos bancarios.
---

# Finanzas Sommos — Devengo Operativo

## Propósito

Gestionar la capa de devengo del workflow financiero de Sommos.

Esta skill determina principalmente:

- qué ingresos corresponden a cada periodo;
- qué gastos operativos corresponden a cada periodo;
- qué salarios corresponden a cada periodo;
- qué valores deben alimentar CxC y CxP;
- qué valores deben alimentar Real P&L;
- cómo mantener histórico y forecast consistentes.

Esta skill opera principalmente sobre:

- `Operative incomes`
- `Real S&A`
- `Sueldos 2026`

---

# Principio fundamental

El modelo financiero de Sommos utiliza contabilidad por devengo.

Por lo tanto:

**el mes del ingreso o gasto no depende necesariamente del mes en que entra o sale el dinero del banco.**

Separar siempre:

`Devengo`
vs
`Cash`

## Ingresos

`Operative incomes`
→ define el ingreso del periodo

`Transacciones`
→ confirma el cobro

## Gastos

`Real S&A`
→ define el gasto del periodo

`Transacciones`
→ confirma el pago

## Sueldos

`Sueldos 2026`
→ define el gasto salarial del periodo

`CxP Sueldos`
→ controla obligación, adelantos, pagos y saldo

Nunca mover automáticamente un devengo al mes del cash.

---

# Archivo principal

Google Sheet:

`Finanzas Sommos — Workflow y Control V2.0`

Spreadsheet ID:

`1z0ON-50Ps3V9AYACSZxVBe6sNuAuYxE4qwrV2N5tQZY`

URL:

`https://docs.google.com/spreadsheets/d/1z0ON-50Ps3V9AYACSZxVBe6sNuAuYxE4qwrV2N5tQZY/edit`

Antes de cualquier modificación:

1. leer la estructura viva;
2. identificar el periodo;
3. leer fórmulas y valores actuales;
4. revisar histórico vs forecast;
5. revisar dependencias en CxC/CxP y P&L;
6. comparar contra documentos fuente cuando corresponda.

Nunca asumir filas o columnas por memoria.

---

# Pestañas principales

Esta skill opera principalmente:

- `Operative incomes`
- `Real S&A`
- `Sueldos 2026`

Debe consultar cuando corresponda:

- `Transacciones`
- `CxC Mensual`
- `CxP Mensual`
- `CxP Sueldos`
- `Real P&L`
- `Presupuesto`
- `Config`
- `Reglas categorización`

Puede validar impacto posterior en:

- `Cash Flow`
- `Balance Sheet`
- `Runway Mensual`
- `Dashboard`

---

# Arquitectura del devengo

La dirección correcta del modelo es:

`Operative incomes`
→ `CxC Mensual`
→ `Real P&L`

`Real S&A`
→ `CxP Mensual`
→ `Real P&L`

`Sueldos 2026`
→ `CxP Sueldos`
→ `Real P&L`

No invertir estas dependencias.

Por ejemplo:

no calcular el gasto de `Real S&A` desde el pago de `CxP`.

---

# Operative incomes

## Propósito

`Operative incomes` representa el ingreso devengado o programado por:

- cliente;
- concepto;
- periodo.

No representa necesariamente cash recibido.

---

# Fuente de CxC operativa

El valor de:

`Monto a facturar`

en `CxC Mensual`

debe provenir principalmente de:

`Operative incomes`

Por lo tanto:

`Ingreso devengado ≠ Cobro`

---

# Fuente de P&L

Las líneas de ingresos operativos de `Real P&L` se alimentan desde `Operative incomes`.

Entre las líneas conocidas pueden encontrarse:

- Full new integration incomes
- Full Integration monthly maintenance fee
- Proof of concept incomes
- Transactions Fee
- Extra features development income
- Others

La estructura viva prevalece.

---

# Clientes conocidos

Entre los clientes/proyectos históricos pueden aparecer:

- Banco Sol
- BCP Perú
- BCP Perú + Habitat
- Rendinero
- LARA
- Leads Quiero BCP
- Prima
- otros clientes vigentes

No eliminar clientes históricos únicamente porque un mes sea cero.

---

# Grants

`Operative incomes` puede contener también un bloque separado de grants u otros ingresos extraordinarios según la estructura viva.

Los grants deben mantenerse separados conceptualmente de ingresos operativos ordinarios.

Programas conocidos:

- INNOVATECH
- Startup Perú
- INCOFIN
- FIID Guatemala

No mover un grant a revenue operativo solamente porque exista un cobro.

---

# Forecast de ingresos

Los meses futuros deben reflejar el mejor forecast aprobado disponible.

No reemplazar el forecast automáticamente con:

- cash recibido;
- facturas históricas;
- extrapolaciones inventadas.

Cuando exista un Control antiguo o presupuesto validado como fuente:

preservar su lógica hasta que exista una nueva decisión explícita.

---

# Real S&A

## Propósito

`Real S&A` representa el gasto operativo devengado por:

- proveedor;
- concepto;
- categoría;
- periodo.

No representa necesariamente el pago bancario del mes.

---

# Fuente de CxP

El valor:

`Monto a pagar`

en `CxP Mensual`

debe provenir principalmente de:

`Real S&A`

Conceptualmente:

`Real S&A = obligación/gasto del periodo`

`Transacciones = pago`

---

# Fuente de P&L

Las categorías de `Real S&A` alimentan las líneas correspondientes de `Real P&L`.

Entre conceptos conocidos pueden aparecer:

- Platform cost
- Softwares for development
- RH expenses
- Administrative expenses
- Sales expenses
- Product expenses
- Startup Chile
- Bank fees
- Travel
- Innovatech
- Contingency
- Marketing services
- Outsourced services
- Taxes
- otros conceptos vigentes

No inventar categorías.

---

# Proveedores recurrentes

Pueden existir gastos recurrentes como:

- PPO
- Big Picture
- Ronny - Sommos
- Caja Nacional de Salud
- Gestora
- ChatGPT
- Microsoft
- Anthropic / Claude
- GitHub
- Google Cloud
- Google Workspace
- Udemy
- impuestos;
- marketing;
- viajes.

La recurrencia no significa que el importe deba copiarse automáticamente de un mes a otro.

Usar:

- contrato;
- factura;
- forecast aprobado;
- histórico validado;
- instrucción explícita.

---

# PPO

PPO puede tener facturas individuales por periodo aunque el pago bancario sea consolidado.

El gasto debe reconocerse en el periodo de cada factura.

No mover todas las facturas al mes del pago.

Preservar:

- fecha documental;
- importe;
- periodo;
- soporte.

---

# Big Picture

Big Picture corresponde históricamente a:

`Outsourced services`

No cambiar de categoría únicamente por el nombre del proveedor.

---

# Endeavor

Existe una clasificación histórica validada:

`Endeavor → Outsourced services`

Mantener mientras no exista evidencia de un cambio en la naturaleza del gasto.

---

# Cutoff

El devengo puede diferir del momento de cash por reglas de cierre.

Caso conocido:

Figma en agosto de 2026.

Existió movimiento bancario, pero la lógica histórica mantuvo la obligación abierta.

No utilizar el banco como única fuente para decidir el cutoff.

---

# Impuestos y partidas contables

Conceptos como:

- IVA Sommos;
- IT Sommos;
- Exchange rate differences;
- intereses;

pueden requerir lógica contable distinta del cash bancario.

No reemplazar automáticamente el devengo con el monto pagado.

---

# Sueldos 2026

## Propósito

`Sueldos 2026` es el maestro y planificación salarial del modelo.

Determina principalmente:

- persona;
- área;
- cargo;
- concepto salarial;
- gasto mensual;
- forecast de nómina.

---

# Fuente de P&L salarial

Las líneas de salarios del P&L deben provenir de `Sueldos 2026`.

Entre los conceptos conocidos:

- IT salaries
- Operative salaries
- Finance Salary
- RH Salary
- Sales salaries

La denominación viva del Sheet prevalece.

---

# Fuente de CxP Sueldos

El devengo mensual de nómina alimenta:

`CxP Sueldos`

Luego:

- adelantos;
- pagos;
- saldos;

se controlan allí.

No utilizar CxP Sueldos para redefinir retroactivamente el gasto salarial.

---

# Personas y estructura

`Sueldos 2026` puede contener:

- Área
- Cargo
- Nombre
- Concepto
- meses
- otros campos administrativos

No cambiar nombres, cargos o conceptos históricos sin revisar su efecto en:

- CxP Sueldos;
- P&L;
- presupuesto.

---

# Precisión

Preservar decimales exactos cuando existan.

No redondear valores fuente únicamente porque visualmente se muestran sin decimales.

La precisión es especialmente importante porque:

`Sueldos 2026`
→ `CxP Sueldos`
→ `Balance Sheet`
→ `Cash Flow`

Una diferencia pequeña puede propagarse por todo el modelo.

---

# Histórico vs Forecast

Distinguir siempre:

## Histórico

Periodo ya ocurrido y validado.

Debe sustentarse en:

- documentación;
- Control antiguo;
- registros aprobados.

## Forecast

Periodo futuro.

Debe sustentarse en:

- presupuesto;
- contratos;
- planificación;
- estimación aprobada.

No reemplazar históricos con forecast ni viceversa.

---

# Histórico reconciliado 2026

Los meses históricos utilizados en el nuevo modelo fueron reconciliados contra el Control antiguo.

Especialmente:

- `Operative incomes`;
- `Real S&A`;
- `Sueldos 2026`;

tienen valores que alimentan estados ya validados.

No modificar meses cerrados automáticamente.

---

# Forecast Sep–Dic 2026

El forecast Sep–Dic fue reconstruido utilizando la lógica y valores del Control antiguo.

Cambiar estos valores puede afectar:

- CxC;
- CxP;
- P&L;
- Cash Flow;
- Balance Sheet;
- Runway.

Antes de modificar forecast:

identificar explícitamente si el usuario desea:

- actualizar una expectativa;
- reemplazar un contrato;
- agregar/quitar personal;
- modificar un gasto;
- modificar un ingreso.

---

# Presupuesto vs Forecast

No confundir:

`Presupuesto`

con:

`Forecast`

El presupuesto representa una referencia/plan aprobado.

`Operative incomes`, `Real S&A` y `Sueldos 2026` pueden representar el forecast vivo.

Las diferencias entre ambos son precisamente lo que permite analizar:

`Budget vs Actual / Forecast`

No cambiar el devengo únicamente para coincidir con presupuesto.

---

# Relación con Transacciones

`Transacciones` puede servir para validar:

- que un cliente pagó;
- que un proveedor fue pagado;
- que un sueldo salió del banco.

Pero no debe utilizarse automáticamente para cambiar el periodo del ingreso/gasto.

Ejemplo:

factura de julio pagada en agosto:

`Real S&A julio`
→ gasto julio

`Transacciones agosto`
→ cash agosto

---

# Relación con CxC

`Operative incomes`
→ Monto a facturar

`Transacciones`
→ Cobro

`CxC Mensual`
→ Saldo

---

# Relación con CxP

`Real S&A`
→ Monto a pagar

`Transacciones`
→ Pago

`CxP Mensual`
→ Saldo

---

# Relación con CxP Sueldos

`Sueldos 2026`
→ sueldo devengado

`CxP Sueldos`
→ pago / adelanto / saldo

---

# Relación con Real P&L

Esta skill contiene las principales fuentes operativas del P&L.

Por lo tanto, cualquier modificación material debe revisarse posteriormente en:

`Real P&L`

Especialmente:

- Operative incomes
- S&A
- salaries
- EBITDA
- EBIT
- Net Revenue

---

# No hardcodear para cuadrar

Nunca modificar:

- ingresos;
- gastos;
- salarios;

únicamente para:

- hacer cuadrar CxC;
- hacer cuadrar CxP;
- eliminar una diferencia de Balance;
- conseguir un Cash Flow esperado.

La cifra debe representar el devengo correcto.

---

# Validaciones antes de modificar Operative incomes

- [ ] Leer cliente/concepto.
- [ ] Identificar mes.
- [ ] Revisar valor actual.
- [ ] Revisar fuente/documentación.
- [ ] Revisar CxC relacionada.
- [ ] Revisar P&L.
- [ ] Distinguir histórico vs forecast.

---

# Validaciones antes de modificar Real S&A

- [ ] Identificar proveedor/concepto.
- [ ] Identificar categoría.
- [ ] Identificar mes.
- [ ] Revisar factura/forecast.
- [ ] Revisar CxP.
- [ ] Revisar P&L.
- [ ] Revisar cutoff.
- [ ] Distinguir histórico vs forecast.

---

# Validaciones antes de modificar Sueldos 2026

- [ ] Identificar persona.
- [ ] Revisar área.
- [ ] Revisar cargo.
- [ ] Revisar concepto salarial.
- [ ] Revisar mes.
- [ ] Revisar CxP Sueldos.
- [ ] Revisar P&L.
- [ ] Preservar precisión.

---

# QA posterior

Después de modificar el devengo:

1. releer exactamente las celdas modificadas;
2. comprobar que fórmulas dependientes recalcularon;
3. revisar `CxC Mensual` o `CxP Mensual`;
4. revisar `CxP Sueldos` cuando aplique;
5. revisar `Real P&L`;
6. comprobar que no existan errores.

Buscar:

- `#REF!`
- `#VALUE!`
- `#N/A`
- `#DIV/0!`
- `#ERROR!`

Cuando el cambio sea material, revisar además:

- `Cash Flow`
- `Balance Sheet`
- `Dashboard`

---

# Guardrails

- No confundir devengo con cash.
- No mover ingresos al mes del cobro.
- No mover gastos al mes del pago.
- No modificar salarios desde una salida bancaria.
- No inventar forecast.
- No inventar proveedores/clientes.
- No inventar categorías.
- No cambiar históricos cerrados silenciosamente.
- No redondear prematuramente.
- No hardcodear para cuadrar estados.
- No reemplazar documentación por inferencia si existe una fuente mejor.

---

# Regla de finalización

Una modificación de devengo solamente se considera terminada cuando:

- la fuente es correcta;
- el periodo es correcto;
- el importe es correcto;
- CxC/CxP responde correctamente;
- P&L responde correctamente;
- las celdas fueron releídas;
- no se introdujeron errores.

Nunca decir “listo” únicamente porque se ejecutó una escritura.

---

# Coordinación con otras skills

## `finanzas-config-categorizacion`

Usar para:

- categorías;
- catálogos;
- taxonomía.

## `finanzas-transacciones-tc`

Usar para:

- cash;
- extractos;
- pagos;
- cobros;
- TC.

## `finanzas-cxc-cxp`

Usar para:

- saldos CxC;
- saldos CxP;
- CxP Sueldos;
- vencimientos;
- liquidaciones.

## `finanzas-estados-financieros`

Usar para:

- Real P&L;
- Cash Flow;
- Balance Sheet.

## `finanzas-presupuesto-vs`

Usar para:

- Budget vs P&L;
- análisis de variaciones.

## `finanzas-cierre-mensual`

Usar para:

- validar el devengo como parte del cierre.

---

# Referencias

Consultar cuando corresponda:

- `references/operative-incomes.md`
- `references/real-sa.md`
- `references/sueldos.md`

---

# Alcance final

Esta skill debe responder principalmente:

**¿qué ingreso y qué gasto corresponde realmente a cada mes?**

No:

**¿cuándo entró o salió el dinero?**

Esa diferencia es la base del modelo financiero de Sommos.
