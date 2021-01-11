# Iterator 

Itérateur est un patron de conception comportemental qui permet de parcourir les éléments d’une collection sans révéler sa représentation interne (liste, pile, arbre, etc.).  

# Problème  

Les collections ne servent que de conteneur pour un groupe d’objets, mais elles demeurent l’un des types de données les plus utilisés en programmation.  

La majorité des collections stockent leurs éléments dans de simples listes, mais certaines d’entre elles sont basées sur les piles, les arbres, les graphes ou d’autres structures complexes de données.  

Quelle que soit sa structure, une collection doit fournir un moyen d’accéder à ses éléments pour permettre au code de les utiliser. Elle doit donner la possibilité de parcourir tous ses éléments sans passer plusieurs fois par les mêmes.  

# Solution  

Le but du patron de conception itérateur est d’extraire le comportement qui permet de parcourir une collection et de le mettre dans un objet que l’on nomme itérateur.  

En plus d’implémenter l’algorithme de parcours, un objet itérateur encapsule tous les détails comme la position actuelle et le nombre d’éléments restants avant d’atteindre la fin. Grâce à cela, plusieurs itérateurs peuvent parcourir une même collection simultanément et indépendamment les uns des autres.  

# Possibilités d’application  

* Quand la structure de données de votre collection est trop complexe et que vous voulez cacher ces détails aux clients (parce que c’est pratique ou pour des raisons de sécurité).

   * L’itérateur encapsule le détail du fonctionnement de la structure complexe de données et passe plusieurs méthodes simples au client qui lui permettent d’accéder aux éléments de la collection. En plus d’être très pratique pour le client, ce fonctionnement permet de protéger la collection d’actions maladroites ou malicieuses que le client pourrait entreprendre s’il travaillait directement avec la collection.  

* Pour que le code du parcours soit le moins dupliqué possible dans votre application.

    * Un algorithme qui permet une itération complexe sur la collection a tendance à être très volumineux. Si on le place à l’intérieur de la logique de l’application, cela va masquer la responsabilité du code original et le rendre moins maintenable. Pour rendre le code encore plus simple et propre, vous pouvez écrire l’algorithme de parcours dans leur itérateur.  

* Permettre à votre code de naviguer dans des structures de données complexes ou inconnues.
  
    * Ce patron procure des interfaces génériques pour les collections et les itérateurs. Si votre code utilise bien ces interfaces, il va pouvoir manipuler toutes les collections (et leurs itérateurs) qui les implémentent.  

# Mise en œuvre  

* Déclarez l’interface itérateur. Elle doit comporter au moins une méthode qui récupère le prochain élément de la collection. Mais pour qu’elle soit vraiment utile, vous devriez en ajouter d’autres, par exemple récupérer l’élément précédent, connaitre la position actuelle ou vérifier la fin de l’itération.

* Déclarez l’interface de la collection et écrivez une méthode pour récupérer les itérateurs. Le type de la valeur de retour doit être l’interface de l’itérateur. Vous pouvez déclarer des itérateurs supplémentaires si vous pensez en utiliser d’autres.

* Mettez en place les classes concrètes des itérateurs pour les collections que vous allez parcourir. Un objet itérateur ne peut être lié qu’à une seule instance d’une collection. En général, ce lien est établi dans le constructeur de l’itérateur.

* Implémentez l’interface de la collection dans les classes de collection. Son but est de fournir un raccourci pour le client qui crée les itérateurs spécifiques à chaque classe de la collection. L’objet collection doit s’envoyer lui-même au constructeur de l’itérateur pour établir un lien entre eux.

* Écumez le code et remplacez toutes les occurrences de parcours de collection par vos itérateurs. Le client va chercher un nouvel itérateur chaque fois qu’il parcourt les éléments d’une collection.  

# Avantages 

* Principe de responsabilité unique. Vous allez nettoyer le code client et les collections en déplaçant les algorithmes de parcours ( souvent très lourds ) dans des classes séparées.  

* Principe ouvert/fermé. Vous pouvez implémenter de nouveaux types de collections et d’itérateurs et les utiliser avec le code existant sans rien endommager.  
  
* Vous pouvez parcourir une même collection avec plusieurs itérateurs simultanément, car chacun possède son propre état d’itération.  
  
* Pour cette même raison, vous pouvez arrêter une itération et la reprendre quand vous le souhaitez.  

# inconvénients

* L’utilisation de ce patron est exagérée si votre application ne se sert que de collections simples.  
* Les itérateurs sont parfois moins efficaces que certaines collections spécialisées.  

