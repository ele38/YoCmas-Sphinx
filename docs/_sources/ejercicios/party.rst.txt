The Party, Part I
=================================

Problema
--------

Descripción
***********

Don Giovanni likes to dance-especially with girls! And everyone else in the party enjoyed the dance, too. Getting a chance to dance with the host (that is Don Giovanni) is the greatest honour; failing that, dancing with someone who has danced with the host or will dance with the host is the second greatest honour. This can go further. De ne the Giovanni number of a person as follows, at the time after the party is over and therefore who has danced with whom is completely known and fixed:

1. No one has a negative Giovanni number.

2. The Giovanni number of Don Giovanni is 0.

3. If a personpis not Don Giovanni himself, and has danced with someone with Giovanni number n, and has not danced with anyone with a Giovanni number smaller thann, thenphas Giovanni number n + 1.

4. If a person's Giovanni number cannot be determined from the above rules (he/she has not danced with anyone with a  nite Giovanni number), his/her Giovanni number is 1. Fortunately, you will not need this rule in this problem.

Your job is to write a program to compute Giovanni numbers.

Input
*****

The input begins with a single positive integer on a line by it self indicating the number of the cases following, each of them as described below. This line is followed by a blank line, and there is also a blank line between two consecutive inputs.

The  rst line has two numbersPandD; this means there are P persons in the party (including Don Giovanni) and Ddancing couples (P ≤ 1000 and D ≤ P(P - 1)/2). ThenDlines follow, each containing two distinct persons, meaning the two persons has danced. Persons are represented by numbers between 0 and P - 1; Don Giovanni is represented by 0.

As noted, we design the input so that you will not need the1rule in computing Giovanni numbers.

We have made our best effort to eliminate duplications in listing the dancing couples, e.g., if there is a line "4 7" among the D lines, then this is the only occurrence of "4 7", and there is no occurrence of "7 4". But just in case you see a duplication, you can ignore it (the duplication, not the first occurrence).

Output
******

For each test case, the output must follow the description below. The outputs of two consecutive cases will be separated by a blank line.

Output P - 1 lines. Line i is the Giovanni number of personi, for 1 ≤ i ≤ P - 1. Note that it is P - 1 because we skip Don Giovanni in the output.

Sample Input
************

1

5 6
0 1
0 2
3 2
2 4
4 3
1 2

Sample Output
*************

1 
1
2
2

Solución
--------

Explicación de la solución
**************************

Todo lo explicado durante el problema se puede traducir a un problema de grafos, donde se quiere saber la mínima distancia de un punto a cualquier lado. Además, se indica que las distancias serían todas equivalente. Por lo que se debe realizar un BFS, algoritmo que permitiría solucionar lo anterior mencionado. Donde cada pareja correspondería a una arista del grafo, que representaría la conexión. Entonces se aplicaría BFS, y luego se revisaría el arreglo de distancias desde 1 hasta P - 1 y se mostraría eso por pantalla.

Código
******

.. code:: cpp
  :number-lines:
  
  #include<bits/stdc++.h>
  using namespace std;

  #define INF 1000000

  vector < vector< int > > adjlist;
  vector < int > distancia;

  void bfs(int nodoInicial){
      queue< int > colita;
      distancia[nodoInicial] = 0;
      colita.push(nodoInicial);
      while(!colita.empty()){
          int nodoActual = colita.front();
          colita.pop();
          for(int i = 0; i < adjlist[nodoActual].size(); i++){
              int vecino = adjlist[nodoActual][i];
              if(distancia[vecino] == INF){
                  distancia[vecino] = distancia[nodoActual] + 1;
                  colita.push(vecino);
              }
          }
      }
  }

  int main(){
      int t, i;
      cin >> t;
      while(t--){
          int p, d;
          cin >> p >> d;

          adjlist.assign(p, vector< int >());
          distancia.assign(p, INF);

          for(i = 0; i < d; i++){
              int a, b;
              cin >> a >> b;
              adjlist[a].push_back(b);
              adjlist[b].push_back(a);
          }

          bfs(0);

          for(i = 1; i < p; i++){
              cout << distancia[i] << "\n";
          }

          if(t > 0)
              cout << "\n";
      }
  }

Información adicional
---------------------

Link del problema: https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=1900

Autor de la solución: Gabriel Carmona

Contacto en caso de dudas:
**************************

Discord: MrYhatoh#8885

Email: gabriel.carmonat@sansano.usm.cl
