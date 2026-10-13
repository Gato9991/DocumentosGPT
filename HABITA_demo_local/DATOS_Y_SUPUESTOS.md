# Datos y supuestos del prototipo HABITA

## Datos calculados desde GTFS

Fuente: `HABITA_GTFS_Movilidad_v1_2_1.zip` del repositorio DocumentosGPT, dos reportes JSON de `analysis_..._2026-09-23_v1_2_1.json`. Feed `V167.20260829`, an�lisis del 23-09-2026, zona horaria America/Santiago. La vigencia declarada del feed es 29-08-2026 a 31-12-2026.

| Ubicaci�n | Radio | Puntos de parada | Recorridos activos | Viajes �nicos 07-09 | Eventos de paso 07-09 | Viajes �nicos 17-19 | Eventos de paso 17-19 |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| Plaza de Armas, San Bernardo | 500 m | 23 | 20 | 480 | 1.400 | 433 | 1.307 |
| Plaza de Armas, San Bernardo | 800 m | 57 | 22 | 554 | 3.077 | 489 | 2.772 |
| Estadio Nacional, �u�oa | 500 m | 25 | 18 | 487 | 914 | 491 | 935 |
| Estadio Nacional, �u�oa | 800 m | 46 | 19 | 517 | 1.802 | 527 | 1.835 |

| Ubicaci�n | Coordenadas del reporte | Parada activa m�s pr�xima | Distancia geod�sica | Caminata te�rica | Recorridos en esa parada |
| --- | --- | --- | ---: | ---: | --- |
| Plaza de Armas, San Bernardo | -33.5922368, -70.704706 | PG1599 | 94,2 m | 1,1 min | 201, 201e, 211, 211c, 217e, 271 |
| Estadio Nacional, �u�oa | -33.4644994, -70.6112756 | PD561 | 308 m | 3,7 min | 508, 511 |

Los **viajes �nicos** cuentan una instancia programada una vez en el �rea. Los **eventos de paso** cuentan su paso por cada parada del radio, por lo que pueden repetir el mismo viaje. No deben sumarse ni leerse como n�mero de buses distintos.

## Reglas demostrativas, no validadas

Solo clasifican **densidad de puntos de parada**, no calidad global del transporte.

| Radio | Baja | Limitada | Buena | Excelente |
| --- | --- | --- | --- | --- |
| 500 m | 0-4 | 5-9 | 10-19 | 20 o m�s |
| 800 m | 0-9 | 10-19 | 20-49 | 50 o m�s |

Los puntajes del �ndice HABITA y sus variables ambientales son n�meros inventados para probar la interfaz:

| Ubicaci�n | Escenario | �ndice HABITA | Ambiente | Ruido | Seguridad |
| --- | --- | ---: | ---: | ---: | ---: |
| Plaza de Armas, San Bernardo | D�a | 82 | 84 | 74 | 79 |
| Plaza de Armas, San Bernardo | Noche | 71 | 76 | 57 | 68 |
| Estadio Nacional, �u�oa | D�a | 78 | 76 | 69 | 74 |
| Estadio Nacional, �u�oa | Noche | 67 | 70 | 53 | 64 |

El analizador GTFS no calcula el �ndice HABITA. Ninguna variable ficticia representa una medici�n en estas ubicaciones.

## L�mites que deben explicarse al presentar

- El GTFS es un horario programado; no mide puntualidad, cancelaciones ni estado en tiempo real.
- La distancia a la parada es en l�nea recta. El tiempo a pie supone 1,4 m/s, tambi�n en l�nea recta; obst�culos y cruces reales pueden cambiarlo.
- M�s paradas pueden corresponder a los mismos recorridos. Por eso una categor�a de densidad no equivale a una calificaci�n de movilidad.
- El reporte analiza dos puntos concretos, no cualquier vivienda de la comuna.
- Las direcciones y coordenadas son reales: Estadio Nacional, [Av. Grecia 2001](https://ind.cl/noticias/las-claves-de-la-corrida-de-la-ninez-en-el-parque-estadio-nacional/), y el punto de Plaza de Armas de San Bernardo definido por el reporte. El enlace de mapa usa esas coordenadas, no geocodifica una direcci�n postal.

