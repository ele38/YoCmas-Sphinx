Algoritmos de Decrecer y Conquistar
===================================

Acerca de
---------

Rellenar

Selection sort
--------------

-  Tiene dos sub-arreglos, uno de elementos ya ordenados y uno de los elementos resantes.
-  El arreglo ya ordenado parte vacío.
-  Busca el valor mínimo entre los elementos no ordenados y lo añade al final de los ordenados.

Ejemplo
*******
	
    ===== ===== ===== ===== =====
    Step  Pos 0 Pos 1 Pos 2 Pos 3
    0     5     3     4     1
    1     5     3     4     *1*
    2     **1** 5     *3*   4
    3     **1** **3** 5     *4*
    4     **1** **3** **4** **5**
    ===== ===== ===== ===== =====

Código de ejemplo
*****************

.. code:: cpp
    :number-lines: 

	void swap(vector<int> &vec, int i, int j){
		int aux = vec[i];
		vec[i]=vec[j];
		vec[j]= aux;
	}

	void selectionSort(vector <int> &vec){
		int size = vec.size(); //tamaño :D
		for(int i = 0; i < size - 1; i++){ // 
			int min_in = i;
			for(int j= i + 1; j < size; j++){
				if(vec[j] < vec[min_in]){
					min_in=j;
				}
			}
			swap(vec, min_in, i);
		}
	}

**Nota: este código fue robado de Natalia Carrión**