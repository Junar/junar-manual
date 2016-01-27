1. Introducción
=====================

En el siguiente documento se detallan las funcionalidades que soporta la implementación de la Plataforma Junar de Datos Abiertos. Las funcionalidades de la plataforma se categorizan bajo los siguientes temas:

+ Accesibilidad y Tipo de Usuarios.
+ Creación, Edición, Publicación y Eliminación de Conjuntos de Datos.
+ Creación, Edición, Publicación y Eliminación de Vistas.
+ Creación, Edición, Publicación y Eliminación de Visualizaciones.
+ Creación, Edición, Publicación y Eliminación de Colecciones.
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

Una visualización es una representación gráfica de una selección de datos elegidos por el usuario a partir de una vista de datos. Son recursos independientes los cuales pueden ser compartidos de manera individual y/o agregado a una colección. La plataforma Junar soporta son los siguientes tipos de visualizaciones: columnas, barras, gráfico de torta, línea y área.

1.4 Qué es una Colección
------------------------

Una colección es un grupo de vistas y visualizaciones que es posible de ser publicado dentro de un sitio de Datos Abiertos además de ser compartido de manera directa a través de redes sociales, descargable, usable vía API, etc. 

Una colección generalmente aborda un tema específico elegido por el usuario y agrupa tantos recursos como el usuario quisiera compartir.
