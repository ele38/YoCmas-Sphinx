Estructuras de Datos No Lineales
================================

Acerca de 
---------

A diferencia de las EDD lineales, las no lineales se basan en el hecho de que ahora los elementos no estan contiguos, sino que la forma de buscarlos sigue alguna otra lógica que no sea mirar el siguiente. 

Algunos ejemplos son:

* Árboles binarios
* Tablas de hashing

Set (conjunto) 
--------------

Es una EDD que consiste en organizar elementos no repetidos. Esto quiere decir que cada elemento va a encontrar una y una sola vez en el conjunto.

Inicialización 
**************

Incluimos la librería:

::

	#include <set>


Inicializamos nuestro conjunto:

::

	set < int > conjunto; // int puede ser reemplazado con cualquier otro tipo de dato

insert (Insertar)
*****************

Inserta un dato. Retorna un par de elementos, el primero siendo el iterador del valor insertado y el segundo siendo un bool que marca si es que ya existía o no. En el ejemplo de abajo, usamos .second para comprobar si se insertó correctamente o no.

::

	// Retorna TRUE ya que no estaba anteriormente
	if (conjunto.insert(10).second)
		// Retorna FALSE ya que ya había un 10.
	    cout << "ganai\n"; if (conjunto.insert(10).second); 
	cout << "no ganai\n";
	conjunto.insert(20);
	conjunto.insert(40);
	conjunto.insert(30);
	conjunto.insert(11);

find (Encontrar) 
****************

Busca un elemento en el set y si lo encuentra retorna un iterador al valor. De lo contrario, retorna conjunto.end();

::

	if (conjunto.find(10) != conjunto.end())
	    cout << "ganai\n";

erase (borrar) 
**************

Puedes borrar un valor si le entregas el iterador al valor.

::

	set < int >::iterator it = conjunto.find(11);
	if (it != conjunto.end())
	    conjunto.erase(it);

Iterar a través de un conjunto 
******************************

Puedes iterar a través de un conjunto con los valores ya ordenados con un iterador:

::

	// Imprime 10 11 20 30 40
	for (it = conjunto.begin(); it != conjunto.end(); ++it)
	    cout << *it << " ";
	cout << '\n';

Map (mapa, tabla de hashing) 
----------------------------

Toma dos datos, una llave y un valor. Puedes buscar una llave en tiempo logarítmico con la implementación de la STL. Pero con otras implementaciones se puede hacer en tiempo constante. Las llaves no se pueden repetir.

Ejemplo cotidiano 
*****************

* Libros:

   ============================ ===============
   Título (Llave)               Autor (Valor)
   ============================ ===============
   The C Programming Language   Brian Keringhan
   The AWK Programming Language Brian Keringhan
   1984                         George Orwell
   ============================ ===============

* Curso:

   ======== ===================================
   Apellido Cantidad de alumnos con el apellido
   ======== ===================================
   Gonzalez 3
   Perez    2
   ======== ===================================

Inicializar {#inicializar}
**************************

Incluimos la librería de map:

::

	#include <map>


Inicializamos el mapa curso:

::

	map<string, int> curso;

Insert (insertar)
*****************

* Forma 1:

::

	curso["perez"] = 1;


* Forma 2:

::

	curso.insert(pair<string, int>("gonzalez, 3"));

Operar con los valores 	
**********************

Se puede operar con el valor tomando la llave.
Ejemplo 1:

::

	// Incrementar el valor de la llave perez, por ejemplo.
	++curso.["perez"];


Ejemplo 2:

::

	cout << curso.["perez"] << endl; // El output será 2.


Cuidado con operar con valores no existentes, pues los inicializará de una forma inesperada.

Find (encontrar)
****************

Retorna un iterador, si no lo encuentra, apunta a map.end().
Asignamos el iterador ``it`` a gonzalez, y luego lo usamos:

::

	map<string, int>::iterator it;
	it = curso.find("gonzalez");

	if (it != curso.end()){
		cout << "Hay " << it->second << " " << it->first << " en el curso:\n";
		cout << "Llave: " << it->first << " Valor: " << it->second << '\n';
	}


Podemos incluso operar usando los iteradores:

::

	it->++second;

Erase (borrar)
**************

* Forma 1:

::

	it = curso.find("perez");
	curso.erase(it);


* Forma 2:

::

	curso.erase("gonzalez");

Recorrer los valores de un mapa 
*******************************

Es exactamente igual que en un conjunto:

::

	for (it = curso.begin(); it != curso.end(); ++it){
	    cout << "Llave: " << it->first << " Valor: " << it->second << '\n';
	}

Dudas que no dejan dormir 
*************************

1. ¿Qué pasa si modifico una llave? 

No se puede, tu código no compilará pues es ilegal hacerlo 👮🚓🚨

2. ¿Puedo buscar con el second? 

No, en ese caso recomendamos otra estructura, o tener dos maps 👀

3. ¿Puedo tener un map dentro de un map? 

Si, pero es de psicópata buscar dentro de ese map.
