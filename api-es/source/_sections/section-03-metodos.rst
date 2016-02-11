3. Métodos
==========

GET Listados
------------

Busca un litado de recursos

::

  GET /api/v2/resources

Busca un listado de datastreams.

::

  GET /api/v2/datastreams


Busca un listado de datasets.

::
  
  GET /api/v2/datasets

Busca un listado de visualizaciones.

::

  GET /api/v2/visualizations

Si no hay parametros GET la API devuelve todos los recursos que le corresponden a la cuenta y sino se pueden pasar los siguientes parametros para ordenar o filtrar la búsqueda.

+ query: texto que se busca en todos los parametros del datastream

+ offset: a partir de que datastream traer el resultado (se usa para paginar)

+ limit: junto con offset se usa para limitar la cantidad de resultados

+ order: pudiendo ser su valor top, viewed, downloaded o last y ordenando el resultado según esos criterios.

+ categories: listado de los nombres de categorias separados por coma

+ resources: listado de recursos (Ej. "dt,ds,vz")

Cuando se aplican limites a las busquedas el resultado se devuelve encapsulando los objetos en otros paramteros.

+ count: el total de los resultados si no hubiera paginado

+ next: un link a la próxima petición de la api según el paginado

+ previous: un lina a la previa petición de la api según el paginado

+ result: un array con el resultado final

Un ejemplo de resultados con limit igual a 2 sería asi

::

  {
    "count": 20,
    "next": "http://api.dev:8080/api/v2/datasets/?auth_key=576bba0dd5a27df9aaac12d1d7ec25c8411fe29e&limit=2&offset=2",
    "previous": null,
    "results": [
        {
            "endpoint": "http://datastorage.mineduc.cl/tablas/Nivel_Calificaciones_anio_2006.csv",
            "description": "Descripcion del conjuto de datos",
            "parameters": [],
            "tags": [
                ""
            ],
            "created_at": 1337611920,
            "title": "Nivel de Calificaciones 2006",
            "link": "http://microsites.dev:8080/datasets/61649/nivel-de-calificaciones-2006",
            "user": "publicador",
            "guid": "DATASET-ID-61649",
            "category_name": "Educación"
        },
        {
            "endpoint": "http://datastorage.mineduc.cl/tablas/Nivel_Rendimiento_anio_2010.csv",
            "description": "Descripcion del conjuto de datos",
            "parameters": [],
            "tags": [
                ""
            ],
            "created_at": 1337611453,
            "title": "Nivel de Rendimiento 2010",
            "link": "http://microsites.dev:8080/datasets/61648/nivel-de-rendimiento-2010",
            "user": "publicador",
            "guid": "DATASET-ID-61648",
            "category_name": "Educación"
        }
    ]
  }

GET
---

Trae la información asociada a una vista

::

  GET /api/v2/datastreams/:guid

Trae la información asociada completa (incluye los valores de la vista) a una vista

::

  GET /api/v2/datastreams/:guid/data

Trae la información asociada a un dataset

::
  
  GET /api/v2/datasets/:guid

Trae la información asociada a una visualización

::

  GET /api/v2/visualizations/:guid

Un ejemplo de resultado de un datastream sería así

::

  {
    "endpoint": "http://datastorage.mineduc.cl/tablas/Nivel_Calificaciones_anio_2006.csv",
    "description": "Contiene indicadores para promedio anual de calificaciones (para Enseñanza Básica de Niños y Enseñanza Media de Jóvenes).",
    "parameters": [],
    "tags": [],
    "created_at": "2012-06-04T14:12:52",
    "title": "Nivel Calificaciones 2006",
    "link": null,
    "user": "publicador",
    "guid": "NIVEL-DE-CALIF-2006-53010",
    "category_name": "Educación"
  }

POST / PUT / PATCH
------------------
Creación, Edición y Edición Parcial de recursos.

Al momento solo podemos crear y editar datasets y vistas. Y para poder hacerlo hay que tener acceso a una clave privada que esté asociada a un usuario.

Por lo tanto la operación de edición y creación se realiza sobre las últimas revisiones de los recursos y no sobre laas últimas revisiones publicadas de los mismos.

Datasets
~~~~~~~~

::

  POST /api/v2/datasets

  PUT/PATCH /api/v2/datasets/:guid


+ title: Título del conjunto de datos

+ description: Descripción del conjunto de datos

+ category: Slug de la categoría para clasificar los recursos. Debe coincidir con alguna de las categorías de la cuenta

+ notes: Opcional. Texto de la nota del conjunto de datos

+ end_point: Opcional. Url apuntando al recurso con los datos (archivos o página web).

+ file: Opcional. Archivo a subir a la plataforma

+ license: Opcional. Tipo de licencia que aplica sobre el conjunto de datos

+ spatial: Opcional. Zona geográfica a la cual aplica el conjunto de datos

+ frequency: Opcional. Tipo de licencia que aplica sobre el conjunto de datos

+ mbox: Opcional. Correo electronico de quien administra el conjunto de datos

+ tags: Opcional. Tags separados por coma.


Datastreams
~~~~~~~~~~~

:: 
  
  POST /api/v2/datastreams

+ title: Título del conjunto de datos

+ description: Descripción del conjunto de datos

+ category: Slug de la categoría para clasificar los recursos. Debe coincidir con alguna de las categorías de la cuenta

+ notes: Opcional. Texto de la nota del conjunto de datos

+ table_id: Opcional. Indice de la tabla en el conjunto de datos, comenzando de cero.

+ header_row: Opcional. Indice de la fila a usar como cabecera de la tabla comenzando de cero. Por defecto es vacio

+ dataset: GUID del conjunto de datos asociado a la vista

+ tags: Opcional. Tags separados por coma.

Ejemplo de llamada para crear un datastream

::

  curl -H 'Accept: application/json; indent=4' -H "Content-Type: application/json" -X POST -d @api/tests/datastream-ok.json "http://api.dev:8080/api/v2/datastreams.json?auth_key=576bba0dd5a27df9aaac12d1d7ec25c8411fe29e"
