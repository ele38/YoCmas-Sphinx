Algoritmos de Fuerza Bruta
==========================

Acerca de
---------

Los algoritmos de fuerza bruta son algoritmo en general simples, que realizan una idea de ''Todos con todos''. Esto puede llegar a ser muy costoso en complejidad.

Bubble sort
-----------

-  Se van comparando los elementos, haciendo que los más grandes suban en el arreglo, como una burbuja.
-  Da lo mismo cómo estén ordenadas las cosas, porque puedes modificar la función de comparación.
-  Funciona invirtiendo el orden de cada par de elementos, si es que el primero es mayor que el segundo.
-  Por ejemplo, se podría usar para contar el número de inversiones que hay que hacer.

Ejemplo
*******

    ===== ===== ===== ===== =====
    Step  Pos 0 Pos 1 Pos 2 Pos 3
    0     5     3     4     1
    1     *5*   *3*   4     1
    2     3     *5*   *4*   1
    3     3     4     *5*   *1*
    4     3     4     1     **5**
    5     *3*   *4*   1     **5**
    6     3     *1*   *4*   **5**
    7     3     1     **4** **5**
    8     *3*   *1*   **4** **5**
    9     1     **3** **4** **5**
    10    **1** **3** **4** **5**
    ===== ===== ===== ===== =====

Código de ejemplo
*****************

.. code:: cpp
    :number-lines: 

    void swap(vector<int> &arr, int i, int j){
        int aux = arr[i];
        arr[i] = arr[j];
        arr[j] = aux;
    }

    void bubblesort (vector<int> &vec) {
        int size = vec.size();
        for (int i = size - 1; i > 0; --i) {
            for (int j = 0; j < i; ++j) {
                if (vec[j] > vec[j+1]) {
                    swap(arr, j, j + 1);
                }
            }
        }
        return;
    }

Insertion sort
--------------

-  Se va de izquierda a derecha, se compara el segundo con el primero, se intercambian si el segundo es menor, si este es el caso, se vuelve a preguntar si el de la izquierda es menor al de mas a la izquierda y así hasta que se encuentre un caso en el que no o se llegue al principio del arreglo.

Ejemplo
****************

    ===== ===== ===== ===== =====
    Step  Pos 0 Pos 1 Pos 2 Pos 3
    0     5     3     4     1
    1     *5*   *3*   4     1
    2     **3** 5     4     1
    3     3     *5*   *4*   1
    4     *3*   *4*   5     1
    5     **3** **4** 5     1
    6     3     4     *5*   *1*
    7     3     *4*   *1*   5
    8     *3*   *1*   **4** **5**
    9     **1** **3** **4** **5**
    ===== ===== ===== ===== =====

Código de ejemplo
**************************

.. code:: cpp
    :number-lines: 

    void swap(vector<int> &arr, int i, int j){
        int aux = arr[i];
        arr[i] = arr[j];
        arr[j] = aux;
    }

    void insertion_sort(vector<int> &arr){
        for(int i = 1; i < arr.size(); ++i){
            for(int j = i; j >= 0; --j){
                //caso swap
                if(arr[j] < arr[j-1]){
                  swap(arr, j, j-1);   
                }
                //caso no swap = todo ok todo correcto :]
                else if(arr[j] >= arr[j-1] || j == 0){
                    break; 
                }
            } 
        }
        return;
    }

**Nota: este código fue robado de Julieta Coloma**