# Design Pattern Command

## Son objectif :

Lors d'une conception d'application on a souvent besoin d’émettre des requêtes sur n'importe quel objet, et ce, sans connaître, ni ses caractéristiques, ni ses fonctions/méthodes. C'est ici que le Command Pattern va jouer son rôle, puisque il va l’encapsuler les requêtes.

Petit rappel :  
l’encapsulation en langage orienté objet consiste à cacher l'implémentation de l'objet, en empêchant l'accès aux données par un autre moyen que les services proposés.  
L'encapsulation permet donc de garantir l'intégrité des données contenues dans l'objet.  
C'est l'un des principes les plus importants en Java et langages similaires.

Ce pattern permet en premier lieu, d'apporter une sécurité dans les applications, grâce à cette fameuse encapsulation.  
Mais il permet aussi supprimer toutes duplications de code, au moyen d'une abstraction qui va lui permettre de fonctionner sans connaître l'objet cible ! Plus d'abstraction permet donc une meilleure maintenance du code, permettant de facilement le modifier ou l'étendre.

# Exemple d'une application du Command Pattern

Une personne veut aller ou éteindre son ordinateur :

Avec le pattern command :  
La personne actionne l’Invoker de son ordinateur, ici c'est un switch.
La ConcreteCommande « RestartCommand » ou « ShutDownCommand » est exécutée
Cela permet ensuite d'invoquer les méthodes shutDown() et restart() du Computer (Receiver).  
L'encapsulation permet de le faire fonctionner sur n'importe quel objet qui aurait une méthode restart() et shutDown().

Sans pattern command : La personne commande l'arrêt ou le démarrage de son ordinateur. Il va créer un objet Computer et apeller les méthodes restart() et shutDown().

Grâce à cet exemple, nous pouvons voir ici le rôle majeur du Command Pattern à savoir l'encapsulation. En l'appliquant, à note programme le client ne sait rien de se qui se passe. L’objet Computer, et méthodes qui lui sont appliquées pour l'éteindre ou l'allumer restent encapsulées !

# Possibilités d’application 

* *lorsque vous voulez paramétrer des objets avec des traitements.

    * Le patron de conception commande peut transformer l’appel d’une méthode en un objet autonome. Cette approche permet des utilisations très intéressantes : vous pouvez passer des commandes dans les paramètres d’une méthode, les stocker à l’intérieur d’objets, modifier les liens des commandes à l’exécution, etc.  

* lorsque vous voulez paramétrer des objets avec des traitements.

    * Le patron de conception commande peut transformer l’appel d’une méthode en un objet autonome. Cette approche permet des utilisations très intéressantes : vous pouvez passer des commandes dans les paramètres d’une méthode, les stocker à l’intérieur d’objets, modifier les liens des commandes à l’exécution, etc.  

* quand vous voulez implémenter des opérations réversibles.

    *Parmi les nombreuses techniques qui permettent d’implémenter la fonctionnalité annuler/rétablir, le patron de conception commande est probablement le plus populaire.  
    Pour pouvoir annuler des traitements, vous devez mettre en place un historique des actions effectuées. L’historique des commandes est une pile qui contient tous les objets des commandes exécutées avec l’état de l’application correspondant.  

