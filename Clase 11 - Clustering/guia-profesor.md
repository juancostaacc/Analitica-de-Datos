# Guía del profesor — Clase 11: Clustering (distribuidor mayorista)

Material para el profesor, no se reparte. Todos los números salen de correr `practica11.ipynb` con `random_state=42`.

## Idea de la clase

No es una clase de código. Es una clase de **tres decisiones que toma el curso entero en el pizarrón**: cuántos grupos (K), cómo se llama cada grupo (arquetipos) y qué hacemos con US$ 600.000 de presupuesto. El notebook va proyectado y corre los números; el pizarrón es donde se decide. Cada decisión vuelve al notebook para validarse.

Tiempo orientativo: secciones 1 a 3 (20 min, la 3 es la más densa), sección 4 con pizarrón 1 (15 min), sección 5 con pizarrón 2 (15 min), sección 6 con pizarrón 3 (10 min), sección 7 con pizarrón 4 (20 min), cierre (5 min).

## El dataset

[Wholesale Customers](https://archive.ics.uci.edu/dataset/292/wholesale+customers), UCI (Cardoso, 2013, CC BY 4.0): 440 clientes reales de un distribuidor mayorista de Portugal. Sin nulos. Las columnas se tradujeron al español y `Channel`/`Region` se pasaron a texto (1 = Horeca / 2 = Retail; 1 = Lisboa / 2 = Oporto / 3 = Otra). El dataset no aclara la moneda (dice "unidades monetarias"); en el notebook se expresa en dólares para simplificar. Es un caso real pero **no argentino**: conviene decirlo y aclarar que el problema es el mismo en cualquier distribuidor de acá.

Lo que hace especial a este dataset es que es **real y desprolijo**: cola larga en todas las categorías, clientes gigantes y grupos que se pisan. Eso es a propósito parte de la clase.

## Perfiles con K=4

| Cluster | Clientes | Perfil | % ventas | Canal | Nombre posible |
|---|---|---|---|---|---|
| 0 | 61 | almacén 12.349, lácteos 7.062, limpieza 5.343, casi sin frescos ni delicatessen | 12% | 40 Retail / 21 Horeca | Tiendas de almacén |
| 1 | 129 | frescos 19.374, congelados 6.184, delicatessen 2.323 | 33% | 122 Horeca / 7 Retail | Gastronomía de frescos |
| 2 | 132 | compra poco de todo (gasto total 16.379) | 15% | 131 Horeca / 1 Retail | Cuentas chicas |
| 3 | 118 | lácteos 11.759, almacén 16.088, limpieza 6.806, el mayor gasto total (50.124) | 40% | 94 Retail / 24 Horeca | Grandes compradores de almacén |

Los números de cluster pueden variar si cambian el `random_state`; el perfil no.

## Celda por celda

**Header y sección 1.** Que el curso entienda que **no hay variable objetivo**: esa es la diferencia con todo lo anterior. En el `describe()`, que miren `mean` contra `50%` y contra `max` (frescos: mediana 8.504, máximo 112.151). Es el anzuelo para la sección 3.

**Sección 2 (EDA).** Seis histogramas con la misma forma: pila a la izquierda y cola larga. El 10% de los clientes (44) concentra el 28% de las ventas. Conviene remarcar el contrapunto: el 72% restante viene de los medianos y chicos.

**Sección 3 (escalado y log). Es el corazón técnico de la clase.**
1. Se estandariza (conexión con KNN, Clase 05; contraste con CART, Clase 07, que no escala) y se corre K-Means con 4 grupos. Resultado: grupos de **110, 315, 10 y 5** clientes. Dos de los cuatro grupos están dedicados a 15 clientes.
2. La tabla de esos 15 clientes muestra gente enorme que compra decenas de miles en una categoría. **Trampa:** el reflejo de quien viene de modelos donde sacar outliers era automático es borrarlos, pero acá serían los mejores clientes. El reflejo de CART ("son señal, no se tocan") tampoco alcanza: dejarlos rompe el agrupamiento. La salida es transformar la escala.
3. **Cómo explicar el logaritmo.** Una frase: el log cambia la pregunta, de "cuántos dólares más compra" a "cuántas veces más compra". El notebook lo muestra con cuatro compras (1.000, 2.000, 50.000 y 100.000): en dólares la distancia entre los grandes es 50 veces la de los chicos, aunque los dos pares duplicaron la compra; en logaritmo (base 10) las dos diferencias valen 0,3. Cada punto de la columna del log es multiplicar por 10. Tres cosas que suelen preguntar: (a) no cambia el orden, el más grande sigue siendo el más grande; (b) en el código es `log1p`, el logaritmo natural de 1 + compra, y la base cambia la escala del número, no la idea; (c) al final se deshace para mostrar en dólares. Orden: **primero log, después estandarizar**.
4. Si preguntan por qué `log1p` y no `log`: para no romper con valores en cero (en este dataset no hay ceros, pero es el hábito correcto).

**Sección 4 (codo).**
- Mejora por K: K=2 30,1%, K=3 15,8%, K=4 10,7%, K=5 8,7%, K=6 7,2%, K=7 7,5%. **No hay codo nítido**: el notebook lo dice abiertamente. Es un buen momento para decir que con datos reales casi nunca hay un codo de manual.
- Aclarar que la inercia es suma de distancias **al cuadrado** (el PDF dice "distancias"). Un comentario al pasar.
- Trampa: "la inercia más baja es mejor, entonces K=10". Siempre baja al agregar grupos.
- Demo de inicialización: inercias entre 1.387 y 1.444, unos 4% de diferencia. **El efecto es chico en este dataset y el notebook lo dice.** No hay que exagerarlo. El mensaje es `n_init=10` porque no cuesta nada.

**Pizarrón 1 (K).** Anotar K=3, 4 y 5 y votar. Empujar con "¿cuántas estrategias comerciales distintas podemos sostener con US$ 600.000?". Qué pasa con cada elección (verificado):

| K | Qué cambia | Para qué sirve |
|---|---|---|
| 3 | Aparece un grupo de 213 clientes (210 Horeca, 3 Retail) que compra poco y medio de todo. El grupo de frescos y congelados desaparece como tal: queda repartido entre ese y un grupo mixto de 147 (56 Horeca, 91 Retail). Queda un grupo de 80 de almacén, lácteos y limpieza (48 Retail, 32 Horeca). Ojo: el grupo mixto de 147 es el de gasto alto en todo (gasto total cercano a 53.000) y concentra el 53% de las ventas. | Discutir qué se pierde: ya no hay un grupo para el cliente que compra mucho fresco. |
| 4 | Los cuatro arquetipos de la tabla de arriba. | Es el recorrido que usa el texto de las celdas siguientes. |
| 5 | Conserva los cuatro arquetipos de K=4, algo más chicos (90 de bajo gasto, 54 de tiendas de almacén, 100 de grandes compradores y 100 de frescos), y agrega un grupo nuevo de 96 compradores medianos (gasto total cercano a 21.000) que toma clientes de los cuatro grupos de K=4. | ¿Ese grupo intermedio justifica una acción propia, o se atiende igual que alguno de los otros? |

Si la clase elige K=3 o K=5, el notebook corre igual: las celdas son independientes de K. Hay que actualizar `NOMBRES` y `DECISION` con los números de cluster que correspondan. **Ojo:** el comentario sobre los cuatro cuadrantes en la sección 6 y el ejemplo de `DECISION` asumen K=4; adaptarlos al hablar.

**Sección 5 (perfilado).** Pasar primero por el mapa de calor (ver el patrón; está en escala log estandarizada) y después por la tabla (dólares sin transformar y % de ventas). Mensaje: el grupo más grande en cantidad de clientes (132, "cuentas chicas") no es el que más factura (15%); el grupo de grandes compradores de almacén tiene 118 clientes y el 40% de las ventas.

*Chequeo con la columna `canal`.* El algoritmo nunca la vio. Dos grupos son casi todo Horeca (122/7 y 131/1) y los otros dos son mayoritariamente Retail (40/21 y 94/24). **No es un accuracy**, es sentido común: los grupos reflejan algo real. Y lo más interesante para negocio: el Horeca se parte en dos grupos muy distintos. Ese es el valor que el canal solo no da.

**Pizarrón 2 (arquetipos).** Un nombre por cluster. Pedir nombres que describan lo que el cliente **compra**, no lo que **vale**. Cargar los nombres en `NOMBRES` y volver a correr desde la sección 6.

**Sección 6 (matriz).** Ejes por defecto: `almacen` y `delicatessen`, en escala log. Con K=4 las cuatro X caen en cuadrantes distintos (alto/bajo, bajo/alto, bajo/bajo y alto/alto). Las X son los centroides del modelo devueltos a dólares (por eso quedan en el medio de cada nube y no tirados hacia arriba). Aclarar que **los puntos se mezclan bastante**: en datos reales las nubes se pisan. Hay que leer las X. Otros ejes para probar: `frescos` y `limpieza_papel`, o `lacteos` y `congelados`. No todos los pares separan los cuatro grupos, y ese es el punto.

**Pizarrón 3 (matriz).** La clase dibuja los ejes y ubica los nombres. Preguntar por cuadrantes vacíos con otros ejes o K.

**Sección 7 (presupuesto).** El menú suma US$ 1.080.000 para US$ 600.000 de presupuesto: hay que elegir. Cada acción tiene un público descrito por comportamiento de compra, no por nombre de cluster: **la clase** decide a qué arquetipo se la asigna. La decisión es un diccionario `{id de acción: cluster}`. El resumen devuelve costo, clientes alcanzados, costo por cliente, gasto anual promedio del grupo y costo como % de ese gasto. Ejemplo que viene cargado: entrega de frescos al cluster 1 (US$ 1.938 por cliente, 5,2% de su gasto anual) y descuento por volumen al cluster 3 (US$ 1.695 por cliente, 3,4%).

**Pizarrón 4 (reparto).** Preguntas para empujar: ¿un poco a todos o mucho a pocos?, ¿blindar a los grandes o desarrollar a los chicos?, ¿qué pasa con US$ 300.000? Cada acción se puede usar una sola vez, pero un grupo puede recibir más de una. No hay respuesta correcta; sí hay que defenderla con un número. Trampa: el costo por cliente más bajo no es necesariamente la mejor inversión; mirar el costo como % del gasto anual y el peso del grupo en las ventas.

## Trampas habituales (resumen)

1. Querer sacar los outliers sin mirarlos (o creer que "como en CART" se dejan tal cual).
2. Creer que escalar alcanza con datos de cola larga.
3. Elegir el K de menor inercia.
4. Pensar que "más grupos = mejor análisis".
5. Leer los números de cluster como si significaran algo antes de nombrarlos.
6. Querer medir el clustering con accuracy (el chequeo con `canal` no lo es).
7. Leer la matriz por los puntos en vez de por los centroides.
8. Confundir "más clientes" con "más ventas" a la hora de repartir el presupuesto.
