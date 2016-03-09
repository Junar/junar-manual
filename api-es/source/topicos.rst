Autenticación
=============

Existen 3 pasos para intentar identificar quien está llamando a la API

1. Lo primero que se hace es tratar de identificar la cuenta (Account) mediante el dominio. 
2. Luego se intenta identificar la auth_key que debe coincidir con una de las auth_key dentro de las habilitadas en la cuenta.
3. Por último, se trata de identificar el usuario y en caso negativo se lo considera un usuario anónimo.

El sistema tiene dos tipos de auth_key; públicas y privadas. Las privadas las emite cada cuenta a travez de su configuración y las publicas entrando al path ``/developers`` dentro del portal de la cuenta.

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
- ValidationError: Parametros inválidos "400 Bad Request".
- UnexpectedError: Error inesperado "500 internal Server".

Paginación
==========

Todos los métodos de listado de recursos de la API tienen el funcionamiento de paginado. Cualquiera puede recibir los siguientes parámetros: 

- limit: cantidad de resultados por búsqueda
- offset: número de resultado a partir del cual se realiza la busqueda.

Cuando aparecen estos parametros la respuesta se ordena de otra manera y agrega los siguientes campos

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

Los filtros aplican tambien a los listdos de todos los recursos de la API.

Las búsquedas se realizan utilizando el parámetro ``query`` y actualmente se puede filtrar por categorias utilizando el parmaetro ``categories`` que recibe los nombres de las categorias separadas por coma.

Busquedas Múltiples
===================

Existe la posibilidad de tener un listado de múltiples recursos y para ello se creo el siguiente path:

``GET /api/v2/resources``

Para poder filtrar los tipos de recursos se utiliza el parámetro ``resources`` que puede tener mas de un de los siguientes valores separados por coma.

- dt: Conjunto de datos
- ds: Vistas
- vz: Visualizaciones
- db: Colecciones

En los resultados se agrega el parametro ``type`` para identificar el recurso


Versiones
=========

Actualmente la api se encuentra en su version 2. Para obtener información de la versión 1 ingresar a http://wiki.junar.com/index.php/API

