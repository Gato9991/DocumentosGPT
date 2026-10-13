# HABITA · prototipo local de entorno y movilidad

Demo de presentación, autocontenida en `index.html`. Puedes abrir ese archivo con doble clic. Para servirla en localhost desde esta carpeta:

```powershell
python -m http.server 8000
```

Luego visita [http://localhost:8000](http://localhost:8000). Detén el servidor con `Ctrl+C`. No requiere paquetes, API ni conexión para funcionar; los enlaces externos sí necesitan internet.

## Qué se puede hacer

- Alternar entre **Plaza de Armas de San Bernardo** y **Estadio Nacional**.
- Cambiar el radio de **500/800 m** y la hora punta **07–09/17–19 h**. Todas las cifras de movilidad y la comparación responden a esos controles.
- Ver densidad de paradas, recorridos, viajes únicos programados, eventos de paso y parada activa más próxima.
- Cambiar el escenario ilustrativo de día/noche del índice HABITA.
- Abrir la ubicación geográfica y desplegar las limitaciones metodológicas.
- Abrir **Futuras actualizaciones** desde la esquina superior derecha. Incluye el enlace al [Mapa de Ruido del Gran Santiago 2023](https://mapa-ruido-santiago-2023.sicky616.chatgpt.site/) y una vista conceptual interactiva de cinco perfiles: familia, universitario/a, persona mayor, traslado diario y vida activa.

La integración acústica y los cálculos personalizados de cercanía son propuestas futuras. Cambiar de perfil solo muestra prioridades ilustrativas; no altera los indicadores actuales ni realiza consultas a servicios cercanos. El mapa enlazado es un sitio aparte que permite explorar ruido de día y noche por comuna.

## Procedencia

Los datos de movilidad salen de los JSON `analysis_Plaza_de_Armas_-_San_Bernardo_2026-09-23_v1_2_1.json` y `analysis_Estadio_Nacional_Julio_Martínez_Prádanos_2026-09-23_v1_2_1.json` incluidos en [HABITA_GTFS_Movilidad_v1_2_1.zip](https://github.com/Gato9991/DocumentosGPT/blob/main/HABITA_GTFS_Movilidad_v1_2_1.zip). El feed es `V167.20260829` y la fecha analizada es el **23 de septiembre de 2026**. Las ubicaciones se representan con las coordenadas de los reportes; el recinto Estadio Nacional tiene dirección pública [Av. Grecia 2001, Ñuñoa](https://ind.cl/noticias/las-claves-de-la-corrida-de-la-ninez-en-el-parque-estadio-nacional/).

El índice HABITA /100, ambiente, ruido, seguridad y las categorías de densidad **son una demostración**. Los valores /100 son enteramente ficticios. La etiqueta de densidad usa puntos de parada realmente contados, pero sus umbrales son una regla provisional, no un estándar validado. [DATOS_Y_SUPUESTOS.md](DATOS_Y_SUPUESTOS.md) contiene la tabla completa y las reglas.

**No interpretar eventos de paso como buses distintos:** un mismo viaje puede pasar por varias paradas del radio. El indicador principal de intensidad son los viajes únicos programados. Las distancias son geodésicas, no recorridos a pie. El GTFS es horario programado, no tiempo real.
