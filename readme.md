## Aportar

### Archivo

Para agregar un temario, debe primero agregar una carpeta llamada acortada, descriptivamente llamada, por ejemplo temario y dentro de esta debe existir un archivo temario.rst, que corresponderá al inicio de esa categoría.

```
+-- source
|   +-- busqueda
|   +-- edd
|   +-- ordanamiento
|   +-- temario
|   |   +-- temario.rst
|   +-- index.rst
```

Ahora dentro del archivo index.rst, deben añadir el camino, pongalo donde creen que debería corresponder. Si es que se debe cambiar se cambiará.

```rst
.. toctree::
    :maxdepth: 3

    edd/edd
    ordenamiento/ordenamiento
    busqueda/busqueda
    temario/temario
```

Luego, dentro de este temario.rst se debe escribir una descripción respecto al temario y un toctree para mostrar las subcategorias dentro de este temario. Y cada una de estas subcategorias deben estar dentro de la misma carpeta temario.

```
+-- source
|   +-- busqueda
|   +-- edd
|   +-- ordanamiento
|   +-- temario
|   |   +-- temario.rst
|   |   +-- catego1.rst
|   |   +-- catego2.rst
|   +-- index.rst
```

Ejemplo en el interior de temario.rst.

```rst
Temario
=======

Descripcion bla bla

.. toctree::
    :maxdepth: 3

    catego1.rst
    catego2.rst
```

### Formato

Para manterener una constancia el texto debe estar formeteado de la siguiente forma:

```rst
Titulo principal
================

Sub Titulo 1
------------

Sub Sub Titulo 1
****************

Sub Sub Titulo 2
****************

Sub Titulo 2
------------
```

## Compilar
Luego, para compilar basta correr el comando 'make github' desde la raiz del proyecto. Para poder probar los cambios recién hechos, puedes abrir docs/index.html con tu navegador.
