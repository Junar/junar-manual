1. Introduccion
===============

Bienvenido
----------

Junar ofrece la plataforma de datos abiertos basada en la nube mas fácil de usar, que permite a las empresas, gobiernos, ONGs y al mundo académico liberar sus datos para impulsar la colaboración, nuevas oportunidades y la transparencia. Algunas de las principales empresas del mundo confían a Junar sus recursos más valiosos: los datos, compartiendo su uso a usuarios de todo el mundo.

Con Junar se puede abrir datos rápidamente, decidir qué se conserva para uso interno, qué se hace público y optimizar el uso de los datos mediante la adición de metadatos que promueven la optimización de motores de búsqueda.

Desde el lanzamiento de la plataforma Junar, gobiernos y empresas innovadoras en todo el mundo han puesto en marcha sitios de datos abiertos para maximizar transparencia, unificar intereses, y mostrar la información de una manera mas eficiente.

Junar ofrece todo lo necesario para abrir sus datos con confianza. Está construido para escalar masivamente y apoya a las organizaciones basadas en datos locales y globales. Con Junar, usted puede elegir qué datos se recolectan, cómo quiere que se presenten, y cuando deberían ponerse a disposición del público. También puede determinar qué conjuntos de datos están disponibles al público y cuáles sólo son para su uso interno.

Sin importar si usted quiere integrar sus datos a su sitio web o que nosotros se los alojemos, Junar proporciona un espacio de trabajo simple que le permite colaborar con sus colegas y gestionar todo el proyecto de datos abiertos.

La plataforma de datos abiertos Junar es el servicio que usted necesita para:

+ **Recolectar**: La plataforma de datos abiertos Junar actúa como un puente para ayudar a recopilar y organizar todos los datos que desee abrir en un solo lugar.

+ **Mejorar**: La plataforma de datos abiertos Junar le ofrece la posibilidad de transformar conjuntos de datos en productivos recursos informativos a los que las personas podrán acceder, compartir y reutilizar a través de gráficos, tablas y mapas.

+ **Publicar**: Publicar datos en formatos convincentes es esencial para crear la mayor valoración. Hemos creado un flujo de trabajo para ayudarle a gestionar la forma en la cual usted publica sus datos – teniendo en cuenta que tienen procesos internos específicos y ciclos de aprobación.

+ **Compartir**: Los medios sociales continúan cambiando cómo las organizaciones se comunican con el mundo. La plataforma de datos abiertos Junar ofrece un diseño de conjunto de datos intuitivo con funciones que hacen que la navegación y la gestión de datos sea simple y atractiva. Usted puede compartir datos a través de redes sociales como Twitter, Facebook, y la Comunidad Junar.

+ **Analizar**: Los reportes de Junar le indican cuales son las vistas de datos, visualizaciones y conjuntos de datos que son más populares e incluso presentan los datos que se consumen a través de la API de Junar. Los informes incluyen métricas en tiempo real y proporcionan la información más importante acerca del trafico de sus iniciativas de datos abiertos y de sus conjuntos de datos.

Si aún no está seguro por dónde comenzar con datos abiertos o desea solicitar una demostración, escríbanos a contact@junar.com

En el siguiente documento se detallan las funcionalidades que soporta la implementación de la Plataforma Junar de Datos Abiertos. Las funciones de la plataforma se categorizan bajo los siguientes temas:

+ Accesibilidad y Tipo de Usuarios.
+ Crear, Editar, Publicar y Eliminar Conjuntos de Datos.
+ Crear, Editar, Publicar y Eliminar Vistas.
+ Crear, Editar, Publicar y Eliminar Visualizaciones.
+ Crear, Editar, Publicar y Eliminar Colecciones.
+ Crear, Editar, Publicar y Eliminar Historias de Datos.
+ Crear, Editar, Publicar y Eliminar APIs.
+ Creación y Configuración de una Cuenta.

1.1 Qué es un Conjunto de Datos
-------------------------------
Un Conjunto de Datos es un recurso que puede obtenerse a partir de documentos hospedados en su computador, en la red o servicios web.

Actualmente nuestra plataforma soporta los siguientes tipos de formatos para ser convertidos a Conjunto de Datos: DOC, DOCX, DOCM, DOTX, DOTM, XLS, XLSX, XLSM, XLTX, XLTM, XLSB, XLAM, XLL, ODT, ODS, CSV, TXT, PDF, HTML, HTM, XML, KML, KMZ, TSV,  GIF, GZ, JPEG, JPG,  PNG, TAB, TAR, ZIP y servicios web SOAP o REST.

1.2 Qué es una Vista de Datos
-----------------------------

Una vista de datos o Vista es un recurso generado a partir de un Conjunto de Datos, el cual puede estar compuesto por  una celda, una combinación de filas y columnas, o incluso de tablas enteras. Las Vistas son actualizadas cada vez que se realizan modificaciones al  Conjunto de Datos de origen.

Las Vistas  funcionan de manera independiente del Conjunto de Datos, por lo que puede invocarse a través de la API, descargarse en distintos formatos, generar visualizaciones a partir de ella, incrustarse en otros sitios, compartirse a través de distintas redes sociales, etc.

1.3 Qué es una Visualización
----------------------------

Una visualización es una representación gráfica de una selección de datos elegidos por el usuario a partir de una vista de datos. Son recursos independientes los cuales pueden ser compartidos de manera individual y/o agregado a una colección. La plataforma Junar soporta visualizaciones de comparación entre ítems (gráficos de columnas, barras y divergencia), comparación en el tiempo (líneas y áreas), composición estática (de torta y dona), mapas de marcadores, polígonos, líneas y densidad.

1.4 Qué es una Colección
------------------------

Una colección es un grupo de conjuntos de datos, vistas, visualizaciones y widgets adicionales que es publicado dentro de un portal de Datos Abiertos.

Una colección generalmente aborda un tema específico elegido por el usuario y agrupa tantos recursos como el usuario quisiera compartir.

1.5 Qué es una Historia de Datos
--------------------------------

Una historia con datos es un relato basado en recursos sobre un hecho o tema particular que tiene el objetivo de comunicar de maanera clara los datos a públicos no especializados. Está formada por capítulos que contienen vistas, visualizaciones y recursos complementarios (textos, imágenes, videos).

1.6 Qué es una API
--------------------------------

Podemos entender la API como un código que indica a distintas aplicaciones cómo pueden mantener una correspondencia entre sí. Sirve para establecer una comunicación con una base de datos, un sistema operativo o un protocolo de comunicaciones lo que permite agregar diversas funciones a sitios web y aplicaciones. La plataforma Junar soporta tanto los protocolos REST como SOAP.