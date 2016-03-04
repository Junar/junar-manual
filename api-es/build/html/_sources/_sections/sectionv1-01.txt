1. Junar API
============

La mayoría de los métodos retorna sus resultados en formato JSON, excepto el metodo invoke donde puede elegirse entre varios formatos de salida.

Cada portal de Datos Abiertos tiene sus propios módulos de API con sus propias limitaciones respecto a consultas (requests) por minuto y totales mensuales. Por favor referirse a los sitios de desarrolladores de cada uno o contactennos a developers@junar.com para más detalles.

La API de Junar Community usa un ambiente de pruebas apisandbox que está limitado a 1000 reqs/mes y 1 req/5 seg. Si tienen necesidades que van más allá de esos límites, no duden en contactarnos a developers@junar.com.

La API soporta protocolos HTTP/REST y está organizada en los siguientes módulos:

1. Métodos para consumir vistas de datos

2. Métodos para accesar una coleccion particular o las propiedades de objeto de una vista de datos

3. Métodos para buscar colecciones y vistas de datos

4. Métodos para obtener métricas para la cuenta de datos abiertos


1.1		Snippets de código y API Wrappers
-----------------------------------------

Junar API Python Client es una libreria del lado del cliente para implementar la API de Junar.

Junar API PHP Client es una libreria del lado del cliente para implementar la API de Junar.

Junar API Java Client es una libreria del lado del cliente para implementar la API de Junar.

Junar SDK for Node JS es una implementación SDK para la API de Junar.

Junar JSON Structure Parsing es un ejemplo de código en Python para parsear la estructura JSON devuelta por Junar.

Using prettyjson Cómo usar el formato de salida prettyjson


1.2		Metodos para consumir Vistas de Datos
---------------------------------------------

1.2.1	Consumiendo una Vista de Datos
......................................

Ejecuta una vista de datos y devuelve sus resultados en formato JSON

1.2.1.1 	Estructura JSON
~~~~~~~~~~~~~~~~~~~~~~~~~~~

El resultado es un objeto Argumento, el cual es una estructura recursiva de datos que contiene las siguientes propiedades:

fType: Indicates el tipo de dato del Argument. Sus valores pueden ser ARRAY | TEXT | NUMBER. El tipo ARRAY indica que el argumento contiene una TABLA.

Cuando el tipo de datos es un ARRAY fRows y fCols indican el número de filas y columnas de la TABLA. De la misma manera, fArray contiene los datos de la TABLA como un arreglo de objetos Argument.

Cuanto el tipo de datos es TEXT el valor está contenido en fStr. Para un tipo de dato NUMBER el valor esta contenido en fNum. fBool no se usa en estos dias.

Un Argument puede contener un enlace LINK. En esos casos, fType contiene LINK, la uri correspondiente viene en fUri y el texto a mostrar está contenido en fStr.

Cuando el tipo de datos es ERROR, ocurrió un error al ejecutar la vista de datos. El mensaje de error estará contenido en fStr.

Cuando un error ocurre, el resultado es reemplazado con el último resultado que fue ejecutado correctamente.

Para reconocer si el resultado está actualizado, existe una propiedad adicional llamada fTimestamp. Contiene el tiempo POSIX de cuando fue ejecutada exitosamente por última vez. Si fTimestamp tiene un valor igual a 0, significa que el resultado fue obtenido en ese instante.

La respuesta está limitada por defecto a 1000 filas. Para obtener más resultados deben utilizarse en la consulta los parámetros limit y page.

1.2.2 	URL
...........

http://apisandbox.junar.com/dataviews/invoke/{id}

1.2.3	Métodos de consulta soportados
......................................

GET

1.2.4 	Parámetros
..................

+ GUID : Requerido. Un Identificador Único Global que identifica cada recursos de datos en el catálogo de datos abiertos de Junar.

+ auth_key : Requerido. Se obtiene desde una página de desarrolladores de Junar (sitio de desarrolladores de Junar Community aquí)

+ callback : Opcional. Si se entrega, la respuesta usará el formato JSONP con un callback del nombre dado.

+ output : Opcional. La Estructura del JSON Junar explicada abajo es el formato de salida por defecto. Otras opciones son:

  + prettyjson: Permite clarificar cada columna con un alias distintivo configurado durante el proceso de recolección y creación de las vistas.
  
  + json_array: Una respuesta con un array de arrays.
  
  + csv: Valores separados por coma.
  
  + xml: Retorna un XML usando la misma configuración de alias que prettyjson.

