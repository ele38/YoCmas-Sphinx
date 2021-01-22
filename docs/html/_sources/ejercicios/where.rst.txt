Where's My Internet?
=================================

Problema
--------

Descripción
***********

A new town is being built far out in the country, and currently there are N

houses. People have already started moving in. However, some of the houses aren’t connected to the internet yet, and naturally residents are outraged.

The houses are numbered 1
to N. House number 1

has already been connected to the internet via a long network cable to a neighboring town. The plan is to provide internet to other houses by connecting pairs of houses with separate network cables. A house is connected to the internet if it has a network cable to another house that’s already connected to the internet.

Given a list of which pairs of houses are already connected by a network cable, determine which houses are not yet connected to the internet.

Input
*****

The first line of input contains two integers 1 ≤ N,M ≤ 200000, where N is the number of houses and M is the number of network cables already deployed. Then follow M lines, each containing a pair of distinct house numbers 1 ≤ a,b ≤N meaning that house number a and house number b are already connected by a network cable. Each house pair is listed at most once in the input.

Output
******

If all the houses are already connected to the internet, output one line containing the string Connected. Otherwise, output a list of house numbers in increasing order, one per line, representing the houses that are not yet connected to the internet.

Sample Input
************

6 4
1 2
2 3
3 4
5 6

Sample Output
*************

5
6

Solución
--------

Explicación de la solución
**************************

Este problema es tratar de ver cuales son las cosas que no hacen parte de la componente conexa en que se encuentra la casa número 1. Entonces lo que hay que realizar es un DFS a partir de 1, y luego hay que revisar que nodos no han sido visitados e imprimirlos en el orden correcto. En el caso que no se vaya a imprimir nada puesto que todos son visitados se imprime 'Connected'.

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
    int n, m, i;
    
    cin >> n >> m;
    adjlist.assign(n, vector< int >());
    visitados.assign(n, NO_VISITADO);

    for(i = 0; i < m; i++){
      int a, b;
      cin >> a >> b;
      adjlist[a - 1].push_back(b - 1);
      adjlist[b - 1].push_back(a - 1);
    }

    dfs(0);

    int connected = 1;
    for(i = 0; i < n; i++){
      if(visitados[i] == NO_VISITADO){
        cout << i + 1 << "\n";
        connected = 0;
      }
    }

    if(connected)
      cout << "Connected\n";
    return 0;
  }

Información adicional
---------------------

Link del problema: https://open.kattis.com/problems/wheresmyinternet

Autor de la solución: Gabriel Carmona

Contacto en caso de dudas:
**************************

Discord: MrYhatoh#8885

Email: gabriel.carmonat@sansano.usm.cl
