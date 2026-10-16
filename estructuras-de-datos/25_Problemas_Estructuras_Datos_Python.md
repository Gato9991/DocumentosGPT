# 25 problemas de estructuras de datos en Python

Cuaderno de práctica de nivel medio · Daniel Morales · 15 de octubre de 2026

Este cuaderno propone 25 problemas de dificultad media para practicar listas, tuplas, diccionarios, pilas y colas en Python. Parte de operaciones básicas y exige combinarlas con validaciones, decisiones y seguimiento del estado. No incluye soluciones.

Trabaja con funciones y datos definidos en el código. No necesitas interfaz gráfica, archivos, bases de datos, clases, recursividad, librerías externas ni un menú interactivo. Puedes usar herramientas incorporadas de Python, salvo las restricciones expresas de cada problema. Para colas, usa collections.deque; para pilas, listas con operaciones en el extremo final.

Antes de programar, escribe qué recibe tu función, qué devuelve y qué estructura usarás. Después implementa el caso normal y prueba los casos límite. Si un ejercicio no define una entrada inválida concreta, puedes suponer que se respetan los tipos y dominios descritos. No añadas validaciones ajenas al objetivo.

Los índices comienzan en cero. En los ejemplos de pilas se escribe de base a tope y en las colas de frente a fondo. Los ejemplos fijan el comportamiento esperado, no el formato exacto de impresión. Ante errores, puedes devolver un estado y un mensaje, sin obligarte a usar excepciones.

Media inicial significa combinar operaciones conocidas; media añade varias reglas o cruces de datos; media alta exige coordinar estados o conservar una propiedad entre operaciones. Cada problema es independiente y todos permanecen dentro del temario.

## Selección para comenzar

Ruta sugerida de 13 problemas: 1, 3, 5, 6, 8, 11, 13, 15, 16, 18, 21, 23 y 25. Cubre las cinco estructuras y termina con una integración. Para hacer 12, deja el 13 como reserva; todavía practicas diccionarios en 11 y 15. Puedes sustituir ejercicios por otros de su mismo bloque.

Considera resuelto un problema cuando funciona el ejemplo, superas al menos tres casos propios (incluido uno límite), puedes explicar la estructura elegida y puedes anticipar el efecto de una operación sin ejecutar el programa. Si te bloqueas, reduce la entrada y traza a mano el estado; pide una pista concreta antes de consultar una solución completa.

## Mapa del cuaderno

| Problemas | Estructura principal | Trabajo central |
| --- | --- | --- |
| 1–5 | Listas | Recorridos, repetidos, mezcla y reservas |
| 6–10 | Tuplas | Registros, desempates, intervalos y resultados compuestos |
| 11–15 | Diccionarios | Acumulación, actualización y cruces por clave |
| 16–20 | Pilas | Historial, cancelación y restricciones LIFO |
| 21–25 | Colas | Turnos, reintentos y simulaciones FIFO |

## 1 Inscripciones sin duplicados

**Listas · Media inicial · Ruta de 13**

Depura una lista de nombres sin perder el orden de inscripción. Devuelve dos listas: nombres aceptados y entradas rechazadas, estas últimas con su índice original y motivo.

**Reglas.** Quita espacios al inicio y al final. La comparación ignora mayúsculas; conserva la escritura de la primera aparición válida. Rechaza nombres vacíos y repeticiones posteriores. Usa listas, sin set ni diccionario, para practicar búsqueda y construcción de resultados.

**Datos de ejemplo.** [" Ana ", "LUIS", "ana", "", " Luis ", "Eva"]

**Resultado esperado.** Aceptados: ["Ana", "LUIS", "Eva"]. Rechazados: índices 2 y 4 por duplicado; índice 3 por vacío.

**Pruebas propias.** Prueba lista vacía, nombres solo con espacios y tres variantes del mismo nombre. La lista recibida debe permanecer intacta.

**Para explicar.** ¿Por qué eliminar elementos de la lista mientras la recorres puede hacerte saltar una inscripción?

## 2 Rachas de mediciones elevadas

**Listas · Media**

