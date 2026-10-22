---
name: claude-tics
description: Usar antes de entregar cualquier deck, presentación, slides, PPTX, documento o salida visual generada por Claude. Lista los patrones por defecto de Claude (diseño, layout, tipografía y redacción) con qué evitar, con qué reemplazarlo y un ejemplo. Dispara con "deck", "presentación", "slides", "PowerPoint", "pptx", "informe", "one pager", "revisá el diseño", "esto parece hecho por IA".
---

# Los tics de Claude: cómo detectarlos y corregirlos

Claude tiene defaults. Cuando no le decís nada sobre diseño o tono, cae siempre en las mismas decisiones, y el resultado se reconoce a diez metros: barra de color a la izquierda, tres bullets de largo idéntico, "potenciar", em dashes por todos lados.

Esta skill es el catálogo de esos defaults. **Cómo usarla:** antes de mandar un deck o un documento, pasalo por cada tabla. Cada fila es un tic: qué evitar, con qué reemplazarlo y un ejemplo concreto.

**Sobre la marca.** Los tics son universales; los reemplazos dependen de tu sistema visual. Donde dice *tu tipografía de marca*, *tu color de acento* o *tu paleta*, completá con lo que corresponda. Si no tenés un sistema definido, definilo una vez antes de corregir: dos fuentes, tres grises y un acento alcanzan.

---

## 1. Ornamento visual

El patrón de fondo: Claude agrega decoración cuando no tiene nada que decir. Si un elemento no carga información, va afuera.

| # | Evitar | Reemplazar por | Ejemplo |
|---|--------|----------------|---------|
| 1 | **Barra vertical de color en cada slide.** El filete a la izquierda es la firma más reconocible de Claude. | Reservá la barra para la portada o los separadores de sección. Una vez alcanza. | 8 slides de contenido sin barra. Solo la portada la usa. |
| 2 | **Línea o subrayado de acento abajo de cada título.** El segundo tic más común después de la barra. | Ninguna línea. Si necesitás separar, una sola hairline de ancho completo, consistente en todo el deck. | Título, espacio, contenido. Sin el guioncito decorativo. |
| 3 | **Arcos concéntricos, círculos o grillas de puntos como decoración.** Gráficos de relleno sin valor informativo. | Fondo blanco. Agregá un visual solo si carga datos o estructura real. | Reemplazá el fondo decorativo por un gráfico de barras. Si no hay datos, no hay gráfico. |
| 4 | **Gradiente color-a-transparente como fondo de slide.** El lavado de color, o el oscuro que se desvanece. | Rellenos sólidos. Si necesitás un bloque de color, dale un borde definido. | Panel gris claro con borde neto al 30% del ancho. No un gradiente difuso. |
| 5 | **Cortes diagonales o clip-paths** en imágenes y bloques de contenido. Marcos en paralelogramo, bordes biselados. | Recortes rectangulares. El corte diagonal delata la plantilla. | Foto en rectángulo 4x3 al ras del margen. No en marco romboidal. |
| 6 | **Sombras, glows y esquinas redondeadas en todo.** | Rellenos planos, bordes netos, sin sombra. | Un panel plano con borde de 1pt, no una tarjeta flotante con sombra suave. |
| 7 | **Sopa de tarjetas.** Cada idea es un rectángulo redondeado con sombra, muchas veces una tarjeta adentro de otra. | Agrupá con espacio en blanco y alineación. Usá un contenedor solo cuando marca un límite real. | Un mensaje clave es un título más una frase sobre blanco, no un tile con caja. |
| 8 | **Emojis o íconos dentro de círculos como bullets o cabeceras de columna.** Un ícono genérico arriba de cada columna, uno por idea. | Texto plano, o un solo ícono con significado del set de tu marca. | Reemplazá los cinco íconos de cohete, gráfico y lamparita por los cinco números que representan. |
| 9 | **Badges tipo píldora y chips** ("NUEVO", "CLAVE", "PRIORIDAD") como relleno. | Borralos. Si el estado importa, decilo en el texto. | Sacá la píldora "ALTO IMPACTO". Escribí "Es el de mayor impacto en margen". |
| 10 | **Numerales decorativos gigantes ("01 / 02 / 03") o círculos numerados** en slides de agenda y proceso. | Una lista numerada común. Numerales solo cuando la secuencia importa de verdad. | Una agenda en texto de 14pt, no tres números gigantes en contorno. |
| 11 | **Un mismo símbolo repetido como motivo decorativo** en todas las slides: flechas, chevrons, el signo `>` entre conceptos. | Usá el símbolo solo cuando muestra progresión o causalidad real. Una vez por deck. | Un solo `>` en la slide de proceso: "Datos > Modelo > Decisión". En ninguna otra. |
| 12 | **Etiqueta flotante en versalitas arriba del título**, tipo "PERSPECTIVA MACRO \| Q1 FY26" sobre el titular. | Que el titular cargue solo la señal de categoría. Si la etiqueta no agrega información, borrala. | Sacá el "KEY INSIGHT" en mayúsculas. El título "India crece más rápido que el resto" se explica solo. |
| 13 | **Imágenes decorativas o genéricas:** apretones de manos de stock, redes abstractas, arte de gradiente con cara de IA. | Datos reales, capturas del producto, o ninguna imagen. | Reemplazá el globo terráqueo abstracto por un mapa de los mercados que estás analizando. |
| 14 | **Paleta neón sobre azul marino, o acento púrpura/índigo por defecto** cuando nadie pidió una paleta. | Tu paleta de marca. Fondos oscuros solo si el brief lo pide. | Slide blanca, texto negro, un solo color de acento. |

