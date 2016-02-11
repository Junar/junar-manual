1. Data Resources
=================

All API resources, except where an exception is declared, will be returned as an object with the following attributes:

+ guid: Unique identifier of the resource.

+ title: Title of the resource.

+ description: Description of the resource.

+ user: Username of the creator of the resource.

+ tags: Tags associated with the resource.

+ created_at: Creation date of the resource.

+ endpoint: Location of the source of the resource.

+ link: URL to the resource on the Open Data portal.

+ category_name: Name of the category of the resource.

+ parameters (data views only) : Dynamic values, defined by the user on the Open Data portal, that allow custom filtering of a data view based on rules set during the creation of the data view.

+ result (data views only) : content of the data view

+ type (search results only): a two character string of text identifying a resource as a data view (‘ds’), a dataset (‘dt’) or a visualization (‘vz’)

:: 
 
  {

  "guid": "INDIC-DIARI", 

  "title": "Indicadores Diarios", 

  "description": "Datos obtenidos en l\u00ednea del Banco Central de Chile.", 

  "user": "cne", 

  "tags": [], 

  "created_at": "2015-07-28 11:20:24", 

  "endpoint": "https://docs.google.com/spreadsheets/d/1wiUQlRiIPMbTWFDVn3Ug8Rp15yHuXwsCU3ZGz39xJhg/pub?gid=0&single=true&output=csv", 

  "link": "http://datos.energiaabierta.cne.cl/datastreams/94287/indicadores-diarios/", 

  "category_id": 41111,

  "category_name": "Internacional",

  "parameters": [

    {

      "name": "param0",

      "position": 0,

      "description": "Un parametro",

    },

    {

      "name": "param0",

      "position": 0,

      "description": "Un parametro",

    }

  ],

  "result": {

    "fType":"ARRAY",

    "fArray": [

      {

        "fStr":"Indicador",

        "fType":"TEXT",

        "fHeader":true

      },

      {

        "fStr":"Valor",

        "fType":"TEXT",

        "fHeader":true

      },

      {

        "fStr":"UF",

        "fType":"TEXT"

      },

      {

        "fNum":25152.06,

        "fType":"NUMBER",

        "fDisplayFormat": {"fPattern":"#,###.##", "fLocale":"es"}

      },

      {

        "fStr":"UTM (Agosto)",

        "fType":"TEXT"

      },

      {

        "fNum":44067.0,

        "fType":"NUMBER",

        "fDisplayFormat":{"fPattern":"#,###.##","fLocale":"es"}

      },

      {

        "fStr":"Dólar Observado",

        "fType":"TEXT"

      },

      {

        "fNum":689.36,

        "fType":"NUMBER",

        "fDisplayFormat":{"fPattern":"#,###.##","fLocale":"es"}

      },

      {

        "fStr":"Dólar Observado19-08-2015",

        "fType":"TEXT"

      },

      {

        "fNum":697.25,

        "fType":"NUMBER",

        "fDisplayFormat":{"fPattern":"#,###.##","fLocale":"es"}

      }

    ],

    "fRows":4,

    "fCols":2,

    "fTimestamp":1439937039829,

    "fLength":0

  }, 

  }

Resources managed by the API are:

+ datasets

+ data views

+ visualizations