Detecta todas las rachas de al menos k mediciones consecutivas mayores o iguales a un umbral. Devuelve una tupla (inicio, fin, máximo) por cada racha, con índices desde cero e inicio y fin incluidos.

**Reglas.** Cada racha debe ser maximal: no la dividas en ventanas solapadas. Una lectura menor que el umbral la termina. k debe ser un entero positivo; si no lo es, devuelve un error claro.

**Datos de ejemplo.** Mediciones: [12, 20, 22, 18, 21, 25, 26, 10]. Umbral: 20. k: 2.

**Resultado esperado.** [(1, 2, 22), (4, 6, 26)].

**Pruebas propias.** Prueba una racha que llegue al último elemento, ninguna racha, toda la lista elevada y k mayor que la longitud.

**Para explicar.** ¿Qué información necesitas conservar cuando una racha todavía no ha terminado?

## 3 Conciliación de entregas repetidas

**Listas · Media · Ruta de 13**

Compara los artículos pedidos con los recibidos. Devuelve faltantes y sobrantes respetando, respectivamente, el orden de pedido y de recepción.

**Reglas.** Las repeticiones representan unidades distintas. Cada unidad recibida solo puede satisfacer una unidad pedida. No basta con preguntar si el artículo aparece. Resuelve con listas y sin modificar las entradas; no uses Counter, set ni diccionario.

**Datos de ejemplo.** Pedidos: ["A", "B", "A", "C"]. Recibidos: ["A", "C", "C", "D"].

**Resultado esperado.** Faltantes: ["B", "A"]. Sobrantes: ["C", "D"].

**Pruebas propias.** Prueba listas idénticas con duplicados, pedido vacío, recepción vacía y exceso de un único artículo.

**Para explicar.** ¿Qué dato perderías si convirtieras ambos registros en conjuntos?

## 4 Mezcla de dos registros ordenados

**Listas · Media**

Recibe dos listas de enteros ordenadas de menor a mayor y devuelve una lista ordenada que contenga todos sus elementos, incluidos los repetidos.

**Reglas.** No uses sort ni sorted, ni concatenes para ordenar después. Recorre los datos sin volver al principio en cada búsqueda. Si hay igualdad, incorpora primero el elemento de la primera lista. Supón entradas ya ordenadas.

**Datos de ejemplo.** Primera: [1, 4, 4, 9]. Segunda: [2, 4, 7].

**Resultado esperado.** [1, 2, 4, 4, 4, 7, 9].

**Pruebas propias.** Prueba dos listas vacías, una vacía y una lista cuyos valores sean todos menores que los de la otra.

**Para explicar.** ¿Cómo incorporarías lo que queda cuando una lista se termina antes que la otra?

## 5 Reserva contigua de asientos

**Listas · Media alta · Ruta de 13**

Una sala se representa como una lista de filas, cada una con 0 para asiento libre y 1 para ocupado. Reserva k asientos contiguos en una sola fila.

**Reglas.** Elige la primera fila que sirva y, dentro de ella, el bloque más a la izquierda. Devuelve las coordenadas reservadas y actualiza la sala solo si puedes completar la reserva. k debe ser positivo. Las filas pueden tener longitudes distintas; los índices parten en cero.

**Datos de ejemplo.** Sala: [[0, 1, 0, 0], [0, 0, 0, 1]]. k: 3.

**Resultado esperado.** Reserva: [(1, 0), (1, 1), (1, 2)]. Sala final: [[0, 1, 0, 0], [1, 1, 1, 1]].

**Pruebas propias.** Prueba ausencia de bloques suficientes, sala vacía y reserva del tamaño exacto de una fila. Un rechazo no debe cambiar ningún asiento.

**Para explicar.** ¿En qué momento puedes modificar la sala sin dejar una reserva incompleta?

## 6 Selección de vivienda con desempate

**Tuplas · Media · Ruta de 13**

Analiza una lista de tuplas (código, arriendo, minutos_de_viaje). Devuelve la vivienda elegida o None si ninguna cumple.

