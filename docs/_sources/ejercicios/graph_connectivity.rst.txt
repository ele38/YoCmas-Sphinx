Graph Connectivity
=================================

Problema
--------

Descripción
***********

Consider a graphGformed from a large number of nodes connected by edges. G is said to be connected if a path can be found in 0 or more steps between any pair of nodes inG. For example, the graph below is not connected because there is no path from A to C.This graph contains, however, a number of subgraphs that are connnected, one for each of the following sets of nodes: {A}, {B}, {C}, {D},{E}, {A,B}, {B,D}, {C,E}, {A,B,D}.

A connected subgraph is maximal if there are no nodes and edges in the original graph that could be added to the subgraph and still leave it connected. There are two maximal connected subgraphs above, one associated with the nodes {A;B;D} and the other with the nodes {C;E}.Write a program to determine the number of maximal connected sub-graphs of a given graph.

Input
*****

The input begins with a single positive integer on a line by it self indicating the number of the cases following, each of them as described below. This line is followed by a blank line, and there is also a blank line between two consecutive inputs. 

The first line of each input set contains a single uppercase alphabetic character. This character represents the largest node name in the graph. Each successive line contains a pair of upper case alphabetic characters denoting an edge in the graph.

The sample input section contains a possible input set for the graph pictured above. Input is terminated by a blank line.

Output
******

For each test case, write in the output the number of maximal connected subgraphs. The outputs of two consecutive cases will be separated by a blank line.

Sample Input
************

1

E
AB
CE
DB
EC

Sample Output
*************

2

Solución
--------

Explicación de la solución
**************************

En el presente problema te representan un problema de grafos, donde piden encontrar cuantas componentes conexas existen. Para ello se ocupará el algoritmo DFS, de tal forma de determinar estas componentes, por lo que se realizará un loop que pasará nodo por nodo, donde si el nodo no ha sido visitado todavía, entonces se aplicará DFS y se sumará 1 a la cantidad de componentes conexas.

Lo otro es que como detalle te pasan los nodos como caracteres en letras mayusculas, pero eso en verdad no es distinto al como se pasa normalmente (0 a n - 1, por ejemplo). Lo que hay que realizar es basicamente transformar esto basandosé en el código ASCII, puesto que todos estos caracteres son continuos entre sí. Entonces se puede definir: 'A' -> 1, 'B' -> 2, y así hasta 'Z'.

En realidad, este es un problema directo. Lo más complicado del problema sería leer ese input. Para ello, primero se leerá el entero de cantidad de casos, luego se leerá el primer salto de línea. Ahora, mientras que la cantidad de casos que falten por revisar es mayor a 0, entonces se reducerá uno a la cantidad de casos y se leerá el nodo más grande que se verá. Luego se hace un loop mientras no lea un salto de línea que corresponde a que comienza un caso nuevo o el final del archivo, significa que no hay más input.

Código
******

.. code:: cpp
  :number-lines:
  
  #include<bits/stdc++.h>
  using namespace std;

  #define VISITADO true
  #define NO_VISITADO false

  vector < vector< int > > adjlist;
  vector < bool > visitados;

  void dfs(int nodoActual){
      visitados[nodoActual] = VISITADO;

      //adjlist[nodoActual].size() cuantos vecinos tiene el nodo actual
      for(int i = 0; i < adjlist[nodoActual].size(); i++){
          int vecino = adjlist[nodoActual][i];
          if(visitados[vecino] == NO_VISITADO){
              dfs(vecino);
          }
      }

  }

  int main(){
    int t;
    char line;
    scanf("%d%c", &t, &line);
    scanf("%c", &line);
    while(1){
      if(t == 0){
        break;
      }
      
      t--;

      char masGrande, nodeA, nodeB;
      scanf("%c%c", &masGrande, &line);
      int tamano = masGrande - 'A' + 1;
      adjlist.assign(tamano, vector< int >());
      visitados.assign(tamano, NO_VISITADO);
      while(scanf("%c", &nodeA) != EOF && nodeA != '\n'){
        scanf("%c%c", &nodeB, &line);

        int realA, realB;
        realA = nodeA - 'A';
        realB = nodeB - 'A';
        

        adjlist[realA].push_back(realB);
        adjlist[realB].push_back(realA);
      }

      int componentes = 0;
      for(int i = 0; i < tamano; i++){
        if(visitados[i] == NO_VISITADO){
          dfs(i);
          componentes++;
        }
      }

      printf("%d\n", componentes);
      if(t != 0)
        printf("\n");

      adjlist.clear();
      visitados.clear();
    }
    return 0;
  }

Información adicional
---------------------

Link del problema: https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&category=0&problem=400&mosmsg=Submission+received+with+ID+25995168

Autor de la solución: Gabriel Carmona

Contacto en caso de dudas:
**************************

Discord: MrYhatoh#8885

Email: gabriel.carmonat@sansano.usm.cl
