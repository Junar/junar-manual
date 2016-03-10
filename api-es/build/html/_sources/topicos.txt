Autenticación
=============

Existen 3 pasos para intentar identificar quien está llamando a la API

1. Lo primero que se hace es tratar de identificar la cuenta (Account) mediante el dominio. 
2. Luego se intenta identificar la auth_key que debe coincidir con una de las auth_key dentro de las habilitadas en la cuenta.
3. Por último, se trata de identificar el usuario y en caso negativo se lo considera un usuario anónimo.

El sistema tiene dos tipos de auth_key; públicas y privadas. Las privadas las emite cada cuenta a través de su configuración y las publicas entrando al path ``/developers`` dentro del portal de la cuenta.

Autorización
============

Si el dominio no es un dominio que corresponde con una cuenta activa, se deniega el acceso

Si la auth_key no se reconoce o no corresponde a la cuenta, se deniega el acceso

Si la auth_key es pública se chequea el referer y si no se puede identificar (configurable por sistema) no se permite el acceso.

Las auth_key públicas solo permiten operaciones de lectura.

Errores
=======

Datal usa respuesta HTTP convencionales para indicar el éxito o el fracaso de una llamada a la API. Siguiendo los lineamientos HTTP los códigos de rango 2xx indicana éxito y los códigos de rango 4xxx indicana un error.


- ParseError: Error de parseo de datos "400 Bad Request".
- AuthenticationFailed: Error de autenticación "401 Unauthenticated" 
- NotAuthenticated: El query viene sin autenciación "401 Unauthenticated"
- PermissionDenied: Error de acceso no permitido "403 Forbidden".
- NotFound: El recurso no se encuenta "404 Not Found".
- MethodNotAllowed: Se quiere ejecutar un método (POST, PUT, ect) no permitido "405 Method Not Allowed".
- NotAcceptable: Se pide que se devuelva la inforamción en un tipo de dato que no es válido "406 Not Acceptable".
- UnsupportedMediaType: Se intenta subir un tipo de dato que no es válido "415 Unsupported Media Type".
- Throttled: Se super el límite de accesos "429 Too Many Requests".
- ValidationError: Parámetros inválidos "400 Bad Request".
- UnexpectedError: Error inesperado "500 internal Server".

Paginación
==========

Todos los métodos de listado de recursos de la API tienen el funcionamiento de paginado. Cualquiera puede recibir los siguientes parámetros: 

- limit: cantidad de resultados por búsqueda
- offset: número de resultado a partir del cual se realiza la búsqueda.

Cuando aparecen estos parámetros la respuesta se ordena de otra manera y agrega los siguientes campos

- count: la cantidad todal de resultados
- next: un link a la llamada siguiente
- preview: un link a la llamada previa
- result: el listado de resultados.

Un ejemplo de respuesta con limit igual a 2 podría ser

.. code-block:: json

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

Ordenamiento
============

Para poder ordenar los listados de todos los recursos se usa el parámetro ``order`` que puede tener uno de los siguientes valores.

- viewed: se ordena por los mas vistos (vistos en el portal)
- downloaded: se ordena por los recursos mas descargados (acceso a través de la API).
- top: se ordena por una suma de los dos campos anteriores
- last: se ordena por fecha de actualización.

Filtros
=======

Los filtros aplican también a los listados de todos los recursos de la API.

Las búsquedas se realizan utilizando el parámetro ``query`` y actualmente se puede filtrar por categorias utilizando el parámetro ``categories`` que recibe los nombres de las categorias separadas por coma.

Busquedas Múltiples
===================

Existe la posibilidad de tener un listado de múltiples recursos y para ello se creo el siguiente path:

``GET /api/v2/resources``

Para poder filtrar los tipos de recursos se utiliza el parámetro ``resources`` que puede tener mas de un de los siguientes valores separados por coma.

- dt: Conjunto de datos
- ds: Vistas
- vz: Visualizaciones
- db: Colecciones

En los resultados se agrega el parámetro ``type`` para identificar el recurso

Vista de datos
==============

En el recurso vista existe una llamada especial para mostrar todos sus datos: 

::
  
  GET   /api/v2/datastreams/{guid}/data.{format}
  
  
