Especificación de una [API] para OpenDataMX
===========

Draft de la primera especificación de una API para el [OpenDataMX]

## Razón

### Introducción

[OpenDataMX] es un hackatón enfocado en desarrollar tecnología para promover la transparencia del Gobierno de México.

Para el evento se publican _datasets_ en el repo de [Github](https://github.com/opendatamx) o en la [página oficial del evento](http://opendata.mx/datasets), y varios equipos destinan 36 horas del fin de semana para concretar un producto de la depuración, procesamiento, y visualización de los datos.

### Problema

* El producto de los equipos del evento concretan necesidades tan específicas que terminan limitando el esfuerzo a una visualización en particular y por ende aislando el avance generado en el procesamiento de los datos.
* Cada equipo trabaja la fase de depuración de datos de manera independiente y no está disponible de manera digerida para terceros. ¿Dónde están los datos procesados de los OpenDataMX pasados? Al final del evento sólo veo el repositorio original con documentos .zip, .pdf, .xls, el anuncio de un proyecto ganador, y un par de infografías (datos digeridos, presentables, pero no flexibles ni estandarizados para nuevos desarrollos).
* El repositorio de datasets de OpenDataMX no está centralizado en una base de datos, por lo tanto no provee una interfaz flexible para la manipulación, consulta, y generación de referencias cruzadas con los datos.

Ejemplos:

1 [Datasets de agosto 2012 de OpenDataMX, .zip, .xls, .csv](https://github.com/opendatamx/datasetsagosto2012)

2 Estos datasets de educación indígena en DataHub están comprimidos en formato .zip
![DataHub: Educación Indígena (formato .zip)](http://f.cl.ly/items/3l32322v0w3i0o1p303L/DataHub.png)

### Retomando algunos de los principios del [Open Government Working Group]

Los datos de gobierno:

1. Deben ser completos: datos públicos significa que no están sujetos a confidencialidad, privacidad o algún otro status restrictivo.
2. Deben ser primarios, i.e. con el mayor grado de granularidad posible.
4. Deben ser legibles tanto para humanos como para un programa computacional.
5. Deben estar disponibles sin discriminación para el mayor número de usuarios y propósitos. 
6. Deben almacenarse en formatos no propietarios.  

## Propuesta

1. Estandarizar el formato de datos
2. Centralizar la información
3. Facilitar el acceso de los datos a las masas
4. Permitir la generación de consultas
5. Agilizar y humanizar la importación de datos

En resumen, cualquier humano o programa informático debe poder accesar, entender, y procesar los datos del [OpenDataMX] desde cualquier parte de la red.

Proponemos un [API] público que permita centralizar el procesamiento, distribución y consulta de estos datos.

## Descripción de la [API]

1. El API facilitará el consumo de datos entregándolos en [JSON](http://es.wikipedia.org/wiki/Json) o en [XML](http://es.wikipedia.org/wiki/Xml).
2. Arquitectura simple basada en [REST](http://es.wikipedia.org/wiki/REST) sin autenticación.
3. Facilitará la consulta de datos bajo los siguientes rubros:  
  3.1 Categorías, ej. educación, salud, gasto público  
  3.2 Datasets/temáticas/contextos, ej. bullying, licitaciones de software  
  3.3 Zona geográfica, ej. Baja California  
  3.4 Fechas, ej. 2009 - 2011  
4. Los datos deben tener referencia, i.e. autor, organización a cargo.  
5. Los datos deben estar ligados a una zona geográfica y al tiempo. 
6. Los campos deben tener una descripción, p.ej. en el data set ["Financiamiento a la actividad forestal por programa 2011"](http://thedatahub.org/es/dataset/ccmss/resource/d009e5c6-20aa-4320-8bef-40b624dc66f1), el campo o columna "solicitante" llevaría una descripción más específica similar a "Nombre del apoderado legal del subsidio entregado".

Ejemplo de descripción de servicios de API en [Open311]

![Ejemplo de descripción del servicio del API en Open311](http://f.cl.ly/items/1X2U030r0N0m2j3q2C1D/311Spec.png)

### Contextos, datasets, temática

```
➜  ~  curl http://opendata.mx/api/educacion
{ datasets: ["bullying", "nivel-de-escolaridad"] }
➜  ~  curl http://opendata.mx/api/presupuesto
{ datasets: ["licitaciones", "compras-de-software", "pronabes"] }

```
### Datos en tiempo y espacio

Dataset de bullying filtrado al DF

```
➜  ~  curl http://opendata.mx/api/educacion/bullying?w=-99.364067&s=19.048220&e=-98.940193&n=19.591579
```
Presupuesto para compra de software desde 2009

```
➜  ~  curl http://opendata.mx/api/presupuesto/compras-de-software?since=2009
```
[Financiamiento a bosques en 2011](http://thedatahub.org/es/dataset/ccmss/resource/d009e5c6-20aa-4320-8bef-40b624dc66f1)

```
➜  ~  curl http://opendata.mx/api/presupuesto/financiamiento-a-bosques?year=2011
```
```json
{
    "results": [
        {
            "Estado": "Chiapas",
            "Solicitante": "Emilio Jiménez Pérez",
            "Monto": 2450,
            "Municipio": "San Fernando",
            "Superficie": 2,
            "Programa": "Restauración y conservación del Río Grijalva"
        },
        {
            "Estado": "Chiapas",
            "Solicitante": "Esteban Vázquez Sánchez",
            "Monto": 1080,
            "Municipio": "San Fernando",
            "Superficie": 1,
            "Programa": "Restauración y conservación del Río Grijalva"
        }
    ]
}
```

## Futuros escenarios

* Un ecosistema de desarrollo alrededor del API
  * [SDKs](http://es.wikipedia.org/wiki/SDK) para diferentes lenguajes de programación
  * Aplicación Web para la fácil incorporación de nuevos datasets
  * Cuentas validadas para organizaciones que mantendrán sanos los datos
* Productos más robustos y más completos
* Repositorio histórico de datos
* Minería de datos
* Referencias cruzadas entre datasets

## Referencias

* [OpenDataMX]  
* [The Data Hub](http://thedatahub.org)
* [Open311]
* [Open Government Working Group]

[OpenDataMX]: http://opendata.mx  "OpenDataMX"
[API]: http://es.wikipedia.org/wiki/Interfaz_de_programaci%C3%B3n_de_aplicaciones "API"
[Open311]: http://open311.org/ "Open311"
[Open Government Working Group]: http://www.opengovdata.org/home/8principles "Open Government Working Group"

## Licencia

![Creative Commons License](http://i.creativecommons.org/l/by-nc-sa/3.0/88x31.png)

Licencia bajo [Creative Commons Attribution-NonCommercial-ShareAlike 3.0 Unported License](http://creativecommons.org/licenses/by-nc-sa/3.0/).

2012 Rodolfo Wilhelmy <rwilhelmy@gmail.com>
