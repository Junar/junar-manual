Conjunto de Datos
====================

Los path con sus métodos existentes son


::

  GET   /api/v2/datasets.json
  GET   /api/v2/datasets/{guid}.json
  POST  /api/v2/datasets.json
  PUT   /api/v2/datasets/:guid.json
  PATCH /api/v2/datasets/:guid.json


Y los parametros son los siguientes.

- guid (L): Identificador del recurso,
- title (E/L): Título del conjunto de datos
- description (E/L): Descripción del conjunto de datos
- category (E): Slug de la categoría para clasificar los recursos. Debe coincidir con alguna de las categorías de la cuenta
- category_name (L): Nombre de la categoría
- notes (E): Opcional. Texto de la nota del conjunto de datos
- end_point (E): Opcional. Url apuntando al recurso con los datos (archivos o página web).
- endpoint (L): Url apuntando al recurso con los datos (archivos o página web)
- file (E): Opcional. Archivo a subir a la plataforma
- license (E): Opcional. Tipo de licencia que aplica sobre el conjunto de datos
- spatial (E): Opcional. Zona geográfica a la cual aplica el conjunto de datos
- frequency (E): Opcional. Frecuencia de actualiación del resucro
- mbox (E): Opcional. Correo electronico de quien administra el conjunto de datos
- tags (E/L): Opcional. Tags separados por coma.
- user (L): Usuario que publica el recurso.
- parameters (L): Parametros que tiene el recurso.
- created_at (L): Fecha de creación de la versión del recurso
- link (L): Link a la vista del recurso en el portal

Por ejemplo el ``GET   /api/v2/datasets/{guid}.json`` muestra los siguientes datos:

.. code-block:: json

  {
    "result": null,
    "endpoint": "file://1995/46721/71341786542282142096488420671282999110",
    "description": "res",
    "parameters": null,
    "tags": [ "" ],
    "created_at": "2016-02-10T17:10:39",
    "title": "resto",
    "link": null,
    "user": "junarcity",
    "guid": "RESTO",
    "category_name": "Financial"
  }

Vista
=====

Los path con sus métodos existentes son


::

  GET   /api/v2/datastreams.json
  GET   /api/v2/datastreams/{guid}.json
  GET   /api/v2/datastreams/{guid}/data.{format}
  POST  /api/v2/datastreams.json
  PUT   /api/v2/datastreams/:guid.json
  PATCH /api/v2/datastreams/:guid.json


Y los parametros son los siguientes.


- guid (L): Identificador del recurso,
- title (E/L): Título del recurso
- description (E/L): Descripción del recurso
- category (E): Slug de la categoría para clasificar los recursos. Debe coincidir con alguna de las categorías de la cuenta
- category_name (L): Nombre de la categoría
- notes (E): Opcional. Texto de la nota del conjunto de datos
- dataset (E): GUID del conjunto de dataos asociado a la vista.
- header_row (E): Opcional. Indice númerico de la fila a usar como cabecera de la tabla comenzando de cero. Por defecto es vacio
- table_id (E): Opcional Indice numérico de la tabla en el conjunto de datos, comenzando de cero
- tags (E/L): Opcional. Tags separados por coma.
- user (L): Usuario que publica el recurso.
- parameters (L): Parametros que tiene el recurso.
- created_at (L): Fecha de creación de la versión del recurso
- link (L): Link a la vista del recurso en el portal

El path que termine en data.{format} permite retornar un nuevo campo ``result``: donde están los datos del origen del recurso 

Por ejemplo el ``GET   /api/v2/datastreams/{guid}.json`` muestra los siguientes datos: 

.. code-block:: json

  {
    "result": null,
    "endpoint": "file://1995/46721/313214253556015558595838280659574174401",
    "description": "prueba mesa copypaste",
    "parameters": [ ],
    "tags": [ ],
    "created_at": "2016-02-23T10:34:42",
    "title": "prueba",
    "link": null,
    "user": "junarcity",
    "guid": "PRUEB",
    "category_name": "Financial"
  }


Estructura JSON de los datos de Origen
--------------------------------------

El resultado es un objeto Argument, el cual es una estructura recursiva de datos que contiene las siguientes propiedades:

fType: Indica el tipo de dato del Argument. Sus valores pueden ser ARRAY | TEXT | NUMBER | DATE. El tipo ARRAY indica que el argumento contiene una TABLA.

Cuando el tipo de datos es un ARRAY fRows y fCols indican el número de filas y columnas de la TABLA. De la misma manera, fArray contiene los datos de la TABLA como un arreglo de objetos Argument.

Cuando el tipo de datos es TEXT el valor está contenido en fStr. Para un tipo de dato NUMBER el valor esta contenido en fNum. Para un tipo de dato DATE el valor está contenido en fNum como epoch time.

