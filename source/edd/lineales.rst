Estructuras de Datos Lineales
=============================

Acerca de
---------

Estas estructuras se basan en que los elementos estan contiguos, esto quiere decir que los elementos estan ordenados de manera que un elemento va a después del otro.

Arrays
------

Los arrays son conjuntos de datos que se almacenan en memoria de manera contigua usando el mismo nombre. Se usan índices para diferenciar los distintos valores del arreglo.

Para crear una arreglo es necesario saber la cantidad de elementos que van a componer nuestro arreglo, pues la cantidad de elementos no se puede cambiar.

Una cosa muy importante que al principio uno suele olvidar es que los índices de los arreglos parten en 0. Es decir, un arreglo de tamaño n puede tomar índices desde el 0 hasta el n-1.


Inicialización 
**************

Hay dos formas de inicializar un array, especificando su tamaño o llenandolo con valores por defecto.

Inicializar un array por su tamaño 
**********************************

Para inicializar un array por su tamaño, lo único que hay que especificar es el nombre de la variable y colocar entre "[]" el tamaño de nuestro arreglo. Recordar que como los arrays parten en 0, el valor máximo que podremos acceder será el tamaño del array menos 1.

::
	
	// Inicializar un arreglo de ints de tamaño 38.
	int arreglo[38]; 



Inicializar un array con valores por defecto 
********************************************

Para inicializar un array con valores por defecto, no es necesario especificar el tamaño de nuestro array, pues este está implícito en la cantidad de valores que introducimos.

::

	// Esto genera el arreglo siguiente 
	//[3, 6, 2, 1]
	int arreglo2[] = {3, 6, 2, 1};



Leer el valor de un arreglo 
***************************

Para leer un valor de nuestro arreglo, solo hay que especificar el nombre del arreglo y su índice. Notar que sólo se puede acceder a un valor de un arreglo a la vez.

::

	// Retorna 1
	arreglo2[3];



Asignar valores a un arreglo 
********************************

Para esto, hay que especificar la variable, el índice al cuál acceder y especificar su nuevo valor. Recordar que el valor del índice puede ser una variable, pero que no puede estar fuera del rango del tamaño de nuestro arreglo.

::
	
	// El indice 3 de nuestro arreglo, ahora tiene el valor 3
	arreglo2[3] = 5;



Arrays multidimensionales 
-------------------------

Un array multidimensional es aquel que requiuere de más de un índice para ser llamado, como su nombre lo indica, es útil para cuando necesitamos acceder a datos que requieren más de una dimensión, como por ejemplo valores dentro de una malla. Otra forma de enternder los arrays multidimensionales es como un arreglo de arreglos (de arreglos de arreglos.. n veces, siendo n la cantidad de dimensiones). Los arreglos de 2 dimensiones también son conocidos como matrices.


Inicializar un arreglo multidimensional 
***************************************

Para esto, hay que especificar el tamaño de cada dimensión del array. Notar que la regla de que empiezan en 0 y terminan en n-1 se sigue cumpliendo. Es posible asignarles valores predeterminados, pero creo que eso se va poniendo exponencialmente más psicópata a medida de que vas incrementando las dimensiones del array a crear, por lo que no lo voy a demostrar.

::

	int matriz[3][4];
	int tridimensional[100][100][100];



Asignar valores en un arreglo multidimensional 
**********************************************

Es muy similar a cómo se hace en un arreglo unidimensional, solo que se especifica cada índice.

::

	int n = 3, m = 5;
	matriz[2][1] = 10;
	tridimensional[n][m] = 4;



## Vectors (vectores) {#vectors--vectores}

Los vectores son como arreglos, excepto de que el tamaño es dinámico, es decir, se puede cambiar.


Inicializar un vector
*********************

Incluimos la librería:

::

	#include <vector>


Inicializamos nuestro vector "vec":

::

	// Inicializa un vector de tamaño 3 con todos sus valores = 0
	// Tanto el tamaño como valor son opcionales.
	int n = 3;
	vector < int > vec(n, 0);



Asignar un valor
****************