El path que termina en data. ``{format}``  permite retornar un nuevo campo ``result``: donde están los datos del origen del recurso

El ``{format}``  puede contener lo siguiente:

-	json

-	ajson

-	pjson

-	csv

-	xml

-	xls



Ejemplo sobre el retorno de data.json

.. code-block:: json

	{
	  "result": {
		"fLength": 8,
		"fType": "ARRAY",
		"fTimestamp": 1457102225405,
		"fArray": [
		  {
			"fStr": "Congreso Nacional - Biblioteca del Congreso",
			"fType": "TEXT"
		  },
		  {
			"fStr": "",
			"fType": "TEXT"
		  },
		  {
			"fStr": "",
			"fType": "TEXT"
		  },
		  {
			"fStr": "",
			"fType": "TEXT"
		  },
		  {
			"fStr": "",
			"fType": "TEXT"
		  },
		  {
			"fStr": "Cifras en miles de $",
			"fType": "TEXT"
		  },
		  {
			"fStr": "Código BIP",
			"fType": "TEXT"
		  },
		  {
			"fStr": "Nombre de Proyecto",
			"fType": "TEXT"
		  },
		  {
			"fStr": "Monto Identificado",
			"fType": "TEXT"
		  },
		  {
			"fStr": "",
			"fType": "TEXT"
		  },
		  {
			"fStr": "Remodelación Administración Valparaíso",
			"fType": "TEXT"
		  },
		  {
			"fStr": "26,505",
			"fType": "TEXT"
		  },
		  {
			"fStr": "",
			"fHeader": true,
			"fType": "TEXT"
		  },
		  {
			"fStr": "Bóveda y sala preservación colecciones valiosas",
			"fHeader": true,
			"fType": "TEXT"
		  },
		  {
			"fStr": "111,564",
			"fHeader": true,
			"fType": "TEXT"
		  },
		  {
			"fStr": "",
			"fType": "TEXT"
		  },
		  {
			"fStr": "Raparaciones daños terremoto, Sector Biblioteca",
			"fType": "TEXT"
		  },
		  {
			"fStr": "66,440",
			"fType": "TEXT"
		  },
		  {
			"fStr": "",
			"fType": "TEXT"
		  },
		  {
			"fStr": "Proyectos de climatización en Santiago y Valparaíso",
			"fType": "TEXT"
		  },
		  {
			"fStr": "62,101",
			"fType": "TEXT"
		  },
		  {
			"fStr": "TOTAL IDENTIFICADO",
			"fType": "TEXT"
		  },
		  {
			"fStr": "",
			"fType": "TEXT"
		  },
		  {
			"fStr": "266,610",
			"fType": "TEXT"
		  }
		],
		"fRows": 8,
		"fCols": 3
	  },
	  "endpoint": "http://www.dipres.gob.cl/574/articles-74267_doc_xls.xls",
	  "description": "Inversiones BCN durante el año 2011 según art. 24 de Ley de Presupuestos N° 18.482",
	  "parameters": [],
	  "tags": [],
	  "created_at": "2012-06-04T14:12:52",
	  "title": "Nóminas de Iniciativas de Inversión (M$) Biblioteca del Congreso Nacional",
	  "link": null,
	  "user": "publicador",
	  "guid": "NOMIN-DE-BIBLI-DEL-12877",
	  "category_name": "Finanzas"
	}


Ejemplo sobre el retorno de data.pjson

.. code-block:: json
	

	{
	  "result": [
		{
		  "null": ""
		},
		{
		  "null": "Cifras en miles de $"
		},
		{
		  "null": "Monto Identificado"
		},
		{
		  "null": "26,505"
		},
		{
		  "null": "111,564"
		},
		{
		  "null": "66,440"
		},
		{
		  "null": "62,101"
		},
		{
		  "null": "266,610"
		},
		{
		  "timestamp": 1457102225405,
		  "length": 8
		}
	  ],
	  "endpoint": "http://www.dipres.gob.cl/574/articles-74267_doc_xls.xls",
	  "description": "Inversiones BCN durante el año 2011 según art. 24 de Ley de Presupuestos N° 18.482",
	  "parameters": [],
	  "tags": [],
	  "created_at": "2012-06-04T14:12:52",
	  "title": "Nóminas de Iniciativas de Inversión (M$) Biblioteca del Congreso Nacional",
	  "link": null,
	  "user": "publicador",
	  "guid": "NOMIN-DE-BIBLI-DEL-12877",
	  "category_name": "Finanzas"
	}


