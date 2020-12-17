Búsqueda binaria
================

Acerca de
---------

La búsqueda binaria es un algoritmo de *divide and conquer* (dividir y
conquistar), que nos permite encontrar un elemento dentro de una
estructura **ordenada** rápidamente. Al ejecutarse, toma el centro de un
arreglo y comprueba si el valor que se busca es igual al del centro. De
no serlo, verifica si el valor es menor o mayor al del centro.

Si el valor es mayor al del centro, se ignoran todos los valores
anteriores al centro, dividiendo la cantidad de números a la mitad.

Si el valor es menor al del centro, se ignoran todos los valores de
después del centro, dividiendo la cantidad de números a la mitad.

La complejidad de este algoritmo es **O(log(N))**, comparada con un
algoritmo lineal, que en el peor de los casos tiene complejidad
**O(N)**.

#. Ejemplos

   #. en la vida real

      Ir al medio de un diccionario, y buscar alfabéticamente, tomando
      una palabra central (más o menos), viendo si la palabra que
      queremos está antes o después y repetir el proceso de buscar una
      palabra central.

   #. Ejemplo computacional

      En esta imágen, se usa la búsqueda binaria para encontrar el 19.
      |image1|

Uso mediante la librería STL
----------------------------

* Importar

   Podemos directamente importar toda la stl o podemos importar la
   librería <algorithm> de la siguiente forma:

.. code:: cpp
    :number-lines: 

    #include <algorithm>

* binary\_search()

   La librería STL ya incluye binary search, si queremos saber si el valor 3 está en un vector, podemos ejecutar:

.. code:: cpp
    :number-lines: 

    vector<int> v{1,2,5,7};
    if (binary_search (v.begin(), v.end(), 3)) {
      cout << "Se encuentra el valor 3 en nuestro vector\n";
    }
    else {
      cout << "No hay ningún 3 en nuestro vector\n";
    }

Retorna un *bool*.

* lower\_bound() (límite inferior)

   La función lower_bound() de la librería STL retorna un puntero a un valor **superior** o, si es posible, **igual** al entregado dentro de una estructura ordenada.

   Si todos los elementos en el arreglo son inferiores al valor pedido, se entrega el último elemento del arreglo. Si los elementos del arreglo son superiores al valor pedido, se entrega el primer elemento del arreglo.

   Por ejemplo:

.. code:: cpp
    :number-lines: 

    vector<int> v{ 10, 20, 30, 30, 30, 40, 50 };
    *lower_bound(v.begin(), v.end(), 30);

Valor de retorno: un iterador que apunta hacia **30** (el primero en el arreglo, en la posición [2])

* upper\_bound() (límite superior)

   La función upper\ :sub:`bound`\ () de la librería STL nos entrega un puntero a un valor **superior** al pedido en un arreglo ordenado.

   En el caso de que no haya un valor superior al pedido, nos entrega el último valor del arreglo.

   Por ejemplo:

.. code:: cpp
    :number-lines: 

    *upper_bound(v.begin(), v.end(), 30);

Valor de retorno: iterador al **40** (posición [4])

Implementaciones propias
------------------------

Implementación con while
************************

   Esta implementación nos retorna el índice del número a buscar dentro de un arreglo.

.. code:: cpp
    :number-lines: 

    int binarySearch(int arr[], int l, int r, int x)
    {

        while (l <= r) {
            //esto es lo mismo que hacer (r + l) / 2 
            int m = l + (r - l) / 2;

            // Revisa si x esta al medio
            if (arr[m] == x){
                return m;
            }

            // Si x es mayor, ignorar la izquierda
            if (arr[m] < x){
                l = m + 1;
            }
            // Si x es menor, ignorar la derecha
            else{
                r = m - 1;
            }
        }
        return -1;

    }

Implementación recursiva
************************

   Esta implementación nos retorna el índice del número a buscar dentro de un arreglo.

.. code:: cpp
    :number-lines: 

    int binarySearch(int arr[], int l, int r, int x){
        if (r >= l){
            //esto es lo mismo que hacer (r + l) / 2 
            int mid = l + (r - l) / 2;

            // Revisa si x esta al medio

            if (arr[mid] == x){
                return mid;
            }

            // Si x es mayor, ignorar la izquierda
            if (arr[mid] > x){
                return binarySearch(arr, l, mid - 1, x);
            }
            // Si x es mayor, ignorar la derecha
            return binarySearch(arr, mid + 1, r, x);
        }
        return -1;
    }

.. |image1| image:: https://uniwebsidad.com/static/libros/imagenes/algoritmos-python/f0801.png