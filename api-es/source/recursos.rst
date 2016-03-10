Conjunto de Datos
====================

Las llamadas GET nos devuelve los siguientes parámetros :

::

	GET   /api/v2/datasets.json
	GET   /api/v2/datasets/{guid}.json

- guid : Identificador del recurso,
- title : Título del conjunto de datos
- description : Descripción del conjunto de datos
- category_name : Nombre de la categoría
- endpoint : Url apuntando al recurso con los datos (archivos o página web)
- tags : Opcional. Tags separados por coma.
- user : Usuario que publica el recurso.
- parameters : Parámetros  que tiene el recurso.
- created_at : Fecha de creación de la versión del recurso
- link : Link a la vista del recurso en el portal

Las llamadas POST/PUT/PATCH recibe los siguientes parámetros :

::

	POST  /api/v2/datasets.json
	PUT   /api/v2/datasets/:guid.json
	PATCH /api/v2/datasets/:guid.json



- title : Título del conjunto de datos
- description : Descripción del conjunto de datos
- category : Slug de la categoría para clasificar los recursos. Debe coincidir con alguna de las categorías de la cuenta
- notes : Opcional. Texto de la nota del conjunto de datos
- end_point : Opcional. Url apuntando al recurso con los datos (archivos o página web)
- file : Opcional. Archivo a subir a la plataforma
- license : Opcional. Tipo de licencia que aplica sobre el conjunto de datos
- spatial : Opcional. Zona geográfica a la cual aplica el conjunto de datos
- frequency : Opcional. Frecuencia de actualiación del resucro
- mbox : Opcional. Correo electronico de quien administra el conjunto de datos
- tags : Opcional. Tags separados por coma.



Todas las llamadas en caso de éxito devuelven lo mismo,	por ejemplo:

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

Las llamadas GET nos devuelven los siguientes parámetros :

::

  GET   /api/v2/datastreams.json
  GET   /api/v2/datastreams/{guid}.json
  
  

- guid : Identificador del recurso,
- title : Título del recurso
- description : Descripción del recurso
- category_name : Nombre de la categoría
- tags : Opcional. Tags separados por coma.
- user : Usuario que publica el recurso.
- parameters : Parametros que tiene el recurso.
- created_at : Fecha de creación de la versión del recurso
- link : Link a la vista del recurso en el portal


Las llamadas POST/PUT/PATCH recibe los siguientes parámetros:

::  
  
  POST  /api/v2/datastreams.json
  PUT   /api/v2/datastreams/:guid.json
  PATCH /api/v2/datastreams/:guid.json
  
- title : Título del recurso
- description : Descripción del recurso
- category : Slug de la categoría para clasificar los recursos. Debe coincidir con alguna de las categorías de la cuenta  
- notes : Opcional. Texto de la nota del conjunto de datos
- dataset : GUID del conjunto de dataos asociado a la vista.
- header_row : Opcional. Indice númerico de la fila a usar como cabecera de la tabla comenzando de cero. Por defecto es vacio
- table_id : Opcional Indice numérico de la tabla en el conjunto de datos, comenzando de cero
- tags : Opcional. Tags separados por coma.

El path que termine en data.{format} permite retornar un nuevo campo ``result``: donde están los datos del origen del recurso 


Todas las llamadas en caso de éxito devuelven lo mismo,	por ejemplo:

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


Nuevos tipos de salida se irán incluyendo con el tiempo.


Visualizaciones
====================

Las llamadas GET nos devuelve los siguientes parámetros  :


::

  GET   /api/v2/visualizations.json
  GET   /api/v2/visualizations/{guid}.json


Y los parámetros  son los siguientes.

- guid: Identificador del recurso,
- title: Título del recursos.
- description: Descripción del recursos.
- category_name: Nombre de la categoría.
- endpoint: Viene en null y se utiliza para concoordar con otros recursos de datos
- tags : Opcional. Tags separados por coma.
- user : Usuario que publica el recurso.
- parameters : Viene en null y se utiliza para concoordar con otros recursos de datos
- created_at : Fecha de creación de la versión del recurso
- link : Link a la vista del recurso en el portal

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

Las llamadas GET nos devuelve los siguientes parámetros  :


::

  GET   /api/v2/dashboards.json
  GET   /api/v2/dashboards/{guid}.json


Y los parámetros  son los siguientes.

- guid: Identificador del recurso,
- title: Título del recurso
- description: Descripción del recurso
- category_name: Nombre de la categoría
- endpoint: Viene en null y se utiliza para concoordar con otros recursos de datos
- tags : Opcional. Tags separados por coma.
- user : Usuario que publica el recurso.
- parameters : Viene en null y se utiliza para concoordar con otros recursosde datos
- created_at : Fecha de creación de la versión del recurso
- link : Link a la vista del recurso en el portal

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
	
	
	
	









