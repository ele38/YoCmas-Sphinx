Búsqueda Lineal
===============

Acerca de
---------

La búsqueda lineal es un algoritmo se trata de pasar elemento por elemento hasta encontrar el correcto. Esto lo hace de forma secuencial, de ahí el nombre lineal. 

Entonces analizando, si uno tiene **N** elementos toma un elemento y ve si es el correcto. Si corresponde listo ganamos, si no pasa al siguiente. Esto lo repite hasta el último elemento.

Este algoritmo tiene complejidad **O(N)**. La principal gracia de este algoritmo es cuando el grupo de elementos no están ordenados por lo cual uno no sabría como moverse. En la siguiente sección se revisará un algoritmo para cuando el grupo este ordenado.

Ejemplo
-------

    ===== ===== ===== ===== ===== ===== 
    Step  Pos 0 Pos 1 Pos 2 Pos 3 Ele
    0     4     2     5     1     5
    1     **4** 2     5     1     5
    2 	  4     **2** 5     1     5
    3     4     2     **5** 1     5
    ===== ===== ===== ===== ===== =====

Aquí se ve como en la iteración número 3 encuentra el elemento por lo deja de revisar :D.

Código
------

.. code:: cpp
    :number-lines: 

    int linealSearch(vector< int > &vec, int ele){
    	for(int i = 0; i < vec.size(); i++){
    		if(vec[i] == ele){
    			// Retorna la posicion en que se encuentra
    			return i;
    		}
    	}
    	// Retorna -1 en caso de que el elemento no este
    	return -1;
    }