1.2.5 	Ejemplo
...............

http://paloalto.cloudapi.junar.com/dataviews/invoke/PALO-ALTO-POPUL-BY-12452?auth_key=YOUR_AUTH_KEY

::

  {
   "id":"PALO-ALTO-POPUL-BY-12452",
   "title":"Palo Alto Population by Age Groups",
   "description":"Source: US Census Bureau",
   "user":"cityofpaloalto",
   "result":{
      "fArray":[
         {
            "fStr":"People QuickFacts",
            "fType":"TEXT",
            "fHeader":true
         },
         {
            "fStr":"Palo Alto",
            "fType":"TEXT",
            "fHeader":true
         },
         {
            "fStr":"Persons under 5 years, percent, 2010",
            "fType":"TEXT"
         },
         {
            "fStr":"5.4%",
            "fType":"TEXT"
         },
         {
            "fStr":"Persons under 18 years, percent, 2010",
            "fType":"TEXT"
         },
         {
            "fStr":"23.4%",
            "fType":"TEXT"
         },
         {
            "fStr":"Persons under 64 years, percent, 2010",
            "fType":"TEXT"
         },
         {
            "fStr":"82.9%",
            "fType":"TEXT"
         },
         {
            "fStr":"Persons 65 years and over",
            "fType":"TEXT"
         },
         {
            "fStr":"17.1%",
            "fType":"TEXT"
         }
      ],
      "fRows":5,
      "fCols":2,
      "fType":"ARRAY",
      "fTimestamp":1349219063874,
      "fLength":0
   },
   "tags":[
      "palo alto",
      "Population",
      "2010",
      "age groups",
      "us census",
      "us"
   ],
   "created_at":"2012-07-30 23:13:08",
   "source":"73025-palo-alto-population-by-age-groups.csv",
   "link":"http://paloalto.opendata.junar.com/dataviews/73247/palo-alto-population-by-age-groups/"
  }


1.2.6 Ejemplo de formato de salida
..................................

http://paloalto.cloudapi.junar.com/dataviews/invoke/PALO-ALTO-POPUL-BY-12452?auth_key=YOUR_AUTK_KEY&output=xml

::

  <table>
	<row>
		<column>People QuickFacts</column>
		<column>Palo Alto</column>
	</row>
	<row>
		<column>Persons under 5 years, percent, 2010</column>
		<column>5.4%</column>
	</row>
	<row>
		<column>Persons under 18 years, percent, 2010</column>
		<column>23.4%</column>
	</row>
	<row>
		<column>Persons under 64 years, percent, 2010</column>
		<column>82.9%</column>
	</row>
	<row>
		<column>Persons 65 years and over</column>
		<column>17.1%</column>
	</row>
  </table>

1.2.7 	Consumiendo una vista con parámetros
............................................

Una vista de datos puede contener parámetros. Los parámetros pueden agregarse a la vista de datos solamente durante el proceso de creación. Estos parámetros pueden estar mapeados contra un formulario en un sitio web, directamente contra la URL de la fuente de datos o contra columnas de datos dentro de la tabla sobre la cual se crea la vista. La sintaxis apropiada para agregar parámetros en una solicitud API es

pArgumentN=X

Donde N es la posición del parámetro en la vista, empezando desde cero y X es el valor que tendrá dicho parámetro.

Ejemplo

http://lima.cloudapi.junar.com/dataviews/invoke/VOLUM-DE-PRODU-INGRE-POR?auth_key=YOUR_AUTH_KEY&pArgument0=MAIZ

::

  {
   "id":"VOLUM-DE-PRODU-INGRE-POR",
   "title":"Volumen de Productos Ingresados - Por Producto",
   "description":"Detalla el volumen de productos ingresados por producto seleccionado.",
   "user":"Lima",
   "result":{
      "fArray":[
         {
            "fStr":"AÑO",
            "fType":"TEXT",
            "fHeader":true
         },
        ...
         {
            "fStr":"",
            "fType":"TEXT"
         },
         {
            "fStr":"",
            "fType":"TEXT"
         },
         {
            "fStr":"",
            "fType":"TEXT"
         },
         {
            "fStr":"16477",
            "fType":"TEXT"
         }
      ],
      "fRows":8,
      "fCols":16,
      "fType":"ARRAY",
      "fTimestamp":0,
      "fLength":0
   },
   "tags":[
      "Volumen",
      "productos",
      "ingresados"
   ],
   "created_at":"2012-10-24 10:49:24",
   "source":"Volumen_de_productos_ingresados.xls",
   "link":"http://lima.opendata.junar.com/dataviews/75010/volumen-de-productos-ingresados-por-producto/",
   "parameters":[
      {
         "position":0,
         "name":"Producto",
         "description":"Producto"
      }
   ]
  }


