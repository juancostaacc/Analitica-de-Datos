# Metadata — Equipo B · Cobranzas

Datathon Dafiti · Analítica de Datos · 27-10-2026

**Leé este archivo completo antes de tocar el CSV.** Acá está todo: qué significa cada columna,
cuándo se observa, cuánto cuesta cada error y qué puede y qué no puede hacer el área.
Los datos son sintéticos, construidos sobre un problema real del negocio.

---

## 1. El problema

Dafiti vende en cuotas con su propia billetera, Dafiti Pay. Cuando un cliente no paga una cuota
a tiempo entra en mora: hay que gestionarla, el recupero es más caro y una parte no se recupera nunca.

Cobranzas puede **adelantarse al vencimiento**: llamar al cliente unos días antes para recordarle,
ofrecerle pasar a débito automático o reprogramar. Funciona, pero el call center tiene capacidad
limitada y llamar a quien iba a pagar igual es plata tirada y fricción con un buen cliente.

**La pregunta:** de las cuotas que vencen la semana que viene, ¿a cuáles conviene llamar?

## 2. Los archivos

| Archivo | Qué es |
|---|---|
| `cuotas_train.csv` | 6.000 cuotas de las últimas 7 semanas, **ya vencidas y resueltas**, con la columna `mora` |
| `cuotas_holdout.csv` | 2.000 cuotas que vencen entre el 27-10 y el 02-11, **todavía no vencidas**. No tiene `mora`: es lo que hay que predecir |

## 3. Diccionario de datos

La columna **cuándo se observa** es parte del diccionario, no un detalle: dice en qué momento de
la vida de la cuota existe ese dato.

| Columna | Qué es | Cuándo se observa |
|---|---|---|
| `cuota_id` | identificador de la cuota | al generarse la cuota |
| `fecha_vencimiento` | fecha y hora exactas del vencimiento | al generarse la cuota |
| `monto_cuota` | monto a pagar en pesos | al generarse la cuota |
| `plan_cuotas` | plan contratado: 3, 6 o 12 cuotas | al generarse la cuota |
| `cuota_nro` | qué número de cuota es dentro del plan | al generarse la cuota |
| `metodo_pago_configurado` | débito automático, tarjeta manual o transferencia manual | al generarse la cuota |
| `moras_previas` | moras anteriores del cliente | al generarse la cuota |
| `antiguedad_cliente_meses` | meses como cliente | al generarse la cuota |
| `limite_usado_pct` | porcentaje del límite de crédito ya usado | al generarse la cuota |
| `score_bureau` | score crediticio externo, 300 a 850 | al generarse la cuota |
| `ingreso_declarado` | ingreso mensual declarado | al generarse la cuota |
| `edad` | edad del cliente | al generarse la cuota |
| `compras_ultimos_90d` | compras en los últimos 90 días | al generarse la cuota |
| `canal_alta` | por dónde se dio de alta: app, web o sucursal | al generarse la cuota |
| `provincia` | provincia del cliente | al generarse la cuota |
| `recargo_mora_aplicado` | monto del recargo por mora cargado a la cuenta; 0 si no se aplicó | **después del vencimiento** |
| `gestion_cobranza_registrada` | 1 si el equipo de cobranzas registró una gestión sobre esa cuota | **después del vencimiento** |
| `mora` | 1 si la cuota entró en mora. **Solo está en train** | al cierre del caso |

## 4. Las reglas económicas

Llamar antes del vencimiento cuesta plata y evita la mora cuando el cliente efectivamente iba a
caer. El impacto neto por cuota, ya descontado el costo del llamado:

| Decisión | Resultado real | Impacto |
|---|---|---|
| Llamo | Entraba en mora | **+$9.000** |
| Llamo | Pagaba igual | **-$2.000** |
| No llamo | Entraba en mora | $0 |
| No llamo | Pagaba igual | $0 |

El +$9.000 ya promedia la efectividad del llamado: no siempre se evita la mora, y eso está
dentro del número.

**Plata del equipo = 9.000 × (llamados acertados) − 2.000 × (llamados a clientes que pagaban igual).**

## 5. Restricciones de operación

Esto no está en el CSV y cambia el problema:

- El call center puede hacer **150 llamados en toda la semana**. No 150 por día: 150 en total.
- Cobranzas **trabaja la cola por `fecha_vencimiento`, del vencimiento más cercano al más lejano**.
  Si marcan 800 cuotas, se llaman las primeras 150 de esa lista por fecha, no las 150 más riesgosas.
- Las cuotas marcadas que quedan afuera de los 150 no se llaman y no cuestan nada.

## 6. Qué hay que entregar

Un CSV llamado `equipo-b.csv` con las **2.000 filas** del holdout y exactamente estas columnas:

| Columna | Qué va |
|---|---|
| `cuota_id` | el identificador, igual que en el holdout |
| `prob` | la probabilidad de mora que estimó el modelo, entre 0 y 1 |
| `marcar` | 1 si llaman a ese cliente, 0 si no |

Las dos últimas columnas se puntúan por separado: `prob` mide qué tan bien el modelo ordena el
riesgo, `marcar` mide la decisión. Un equipo puede tener un modelo muy bueno y una decisión mala.
