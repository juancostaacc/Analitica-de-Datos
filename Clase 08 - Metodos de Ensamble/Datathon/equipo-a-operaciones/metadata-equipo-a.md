# Metadata — Equipo A · Operaciones

Datathon Dafiti · Analítica de Datos · 27-10-2026

**Leé este archivo completo antes de tocar el CSV.** Acá está todo: qué significa cada columna,
cuándo se observa, cuánto cuesta cada error y qué puede y qué no puede hacer el área.
Los datos son sintéticos, construidos sobre un problema real del negocio.

---

## 1. El problema

Dafiti vende moda online. La moda es el rubro con más devoluciones del e-commerce: el cliente
compra dos talles para quedarse con uno, o compra sin mirar la guía de calce y devuelve.
Cada devolución se come el margen del pedido y a veces más.

Operaciones puede **intervenir antes de despachar**: llamar al cliente para confirmar el talle,
mandarle la guía de calce, sugerirle el cambio a tiempo. Funciona, pero cuesta y no se puede
hacer sobre todos los pedidos.

**La pregunta:** de los pedidos de la semana que viene, ¿sobre cuáles conviene intervenir?

## 2. Los archivos

| Archivo | Qué es |
|---|---|
| `pedidos_train.csv` | 6.000 pedidos de las últimas 7 semanas, **ya entregados**, con la columna `devuelto` |
| `pedidos_holdout.csv` | 2.000 pedidos de la semana del 27-10 al 02-11, **todavía sin despachar**. No tiene `devuelto`: es lo que hay que predecir |

## 3. Diccionario de datos

La columna **cuándo se observa** es parte del diccionario, no un detalle: dice en qué momento de
la vida del pedido existe ese dato.

| Columna | Qué es | Cuándo se observa |
|---|---|---|
| `order_id` | identificador del pedido | al momento del pedido |
| `fecha_pedido` | fecha y hora exactas de la compra | al momento del pedido |
| `categoria` | calzado, jeans, indumentaria, deportivo, accesorios | al momento del pedido |
| `precio` | total del pedido en pesos | al momento del pedido |
| `descuento_pct` | descuento aplicado | al momento del pedido |
| `cantidad_items` | artículos en el pedido | al momento del pedido |
| `mismo_articulo_dos_talles` | 1 si el pedido incluye el mismo artículo en dos talles distintos | al momento del pedido |
| `es_primera_compra` | 1 si es la primera compra del cliente | al momento del pedido |
| `compras_previas` | compras anteriores del cliente | al momento del pedido |
| `devoluciones_previas` | devoluciones anteriores del cliente | al momento del pedido |
| `metodo_pago` | tarjeta, débito, transferencia, billetera | al momento del pedido |
| `canal` | app o web | al momento del pedido |
| `provincia` | destino del envío | al momento del pedido |
| `envio_dias` | días prometidos de entrega | al momento del pedido |
| `rating_producto` | rating promedio del artículo principal | al momento del pedido |
| `cantidad_reviews` | reviews del artículo principal | al momento del pedido |
| `contacto_postventa_7d` | 1 si el cliente escribió a atención en los 7 días posteriores a recibir el pedido | **7 días después de la entrega** |
| `rating_dejado_por_cliente` | puntaje de 1 a 5 que dejó el cliente al producto; 0 si no dejó ninguno | **después de la entrega** |
| `devuelto` | 1 si el pedido terminó en devolución. **Solo está en train** | al cierre del caso |

## 4. Las reglas económicas

Intervenir sobre un pedido cuesta plata y evita una devolución cuando el pedido efectivamente
se iba a devolver. El impacto neto por pedido, ya descontado el costo de intervenir:

| Decisión | Resultado real | Impacto |
|---|---|---|
| Intervengo | Se iba a devolver | **+$9.000** |
| Intervengo | No se iba a devolver | **-$2.000** |
| No intervengo | Se iba a devolver | $0 |
| No intervengo | No se iba a devolver | $0 |

El +$9.000 ya promedia la efectividad de la intervención: no siempre se evita la devolución,
y eso está dentro del número.

**Plata del equipo = 9.000 × (intervenciones acertadas) − 2.000 × (intervenciones sobre pedidos que estaban bien).**

## 5. Restricciones de operación

Esto no está en el CSV y cambia el problema:

- El equipo de atención puede revisar **150 pedidos en toda la semana**. No 150 por día: 150 en total.
- Atención **trabaja la cola por `fecha_pedido`, de más viejo a más nuevo**. Si marcan 800 pedidos,
  se revisan los primeros 150 de esa lista por fecha, no los 150 más riesgosos.
- Los pedidos marcados que quedan afuera de los 150 no se revisan y no cuestan nada.

## 6. Qué hay que entregar

Un CSV llamado `equipo-a.csv` con las **2.000 filas** del holdout y exactamente estas columnas:

| Columna | Qué va |
|---|---|
| `order_id` | el identificador, igual que en el holdout |
| `prob` | la probabilidad de devolución que estimó el modelo, entre 0 y 1 |
| `marcar` | 1 si intervienen sobre ese pedido, 0 si no |

Las dos últimas columnas se puntúan por separado: `prob` mide qué tan bien el modelo ordena el
riesgo, `marcar` mide la decisión. Un equipo puede tener un modelo muy bueno y una decisión mala.