---

## 2. Layout y composición

Claude no elige el layout según el mensaje: aplica el mismo molde a todo.

| # | Evitar | Reemplazar por | Ejemplo |
|---|--------|----------------|---------|
| 15 | **Grilla simétrica de 3 o 4 columnas para toda comparación.** Grilla por reflejo, sin importar cuánto pesa cada parte. | Un 60/40, o un visual dominante más un callout. No todo tiene que pesar igual. | Gráfico grande al 65% más una cifra clave al 35%. No cuatro tiles iguales. |
| 16 | **Columna izquierda en bold más columna derecha de texto en cada slide.** El default rígido de dos columnas. | Variá el layout según el propósito. Para dirección, un visual fuerte gana a una grilla. | Slide de datos: gráfico a ancho completo. Slide narrativa: título más párrafo, sin columnas. |
| 17 | **Una fila de KPI tiles con números gigantes en cada slide.** Cifra enorme, etiqueta mínima, repetido tres o cuatro veces. | Un número grande solo cuando esa cifra *es* el mensaje. Si no, metela dentro de la oración. | Una cifra de 28pt con su frase. No cuatro tiles de "87%", "3.2x", "$4M", "12". |
| 18 | **El mismo layout repetido en todas las slides** (título más tres tarjetas, o título más bullets). | Elegí el layout por mensaje: gráfico, tabla, cita, imagen a sangre, solo texto. | Cinco layouts distintos en un deck de diez slides, cada uno armado para su contenido. |
| 19 | **Elementos fuera de grilla:** márgenes inconsistentes, objetos desalineados, títulos que saltan de posición entre slides. | Un set de márgenes y una posición de título para todo el deck, definidos en el master. | El título siempre en el mismo x/y. El contenido arranca siempre en el mismo borde izquierdo. |
| 20 | **Slides sobrecargadas con texto de 9pt, o texto que se desborda de la caja.** | Un mensaje por slide. Cortá o mandá el detalle al anexo. Nada por debajo de 10pt salvo la línea de fuente. | Partí la slide de 120 palabras en una slide de titular más una tabla de anexo. |
| 21 | **Cajas de texto en lugar de los placeholders del layout**, con lo cual los títulos no son títulos de verdad. | Usá los layouts del master y los placeholders de título. | La vista esquema muestra el título de todas las slides. |
| 22 | **Gráficos con el estilo default de Office:** series arcoíris, 3D, tortas de 6+ porciones, leyenda y data labels diciendo lo mismo. | Máximo 2-3 colores de tu paleta, destacá la serie que importa, etiquetá directo, sin leyenda si ya etiquetaste. | Barras con una sola en color de acento y el resto en gris, valores sobre las barras. |

