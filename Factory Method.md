# Factory Method  

Factory est un patron de conception de création qui définit une interface pour créer des objets dans une classe mère, mais délègue le choix des types d’objets à créer aux sous-classes.  

# Problème

Imaginez que vous êtes en train de créer une application de gestion logistique. La première version de votre application ne propose que le transport par camion, la majeure partie de votre code est donc située dans la classe Camion.

Au bout d’un certain temps, votre application devient populaire et de nombreuses entreprises de transport maritime vous demandent tous les jours d’ajouter la gestion de la logistique maritime dans l’application.

C’est super, n’est-ce pas ? Mais qu’en est-il du code ? La majeure partie est actuellement couplée à la classe Camion.  
Pour pouvoir ajouter des Bateaux dans l’application, il faudrait revoir la base du code. De plus, si vous décidez plus tard d’ajouter un autre type de transport dans l’application, il faudra effectuer à nouveau ces changements.

Par conséquent, vous allez vous retrouver avec du code pas très propre, rempli de conditions qui modifient le comportement du programme en fonction de la classe des objets de transport.  

# Solution  

Le patron de conception factory vous propose de remplacer les appels directs au constructeur de l’objet (à l’aide de l’opérateur new) en appelant une méthode fabrique spéciale.  
Pas d’inquiétude, les objets sont toujours créés avec l’opérateur new, mais l’appel se fait à l’intérieur de la méthode fabrique. Les objets qu’elle retourne sont souvent appelés produits.  

Il y a tout de même une petite limitation : les sous-classes peuvent retourner des produits différents seulement si les produits ont une classe de base ou une interface commune. De plus, cette interface doit être le type retourné par la méthode fabrique de la classe de base.  

Par exemple, les classes Camion et Bateau doivent toutes les deux implémenter l’interface Transport, qui déclare une méthode livrer. Chaque classe implémente cette méthode à sa façon : les camions livrent par la route et les bateaux livrent par la mer. La méthode fabrique de la classe LogistiqueRoute retourne des camions, alors que celle de la classe LogistiqueMer retourne des bateaux.  

# Possibilités d’application

* si vous ne connaissez pas les types et dépendances précis des objets que vous allez utiliser dans votre code.   
    * La fabrique effectue une séparation entre le code du constructeur et le code qui utilise réellement le produit. Le code du constructeur devient ainsi plus évolutif et indépendant du reste du code.  

* si vous voulez mettre à disposition une librairie ou un framework pour vos utilisateurs avec un moyen d’étendre ses composants internes.  
    * L’héritage est probablement le moyen le plus simple pour étendre le comportement par défaut d’une librairie ou d’un framework. Mais comment le framework peut-il savoir qu’il doit utiliser votre sous-classe plutôt qu’un composant standard?  
    La solution est de réunir dans une seule méthode fabrique le code qui construit les composants dans le framework, et non seulement d’étendre ceux-ci, mais de laisser la possibilité de redéfinir la méthode fabrique.  
    
* lorsque vous voulez économiser des ressources système en réutilisant des objets au lieu d’en construire de nouveaux.  


# Mise en œuvre  

* Implémentez la même interface pour tous les produits. Cette interface doit déclarer des méthodes que tous les produits peuvent avoir en commun.

* Ajoutez une méthode fabrique vide à l’intérieur de la classe créateur. Le type de retour de la méthode doit correspondre à l’interface commune des produits.

* Localisez toutes les références aux constructeurs des produits dans le code du créateur. Remplacez-les une par une par des appels à la méthode fabrique et déplacez le code de la création de produits dans la méthode fabrique.

* Vous allez peut-être devoir ajouter un paramètre temporaire à la méthode fabrique pour vérifier le type du produit retourné.

* À ce stade, le code de la méthode fabrique peut paraître désordonné. Il pourrait même contenir un gros switch qui choisit la classe à instancier. Ne vous inquiétez pas, tout va bientôt rentrer dans l’ordre.

* Pour chaque type de produit listé dans la méthode fabrique, créez une sous-classe de Créateur. Redéfinissez la méthode fabrique dans les sous-classes et récupérez les morceaux de code appropriés de la méthode de base.

* S’il y a trop de types de produits et peu d’intérêt de créer des sous-classes pour tous, vous pouvez réutiliser le paramètre de contrôle de la classe de base dans les sous-classes.

* Si après tous ces changements la méthode fabrique de base est devenue complètement vide, vous pouvez la rendre abstraite. S’il reste encore quelques lignes, vous pouvez y laisser un comportement par défaut.  

# Avantages  

* Vous désolidarisez le Créateur des produits concrets.
* Principe de responsabilité unique. Vous pouvez déplacer tout le code de création des produits au même endroit, permettant ainsi une meilleure maintenabilité.
* Principe ouvert/fermé. Vous pouvez ajouter de nouveaux types de produits dans le programme sans endommager l’existant.

# inconvénients  

* Le code peut devenir plus complexe puisque vous devez introduire de nombreuses sous-classes pour la mise en place du patron. La condition optimale d’intégration du patron dans du code existant se présente lorsque vous avez déjà une hiérarchie existante de classes de création.