**Reglas.** Acepta arriendos menores o iguales al presupuesto y viajes menores o iguales al límite. Prioriza menor arriendo; en empate, menor viaje; si ambos empatan, conserva la primera aparición. Supón códigos únicos y valores no negativos. No modifiques los registros.

**Datos de ejemplo.** [("A", 300, 35), ("B", 300, 25), ("C", 280, 50)]. Presupuesto: 320. Límite: 40.

**Resultado esperado.** ("B", 300, 25).

**Pruebas propias.** Prueba igualdad exacta con los límites, empate completo y ninguna vivienda elegible.

**Para explicar.** ¿Qué se conserva al representar cada vivienda con una tupla y qué sigue pudiendo cambiar en la lista que las contiene?

## 7 Cruces en una agenda

**Tuplas · Media**

Recibe reservas (código, inicio, fin), donde las horas son minutos enteros desde medianoche. Devuelve los pares de códigos cuyas reservas se solapan.

**Reglas.** Los intervalos incluyen el inicio y excluyen el fin: terminar a las 600 y comenzar a las 600 no es conflicto. Cada par aparece una sola vez, en el orden generado al recorrer los índices i y j con i < j. Rechaza toda la entrada si hay inicio >= fin. Los códigos son únicos.

**Datos de ejemplo.** [("A", 540, 600), ("B", 600, 660), ("C", 590, 620)].

**Resultado esperado.** [("A", "C"), ("B", "C")]. A y B no se cruzan.

**Pruebas propias.** Prueba intervalos idénticos, uno contenido en otro y una sola reserva. No necesitas combinar intervalos.

**Para explicar.** ¿Por qué comparar únicamente las horas de inicio no detecta todos los cruces?

## 8 Notas ponderadas con contrato claro

**Tuplas · Media · Ruta de 13**

Calcula la nota final a partir de una tupla de notas y una tupla de ponderaciones enteras expresadas en porcentaje. Devuelve (promedio, aprobado).

**Reglas.** Las tuplas deben ser no vacías y del mismo largo. Cada nota está entre 1 y 7; cada peso es positivo y la suma de pesos debe ser 100. Ante un dato inválido, devuelve un error sin calcular un resultado parcial. Aprueba con promedio sin redondear >= 4; redondea solo al mostrar.

**Datos de ejemplo.** Notas: (5.0, 3.0, 6.0). Pesos: (30, 30, 40).

**Resultado esperado.** Promedio: 4.8. Aprobado: True.

**Pruebas propias.** Prueba pesos que sumen 90, largos distintos, una nota fuera de rango y promedio exactamente 4.

**Para explicar.** ¿Cómo se distingue modificar una tupla de crear una tupla nueva con una nota corregida?

## 9 Auditoría entre dos configuraciones

**Tuplas · Media**

Compara dos configuraciones dadas como listas de tuplas (servicio, puerto, activo). Devuelve tres listas: altas, bajas y cambios.

**Reglas.** Cada servicio aparece como máximo una vez por lista. Un cambio es (servicio, registro_anterior, registro_nuevo) cuando difiere puerto o activo. Altas siguen el orden de la lista nueva; bajas y cambios, el de la anterior. Los registros originales deben permanecer intactos.

**Datos de ejemplo.** Antes: [("web", 80, True), ("ftp", 21, False)]. Después: [("web", 81, True), ("dns", 53, True)].

**Resultado esperado.** Alta: ("dns", 53, True). Baja: ("ftp", 21, False). Cambio: ("web", ("web", 80, True), ("web", 81, True)).

**Pruebas propias.** Prueba configuraciones iguales, una vacía y el cambio de dos campos del mismo servicio; debe contarse una sola vez.

**Para explicar.** ¿Por qué conviene guardar el registro anterior completo al informar un cambio?

## 10 Recorrido sobre una cuadrícula

**Tuplas · Media**

Procesa un recorrido como una lista de puntos (x, y). Devuelve (distancia_total, desplazamiento, primera_revisita). Usa distancia Manhattan: |x2-x1| + |y2-y1|.

**Reglas.** Suma las distancias entre puntos consecutivos. El desplazamiento va del primer punto al último. primera_revisita es (índice, punto) de la primera llegada a un punto ya visto, o None. Una repetición consecutiva también cuenta. En lista vacía devuelve (0, 0, None).