1.2.8 	Filtrar los resultados de una vista
...........................................

La API de Datos Abiertos de Junar permite a sus usuarios filtrar los resultados obtenidos durante la solicitud de una vista de datos utilizando la siguiente sintaxis:

::

  http://lasvegas.cloudapi.junar.com/datastreams/invoke/DEVEL-SERVI-PROJE-INSPE?auth_key=YOUR_AUTH_KEY&filter0=column4[contains]GAS&filter1=column7[==]RANDOLPH&where=(filter0 and filter1)

Esto retornaría todos los datos que contengan la palabra GAS en la columna 4 y la palabra RANDOLPH en la columna 7.

Los filtros pueden ir desde 0 a N (filter0, filter1...filterN) y tienen la siguiente sintaxis:

::

  operando0 | operador lógico | operando1

Los operandos pueden ser : rownum (número de fila), columnN (columna N, donde N es un entero que va desde 0 a N) o una cadena de texto.

Los Operadores Lógicos pueden ser [==], [>], [<], [!=], [contains], [>=], [<=]. Los corchetes [] deben ser incluidos. Si el contenido es una cadena de texto son sensibles a mayúsculas.

La operación where tiene una expresión lógica para unir filtros de manera similar al select_statement. En este caso, se utilizaría (filter0 and filter1). Las expresiones and y or sirven para diferenciar la relación entre los filtros y pueden concatenarse tanto como fuera necesario para cumplir una cierta condicion por ejemplo: (filter0 and filter1) or filter2.

Cuando se agrega una fecha como parámetro debe incluirse utilizando el formato MM/dd/aaaa.


1.2.9 	Formateo de Datos
.........................

Permite a los desarrolladores el dar formato a columnas de datos con un tipo y formato que afectará cómo son devueltos los datos de la consulta. Usa la siguiente sintaxis y debe aplicarse a una columna que ya haya sido objeto de un filtro :

::

  format={"table":[{"id":"column10", "type":"DATE", "format":{"country":"ES", "lang":"es", "style": "dd/MM/yyyy"}}]}


Donde

+ id : Corresponde a la posición de la columna a filtrar. Esta columna debe haber sido objeto de un filtro para poder ser formateada.

+ type: El tipo de dato que contiene la columna. Por defecto todas las columnas se consideran de tipo texto (TEXT), pero pueden cambiarse a fecha (DATE) o número (NUMBER).

+ format : Dependiendo del tipo elegido puede requerir la siguiente información.

El formato DATE requiere country (país), lang (idioma) y style (estilo). Los valores de country y lang corresponden al formato ISO, mientras que posibles valores de style pueden encontrarse aquí:

http://docs.oracle.com/javase/7/docs/api/java/text/SimpleDateFormat.html

::

  {"table":[{"id":"column10", "type":"DATE", "format":{"country":"CL", "lang":"es", "style": "dd/MM/yyyy"}}]}

El formato NUMBER requiere country (país), lang (idioma) y pattern (patrón). Los patrones permiten definir cómo se separarán los miles y los decimales o si las cifran irán agrupadas de acuerdo a estándares asociados al país e idioma elegidos

::

  {"table":[{"id":"column4", "type":"NUMBER", "format":{"country":"US", "lang":"es", "pattern":"", "decimals":"", "thousands":""}}]}

Ejemplo

..../invoke/SACRA-ANNUA-CRIME-STATS?...&filter0=column0[==]Homicide&filter1=column4[>]0&where=(filter0 or filter1)&format={"table":[{"id":"column4", "type":"NUMBER", "format":"format":{"country":"US", "lang":"es", "pattern":"", "decimals":"", "thousands":""}}]}


