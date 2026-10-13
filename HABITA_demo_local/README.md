# HABITA � prototipo local de entorno y movilidad

Demo de presentaci�n, autocontenida en `index.html`. Puedes abrir ese archivo con doble clic. Para servirla en localhost desde esta carpeta:

```powershell
python -m http.server 8000
```

Luego visita [http://localhost:8000](http://localhost:8000). Det�n el servidor con `Ctrl+C`. No requiere paquetes, API ni conexi�n para funcionar; los enlaces externos s� necesitan internet.

## Qu� se puede hacer

- Alternar entre **Plaza de Armas de San Bernardo** y **Estadio Nacional**.
- Cambiar el radio de **500/800 m** y la hora punta **07-09/17-19 h**. Todas las cifras de movilidad y la comparaci�n responden a esos controles.
- Ver densidad de paradas, recorridos, viajes �nicos programados, eventos de paso y parada activa m�s pr�xima.
- Cambiar el escenario ilustrativo de d�a/noche del �ndice HABITA.
- Abrir la ubicaci�n geogr�fica y desplegar las limitaciones metodol�gicas.

## Procedencia

Los datos de movilidad salen de los JSON `analysis_Plaza_de_Armas_-_San_Bernardo_2026-09-23_v1_2_1.json` y `analysis_Estadio_Nacional_Julio_Mart�nez_Pr�danos_2026-09-23_v1_2_1.json` incluidos en [HABITA_GTFS_Movilidad_v1_2_1.zip](https://github.com/Gato9991/DocumentosGPT/blob/main/HABITA_GTFS_Movilidad_v1_2_1.zip). El feed es `V167.20260829` y la fecha analizada es el **23 de septiembre de 2026**. Las ubicaciones se representan con las coordenadas de los reportes; el recinto Estadio Nacional tiene direcci�n p�blica [Av. Grecia 2001, �u�oa](https://ind.cl/noticias/las-claves-de-la-corrida-de-la-ninez-en-el-parque-estadio-nacional/).

El �ndice HABITA /100, ambiente, ruido, seguridad y las categor�as de densidad **son una demostraci�n**. Los valores /100 son enteramente ficticios. La etiqueta de densidad usa puntos de parada realmente contados, pero sus umbrales son una regla provisional, no un est�ndar validado. [DATOS_Y_SUPUESTOS.md](DATOS_Y_SUPUESTOS.md) contiene la tabla completa y las reglas.

**No interpretar eventos de paso como buses distintos:** un mismo viaje puede pasar por varias paradas del radio. El indicador principal de intensidad son los viajes �nicos programados. Las distancias son geod�sicas, no recorridos a pie. El GTFS es horario programado, no tiempo real.