**Datos de ejemplo.** [(0, 0), (2, 0), (2, 1), (0, 0)].

**Resultado esperado.** (6, 0, (3, (0, 0))).

**Pruebas propias.** Prueba un solo punto, coordenadas negativas y repeticiones consecutivas. No se necesita dibujar un mapa.

**Para explicar.** ¿Por qué distancia recorrida y desplazamiento pueden ser distintos?

## 11 Pedido completo o ningún descuento

**Diccionarios · Media alta · Ruta de 13**

Un inventario relaciona código con stock. Un pedido es una lista de tuplas (código, cantidad). Acéptalo completo o recházalo completo; devuelve el estado y el inventario resultante.

**Reglas.** Agrupa cantidades cuando un código se repite. Todas deben ser enteros positivos, todos los códigos deben existir y debe alcanzar el stock acumulado. Si algo falla, no cambies el inventario. Un pedido vacío se acepta sin cambios.

**Datos de ejemplo.** Inventario: {"A": 5, "B": 2}. Pedido: [("A", 3), ("A", 3)].

**Resultado esperado.** Rechazado: A requiere 6 y hay 5. Inventario intacto. Con [("A", 3), ("B", 2)] queda {"A": 2, "B": 0}.

**Pruebas propias.** Prueba un código inexistente, cantidad cero y compra que agote exactamente el stock.

**Para explicar.** ¿Por qué validar cada línea aisladamente permite aceptar un pedido que no puedes entregar?

## 12 Asistencia sin doble conteo

**Diccionarios · Media**

Recibe estudiantes inscritos y registros (día, estudiante). Construye un diccionario con los días asistidos por cada estudiante y otro con la cantidad de asistentes por día.

**Reglas.** Una misma persona cuenta una sola vez por día. Rechaza nombres no inscritos y reporta esos registros aparte. Conserva el orden de primera aparición de los días por estudiante. Incluye inscritos sin asistencia con lista vacía. No hace falta validar el formato del día.

**Datos de ejemplo.** Inscritos: ["Ana", "Luis"]. Registros: [("Lun", "Ana"), ("Lun", "Ana"), ("Mar", "Luis"), ("Lun", "Eva")].

**Resultado esperado.** Por estudiante: {"Ana": ["Lun"], "Luis": ["Mar"]}. Por día: {"Lun": 1, "Mar": 1}. Eva se rechaza.

**Pruebas propias.** Prueba registros vacíos, solo desconocidos y la misma persona en días distintos.

**Para explicar.** ¿Qué diferencia hay entre contar registros y contar asistentes?

## 13 Resumen de gastos por persona

**Diccionarios · Media · Ruta de 13**

Agrupa movimientos (persona, categoría, monto) en un diccionario anidado. Calcula también el total de cada persona y su categoría de mayor gasto.

**Reglas.** Los montos son enteros positivos en pesos. Suma movimientos repetidos de una misma categoría. Si dos categorías empatan dentro de una persona, elige la primera que apareció para ella. No inventes categorías sin movimientos.

**Datos de ejemplo.** [("Ana", "comida", 2000), ("Ana", "viaje", 3000), ("Ana", "comida", 1000), ("Luis", "viaje", 1500)].

**Resultado esperado.** Ana: comida 3000, viaje 3000, total 6000; principal comida. Luis: viaje 1500, total 1500; principal viaje.

**Pruebas propias.** Prueba entrada vacía, una persona con una categoría y empates creados por varios movimientos.

**Para explicar.** ¿Por qué debes sumar antes de decidir cuál es la categoría principal?

## 14 Cambio de código sin pérdida de datos

**Diccionarios · Media**

Implementa el cambio de código de un equipo en un diccionario de fichas. Recibe código anterior y nuevo; devuelve si se hizo el cambio y su motivo.

**Reglas.** El código anterior debe existir y el nuevo no puede pertenecer a otro equipo. Si ambos códigos son iguales y existen, informa que no hay cambios. Conserva íntegra la ficha y la cantidad de equipos. Ante cualquier rechazo, el diccionario queda intacto.