::

  {
  "id": "SACRA-ANNUA-CRIME-STATI",
  "title": "Sacramento Annual Crime Statistics",
  "description": "Year to date information on different types of crimes and variation 2012 2013",
  "user": "sacramento",
  "result": {
    "fType": "ARRAY",
    "fArray": [
      {
        "fStr": "Homicide",
        "fType": "TEXT"
      },
      {
        "fStr": "7",
        "fType": "TEXT"
      },
      {
        "fStr": "10",
        "fType": "TEXT"
      },
      {
        "fNum": 3.0,
        "fType": "NUMBER"
      },
      {
        "fStr": "42.9%",
        "fType": "TEXT"
      },
      {
        "fStr": "Robbery",
        "fType": "TEXT"
      },
      {
        "fStr": "275",
        "fType": "TEXT"
      },
      {
        "fStr": "309",
        "fType": "TEXT"
      },
      {
        "fNum": 34.0,
        "fType": "NUMBER"
      },
      {
        "fStr": "12.4%",
        "fType": "TEXT"
      },
      {
        "fStr": "Burglary",
        "fType": "TEXT"
      },
      {
        "fStr": "944",
        "fType": "TEXT"
      },
      {
        "fStr": "1,084",
        "fType": "TEXT"
      },
      {
        "fNum": 140.0,
        "fType": "NUMBER"
      },
      {
        "fStr": "14.8%",
        "fType": "TEXT"
      }
    ],
    "fRows": 3,
    "fCols": 5,
    "fTimestamp": 0,
    "fLength": 0
  },
  "tags": [
    "Sacramento",
    "POLICE",
    "crime"
  ],
  "created_at": "2013-05-28 00:27:27",
  "source": "http://www.sacpd.org/crime/stats/",
  "link": "http://sacramento.opendata.junar.com/datastreams/77447/sacramento-annual-crime-statistics/"
  }


1.3 Métodos para accesar objetos
--------------------------------

1.3.1 	Información de vistas de datos
......................................

Retorna la información general de la vista según el GUID entregado

**URL**

http://apisandbox.junar.com/dataviews/{id}

**Métodos de Consulta Soportados**

GET

**Parámetros**

+ GUID : Requerido. Un Identificador Único Global que identifica cada recursos de datos en el catálogo de datos abiertos de Junar.

+ auth_key : Requerido. Una clave de autenticación obtenida desde una página de desarrolladores.

+ callback : Opcional. Si se envia, la respuesta usará el formato JSONP con un callback del nombre dado.


Ejemplo

http://paloalto.cloudapi.junar.com/dataviews/PALO-ALTO-POPUL-BY-12452?auth_key=YOUR_AUTH_KEY

::

  {
   "id":"PALO-ALTO-POPUL-BY-12452",
   "title":"Palo Alto Population by Age Groups",
   "description":"Source: US Census Bureau",
   "user":"cityofpaloalto",
   "tags":[
      "palo alto",
      "Population",
      "2010",
      "age groups",
      "us census",
      "us"
   ],
   "created_at":"2012-07-30 23:13:08",
   "source":"73025-palo-alto-population-by-age-groups.csv",
   "link":"http://paloalto.opendata.junar.com/dataviews/73247/palo-alto-population-by-age-groups/"
  }


1.3.2 	Información de Vista de Datos con Parámetros
....................................................

Ejemplo

http://lima.cloudapi.junar.com/dataviews/VOLUM-DE-PRODU-INGRE-POR?auth_key=YOUR_AUTH_KEY

::

  {
   "id":"VOLUM-DE-PRODU-INGRE-POR",
   "title":"Volumen de Productos Ingresados - Por Producto",
   "description":"Detalla el volumen de productos ingresados por producto seleccionado.",
   "user":"Lima",
   "tags":[
      "Volumen",
      "productos",
      "ingresados"
   ],
   "created_at":"2012-10-24 10:49:24",
   "source":"Volumen_de_productos_ingresados.xls",
   "link":"http://lima.opendata.junar.com/dataviews/75010/volumen-de-productos-ingresados-por-producto/",
   "parameters":[
      {
         "position":0,
         "name":"Producto",
         "description":"Producto"
      }
   ]
  }

1.3.3 	Información de las Colecciones
......................................

Retorna la información general de la colección para un GUID dado, incluyendo un resumen de las vistas que contiene

**URL**

http://apisandbox.junar.com/dashboards/{id}

**Métodos de Consulta Soportados**

GET

**Parámetros**

