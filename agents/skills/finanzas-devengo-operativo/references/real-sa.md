# Finanzas Sommos — Real S&A

## Propósito

Documentar la lógica de gastos operativos devengados de Sommos.

Esta referencia pertenece a:

`finanzas-devengo-operativo`

La pestaña principal es:

`Real S&A`

---

# Principio fundamental

`Real S&A` representa principalmente:

- gasto devengado;
- obligación económica del periodo;
- forecast de gastos operativos;
- fuente del monto a pagar de CxP.

No representa necesariamente:

- cash pagado;
- salida bancaria;
- fecha real de liquidación.

La regla central es:

`Gasto devengado ≠ Pago`

---

# Relación con el modelo

La dirección principal es:

`Real S&A`
→ `CxP Mensual`
→ `Real P&L`

Mientras que:

`Transacciones`
→ pago real
→ `CxP Mensual`
→ `Cash Flow`

No construir Real S&A desde los movimientos de banco.

---

# Fuente de Monto a pagar

En `CxP Mensual`:

`Monto a pagar`

debe provenir principalmente de:

`Real S&A`

Conceptualmente:

`Real S&A = gasto/obligación del periodo`

`Transacciones = liquidación`

---

# Fuente de P&L

Las categorías de Real S&A alimentan las líneas correspondientes de `Real P&L`.

Entre las categorías/conceptos conocidos pueden aparecer:

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

La estructura viva prevalece.

---

# Histórico

Los periodos históricos fueron reconciliados contra el Control antiguo.

No sobrescribir valores cerrados únicamente porque:

- el pago ocurrió en otro mes;
- una fórmula nueva parece más sencilla;
- existe una diferencia menor de redondeo.

---

# Forecast

Los meses futuros pueden basarse en:

- contratos;
- gastos recurrentes;
- servicios;
- obligaciones fiscales;
- forecast aprobado;
- Control financiero.

No asumir automáticamente que el importe de un mes se repite en todos los futuros.

---

# Proveedores recurrentes

Pueden existir proveedores como:

- PPO
- Big Picture
- Ronny - Sommos
- Caja Nacional de Salud
- Gestora
- ChatGPT
- Microsoft
- Anthropic / Claude
- GitHub
- Google Workspace
- Google Cloud
- Udemy
- Freepik

El proveedor identifica la contraparte.

La categoría identifica la naturaleza económica.

No crear una categoría por proveedor si ya existe una categoría económica correcta.

---

# PPO

PPO puede tener facturas mensuales individuales que se pagan juntas.

El devengo debe seguir cada factura.

Preservar:

- fecha de factura;
- periodo;
- importe;
- moneda;
- detalle documental.

No mover todas las facturas al mes del pago consolidado.

---

# Big Picture

Históricamente se utiliza:

`Outsourced services`

cuando corresponde a servicios tercerizados.

---

# Endeavor

Clasificación validada:

`Endeavor → Outsourced services`

No cambiar automáticamente a otra categoría sin evidencia.

---

# Innovatech

Distinguir:

## Gasto relacionado con proyecto/programa

Puede corresponder a:

`Innovatech`

## Desembolso recibido del programa

Corresponde a financiamiento/grant y no a este gasto.

No mezclar ambos por compartir nombre.

---

# Figma y cutoff

Existe un caso histórico donde el cash bancario y el saldo de CxP no siguen una correspondencia simple en el mismo mes.

Esto demuestra que:

`movimiento bancario ≠ necesariamente liquidación contable del mismo periodo`

Antes de modificar cutoff:

- revisar Control antiguo;
- revisar factura;
- revisar fecha de cierre;
- revisar CxP.

---

# Impuestos

Partidas como:

- IVA Sommos
- IT Sommos

pueden tener:

- devengo;
- pago;
- saldo;

en meses diferentes.

No utilizar el importe bancario como gasto automático.

---

# Exchange rate differences

Las diferencias de cambio pueden ser:

- contables;
- no cash;
- derivadas de valuación.

No exigir una transacción bancaria uno-a-uno.

---

# Bank fees

Pueden existir diferencias históricas entre el gasto contable y una transacción identificable de forma limpia.

No inventar movimientos para justificar el importe.

Preservar la lógica validada cuando exista soporte histórico.

---

# Capitalización

Los gastos que eventualmente se capitalicen en el modelo no deben alterarse en Real S&A únicamente porque exista una línea de capitalización en el P&L.

La reclasificación contable posterior pertenece a los estados financieros.

---

# Histórico vs pago

Ejemplo conceptual:

Factura julio → USD 500

Pago agosto → USD 500

Correcto:

`Real S&A julio = 500`

`CxP julio += 500`

`Transacciones agosto = pago`

No mover Real S&A a agosto.

---

# Modificación del forecast

Antes de modificar un gasto futuro:

1. identificar proveedor/concepto;
2. identificar categoría;
3. revisar fuente;
4. identificar periodo;
5. revisar CxP;
6. revisar P&L;
7. revisar Runway si es material.

---

# Relación con presupuesto

`Real S&A` no debe modificarse únicamente para coincidir con:

`Presupuesto`

El presupuesto sirve como benchmark.

El devengo/forecast vivo puede diferir.

---

# QA

Después de modificar Real S&A:

- releer la celda;
- comprobar proveedor;
- comprobar categoría;
- comprobar mes;
- comprobar total;
- comprobar `CxP Mensual`;
- comprobar `Real P&L`.

Si el cambio es material:

- revisar Cash Flow;
- Balance Sheet;
- Runway;
- Dashboard.

Buscar:

- `#REF!`
- `#VALUE!`
- `#N/A`
- `#DIV/0!`
- `#ERROR!`

---

# Guardrails

- No usar cash como gasto devengado.
- No mover gastos al mes del pago.
- No inventar recurrencias.
- No duplicar proveedores/categorías.
- No borrar excepciones de cutoff sin entenderlas.
- No modificar históricos cerrados silenciosamente.
- No utilizar Real S&A para hacer cuadrar el Balance.
- No inventar partidas contables para eliminar diferencias.

---

# Regla final

`Real S&A` debe responder:

**¿qué gasto corresponde económicamente a este periodo?**

El banco responde otra pregunta:

**¿cuándo se pagó?**