Un Argument puede contener un enlace LINK. En esos casos, fType contiene LINK, la uri correspondiente viene en fUri y el texto a mostrar está contenido en fStr.

Cuando el tipo de datos es ERROR, ocurrió un error al ejecutar la vista de datos. El mensaje de error estará contenido en fStr.

Cuando un error ocurre, el resultado es reemplazado con el último resultado que fue ejecutado correctamente.

Para reconocer si el resultado está actualizado, existe una propiedad adicional llamada fTimestamp. Contiene el tiempo POSIX de cuando fue **accedida la fuente de datos** de forma exitosamente por última vez. Si fTimestamp tiene un valor igual a 0, significa que el resultado fue obtenido en ese instante.

Modificar el formato de salida
-----------------------------

Puede modificarse el formato de salida de la API cambiando la extensión del argumento data en la llamada realizada al recurso. Por defecto el argumento data es llamado como data.json, lo que trae un objeto JSON con la estructura anterior. Otros formatos posibles son:

- data.json: Trae los datos como json
- data.ajson : Trae los datos como un array json.
- data.ajson : Trae los datos como un json formateado.
- data.xml : Trae los datos como una estructura XML
- data.csv : Trae los datos como un documento CSV
- data.xls : Trae una url dentro de un json para redireccionar hacia un documento XLS

Nuevos tipos de salida se irán incluyendo con el tiempo.


Visualizaciones
====================

Los path con sus métodos existentes son


::

  GET   /api/v2/visualizations.json
  GET   /api/v2/visualizations/{guid}.json


Y los parametros son los siguientes.

- guid: Identificador del recurso,
- title: Título del recursos.
- description: Descripción del recursos.
- category_name: Nombre de la categoría.
- endpoint: Viene en null y se utiliza para concoordar con otros recursosde datos
- tags (E/L): Opcional. Tags separados por coma.
- user (L): Usuario que publica el recurso.
- parameters (L): Viene en null y se utiliza para concoordar con otros recursosde datos
- created_at (L): Fecha de creación de la versión del recurso
- link (L): Link a la vista del recurso en el portal

Por ejemplo el ``GET   /api/v2/visualizations/{guid}.json`` muestra los siguientes datos: 

.. code-block:: json

  {
    "result": null,
    "endpoint": null,
    "description": "prueba apeso 2",
    "parameters": [ ],
    "tags": [ ],
    "created_at": "2016-03-04T17:43:04",
    "title": "prueba p",
    "link": null,
    "user": "junarcity",
    "guid": "PRUEB-P",
    "category_name": "Financial"
  }

Colecciones
===========

Los path con sus métodos existentes son


::

  GET   /api/v2/dashboards.json
  GET   /api/v2/dashboards/{guid}.json


Y los parametros son los siguientes.

- guid: Identificador del recurso,
- title: Título del recurso
- description: Descripción del recurso
- category_name: Nombre de la categoría
- endpoint: Viene en null y se utiliza para concoordar con otros recursosde datos
- tags (E/L): Opcional. Tags separados por coma.
- user (L): Usuario que publica el recurso.
- parameters (L): Viene en null y se utiliza para concoordar con otros recursosde datos
- created_at (L): Fecha de creación de la versión del recurso
- link (L): Link a la vista del recurso en el portal

Por ejemplo el ``GET   /api/v2/dashboards/{guid}.json`` muestra los siguientes datos: 

.. code-block:: json

	{
		"result": null,
		"endpoint": null,
		"description": "ph",
		"parameters": null,
		"tags": [ "" ],
		"created_at": "2016-02-11T09:07:19",
		"title": "Prueba HTML",
		"link": null,
		"user": "junarcity",
		"guid": "PRUEB-HTML",
		"category_name": "Category",
		"resources": 
		[
			{
				"doc_type": "datastream",
				"w": 4,
				"parameters": "",
				"h": 4,
				"last_revision": 
				{
					"slug": "api-publish-test",
					"modified_at": "2016-02-11T09:08:08",
					"id": 211856,
					"parameters": [],
					"title": "API Publish Test"
				},
		 
				"order": 0,
				"link": "http://junarcity.site.beta.junar.com/dataviews/225402/-/",
				"last_published_revision": 
				{
					"slug": "api-publish-test",
					"modified_at": "2016-02-11T09:08:08",
					"id": 211856,
					"parameters": [],
					"title": "API Publish Test"
				},
					"y": 0,
					"x": 0,
					"guid": "API-PUBLI-TEST-50073",
					"type": "ds",
					"id": 225402
			},
			{
				"parameters": "",
				"h": 4,
				"html": "<iframe width='420' height='315' src='https://www.youtube.com/embed/v2I9eSUTPjY' frameborder='0' allowfullscreen></iframe>",
				"w": 4,
				"y": 0,
				"x": 4,
				"type": "html",
				"order": 0
			}
		]
	}