**Datos de ejemplo.** {"PC-01": {"estado": "disponible"}, "PC-02": {"estado": "en uso"}}. Cambiar PC-01 a LAB-01.

**Resultado esperado.** LAB-01 conserva {"estado": "disponible"}; PC-01 desaparece y PC-02 no cambia. Renombrar a PC-02 debe rechazarse.

**Pruebas propias.** Prueba origen ausente, destino ocupado y origen igual al destino.

**Para explicar.** ¿Qué riesgo aparece si borras la clave anterior antes de comprobar el destino?

## 15 Ventas cruzadas con catálogo

**Diccionarios · Media · Ruta de 13**

Cruza un catálogo código → (nombre, precio) con ventas (código, unidades). Devuelve un resumen por código vendido y una lista de ventas con código desconocido.

**Reglas.** Los precios y las unidades son enteros positivos. Acumula unidades e importe por código usando el precio del catálogo. Los desconocidos no aportan ingresos. Presenta el resumen en orden de primera venta válida. Incluye el ingreso total general.

**Datos de ejemplo.** Catálogo: {"A": ("Cuaderno", 1000), "B": ("Lápiz", 300)}. Ventas: [("A", 2), ("X", 1), ("A", 1), ("B", 4)].

**Resultado esperado.** A: 3 unidades y 3000 pesos. B: 4 unidades y 1200 pesos. Total: 4200. Desconocida: ("X", 1).

**Pruebas propias.** Prueba ventas vacías, solo desconocidos y varias ventas del mismo código separadas entre sí.

**Para explicar.** ¿Qué dato usarías como clave si dos productos tuvieran el mismo nombre?

## 16 Editor con deshacer y rehacer

**Pilas · Media alta · Ruta de 13**

Simula un texto con las acciones escribir(cadena), deshacer y rehacer. Usa dos pilas de estados para administrar el historial y devuelve el texto final.

**Reglas.** Escribir agrega al final y guarda el estado anterior. Una escritura nueva borra la posibilidad de rehacer. Deshacer o rehacer sin historial informa que no hay cambios. Escribir cadena vacía tampoco crea historial. Empieza con texto vacío.

**Datos de ejemplo.** escribir("Hola"); escribir("!"); deshacer; rehacer; deshacer; escribir("?"); rehacer.

**Resultado esperado.** Texto final: "Hola?". El último rehacer no cambia nada. El estado "Hola!" ya no está disponible.

**Pruebas propias.** Prueba deshacer al inicio, varios deshacer seguidos y escritura después de retroceder.

**Para explicar.** ¿Por qué una edición nueva invalida los estados que habías deshecho?

## 17 Cancelación de símbolos vecinos

**Pilas · Media**

Reduce una cadena eliminando pares de caracteres iguales que queden adyacentes. Cada eliminación puede provocar una nueva pareja. Devuelve la cadena estable.

**Reglas.** La comparación distingue mayúsculas. Procesa de izquierda a derecha usando una pila; no vuelvas a recorrer toda la cadena después de cada eliminación ni uses reemplazos globales. El orden de los caracteres supervivientes se conserva.

**Datos de ejemplo.** "abbaca"

**Resultado esperado.** "ca". Al desaparecer "bb" queda "aaca"; al desaparecer "aa", queda "ca".

**Pruebas propias.** Prueba "", "aaaa", "abccba", "abc" y "Aa". Para "abccba" el resultado es vacío.

**Para explicar.** ¿Por qué solo necesitas comparar el carácter nuevo con el tope de lo que ya conservaste?

## 18 Retiro de una caja bloqueada

**Pilas · Media · Ruta de 13**

Un depósito es una pila de cajas con identificadores únicos. Retira una caja solicitada usando una pila auxiliar y deja las restantes en su orden original.

**Reglas.** El último elemento de la lista es el tope. Para mover cajas solo usa apilar y desapilar; no uses remove, borrado por índice ni slicing. Si la caja no existe, restaura exactamente la pila inicial. Devuelve si fue encontrada y cuántas cajas la bloqueaban; para ausencia usa None como cantidad.