+ auth_key -> Requerido. Auth key obtenida de un sitio de desarrolladores

+ callback -> Opcional. Si se envia, la respuesta usará el formato JSONP con un callback del nombre dado.

**Ejemplo**

http://paloalto.cloudapi.junar.com/dashboards/PALO-ALTO-2010-CENSU-DATA?auth_key=YOUR_AUTH_KEY

::

  {
   "id":"PALO-ALTO-2010-CENSU-DATA",
   "title":"2010 Census Data",
   "description":"Source: US Census Bureau",
   "user":"cityofpaloalto",
   "tags":[
      "palo alto",
      "2010 Census",
      "Population"
   ],
   "dataviews":[
      {
         "id":"PALO-ALTO-POPUL-STATS",
         "title":"Palo Alto Population Statistics",
         "link":"http://paloalto.opendata.junar.com/dataviews/73021/palo-alto-population-statistics/"
      },
      {
         "id":"PALO-ALTO-POPUL-BY-51574",
         "title":"Palo Alto Population by Ethnicity",
         "link":"http://paloalto.opendata.junar.com/visualizations/4324/palo-alto-population-by-ethnicity/"
      },
      {
         "id":"PALO-ALTO-POPUL-BY-12452",
         "title":"Palo Alto Population by Age Groups",
         "link":"http://paloalto.opendata.junar.com/dataviews/73247/palo-alto-population-by-age-groups/"
      },
      {
         "id":"EDUCA-STATI",
         "title":"Palo Alto Education Statistics",
         "link":"http://paloalto.opendata.junar.com/dataviews/73035/palo-alto-education-statistics/"
      },
      {
         "id":"PALO-ALTO-POPUL-BY-ETHNI",
         "title":"Palo Alto Population by Ethnicity",
         "link":"http://paloalto.opendata.junar.com/dataviews/73029/palo-alto-population-by-ethnicity/"
      },
      {
         "id":"SECON-LANGU-AT-HOME",
         "title":"Palo Alto Secondary Languages at Home",
         "link":"http://paloalto.opendata.junar.com/dataviews/73033/palo-alto-secondary-languages-at-home/"
      },
      {
         "id":"POVER-LEVEL-IN-PALO-ALTO",
         "title":"Palo Alto Poverty Level",
         "link":"http://paloalto.opendata.junar.com/dataviews/73038/palo-alto-poverty-level/"
      },
      {
         "id":"HOUSI-STATI",
         "title":"Palo Alto Housing Statistics",
         "link":"http://paloalto.opendata.junar.com/dataviews/73037/palo-alto-housing-statistics/"
      }
   ],
   "created_at":"2012-08-02 03:03:12",
   "link":"http://paloalto.opendata.junar.com/dashboards/7539/2010-census-data/"
  }

1.4 	Métodos para realizar búsquedas
---------------------------------------

1.4.1	Buscar Vistas de Datos
..............................

Retorna las vistas que coincidan con los criterios de búsqueda en sus títulos, descripciones y tags. El resultado es devuelto como un arreglo de objetos vista de datos.

**URL**

http://apisandbox.junar.com/dataviews/search

**Métodos de Consulta Soportados**

GET

**Parámetros**

+ query    -> Requerido. Términos de busqueda encodeados.
+ auth_key -> Requerido. La llave de autenticación personal obtenida de una página de desarrolladores.
+ max_results -> Opcional. Número máximo de vistas a mostrar. Máximo 100. Por defecto 100.
+ callback -> Opcional. Si se envia, la respuesta usará el formato JSONP con un callback del nombre dado.

**Ejemplo**

http://paloalto.cloudapi.junar.com/datastreams/search?query=Census&auth_key=YOUR_AUTH_KEY&max_results=5