Ejemplo sobre el retorno de data.ajson

.. code-block:: json



	{
	  "result": [
		[
		  "Congreso Nacional - Biblioteca del Congreso",
		  "",
		  ""
		],
		[
		  "",
		  "",
		  "Cifras en miles de $"
		],
		[
		  "Código BIP",
		  "Nombre de Proyecto",
		  "Monto Identificado"
		],
		[
		  "",
		  "Remodelación Administración Valparaíso",
		  "26,505"
		],
		[
		  "",
		  "Bóveda y sala preservación colecciones valiosas",
		  "111,564"
		],
		[
		  "",
		  "Raparaciones daños terremoto, Sector Biblioteca",
		  "66,440"
		],
		[
		  "",
		  "Proyectos de climatización en Santiago y Valparaíso",
		  "62,101"
		],
		[
		  "TOTAL IDENTIFICADO",
		  "",
		  "266,610"
		]
	  ],
	  "endpoint": "http://www.dipres.gob.cl/574/articles-74267_doc_xls.xls",
	  "description": "Inversiones BCN durante el año 2011 según art. 24 de Ley de Presupuestos N° 18.482",
	  "parameters": [],
	  "tags": [],
	  "created_at": "2012-06-04T14:12:52",
	  "title": "Nóminas de Iniciativas de Inversión (M$) Biblioteca del Congreso Nacional",
	  "link": null,
	  "user": "publicador",
	  "guid": "NOMIN-DE-BIBLI-DEL-12877",
	  "category_name": "Finanzas"
	}

	
Ejemplo sobre el retorno de data.xml

.. code-block:: xml

	<?xml version="1.0" encoding="UTF-8"?>
	<table>
		<row>
			<column>Congreso Nacional - Biblioteca del Congreso</column>
			<column/>
			<column/>
		</row>
		<row>
			<column/>
			<column/>
			<column>Cifras en miles de $</column>
		</row>
		<row>
			<column>Código BIP</column>
			<column>Nombre de Proyecto</column>
			<column>Monto Identificado</column>
		</row>
		<row>
			<column/>
			<column>Remodelación Administración Valparaíso</column>
			<column>26,505</column>
		</row>
		<row>
			<column/>
			<column>Bóveda y sala preservación colecciones valiosas</column>
			<column>111,564</column>
		</row>
		<row>
			<column/>
			<column>Raparaciones daños terremoto, Sector Biblioteca</column>
			<column>66,440</column>
		</row>
		<row>
			<column/>
			<column>Proyectos de climatización en Santiago y Valparaíso</column>
			<column>62,101</column>
		</row>
		<row>
			<column>TOTAL IDENTIFICADO</column>
			<column/>
			<column>266,610</column>
		</row>
	</table>

Ejemplo sobre el retorno de data.csv

.. code-block:: csv

	"Congreso Nacional - Biblioteca del Congreso","",""
	"","","Cifras en miles de $"
	"Código BIP","Nombre de Proyecto","Monto Identificado"
	"","Remodelación Administración Valparaíso","26,505"
	"","Bóveda y sala preservación colecciones valiosas","111,564"
	"","Raparaciones daños terremoto, Sector Biblioteca","66,440"
	"","Proyectos de climatización en Santiago y Valparaíso","62,101"
	"TOTAL IDENTIFICADO","","266,610"
	

	Ejemplo sobre el retorno de data.xls

.. code-block:: xls

	{
	  "fUri": "http://datastore.dev:8888/resources/datal_temp/2016-03-10/temp_1386265881861839185.xlsx",
	  "fNum": 302,
	  "fType": "REDIRECT"
	}


Versiones
=========

Actualmente la api se encuentra en su versión 2. 

Para obtener información de la versión 1 ingresar a http://wiki.junar.com/index.php/API