**Datos de ejemplo.** Pila de base a tope: ["A", "B", "C", "D"]. Retirar "B".

**Resultado esperado.** Pila final: ["A", "C", "D"]. Encontrada: True. Bloqueaban: 2.

**Pruebas propias.** Prueba retirar el tope, la base, una caja inexistente y una pila vacía.

**Para explicar.** ¿Por qué devolver las cajas desde la pila auxiliar restaura su orden?

## 19 Salida posible desde un apartadero

**Pilas · Media alta**

Llegan vagones en el orden 1, 2, ..., n. Pueden entrar a una única pila auxiliar y salir desde su tope. Determina si una secuencia objetivo puede producirse y registra las operaciones si es posible.

**Reglas.** Cada vagón entra una vez y sale una vez. No puedes extraer del medio ni alterar las llegadas. Primero verifica que el objetivo contenga exactamente los números de 1 a n, sin duplicados. n = 0 con objetivo vacío es válido.

**Datos de ejemplo.** n = 3. Objetivo A: [2, 1, 3]. Objetivo B: [3, 1, 2].

**Resultado esperado.** A es posible. B no: después de sacar 3, el 2 bloquea al 1.

**Pruebas propias.** Prueba orden natural, orden inverso, un objetivo con repetidos y uno con valor fuera de rango.

**Para explicar.** ¿Qué te impide obtener el siguiente vagón cuando todas las llegadas ya se agotaron?

## 20 Pila con consulta del mínimo

**Pilas · Media alta**

Diseña operaciones apilar, desapilar y consultar_mínimo para números enteros. La consulta del mínimo debe funcionar sin recorrer ni ordenar la pila.

**Reglas.** Usa una pila principal y una auxiliar. Después de cada operación válida, el mínimo debe corresponder al contenido actual. Debes manejar mínimos repetidos y números negativos. Una extracción o consulta sobre pila vacía devuelve un estado de vacío, sin excepción accidental.

**Datos de ejemplo.** Apilar 5, 2, 2, 4. Consultar; sacar 4; sacar 2; consultar; sacar 2; consultar.

**Resultado esperado.** Las tres consultas dan 2, 2 y 5. El primer 2 retirado no elimina el mínimo restante.

**Pruebas propias.** Prueba valores crecientes, decrecientes, todos iguales y vaciar completamente la pila.

**Para explicar.** ¿Qué información adicional necesitas para no perder un mínimo que aparece dos veces?

## 21 Turnos con cancelación

**Colas · Media · Ruta de 13**

Gestiona una cola de identificadores con llegar, atender y cancelar. Devuelve la secuencia atendida, los rechazos y los pendientes.

**Reglas.** Usa collections.deque y respeta FIFO. Rechaza un identificador que ya esté esperando; puede volver a ingresar después de ser atendido o cancelado. Cancelar elimina únicamente al identificador solicitado y conserva el orden relativo de los demás. Atender vacío no cambia el estado.

**Datos de ejemplo.** Llegan A, B, C; cancelar B; llega D; atender; llega A; atender.

**Resultado esperado.** Atendidos: ["A", "C"]. Pendientes de frente a fondo: ["D", "A"].

**Pruebas propias.** Prueba cancelar un ausente, llegada duplicada, atención vacía y cancelación del primero o del último.

**Para explicar.** ¿Por qué una cancelación no debe adelantar ni retrasar a los demás entre sí?

## 22 Impresora por turnos de páginas

**Colas · Media**

Simula una impresora que permite a cada trabajo imprimir como máximo q páginas en su turno. Cada trabajo es (identificador, páginas_restantes). Devuelve el orden de finalización y el total de turnos.

**Reglas.** Si quedan páginas después del turno, el trabajo vuelve al final; si termina, sale. No llegan trabajos nuevos durante la simulación. q y las páginas iniciales son enteros positivos; valida todo antes de comenzar. Los identificadores son únicos.

**Datos de ejemplo.** Cola: [("A", 5), ("B", 2), ("C", 4)]. q = 2.