::

  [
    {
      "description":"Source: US Census Bureau",
      "tags":[
         "palo alto",
         "us",
         "us census",
         "census",
         "poverty"
      ],
      "created_at":"1343437751",
      "title":"Palo Alto Poverty Level",
      "link":"http://paloalto.opendata.junar.com/datastreams/73038/palo-alto-poverty-level/",
      "id":"POVER-LEVEL-IN-PALO-ALTO"
   },
   {
      "description":"Source: US Census Bureau",
      "tags":[
         "Population",
         "Languages",
         "us",
         "census",
         "palo alto",
         "us census"
      ],
      "created_at":"1343438207",
      "title":"Palo Alto Secondary Languages at Home",
      "link":"http://paloalto.opendata.junar.com/datastreams/73033/palo-alto-secondary-languages-at-home/",
      "id":"SECON-LANGU-AT-HOME"
   },
   {
      "description":"Source: US Census Bureau",
      "tags":[
         "Education",
         "palo alto",
         "us",
         "us census",
         "high school"
      ],
      "created_at":"1343438507",
      "title":"Palo Alto Education Statistics",
      "link":"http://paloalto.opendata.junar.com/datastreams/73035/palo-alto-education-statistics/",
      "id":"EDUCA-STATI"
   },
   {
      "description":"Source: US Census Bureau",
      "tags":[
         "us",
         "palo alto",
         "us census",
         "Housing",
         "statistics"
      ],
      "created_at":"1343438013",
      "title":"Palo Alto Housing Statistics",
      "link":"http://paloalto.opendata.junar.com/datastreams/73037/palo-alto-housing-statistics/",
      "id":"HOUSI-STATI"
   },
   {
      "description":"Source: US Census Bureau",
      "tags":[
         "Population",
         "census",
         "us",
         "palo alto"
      ],
      "created_at":"1343437308",
      "title":"Palo Alto Population Statistics",
      "link":"http://paloalto.opendata.junar.com/datastreams/73021/palo-alto-population-statistics/",
      "id":"PALO-ALTO-POPUL-STATS"
   }
  ]

1.4.2 	Búsqueda de Colecciones
...............................

Devuelve las colecciones que coincidan con los criterios de búsqueda en su título, descripcion o tags. Los resultados son entregados como un arreglo de objetos vistas de datos

**URL**

http://apisandbox.junar.com/dashboards/search

**Métodos de Consulta Soportados**

GET

**Parámetros**

+ query    -> Requerido. Términos de busqueda encodeados.
+ auth_key -> Requerido. La llave de autenticación personal obtenida de una página de desarrolladores.
+ max_results -> Opcional. Número máximo de vistas a mostrar. Máximo 100. Por defecto 100.
+ callback -> Opcional. Si se envia, la respuesta usará el formato JSONP con un callback del nombre dado.

**Ejemplo**

http://paloalto.cloudapi.junar.com/dashboards/search?query=Census&auth_key=YOUR_AUTH_KEY&max_results=5

::

  [
    {
      "description":"Source: US Census Bureau",
      "tags":[
         "palo alto",
         "2010 Census",
         "Population"
      ],
      "created_at":"1343890992",
      "title":"2010 Census Data",
      "link":"http://paloalto.opendata.junar.com/dashboards/7539/2010-census-data/",
      "id":"PALO-ALTO-2010-CENSU-DATA"
   }
  ]

1.4.3 	Opciones de Búsqueda
............................

En todos los casos, el argumento de consulta debe contener los criterios de búsqueda expresados en uno de los siguientes formatos:

+ termino1 termino2: Busca por cada uno de los términos 

+ termino1+termino2: Busca por ambos términos

+ "termino1" : Busca por el término específico

La búsqueda está limitada a un máximo de 100 resultados

1.5 	Métodos para obtener métricas para una cuenta de datos abiertos
-----------------------------------------------------------------------

Actualmente hay dos métodos extra para obtener algunas métricas sobre el catálogo de datos de la cuenta de datos abiertos como también de la actividad de los visitantes: last, el cual retorna una lista de los últimos recursos publicados en el catálogo, y top, el cual retorna una lista de las vistas de datos más visitadas de tu catálogo.

Los resultados vienen por defecto en formato JSON. El formato de salida no puede ser modificado.

**URL**

La URL depende de la configuración del dominio de la cuenta
Dependiendo del tipo de recurso solicitado la URL puede contener el elemento datastreams, dashboards, o visualization .

**Métodos de Consulta Soportado**

GET

**Parámetros**

+ auth_key : Requerido. Llave de autenticación privada. Contáctannos a developers@junar.com para asignar una a tu cuenta.

+ max_results : Opcional. Valor por defecto es 5

**Ejemplo**

Top vistas de datos  : http://lanacion.cloudapi.junar.com/datastreams/top?auth_key=YOUR_AUTH_KEY
Últimas colecciones  : http://paloalto.cloudapi.junar.com/dashboards/last?auth_key=YOUR_AUTH_KEY

