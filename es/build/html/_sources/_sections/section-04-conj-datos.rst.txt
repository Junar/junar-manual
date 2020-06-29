4. Creación de un Conjunto de Datos
===================================

Para crear un conjunto de datos lo primero que se debe hacer es: 

Posicionarse sobre el botón → Conjunto de datos

 Seleccionar una opcion para la recoleccion de datos como se muestra en la imagen a continuacion →

## (MODIFICAR IMAGEN x 04-inicio-01)
.. image:: ../_static/images/img004.png
Otra opción para poder acceder es:

Ingresar a la sección → Conjuntos de Datos


(MODIFICAR NUMERO x 04-conjuntodatos-02)
.. image:: ../_static/images/img005.png
  :align: center
Presione el botón que se encuentra en la parte superior a la derecha → Nuevos Conjuntos de Datos

Seleccionar una opción de recolección de datos →

##(MODIFICAR NUMERO 04-conjuntodatos-03)
.. image:: ../_static/images/img006.png
  :align: center

4.1 Desde un Archivo
--------------------
La Plataforma brinda la posibilidad de utilizar archivos recolectados desde su computador como Conjunto de Datos, cargarlos  a la plataforma y convertirlos en  recursos de datos abiertos.

## (AGREGAR IMAGEN 04-desdearchivo-04)
.. image:: ../_static/images/img007.png
  :align: center

 Seleccione el archivo desde su computador y arrastre hacia la pantalla. Tenga en consideracion que el tamaño maximo permitido es 300 MB y que los archivos deben estar codificados en UTF-8. 

## (AGREGAR IMAGEN 04-desdearchivo2-05)
 .. image:: ../_static/images/img007.png
  :align: center

 A continuación se hará la carga de datos y metadatos la cual consta de campos requeridos (*) que deben ser completados, pudiendo omitirse los otros. 

 Se podrá seleccionar una categoría que sirve para clasificar al conjunto de datos y que sea mas fácil de filtrar a la hora de su búsqueda.
 
 Seguido, se puede seleccionar si su uso sera público o privado. 

## (AGREGAR IMAGEN 04-desdearchivo3-06)
 .. image:: ../_static/images/img007.png
  :align: center

 En el margen inferior, se puede agregar información contextual la cual es opcional.

  Las opciones disponibles incluyen:   

  + **Fuente de los datos**: Origen donde se creó el conjunto de datos.

  + **Etiquetas**: Sirven para identificar el contenido del conjunto de datos.

  + **Anotaciones o aclaraciones adicionales**: Información que pueda ser relevante para el usuario final.


## (AGREGAR IMAGEN 04-desdearchivo4-07)
 .. image:: ../_static/images/img007.png
  :align: center

 En el sector derecho se puede: 

  + **Seleccionar bajo que licencia se publicara el conjunto de datos**

  + **Frecuencia de actualización**

  + **Agregar mail de consulta**

  + **Referencia geográfica**

  + **Documentación técnica**

 Luego de completar los campos deseados, presione el botón Continuar.


 ## (MODIFICAR IMAGEN)

4.2 Desde una URL o sitio web
-----------------------------

También nuestra Plataforma permite recolectar datos desde un Sitio Web o Archivos hospedados en la red como Conjunto de Datos, cargarlos a la plataforma y convertirlos en recursos de datos abiertos. 

## (AGREGAR IMAGEN 04-desdeweb-08)
.. image:: ../_static/images/img008.png
  :align: center


+ Sitio Web: Ingrese una URL con un enlace válido a la página web desde donde se quiera recolectar. Luego de completar los campos requeridos, presione el botón Continuar.
+ Archivos hospedados en la red: Se sigue el mismo procedimiento anterior, sin embargo lo que cambia es la fuente de la información. Para esta opción se requiere copiar una dirección de enlace de algún documento en alguno de los formatos soportados por Junar. Para ver la lista completa, ver la sección: ¿Que es un Conjunto de Datos?

