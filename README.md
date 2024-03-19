# Efficient_Graph_Based_Image_Segmentation

---



L'article peut être trouvé à l'adresse suivante : [Efficient Graph-Based Image Segmentation](https://cs.brown.edu/people/pfelzens/papers/seg-ijcv.pdf).

**Objectif :** Développer un algorithme de segmentation d'images par graphe, en appliquant la méthode décrite dans l'article et en y ajoutant des fonctions qui comptent le nombre de composants et affichent les boîtes englobantes.

**Paramètres d'entrée de la fonction :**
- \( k = 20 \) : Paramètre de l'algorithme. Pour la segmentation d'objets plus grands, la valeur de \( k \) devrait être augmentée.
- \( \sigma = 0.60 \) : Paramètre du filtre gaussien. Une petite valeur pour \( \sigma \) implique un lissage faible, tandis qu'une valeur élevée entraîne un lissage plus fort.
- \( \text{min} = 3 \) : Taille minimale des objets à segmenter.

**Algorithme :**

**Description Générale :**
- **Entrée :**
  - Un graphe \( G = (V, E) \) avec \( n \) sommets et \( E \) arêtes.
  - Un paramètre constant \( k \).

- **Sortie :**
  - Une partition de \( V \) en composantes \( S = (C_1, C_2, ..., C_r) \).

- **Initialisation :**
  - Trier toutes les arêtes \( e \in E \) en \( (e_1, e_2, ... e_m) \) selon leurs poids dans un ordre croissant.

**Étape d'itération (pour \( q = 1,2,...,m \)) :**
1. Prendre l'arête \( e_q = (v_i, v_j) \), où \( v_i \in C_i \) et \( v_j \in C_j \).
2. Si \( C_i \neq C_j \) :
   - **Étape 2.1 :** Si le prédicat de frontière \( D(C_i, C_j) \) est faux, fusionner les composants \( C_i \) et \( C_j \).
   - **Étape 2.2 :** Si \( C_i \) et \( C_j \) sont fusionnés, définir \( \text{Int}(C_i \cup C_j) = w(e_q) \).
3. Incrémenter \( q \) ( \( q \leftarrow q + 1 \) ) et retourner à l'Étape 1.

---