---

## 3. Estructura y lógica

| # | Evitar | Reemplazar por | Ejemplo |
|---|--------|----------------|---------|
| 23 | **Títulos-etiqueta:** "Panorama de mercado", "Resumen financiero". | Títulos de acción que enuncian la conclusión como oración completa. | "Los ingresos crecieron 12% porque APAC compensó una Europa más débil." |
| 24 | **Títulos con dos puntos:** "Tema: un subtítulo que explica". | Una sola oración. El tema va en el separador de sección. | "El costo de cloud se duplicó en dos años." No "Cloud: evolución de costos". |
| 25 | **Slides de relleno:** "Agenda", "Conclusiones", "Gracias / ¿Preguntas?" puestas por default. | Incluilas solo si la audiencia las necesita. Cerrá en la decisión o el próximo paso. | Última slide: "Decisión requerida: aprobar el piloto antes del 15/11." |
| 26 | **Números sin unidad, período ni fuente.** | Cada cifra lleva unidad, período y fuente al pie. | "Ingresos USD 4.200M, FY26. Fuente: estados contables." |
| 27 | **Falsa precisión:** "37,482%" en un titular. | Redondeá a lo que la decisión necesita. El valor exacto va al anexo. | "Alrededor del 37%." |

---

## 4. Lenguaje y redacción

El tic de copy más caro: Claude suaviza todo para no equivocarse, y la frase termina sin afirmar nada.

| # | Evitar | Reemplazar por | Ejemplo |
|---|--------|----------------|---------|
| 28 | **Fragmentos nominales apilados como títulos:** "Vientos macro. Giro estratégico. Upside claro." Oraciones sin verbo. | Un verbo en cada afirmación importante. El verbo crea responsabilidad. | "Los vientos macro están ampliando la brecha de costos. El giro es urgente." |
| 29 | **Tres bullets del mismo largo en paralelo perfecto.** El tricolon instintivo de Claude. | Usá dos puntos o cuatro. Combiná una frase corta con una más larga que matice. | En vez de 3 bullets de 8 palabras: un titular de 5 palabras más una oración de apoyo de 18. |
| 30 | **Hedging diplomático en cada afirmación:** "podría indicar", "parecería sugerir". Claude sobre-califica para no equivocarse, y eso debilita el análisis. | Afirmá el hallazgo. Si hace falta, la salvedad o la fuente van al final. | No "Los datos podrían sugerir una desaceleración". Escribí "El crecimiento se está desacelerando". |
| 31 | **Frases de arranque:** "Vale la pena notar que...", "Cabe destacar que...". Preámbulo que demora el punto. | Abrí con la afirmación. Borrá el arranque entero. | No "Vale la pena notar que India rinde mejor". Escribí "India rinde mejor que el resto". |
| 32 | **El contraste "no es solo X, es Y" / "no X sino Y".** | Afirmá Y directo. | No "Esto no es un recorte de costos, es una transformación". Escribí "Esto cambia cómo opera la unidad". |
| 33 | **Preguntas retóricas como título o gancho:** "¿Qué significa esto para vos?". | Contestá en el título. | "El cambio de pricing recorta 3 puntos de margen." |
| 34 | **Vocabulario IA:** potenciar, desbloquear, empoderar, seamless, robusto, holístico, ecosistema, navegar, journey, sinergia, game-changer, "en la intersección de", "en el mundo acelerado de hoy". | Verbos comunes: usar, permitir, fuerte, completo, mercado, gestionar. Si igual suena vacío, borrá la oración. | No "Potenciar analítica robusta para desbloquear valor". Escribí "Usar el modelo de forecast para encontrar ahorros". |
| 35 | **Cada bullet como etiqueta en bold más dos puntos más descripción:** "**Eficiencia:** reduce costos". | Oraciones completas, o sacá la etiqueta y que la oración lidere. | "La automatización reduce 20% el costo de procesamiento." |
| 36 | **Mayúscula Inicial En Cada Palabra Del Título.** | Mayúscula solo al inicio de la oración. | "El crecimiento se desacelera en Europa." |
| 37 | **Cierres que se resumen a sí mismos:** "En conclusión", "En resumen", líneas finales que repiten lo recién dicho. | Cortá cuando el punto está hecho, o cerrá en la acción siguiente. | Borrá la última oración del párrafo. |
| 38 | **Intensificadores y adjetivos de relleno:** muy, realmente, significativo, clave, crítico, integral. | Reemplazalos por un número, o borralos. | "Los costos subieron 18%." No "Los costos subieron significativamente". |
| 39 | **Puntuación y mayúsculas inconsistentes entre bullets**, con fragmentos al lado de oraciones completas. | Una regla por lista: o todos fragmentos o todas oraciones, con el mismo cierre. | Todos los bullets son oración completa y terminan en punto. |
| 40 | **Aperturas conversacionales en documentos:** "Buena pregunta", "Vamos a ver", "Acá va la cosa". | Arrancá con el contenido. | Abrí con el hallazgo. |

