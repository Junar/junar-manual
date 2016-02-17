
Content
*********

.. toctree::
   :maxdepth: 3

   1. Autorización <../_sections/section-01-autorizacion.rst>

   2. Recursos <../_sections/section-02-recursos.rst>

   3. Métodos <../_sections/section-03-metodos.rst>

La API de DATAL debe seguir en la medida de lo posible las guias de diseño del Gobierno de Chile, expuestas en https://github.com/e-gob/api-standards.

En resumen, se estructurarán las URLs de la API siguiendo el patrón REST, asignando URLs a recursos, utilizando los verbos GET, POST, PUT, PATCH, DELETE para las correspondientes acciones y la extension del formato en que se recibiran los resultados, por ejemplo:

::

  GET /api/v2/datasets/12345.json

para solicitar un dataset identificado por el ID 12345 en formato JSON.