## (AGREGAR IMAGEN 04-desdeweb1-09)
.. image:: ../_static/images/img009.png
  :align: center

  A continuación se hará la carga de datos y metadatos la cual consta de campos requeridos (*) y opcionales que deben ser completados como es explicado en el apartado 4.1.

4.3 Desde un Servicio Web
-------------------------

Nuestra Plataforma permite recolectar datos no solamente desde archivos locales, Sitio Web o Archivos Hospedados en la red, sino también a través de Servicios Web SOAP o REST, cargarlos  a nuestra plataforma y convertirlo en un recurso de datos abiertos. 

##(MODIFICAR POR 04-servicioweb-10)
.. image:: ../_static/images/img010.png
  :align: center

+ Servicios Web SOAP: Determine el tipo de servicio web SOAP/XML. 

##(MODIFICAR POR 04-serviciowebSOAP-12)
.. image:: ../_static/images/img010.png
  :align: center

  Ingrese la URL desde donde se está obteniendo el Servicio Web. También se necesitan los siguientes parámetros:

  + Método: Nombre del método asociado al conjunto de datos que queremos obtener.
  + Espacio de Nombres: Provee un método para evitar conflictos de nombre entre recursos.
  + Configuración avanzada: Aparecen distintas opciones.

##(MODIFICAR POR 04-serviciowebSOAP-13)
.. image:: ../_static/images/img010.png
  :align: center

  + Ruta a los datos: Permite acceder a la tabla de datos buscada agregando un atributo XML

##(MODIFICAR POR 04-serviciowebSOAP-14)
.. image:: ../_static/images/img010.png
  :align: center

  + Indicar nombre y contraseña en caso de que sea necesario para acceder al servicio web

##(MODIFICAR POR 04-serviciowebSOAP-15)
.. image:: ../_static/images/img015.png
  :align: center

  + Agregar campos extendidos: Los campos extendidos se utilizan para extraer datos por fuera de la tabla de datos y cabeceras. Para cada campo debe ingresar nombre, descripción y ruta.

##(MODIFICAR POR 04-serviciowebSOAP-16)
.. image:: ../_static/images/img015.png
  :align: center

  + Agregar otros parámetros: En el caso de que sean necesarios para acceder al sitio web.

  Estos parámetros deben ingresarse respetando mayúsculas y minúsculas.

  Esta información suele encontrarse en el mismo sitio desde donde se desea obtener la información, como también puede consultarle al administrador del sistema que esté albergando los servicios web.

+ Servicios Web REST: Determine el tipo de servicio web REST/JSON.

De manera similar a los servicios web SOAP, podemos obtener datos y recolectarlos como Conjunto de Datos desde objetos JSON. 

##(MODIFICAR POR 04-serviciowebREST-11)
.. image:: ../_static/images/img015.png
  :align: center

Ingrese la URL desde donde se está obteniendo el Servicio Web. 

Hay casos donde también es necesario el siguiente parámetro:

  ##modificar por 04-serviciowebREST-17
  .. image:: ../_static/images/img017.png

  + Ruta a los datos: Define la ruta (xpath o json-path) a los datos de la tabla.