---

## 5. Tipografía y formato

El tic más fácil de detectar a simple vista, y el más rápido de arreglar.

| # | Evitar | Reemplazar por | Ejemplo |
|---|--------|----------------|---------|
| 41 | **Títulos en M A Y Ú S C U L A S  E S P A C I A D A S** (tracking exagerado usado como recurso de diseño). | Una caja de texto normal, sin tracking. El peso y el tamaño hacen el trabajo. | Título: "Estrategia" en 36pt bold. No "E S T R A T E G I A" en 28pt. |
| 42 | **Mayúsculas sostenidas en cuerpo de texto o etiquetas largas.** | Mayúscula solo al inicio. Reservá las versalitas para siglas cortas. | "Ingresos netos", no "INGRESOS NETOS POR REGIÓN Y SEGMENTO". |
| 43 | **Tipografía del sistema (Calibri, Arial) como fuente principal.** Claude no tiene acceso a fuentes licenciadas y cae al default del sistema. | Aplicá a mano la tipografía de tu marca al abrir el archivo: una para cuerpo, otra para subtítulos. | Al recibir cualquier PPTX de Claude: seleccionar todo y cambiar a tu fuente de cuerpo en 11pt. |
| 44 | **Mismo cuerpo tipográfico en título, subtítulo y texto.** Claude pone 14-16pt en todo, sin jerarquía real. | Título 36pt bold. Subtítulo 24pt en tu fuente de subtítulos. Cuerpo 11-14pt regular. | Slide ejecutiva: titular 36pt negro, cifra clave 28pt en color de acento, nota al pie 8pt gris. |
| 45 | **Texto centrado** en títulos y subtítulos de slides de contenido. Claude centra cuando no se le especifica alineación. | Alineá todo el texto de contenido a la izquierda, sin excepciones. | Título "Perspectiva macro APAC" alineado a izquierda con margen de 0,9 cm. |
| 46 | **Negro pleno (#000000) en todo el texto.** Claude no separa el negro del título del gris oscuro del cuerpo. | Títulos en negro pleno. Cuerpo en gris oscuro (#4A4A4A). Notas al pie en gris claro (#96968C). | Tres niveles visibles: titular negro, texto de análisis #4A4A4A, fuente y fecha #96968C. |
| 47 | **Interlineado uniforme, simple o doble.** Claude no calibra el espaciado según el tipo de contenido. | Cuerpo ejecutivo: 1,2-1,3x. Bloques de datos o bullets: 1,0-1,1x. Nunca doble. | Párrafo de insight con interlineado 1,25. Lista de ítems en 1,05: denso pero no asfixiante. |
| 48 | **Bold a mitad de párrafo en exceso**, resaltando cada segunda o tercera oración. | El bold se reserva para un término por párrafo, y solo si es verdaderamente crítico. | Reescribí: "Los costos suben. El margen cae. El timing es la variable que importa." |
| 49 | **Subrayado, itálica y bold apilados para enfatizar**, o subrayado en algo que no es un link. | Un solo recurso de énfasis, usado con moderación. Bold únicamente (ver tic 48). | Un solo término en bold. |
| 50 | **Em dashes como bullets y como recurso de ritmo en prosa.** "— Punto uno — Punto dos", o "Los costos subieron — el margen cayó". Efecto premium falso. | Bullets estándar o lista numerada. En prosa, punto, coma o paréntesis. | "Los costos subieron y el margen cayó." No "Los costos subieron — el margen cayó". |
| 51 | **Texto justificado y saltos de línea manuales** que generan ríos y líneas huérfanas. | Alineado a izquierda, bandera derecha, que la caja ajuste sola. | Sacá los enters manuales dentro de los párrafos. |
| 52 | **Gris de bajo contraste sobre fondos tintados**, o blanco sobre un acento de tono medio en tamaños chicos. | Verificá contraste (WCAG AA, 4.5:1 para cuerpo). | #4A4A4A sobre blanco, no #96968C sobre gris claro. |
| 53 | **Autofit achicando el texto** para que entre en una caja sobrecargada. | Redimensioná el contenido, no la fuente. | Cortá texto hasta que entre en 11pt o más. |
| 54 | **Estilo de tabla por default:** líneas pesadas, cabeceras con bandas de colores, números centrados, decimales mezclados. | Solo reglas horizontales livianas, números alineados a derecha, mismos decimales por columna, unidades en la cabecera. | Columna alineada a derecha con 1 decimal en todas las filas. |
| 55 | **Valores de color inconsistentes:** varios grises y varios acentos casi idénticos. | Definí la paleta una vez y elegí solo de ahí. | Un acento, negro, #4A4A4A, #96968C, blanco. Nada más. |
| 56 | **Títulos que ocupan 3 líneas o más.** | Ajustalo a dos líneas máximo. | Cortá la cláusula de preámbulo. |

---

## 6. Higiene del archivo

| # | Evitar | Reemplazar por | Ejemplo |
|---|--------|----------------|---------|
| 57 | **Imágenes estiradas o deformadas** para llenar un marco. | Bloqueá la relación de aspecto y recortá. | Recortá a 4x3, no la aplastes. |
| 58 | **Sin texto alternativo y sin notas del orador.** | Alt text en cada imagen con información, y el guion de lo que vas a decir en las notas. | Alt text del gráfico: "Barras de ingresos por región, FY24-FY26". |
| 59 | **Metadata default y placeholders olvidados** ("Haga clic para agregar título", lorem ipsum, autor "python-pptx"). | Limpiá las propiedades del archivo y borrá los placeholders vacíos antes de mandarlo. | Revisá Archivo > Información y el panel de selección. |

---

## Checklist antes de mandar

1. Seleccioná todo, aplicá la tipografía de tu marca, verificá la jerarquía 36 / 24 / 11-14pt, alineá todo a izquierda.
2. Buscá `—`, `>`, "no es solo", "potenciar", "desbloquear", "vale la pena notar", "podría sugerir". Cada aparición necesita una razón para quedarse.
3. Contá barras laterales, tarjetas, tiles e íconos. Más de uno de cualquiera es un tic.
4. Leé solo los títulos en vista esquema. Tienen que contar la historia como oraciones completas.
5. Confirmá que cada cifra tiene unidad, período y fuente.
