2. Supported Methods
====================

GET Lists
---------

Retrieve a list of all available resources

:: 
  
  GET /api/v2/resources

Retrieve a list of data views

::

  GET /api/v2/datastreams

Retrieve a list of datasets

::

  GET /api/v2/datasets

Retrieve a list of visualizations.

::

  GET /api/v2/visualizations

In no GET parameters are included, the API will return all resources associated with the account. The following parameters can be included in the GET query to sort and/or filter.

+ query: string of text to search in all parameters of the data view

+ offset: starting from which data view will return results

+ limit: used with offset can limit the amount of results

+ order: it can be top, viewed, downloaded o last which sorts the results accordingly.

+ categories: lists the names of the categories, separated by commas

+ resources: a list of resources by type (‘ds’, ‘dt’, or ‘vz’).

+ count: the total amount of results

+ next: a link to the next API request according to pagination

+ previous: a link to the previous API request according to pagination

+ result: an array with the final results

An example of results with limit 2 would be as follows

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

Retrieve information associated to a data view

::

  GET /api/v2/datastreams/:guid

Retrieve information and data content associated to a data view

::

  GET /api/v2/datastreams/:guid/data

Retrieve information associated to a dataset

::

  GET /api/v2/datasets/:guid

Retrieve information associated to a visualization

::
  
  GET /api/v2/visualizations/:guid

An example output of a data view

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