**Resultado esperado.** Finalizan B, C y A. Se necesitan 6 turnos. La cola final queda vacía.

**Pruebas propias.** Prueba cola vacía, un solo trabajo y un trabajo cuyas páginas sean múltiplo exacto de q.

**Para explicar.** ¿Qué ocurre con la espera de los trabajos pequeños si cada trabajo grande imprime todo de una sola vez?

## 23 Reintentos con límite

**Colas · Media · Ruta de 13**

Procesa tareas FIFO con resultados de intento ya definidos. Usa un diccionario id → lista de booleanos para simular éxito o fallo y una cola de tareas. Devuelve completadas y descartadas con su número de intentos.

**Reglas.** En cada turno consumes el siguiente resultado de esa tarea. True la completa; False la devuelve al final salvo que alcance el máximo de intentos, en cuyo caso se descarta. Supón identificadores únicos y suficientes resultados para cada tarea. No uses azar ni red.

**Datos de ejemplo.** Cola: ["A", "B", "C"]. Resultados: A=[False, True], B=[True], C=[False, False]. Máximo: 2.

**Resultado esperado.** Completadas: [("B", 1), ("A", 2)]. Descartadas: [("C", 2)].

**Pruebas propias.** Prueba éxito inicial de todas, fallo de todas, máximo 1 y cola vacía.

**Para explicar.** ¿Por qué devolver la tarea fallida al frente podría retrasar injustamente a las demás?

## 24 Dos prioridades con espera limitada

**Colas · Media alta**

Atiende dos colas, urgente y normal, respetando FIFO dentro de cada una. Devuelve el orden de atención aplicando una regla que evite dejar siempre atrás a la cola normal.

**Reglas.** Con ambas colas ocupadas, atiende como máximo dos urgentes consecutivos y luego un normal. Atender un normal reinicia el contador. Si solo una cola tiene tareas, atiéndela. Cada urgente incrementa el contador, incluso si la normal está vacía. No hay nuevas llegadas; los IDs son únicos.

**Datos de ejemplo.** Urgentes: ["U1", "U2", "U3", "U4", "U5"]. Normales: ["N1", "N2"].

**Resultado esperado.** ["U1", "U2", "N1", "U3", "U4", "N2", "U5"].

**Pruebas propias.** Prueba una cola vacía, ambas vacías y una sola tarea normal frente a muchas urgentes.

**Para explicar.** ¿Qué garantía obtiene un normal mientras ambas colas siguen teniendo tareas?

## 25 Despacho de pedidos con stock cambiante

**Colas · Media alta · Ruta de 13**

Combina inventario y cola de pedidos (id, producto, cantidad). Implementa reponer y procesar_ronda. Una ronda devuelve IDs atendidos, rechazados y aplazados, además de los pendientes.

**Reglas.** Una ronda revisa exactamente los pedidos que estaban en cola al comenzar, una vez cada uno. Si el producto no existe o la cantidad no es positiva, rechaza y retira el pedido. Si alcanza el stock, descuéntalo y atiende; si no, envía el pedido al final. No aceptes entregas parciales. Reponer agrega una cantidad positiva a un producto existente.

**Datos de ejemplo.** Stock: {"A": 2, "B": 1}. Cola: [("P1", "A", 3), ("P2", "B", 1), ("P3", "A", 1)].

**Resultado esperado.** Primera ronda: atendidos P2 y P3; pendiente P1; stock A=1, B=0. Reponer 2 unidades de A y hacer otra ronda atiende P1; A=0.

**Pruebas propias.** Prueba todos los pedidos aplazados, producto desconocido y cola vacía. La ronda debe terminar aunque no pueda atender ninguno.

**Para explicar.** ¿Por qué un while que siga hasta vaciar la cola puede no terminar en este problema?

## Hoja de cierre

Para cada problema elegido, anota: número, estructura empleada, casos probados, error más interesante y una mejora pendiente. Repite al día siguiente uno que te haya costado, partiendo de un archivo vacío.

El objetivo es obtener 12 o 13 soluciones que puedas defender y modificar por tu cuenta. La cantidad escrita no sustituye la comprensión.