+ Configuración avanzada: Aparecen distintas opciones.

 ##modificar por 04-serviciowebREST-18
  .. image:: ../_static/images/img017.png

  + Evaluación de la ruta a los datos: Deberás ingresar los nodos a los que quiere acceder. Los mismos deberán estar separados por | (barra vertical) y si quiere acceder a los hijos de un nodo, se deberá usar . (punto). 

   ##modificar por 04-serviciowebREST-19
  .. image:: ../_static/images/img017.png

  + En el caso de que tengan títulos, se pueden identificar como se muestra en la imagen. En el caso de que esten en una ruta diferente a la de los datos, se deberá configurar la ruta a las cabeceras (path-to-headers).

  ##modificar por 04-serviciowebREST-20
  .. image:: ../_static/images/img017.png

  + GET, POST, PUT, PATCH son las 4 peticiones que son soportadas por el servicio de Junar.

    ##modificar por 04-serviciowebREST-21
  .. image:: ../_static/images/img017.png

  + En el caso de que sea necesario autenticación para conectarse al servicio web. 

   ##modificar por 04-serviciowebREST-22
  .. image:: ../_static/images/img017.png

  + Indicar en el caso de que sea preciso una firma para acceder al servicio web

   ##modificar por 04-serviciowebREST-23
  .. image:: ../_static/images/img017.png

  + Agregar campos extendidos: Los campos extendidos se utilizan para extraer datos por fuera de la tabla de datos y cabeceras. Para cada campo debe ingresar nombre, descripción y ruta.

   ##modificar por 04-serviciowebREST-24
  .. image:: ../_static/images/img017.png

  + Estructura de autenticación: En el caso de que sea necesario un token.

   ##modificar por 04-serviciowebREST-25
  .. image:: ../_static/images/img017.png

  + Esta opción permite agregar cabeceras

     ##modificar por 04-serviciowebREST-26
  .. image:: ../_static/images/img017.png

  + Agregar otros parámetros: En el caso de que sean necesarios para acceder al sitio web.

  Estos parámetros deben ingresarse respetando mayúsculas y minúsculas.

Una vez que se han ingresado los parámetros de manera exitosa, el Servicio Web será procesado de manera normal por lo que los pasos de recolección de los datos son los mismos que para el resto de las fuentes. Luego de completar los campos/parámetros requeridos, presione el botón Continuar.

El sistema visualiza la siguiente pantalla, complete los campos requeridos (*), pudiendo omitirse los siguientes: Categoría, Uso, Fuentes, Etiquetas y Notas del Conjunto de Datos así como el cuadro de información adicional. Luego de completar los campos requeridos, presione el botón Guardar. El Conjunto de Datos se crea por defecto en estatus de Borrador.

##modificar por 04-serviciowebREST-26
.. image:: ../_static/images/img012.png


4.4 Desde archivos alojados en Dropbox
--------------------------------------

Junar permite recoletar datos desde archivos alojados en Dropbox. La ventaja de este conjunto de datos es que al modificarse el archivo alojado en Dropbox, la plataforma detectará el cambio y actualiará los recursos de manera automática, sin necesidad de editar los recursos desde el espacio de trabajo. 

Para habilitar el modulo de conjuntos de datos desde Dropbox debe ingresar a su cuenta de Dropbox seguir los siguientes pasos:

1. Crear una aplicacion en la cuenta de Dropbox y obtener el token para acceder a la API
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Ingrese a https://www.dropbox.com/developers/apps y haga clic en el boton ``Create app``.

.. image:: ../_static/images/05-datasets-dropbox_01.png

Luego, debe seleccionar las opciones resaltadas en la imagen:

  1. Chose an API: Dropbox API
  2. Choose the type of access you need: Full Dropbox
  3. Name your app: Junar (o el nombre que usted decida)
  4. Debe aceptar los términos y condiciones, 
  5. Por último, hacer clic en el botón ``Create ap``.

.. image:: ../_static/images/05-datasets-dropbox_02.png

Luego, verá lo siguiente. Para generar la clave token, debe hacer clic sobre el botón ``Generate``, tal como se resalta en la imagen:

.. image:: ../_static/images/05-datasets-dropbox_03.png

Al hacer clic en el botón, Dropbox generará una clave token. 

.. image:: ../_static/images/05-datasets-dropbox_04.png

Copie esa clave y enviela a support@junar.com indicando el nombre de su cuenta. Con esos datos, habilitaremos el módulo que le permitirá crear conjuntos de datos desde archivos alojados en Dropbox.

2. Crear conjuntos de datos desde Dropbox
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Una vez habilitado el módulo, se mostrará la opción Crear conjuntos de datos desde Dropbox.

.. image:: ../_static/images/05-datasets-dropbox_05.png


Primero, debe localizar el archivo en su cuenta de Dropbox y extraer la ruta al archivo. En este ejemplo, la ruta al archivo es ``/Junar/Datasets/dataset_de_prueba.csv``.

