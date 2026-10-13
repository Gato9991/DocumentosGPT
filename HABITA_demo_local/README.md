# HABITA � demo local

Mini sitio interactivo basado en las capturas: selecci�n de direcci�n, resultado e �ndice HABITA, y detalle del entorno con vista de d�a y de noche.

## Iniciar en localhost

Desde esta carpeta, ejecuta uno de estos comandos:

```powershell
py -m http.server 8000
```

Si `py` no est� disponible, prueba `python -m http.server 8000`. Luego abre [http://localhost:8000](http://localhost:8000). Para detener el servidor, pulsa `Ctrl+C` en la terminal.

Tambi�n puedes abrir `index.html` directamente, pero localhost reproduce mejor el uso previsto. No requiere instalaci�n de paquetes ni conexi�n a internet para funcionar. Los enlaces a las fuentes oficiales s� necesitan internet.

## Alcance

- Tres direcciones reales de lugares p�blicos, con enlace a la fuente oficial en el resultado.
- B�squeda local limitada a esas opciones. No se geocodifican direcciones libres.
- Puntajes, variables, fortalezas y advertencias **inventados** para demostrar la navegaci�n. No son mediciones ni datos para tomar una decisi�n inmobiliaria.
- Sin cuenta, servidor de datos, sensores, seguimiento ni almacenamiento de informaci�n.

### Fuentes de las direcciones

- Municipalidad de Providencia: [Av. Pedro de Valdivia 963](https://www.providencia.cl/provi/municipalidad/direcciones-municipales/administracion-municipal/direccion-administracion-municipal).
- Centro Cultural Gabriela Mistral: [Av. Libertador Bernardo O'Higgins 227](https://gam.cl/es/experiencia/como-llegar/).
- Museo de la Memoria y los Derechos Humanos: [Matucana 501](https://educamemoria.museodelamemoria.cl/taller-visita/obras-exteriores-del-museo/).

