## Détection d'une structure communautaire dans les réseaux

Ce projet consiste à proposer des méthodes de détection des structures communautaires dans les réseaux. 

Pour ce faire, on distingue trois groupes d'algorithmes :

* Les algorithmes de division
* Les algorithmes agglomératifs
* Les méthodes d'optimisation

Dans ce travail, nous nous intéressons plutôt aux méthodes d'optimisation, qui consistent à maximiser une fonction objective générale, la modularité \( Q \).

La modularité \( Q \) est définie par la formule suivante :

$$\
Q = \frac{1}{2m} \sum_{i,j} \left( A_{ij} - \frac{k_i k_j}{2m} \right) \delta(C_i, C_j)
\$$

où :
- $$\( A_{ij} \)$$ est l'élément de la matrice d'adjacence,
- $$\( k_i \) et \( k_j \) sont les degrés des nœuds \( i \) et \( j \)$$,
- \( m \) est le nombre total d'arêtes,
- \( \delta(C_i, C_j) \) est une fonction qui vaut 1 si les nœuds \( i \) et \( j \) appartiennent à la même communauté, et 0 sinon.$$

### Principe de la méthode de Louvain

La méthode de Louvain est un algorithme itératif qui vise à maximiser la modularité. Elle se déroule en deux phases :

1. **Phase de localisation** : Chaque nœud du réseau est initialement placé dans sa propre communauté. L'algorithme parcourt tous les nœuds et tente de les réaffecter à des communautés voisines afin d'augmenter la modularité. Si une réaffectation améliore la modularité, elle est acceptée.

2. **Phase d'agrégation** : Une fois que la modularité ne peut plus être améliorée par des réaffectations locales, les communautés sont agrégées pour former un nouveau réseau, où chaque communauté est représentée par un nœud unique. L'algorithme répète ensuite les étapes ci-dessus sur ce nouveau réseau.

Ce processus se poursuit jusqu'à ce que la modularité atteigne un maximum, permettant ainsi de révéler la structure communautaire sous-jacente du réseau.