::

	// Asigna el valor "1" al índice 2 (es decir, al 3er valor del vector)
	vec[2] = 1; 



push back (empujar atrás) 
*************************

Si no sabemos el tamaño de nuestro vector, podemos simplemente usar push\_back(valor); para enviar es valor al final del vector.

::

	// Inserta un 1 al final del vector
	vec.push_back(1);


Por ejemplo, se podría usar en un for, sin necesidad de inicializar el vector con una cantidad de valores.

::

	vector <int> vec2;
	int n;
	cin >> n;
	for (int i = 0; i < n; ++i){
	    int valor;
	    cin >> valor;
	    vec2.push_back();
	}

pop back (quitar atrás) 
***********************

Elimina el último valor del vector.

::

	// En este caso, elimina el 1
	vec.pop_back();

insert (insertar) 
*****************

Podemos insertar un valor entre dos indices de un vector. El problema de esto es que mueve todos los valores que estén más adelante, lo que es lento.

::

	// Inserta el valor 4 al índice 2
	vec.insert(vec.begin() + 2, 4);

erase (borrar)
**************

Borra un dato del vector. Al igual que el insert, tiene que mover todos los datos siguientes (esta vez a la derecha).

::

	// Elimina el valor con índice 2
	// En nuestro caso, el 4 que insertamos antes.
	vec.erase(vec.begin() + 2);

Iteradores de un arreglo 
************************

Hay ciertos iteradores que podemos usar en un arreglo que nos ayudarán en algunos casos, como por ejemplo si quieremos recorrer un arreglo. Estos son:

-   begin() -- Iterador que accede al primer valor del arreglo.
-   end() -- Accede al final del arreglo.
-   rbegin() -- Accede al ultimo elemento del arreglo
-   rend -- Accede al inicio del arreglo


Stacks (pilas)
--------------

La pila es una estructura de datos lineal al que sólo puedes acceder al último elemento que fue insertado. Imagina una pila de platos, por ejemplo.

::

	stack < int > pilita;

push (empujar)
**************

Empuja un dato a la cima de la pila.

::

	// Empuja un 8 a la cima de la pila.
	pilita.push(8);

top (cima)
**********

Lee lo que hay en la cima de la pila.

::

	// Siguiendo el ejemplo anterior
	// Esto retorna 8
	pilita.top();

pop (quitar)
************

Remueve el dato de la cima de la pila.

::

	// Siguiendo el ejemplo anterior
	// Remueve el 8
	pilita.pop();

empty (vacío)
*************

Retorna 1 si la pila está vacía, de lo contrario retorna 0.

::

	// Retorna 1 ya que nuestra pila está vacía.
	pilita.empty();

size (tamaño)
*************

Retorna el tamaño de nuestra pila.

::

	// Retorna 0 ya que nuestra pila no tiene datos.
	pilita.size();

Queues (colas) 
--------------

La cola es una estructura de datos lineal al que sólo puedes acceder al primer elemento que fue insertado. Imagina una fila de una caja de un supermercado, por ejemplo.

::

	queue < int > colita;

push (empujar)
**************

Añade un dato al final de la cola.

::

	colita.push(5);
	colita.push(4);
	colita.push(3);
	colita.push(2);
	colita.push(1);

front (frente)
**************

Lee el dato que está al frente de la cola.

::

	// Siguiendo el ejemplo construido antes
	// Retorna 5, ya que fue lo primero que empujamos a la cola
	colita.front();

pop (quitar) 
************

Remueve el dato que está al frente de la cola

::

	// Remueve el 5
	colita.pop();
	// Retorna 4, ya que fue lo segundo que empujamos a la cola (y que ahora está primero).
	colita.front();

empty (vacío)
*************

Retorna 1 si la cola está vacía, de lo contrario retorna 0.

::

	// Retorna 1 ya que nuestra cola está vacía.
	colita.empty();

size (tamaño)
*************

Retorna el tamaño de nuestra cola.

::

	// Retorna 0 ya que nuestra cola no tiene datos.
	colita.size();

