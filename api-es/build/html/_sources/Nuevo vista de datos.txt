
Consumiendo una vista con parámetros
====================================

Una vista de datos puede contener parámetros. Los parámetros pueden agregarse a la vista de datos solamente durante el proceso de creación. Estos parámetros pueden estar mapeados contra un formulario en un sitio web, directamente contra la URL de la fuente de datos o contra columnas de datos dentro de la tabla sobre la cual se crea la vista. La sintaxis apropiada para agregar parámetros en una solicitud API es
pArgumentN=X
Donde N es la posición del parámetro en la vista, empezando desde cero y X es el valor que tendrá dicho parámetro.

Ejemplo


http://lima.cloudapi.junar.com/dataviews/invoke/VOLUM-DE-PRODU-INGRE-POR?auth_key=YOUR_AUTH_KEY&pArgument0=MAIZ

.. code-block:: json

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


Filtrar los resultados de una vista
===================================

La API de Datos Abiertos de Junar permite a sus usuarios filtrar los resultados obtenidos durante la solicitud de una vista de datos utilizando la siguiente sintaxis:

http://lasvegas.cloudapi.junar.com/datastreams/invoke/DEVEL-SERVI-PROJE-INSPE?auth_key=YOUR_AUTH_KEY&filter0=column4[contains]GAS&filter1=column7[==]RANDOLPH&where=(filter0andfilter1)

Esto retornaría todos los datos que contengan la palabra GAS en la columna 4 y la palabra RANDOLPH en la columna 7.
Los filtros pueden ir desde 0 a N (filter0, filter1...filterN) y tienen la siguiente sintaxis
operando0 | operador lógico | operando1
Los operandos pueden ser : rownum (número de fila), columnN (columna N, donde N es un entero que va desde 0 a N) o una cadena de texto
Los Operadores Lógicos pueden ser [==], [>], [<], [!=], [contains], [>=], [<=]. Los corchetes [] deben ser incluidos. Si el contenido es una cadena de texto son sensibles a mayúsculas.
La operación where tiene una expresión lógica para unir filtros de manera similar al select_statement. En este caso, se utilizaría (filter0 and filter1). Las expresiones and y or sirven para diferenciar la relación entre los filtros y pueden concatenarse tanto como fuera necesario para cumplir una cierta condicion por ejemplo: (filter0 and filter1) or filter2.
Cuando se agrega una fecha como parámetro debe incluirse utilizando el formato MM/dd/aaaa.


Formateo de Datos
=================

Permite a los desarrolladores el dar formato a columnas de datos con un tipo y formato que afectará cómo son devueltos los datos de la consulta. Usa la siguiente sintaxis y debe aplicarse a una columna que ya haya sido objeto de un filtro :

::

	format={"table":[{"id":"column10", "type":"DATE", "format":{"country":"ES", "lang":"es", "style": "dd/MM/yyyy"}}]}

Donde : 

- id : Corresponde a la posición de la columna a filtrar. Esta columna debe haber sido objeto de un filtro para poder ser formateada.
- type: El tipo de dato que contiene la columna. Por defecto todas las columnas se consideran de tipo texto (TEXT), pero pueden cambiarse a fecha (DATE) o número (NUMBER).
- format : Dependiendo del tipo elegido puede requerir la siguiente información.

El formato DATE requiere country (país), lang (idioma) y style (estilo). Los valores de country y lang corresponden al formato ISO, mientras que posibles valores de style pueden encontrarse aquí:

http://docs.oracle.com/javase/7/docs/api/java/text/SimpleDateFormat.html

::

	{"table":[{"id":"column10", "type":"DATE", "format":{"country":"CL", "lang":"es", "style": "dd/MM/yyyy"}}]}
	El formato NUMBER requiere country (país), lang (idioma) y pattern (patrón). Los patrones permiten definir cómo se separarán los miles y los decimales o si las cifran irán agrupadas de acuerdo a estándares asociados al país e idioma elegidos
	{"table":[{"id":"column4", "type":"NUMBER", "format":{"country":"US", "lang":"es", "pattern":"", "decimals":"", "thousands":""}}]}

Ejemplo

::

	..../invoke/SACRA-ANNUA-CRIME-STATS?...&filter0=column0[==]Homicide&filter1=column4[>]0&where=(filter0 or filter1)&format=
		{"table":[{"id":"column4", "type":"NUMBER", "format":"format":{"country":"US", "lang":"es", "pattern":"", "decimals":"", "thousands":""}}]}
	
	
.. code-block:: json
	
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