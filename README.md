Especificación de una API para OpenDataMX
===========

Draft de la primera especificación de una API para el [OpenDataMX](http://opendata.mx/)

## Razón

### Introducción

[OpenDataMX](http://opendata.mx/) es un hackatón enfocado en desarrollar tecnología para promover la transparencia del Gobierno de México.

Para el evento se publican _datasets_ en el repo de [Github](https://github.com/opendatamx) o en la [página oficial del evento](http://opendata.mx/datasets), y varios equipos destinan 36 horas del fin de semana para concretar un producto de la depuración, procesamiento, y visualización de los datos.

### Problema

* El producto de los equipos del evento concretan necesidades tan específicas que terminan limitando el esfuerzo a una visualización en particular y por ende aislando el avance generado en el procesamiento de los datos.
* Cada equipo trabaja la fase de depuración de datos de manera independiente y no está disponible de manera digerida para terceros. ¿Dónde están los datos procesados de los OpenDataMX pasados? Al final del evento sólo veo el repositorio original con documentos .zip, .pdf, .xls, el anuncio de un proyecto ganador, y un par de infografías (datos digeridos, presentables, pero no flexibles ni estandarizados para nuevos desarrollos).
* El repositorio de datasets de OpenDataMX no está centralizado en una base de datos, por lo tanto no provee una interfaz flexible para la manipulación, consulta, y generación de referencias cruzadas con los datos.

Ejemplos:

1 [Datasets de agosto 2012 de OpenDataMX, .zip, .xls, .csv](https://github.com/opendatamx/datasetsagosto2012)

2 Estos datasets de educación indígena en DataHub están comprimidos en formato .zip
![DataHub: Educación Indígena (formato .zip)](http://f.cl.ly/items/3l32322v0w3i0o1p303L/DataHub.png)

## Propuesta

1. Estandarizar el formato de datos
2. Centralizar la información
3. Facilitar el acceso de los datos a las masas
4. Permitir la generación de consultas
5. Agilizar y humanizar la importación de datos

En resumen, cualquier humano o programa informático debe poder accesar, entender, y procesar los datos del OpenDataMX desde cualquier parte de la red.

## Descripción de la [API](http://es.wikipedia.org/wiki/Interfaz_de_programaci%C3%B3n_de_aplicaciones)

### Principios

1. Los datos deben ser consumibles tanto para el humano como para un programa computacional. Se propone que el API entregue los datos en [JSON](http://es.wikipedia.org/wiki/Json) o en [XML](http://es.wikipedia.org/wiki/Xml).
2. Arquitectura simple basada en [REST](http://es.wikipedia.org/wiki/REST).
3. Facilitará el consumo de datos filtrado bajo los siguientes rubros:  
  3.1 Categorías, ej. educación, salud, gasto público  
  3.2 Datasets/temáticas/contextos, ej. bullying, licitaciones de software  
  3.3 Zona geográfica, ej. Baja California  
  3.4 Fechas, ej. 2009 - 2011  
4. Los datos deben tener referencia, i.e. autor, organización a cargo.  
5. Los datos deben estar ligados a una zona geográfica y al tiempo.  

## Referencias

* OpenDataMX http://opendata.mx

## Licencia

![Creative Commons License](http://i.creativecommons.org/l/by-nc-sa/3.0/88x31.png)

Licencia bajo [Creative Commons Attribution-NonCommercial-ShareAlike 3.0 Unported License](http://creativecommons.org/licenses/by-nc-sa/3.0/).

2012 Rodolfo Wilhelmy <rwilhelmy@gmail.com>
