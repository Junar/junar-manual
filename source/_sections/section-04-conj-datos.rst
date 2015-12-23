4. Creación de un Conjunto de Datos
===================================
Acceso directo desde:

Posicionarse sobre el botón Conjunto de datos

Seleccione una opción de recolección de datos

.. image:: ../_static/images/image82.png

Otra opción para poder acceder es:

Ingrese a la sección Conjuntos de Datos

.. image:: ../_static/images/image81.png
  :align: center

Presione el botón Nuevos Conjuntos de Datos

Seleccione una opción de recolección de datos

.. image:: ../_static/images/image85.png
  :align: center


4.1 Desde un Archivo
--------------------

La Plataforma brinda la posibilidad de utilizar archivos recolectados desde su computador como Conjunto de Datos, cargarlo a nuestra nube y convertirlo en un recurso de datos abiertos. Seleccione el archivo desde su computador, haga clic sobre Seleccionar, el sistema adjunta
el archivo elegido. La recolección de datos consta de campos requeridos (*) que deben ser completados, pudiendo omitirse los otros.
Luego de completar los campos requeridos, presione el botón Continuar.

.. image:: ../_static/images/image83.jpg

4.2 Desde una URL o sitio web
-----------------------------
También nuestra Plataforma permite recolectar datos desde Sitio Web o Archivos hospedados en la red como Conjunto de Datos, cargarlo a la nube y convertirlo en un recurso de datos abiertos.

+ Sitio Web, ingrese una URL con un enlace valido a la página web desde donde se quiera recolectar. La recolección de datos consta de campos requeridos (*) que deben ser completados, pudiendo omitirse los otros. Luego de completar los campos requeridos, presione el botón Continuar.
+ Archivo hospedado en la red, se sigue el mismo procedimiento anterior, sin embargo lo que cambia es la fuente de la información. Para esta opción se requiere copiar una dirección de enlace de algún documento en alguno de los formatos de Junar.

.. image:: ../_static/images/image88.jpg

4.3 Desde un Servicio Web
-------------------------
Nuestra Plataforma permite recolectar datos no solamente desde Archivo Internos, Sitio Web o Archivos hospedados en la red, sino también a través de Servicios Web SOAP o REST, cargarlo a nuestra nube y convertirlo en un recurso de datos abiertos.

+ Servicios Web SOAP, ingrese una URL desde donde se está obteniendo el Servicio Web, determine el tipo de servicio web SOAP/XML, también se necesitan los siguientes parámetros:

  + Método: Nombre del método asociado al conjunto de datos que queremos obtener.
  + Espacio de Nombres: Provee un método para evitar conflictos de nombre entre recursos.
  + Agregar otros parámetros: Si es necesario para acceder al sitio web.

  Estos parámetros deben ingresarse respetando mayúsculas y minúsculas.

  Esta información suele encontrarse en el mismo sitio desde donde se desea obtener la información, como también puede consultarle al administrador del sistema que este albergando los servicios web.

  .. image:: ../_static/images/image95.jpg

+ Servicios Web REST, ingrese una URL desde donde se está obteniendo el Servicio Web, determine el tipo de servicio web REST/JSON, también se necesita el siguiente parámetro:

  + Ruta a los datos: Nombre del método asociado al conjunto de datos que queremos obtener.

De manera similar a los servicios web SOAP, podemos obtener datos y recolectarlos como Conjunto de Datos desde objetos JSON.

Una vez que se han ingresado los parámetros de manera exitosa, el servicio web será procesado de manera normal por lo que los pasos de recolección de los datos son los mismos que para el resto de las fuentes. Luego de completar los campos/parámetros requeridos, presione el botón Continuar.

.. image:: ../_static/images/image92.jpg


El sistema visualiza la siguiente pantalla, complete los campos requeridos (*), pudiendo omitirse los siguientes: Fuentes, Etiquetas y Notas del Conjunto de Datos. Luego de completar los campos requeridos, presione el botón Guardar. El Conjunto de Datos se crea por defecto en estado Borrador.

.. image:: ../_static/images/image94.jpg

4.4 Edición de un Conjunto de Datos
-----------------------------------
Una vez creado el Conjunto de Datos, se visualiza el mismo en un listado, este listado cuenta con una paginación, es decir que se puede ir avanzando página por página dentro del listado o bien presionando la página correspondiente a la que desea acceder, de esta manera esa página es mostrada en el listado de Conjuntos de Datos correspondiente. Para esto se dirige a la sección Conjuntos de Datos

.. image:: ../_static/images/image96.jpg

.. .. image:: ../_static/images/image97.png

Para Editar un Conjunto de Datos, hay dos opciones:

+ Clic sobre el Conjunto de Datos:El sistema visualiza la información del Conjunto de Datos seleccionado, presione |image28| e introduzca los cambios sobre la información del Conjunto de Datos.


.. image:: ../_static/images/image98.png

+ Acercar el mouse sobre el Conjunto de Datos: Se visualiza las siguientes opciones:

  .. image:: ../_static/images/image99.png

  + Crear Vista:Al hacer clic sobre este botón puede crear una nueva Vista, tomando como referencia el Conjunto de datos seleccionado.
  + Editar:Al hacer clic sobre este botón puede realizar cambios a la información del Conjunto de Datos.
  + Borrar:Al hacer clic sobre este botón puede borrar los cambios recientes del Conjunto de datos o todos los cambios el Conjunto de datos.
  + Fuente/Descargar Original:Al hacer clic sobre este botón accede a la página del recurso o descarga el archivo adjunto del Conjunto de Datos.

Cuando el Conjunto de Datos se encuentra En revisión:

+ Los usuarios con rol Editores pueden enviar un Conjunto de Datos a Revisión, el Conjunto de Datos en este estado no puede ser editado, su opción de Editar solo es posible cuando el recurso es Aprobado o Rechazado.

  .. image:: ../_static/images/image100.png

+ Los usuarios con rol Publicadores o Administradores podrán Aceptar o Rechazar ese recurso.

  .. image:: ../_static/images/image101.jpg

4.5 Publicación de un Conjunto de Datos
---------------------------------------
Para publicar un Conjunto de Datos en el micrositio, haga clic sobre el botón Publicar.

.. image:: ../_static/images/image102.png

Para acceder al micrositio y visualizar el Conjunto de Datos publicado |image12|, haga clic sobre |image07|, margen superior derecho de la visualización del Conjunto de Datos.

.. image:: ../_static/images/image71.png

4.6 Eliminación de un Conjunto de Datos
---------------------------------------

Para eliminar un Conjunto de Datos, hay dos opciones:

+ Dentro del Conjunto de Datos, haga clic sobre |image09|
+ En el listado de Conjuntos de Datos, seleccione un Conjunto de Datos y presione el botón |image41|

  .. image:: ../_static/images/image73.png
  .. image:: ../_static/images/image74.png

El sistema permite eliminar la revisión actual del Conjunto de Datos o todas las revisiones del Conjunto de Datos. Esta última acción elimina el Conjunto de Datos y todos sus recursos asociados, como así también los elimina del micrositio. Por revisión se entiende los distintos cambios realizados sobre la información del Conjunto de Datos.

.. image:: ../_static/images/image75.png

.. |image07| image:: ../_static/images/image07.png
.. |image09| image:: ../_static/images/image09.png
.. |image12| image:: ../_static/images/image12.png
.. |image28| image:: ../_static/images/image28.png
.. |image41| image:: ../_static/images/image41.png