.. image:: ../_static/images/05-datasets-dropbox_06.png

Esa ruta, debe escribirla en el siguiente campo:

.. image:: ../_static/images/05-datasets-dropbox_07.png

Luego, deberá completar los metadatos como en cualquier otro caso.


4.5 Edición de un Conjunto de Datos
-----------------------------------
Una vez creado el Conjunto de Datos, se  visualiza el mismo en un listado, este listado cuenta con una paginación, es decir que se puede ir avanzando página por página dentro del listado o bien presionando la página correspondiente a la que desea acceder, de esta manera esa página es mostrada en el listado de Conjuntos de Datos correspondiente. Para esto se dirige a la sección → Conjuntos de Datos

.. image:: ../_static/images/img013.png

Para Editar un Conjunto de Datos, hay dos opciones:

+ Clic sobre el Conjunto de Datos: El sistema visualiza la información del Conjunto de Datos seleccionado, presione el icono |icono-editar| e introduzca los cambios sobre la información del Conjunto de Datos.


.. image:: ../_static/images/img014.png
  :align: center

.. image:: ../_static/images/img015.png

+ Acercar el mouse sobre el Conjunto de Datos: Se visualizan las siguientes opciones:

  .. image:: ../_static/images/img016.png
    :align: center

  + Crear Vistas: Al hacer click sobre este botón puede crear una nueva Vista, tomando como referencia el Conjunto de datos seleccionado.
  + Editar: Al hacer click sobre este botón puede realizar cambios a la información del Conjunto de Datos.
  + Borrar: Al hacer click sobre este botón puede borrar los cambios recientes del Conjunto de datos o todos los cambios el Conjunto de datos.
  + Fuente/Descargar Original: Al hacer click sobre este botón accede a la página del recurso o descarga el archivo adjunto del Conjunto de Datos.

Cuando el Conjunto de Datos se encuentra En revisión:

+ Los usuarios con rol de Editor pueden enviar un Conjunto de Datos a **Revisión**, el Conjunto de Datos en este estatus no puede ser editado, su opción de editar solo es posible cuando el recurso es **Aprobado** o **Rechazado**.

  .. image:: ../_static/images/img017.png

+ Los usuarios con rol de Publicador  o Administrador podrán Aceptar o Rechazar el  recurso.

  .. image:: ../_static/images/img018.png

4.6 Publicación de un Conjunto de Datos
---------------------------------------
Para publicar un Conjunto de Datos en el portal de datos abiertos, haga click sobre el botón Publicar.

.. image:: ../_static/images/img019.png

Para acceder al portal de datos abiertos y visualizar el Conjunto de Datos publicado |icono-publicado|, haga clic sobre |icono-ver-sitio|, localizado en el margen superior derecho de la visualización del Conjunto de Datos.

.. image:: ../_static/images/img020.png

4.7 Eliminación de un Conjunto de Datos
---------------------------------------

Para eliminar un Conjunto de Datos, hay dos opciones:

+ Dentro del Conjunto de Datos, haga clic sobre |icono-eliminar|
+ En el listado de Conjuntos de Datos, seleccione un Conjunto de Datos y presione el botón |btn-borrar|

  .. image:: ../_static/images/img021.png

  .. image:: ../_static/images/img022.png
    :align: center

El sistema permite eliminar la revisión actual o todas las revisiones del Conjunto de Datos. Esta última acción elimina el Conjunto de Datos y todos sus recursos asociados, como así también los elimina del portal de datos abiertos. Por Revisión se entiende los distintos cambios realizados sobre la información del Conjunto de Datos.

.. image:: ../_static/images/img023.png
  :align: center

.. |icono-ver-sitio| image:: ../_static/images/icono-ver-sitio.png
.. |icono-eliminar| image:: ../_static/images/icono-eliminar.png
.. |icono-publicado| image:: ../_static/images/icono-publicado.png
.. |icono-editar| image:: ../_static/images/icono-editar.png
.. |btn-borrar| image:: ../_static/images/btn-borrar.png