Top visualizaciones  : http://recursos.datos.gob.cl/visualizations/top?auth_key=YOUR_AUTH_KEY

::

  [
   {
      "id":"ACTIV-ECONO-DURAN-2012-80010",
      "title":"Actividad econ\u00f3mica durante 2012",
      "description":"Descripci\u00f3n por sector",
      "user":"LNData",
      "tags":[
         "actividad economica",
         "2012"
      ],
      "created_at":"2013-01-10 09:59:13",
      "source":"https://docs.google.com/spreadsheet/pub?key=0AuNh4LTzbqXMdDZkMGY4N043NkQ0TmRQSzdKdGxtZmc&output=html",
      "link":"http://data.lanacion.com.ar/datastreams/76060/actividad-economica-durante-2012/"
   },
   {
      "id":"MATER-RECIC-POR-COMUN",
      "title":"Materiales reciclabes por comuna",
      "description":"Detalle por comuna, barrio, toneladas por d\u00eda, rubro, habitantes y tasa cada 100.000 habitantes",
      "user":"LNData",
      "tags":[
         "Basura",
         "comuna",
         "Ciudad de Buenos Aires",
         "toneladas",
         "Rubro"
      ],
      "created_at":"2013-01-09 10:31:04",
      "source":"https://docs.google.com/spreadsheet/pub?key=0AuNh4LTzbqXMdDNHT29KVVB4OG5LT2x0bFY5MVVEaVE&output=html",
      "link":"http://data.lanacion.com.ar/datastreams/76043/materiales-reciclabes-por-comuna/"
   },
   {
      "id":"CON-CUANT-DEL-SALAR-SE",
      "title":"Con cu\u00e1nto del salario se queda el impuesto a las ganancias",
      "description":"Descripci\u00f3n por a\u00f1o, monto del salario y porcentaje de retenci\u00f3n",
      "user":"LNData",
      "tags":[
         "Salario",
         "Impuesto a las ganancias",
         "AFIP",
         "Argentina"
      ],
      "created_at":"2013-01-09 10:18:22",
      "source":"https://docs.google.com/spreadsheet/pub?key=0AuNh4LTzbqXMdGZlZ0FRaDJUNGNGeURJOVlvZG9RR0E&output=html",
      "link":"http://data.lanacion.com.ar/datastreams/76042/con-cuanto-del-salario-se-queda-el-impuesto-a-las-ganancias/"
   },
   {
      "id":"MUERT-EN-ACCID-VIALE-89761",
      "title":"Muertes en accidentes viales durante 2012",
      "description":"Descripci\u00f3n por provincia, cantidad de muertes, poblaci\u00f3n y tasa cada 100000 habitantes",
      "user":"LNData",
      "tags":[
         "Argentina",
         "Muertes viales",
         "2012"
      ],
      "created_at":"2013-01-08 09:28:05",
      "source":"https://docs.google.com/spreadsheet/pub?key=0AuNh4LTzbqXMdF9PV0t4QnZ5RDZZelBGR2NZQl9wb2c&output=html",
      "link":"http://data.lanacion.com.ar/datastreams/76022/muertes-en-accidentes-viales-durante-2012/"
   },
   {
      "id":"PRODU-AUTOM-2011-2012",
      "title":"Producci\u00f3n automotriz 2011 - 2012",
      "description":"Descripci\u00f3n por per\u00edodo, a\u00f1o, tipo y categor\u00eda",
      "user":"LNData",
      "tags":[
         "Producci\u00f3n automotriz",
         "2011",
         "2012",
         "Categor\u00edas"
      ],
      "created_at":"2013-01-07 12:13:52",
      "source":"https://docs.google.com/spreadsheet/pub?key=0AuNh4LTzbqXMdERYMWc2eUxpQWYwemZmNzgxRElZZlE&output=html",
      "link":"http://data.lanacion.com.ar/datastreams/76004/produccion-automotriz-2011-2012/"
   }
  ]

1.6 	Manejo de Errores
-------------------------

Estos son los errores posibles para todos nuestros métodos:

+ 400 -> Bad Request - Solicitud mal armada

+ 401 -> Unauthorized - No autorizado

+ 404 -> Not Found - No encontrado

+ 405 -> Method Not Allowed - Método no permitido

+ 429 -> Too Many Requests - Demasiadas solicitudes

+ 500 -> Internal Server Error - Error interno del servidor
