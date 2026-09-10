# Finanzas Sommos — Sueldos 2026

## Propósito

Documentar la lógica de nómina utilizada por el modelo financiero de Sommos.

Esta referencia pertenece a:

`finanzas-devengo-operativo`

La pestaña principal es:

`Sueldos 2026`

La vista de obligación relacionada es:

`CxP Sueldos`

---

# Principio fundamental

El gasto salarial y el pago de nómina son eventos distintos.

La lógica es:

`Sueldos 2026`
→ gasto/devengo

`CxP Sueldos`
→ obligación / adelantos / pagos / saldo

`Transacciones`
→ evidencia bancaria cuando corresponda

No reconocer nuevamente el gasto cuando se realiza el pago.

---

# Propósito de Sueldos 2026

La pestaña funciona como maestro y planificación de nómina.

Puede contener:

- Concepto
- Área
- Cargo
- Nombre
- valores por mes

La estructura viva prevalece.

---

# Conceptos salariales

Entre las clasificaciones utilizadas por el P&L pueden aparecer:

- IT salaries
- Operative salaries
- Finance Salary
- RH Salary
- Sales salaries

No modificar estos textos sin revisar las fórmulas del P&L.

---

# Área y cargo

Área y Cargo tienen funciones distintas.

Ejemplos de áreas pueden incluir:

- Technology
- Operations
- Finance
- Human Resources
- Sales

Los nombres exactos deben seguir el Sheet vivo.

No crear áreas nuevas para corregir una clasificación salarial sin revisar primero la estructura.

---

# Nombres y personas

Cada persona debe conservar una identificación consistente entre:

- `Sueldos 2026`
- `CxP Sueldos`

Antes de renombrar una persona:

1. revisar ambas pestañas;
2. revisar fórmulas;
3. revisar P&L;
4. revisar histórico.

No crear duplicados por pequeñas diferencias de nombre.

---

# Devengo mensual

El valor de cada mes representa el gasto salarial correspondiente a ese periodo.

No debe depender automáticamente de la fecha en que se realizó el pago.

Ejemplo:

sueldo de agosto pagado en septiembre:

`Sueldos 2026 agosto`
→ gasto agosto

`CxP Sueldos`
→ saldo agosto

`Pago septiembre`
→ liquidación de obligación

---

# CxP Sueldos

El devengo de `Sueldos 2026` alimenta la obligación de nómina.

Conceptualmente:

`Saldo final = Saldo inicial + Sueldo devengado - Adelantos - Pagos`

La fórmula exacta debe seguir la estructura viva.

---

# Adelantos

Un adelanto salarial:

- no crea un segundo gasto;
- representa cash entregado anticipadamente;
- reduce la obligación correspondiente según la lógica vigente.

No sumar:

`Sueldo + Adelanto`

como si ambos fueran gasto.

---

# Pagos

Los pagos deben liquidar la obligación.

No modificar el gasto de `Sueldos 2026` para que coincida con el monto bancario pagado.

---

# Precisión

Mantener los decimales fuente.

No redondear prematuramente los pagos o valores del modelo.

La precisión es importante porque:

`CxP Sueldos`
→ `Balance Sheet`
→ `Cash Flow`

Pequeñas diferencias pueden propagarse.

---

# Histórico reconciliado

`CxP Sueldos` fue reconciliado contra:

`Accounts P TH`

del Control antiguo.

La nómina de `Sueldos 2026` fue ajustada para preservar los valores históricos y forecast utilizados por ese modelo.

No modificar periodos cerrados sin revisar esa reconciliación.

---

# Forecast salarial

Los meses futuros pueden cambiar por:

- contratación;
- salida de personal;
- cambio salarial;
- bono;
- cambio de rol;
- presupuesto aprobado.

No extrapolar automáticamente sin una fuente.

---

# Modificación de persona

Cuando exista:

- alta;
- baja;
- cambio salarial;
- cambio de área;
- cambio de cargo;

identificar desde qué mes aplica.

No modificar meses anteriores salvo que el cambio sea retroactivo y esté explícitamente documentado.

---

# Relación con P&L

`Sueldos 2026` alimenta las categorías salariales de:

`Real P&L`

Después de cualquier cambio:

comprobar que el importe aparezca en la línea correcta.

---

# Relación con CxP Sueldos

Después de modificar sueldo/devengo:

revisar:

- Sueldos por pagar
- Adelantos
- Sueldos pagados
- Cuenta por pagar Sueldos
- Neto gastado mes

---

# Relación con Balance Sheet

El saldo pendiente de CxP Sueldos alimenta pasivos.

No introducir ajustes manuales paralelos en Balance Sheet si el saldo correcto puede venir directamente de CxP Sueldos.

---

# Relación con Cash Flow

El Cash Flow debe reconocer la liquidación/variación de CxP Sueldos sin volver a reconocer el gasto.

No construir cash salarial únicamente desde la línea de gasto del P&L.

---

# Relación con presupuesto

La nómina puede compararse con presupuesto.

Pero:

`Budget ≠ Devengo`

No modificar Sueldos 2026 simplemente para llevar la variación presupuestaria a cero.

---

# QA antes de modificar

Comprobar:

- persona;
- concepto;
- área;
- cargo;
- mes;
- importe actual;
- fuente del cambio;
- CxP Sueldos relacionada.

---

# QA después de modificar

Revisar:

- `Sueldos 2026`;
- `CxP Sueldos`;
- `Real P&L`;
- `Balance Sheet`;
- `Cash Flow` cuando corresponda.

Buscar:

- `#REF!`
- `#VALUE!`
- `#N/A`
- `#DIV/0!`
- `#ERROR!`

---

# Guardrails

- No usar pago bancario como gasto salarial.
- No duplicar personas.
- No inventar salarios.
- No inventar fecha de alta/baja.
- No redondear prematuramente.
- No modificar periodos históricos sin revisión.
- No sumar adelantos como gasto adicional.
- No hardcodear el Balance para corregir una diferencia de nómina.

---

# Regla final

La nómina debe permitir responder separadamente:

1. ¿cuánto sueldo se devengó?
2. ¿cuánto se adelantó?
3. ¿cuánto se pagó?
4. ¿cuánto queda por pagar?

Esas cuatro cifras no deben confundirse.
