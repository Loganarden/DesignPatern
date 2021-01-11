# Singleton  

Singleton est un patron de conception de création qui garantit que l’instance d’une classe n’existe qu’en un seul exemplaire, tout en fournissant un point d’accès global à cette instance.  

Mettre en place une méthode de création statique qui se comporte comme un constructeur. En sous-main, cette méthode appelle le constructeur privé pour créer un objet et le sauvegarde dans un attribut statique. Tous les appels ultérieurs à cette méthode retournent l’objet en cache.  

Si votre code a accès à la classe du singleton, alors il peut appeler sa méthode statique. À chaque appel de cette méthode, c’est toujours le même objet qui est retourné.  

# Possibilités d’application  

* Utilisez le singleton lorsque l’une de vos classes ne doit fournir qu’une seule instance à tous ses clients. Par exemple, une base de données partagée entre toutes les parties d’un programme.

    * La méthode spéciale de création devient le seul moyen de fabriquer des objets pour la classe, car le singleton désactive les autres. Cette méthode crée un objet ou retourne l’objet existant s’il a déjà été créé.

* Utilisez le singleton lorsque vous voulez un contrôle absolu sur vos variables globales.

    * Contrairement aux variables globales, le singleton garantit l’unicité de l’instance de la classe. Seule la classe singleton peut remplacer l’instance mise en cache.  
    Vous pouvez moduler le nombre d’instances du singleton comme vous le voulez. Vous devez juste apporter une modification dans le corps de la méthode getInstance.  

# Mise en œuvre  

* Ajoutez un attribut statique à la classe pour stocker l’instance du singleton.

* Déclarez une méthode de création publique et statique pour récupérer l’instance du singleton.

* Implémentez une « instanciation paresseuse » (lazy initialization) à l’intérieur de la méthode statique. Elle devrait créer un nouvel objet lors du premier appel et le stocker dans l’attribut statique. La méthode doit retourner cette instance lors de tous les appels suivants.

* Rendez privé le constructeur de la classe. La méthode statique de la classe doit être la seule à pouvoir appeler le constructeur.

* Parcourez le code client et remplacez les appels directs au constructeur du singleton par des appels à la méthode statique.  

# Avantages  

* Vous garantissez l’unicité de l’instance de la classe.  
* Vous obtenez un point d’accès global à cette instance.  
* l’objet du singleton est uniquement initialisé la première fois qu’il est appelé.  

# inconvénients  

* Ne respecte pas le principe de responsabilité unique. Ce patron résout deux problèmes à la fois.    
  
* Le singleton peut masquer une mauvaise conception ; il se peut, par exemple, que les composants aient trop de visibilité les uns envers les autres.  
  
* Il doit bénéficier d’un traitement spécial pour fonctionner dans un environnement multithread afin que le singleton ne se retrouve pas en plusieurs exemplaires.  
  
* Les tests unitaires du code client peuvent se révéler difficiles, car de nombreux frameworks reposent sur l’héritage lorsqu’ils créent des objets fictifs.  
Étant donné que le constructeur de la classe du singleton est privé et que redéfinir la méthode statique est impossible dans la majorité des langages, vous allez devoir être créatif pour reproduire un singleton fictif.  
Ou ne pas faire de tests. Ou ne pas utiliser de singleton.