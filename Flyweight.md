# Flyweight 

Flyeight est un patron de conception structurel qui permet de stocker plus d’objets dans la RAM en partageant les états similaires entre de multiples objets, plutôt que de stocker les données dans chaque objet.  

# Problème

Pour vous détendre après de longues heures de travail, vous décidez de créer un jeu vidéo tout simple dans lequel les joueurs peuvent se déplacer sur une carte et se tirer dessus. Vous choisissez de mettre en place un système réaliste de particules et d’en faire l’une des caractéristiques les plus importantes du jeu.  

Une fois la programmation terminée, vous lancez le dernier commit, assemblez le jeu, puis l’envoyez à votre ami afin qu’il le teste.  
Le jeu fonctionnait parfaitement sur votre machine, mais votre ami n’a pas pu jouer bien longtemps : son ordinateur plante systématiquement au bout de quelques minutes.  
Après plusieurs heures à écumer les logs de debug, vous découvrez que le plantage survient à cause d’une quantité de RAM insuffisante.   

Il semblerait que le problème soit causé par votre système de particules. Chaque particule (une balle, un missile ou un morceau de shrapnel) est représentée par un objet séparé qui contient de nombreuses données.  
Lorsque l’action bat son plein sur l’écran du joueur, les nouvelles particules ne peuvent plus tenir dans la RAM et le programme plante.  

# Solution  

En inspectant la classe Particule de plus près, vous pourrez remarquer que les attributs de couleur et de sprite consomment beaucoup plus de mémoire que les autres attributs.  
Le pire est que ces deux attributs stockent des données quasi identiques dans toutes les particules. Par exemple, toutes les balles ont la même couleur et le même sprite.  

Le patron de conception flyxeught propose de ne plus stocker tous les états extrinsèques à l’intérieur de l’objet. À la place, vous devriez passer cet état à des méthodes spécialisées qui en dépendent.  
Seul l’état intrinsèque va rester à l’intérieur de l’objet, vous permettant de le réutiliser dans différents contextes.  
Vous n’aurez besoin que de quelques-uns de ces objets, car ils diffèrent uniquement dans l’état intrinsèque. Ce dernier possède bien moins de variantes que l’état extrinsèque.   

Si nous extrayons l’état extrinsèque de notre classe particule, trois objets seraient suffisants pour représenter toutes les particules du jeu : une balle, un missile et un morceau de shrapnel.  
Vous l’avez probablement déjà deviné, un objet qui ne stocke que l’état intrinsèque est appelé flyweight.  

# Possibilités d’application  

* uniquement si votre programme génère de nombreux objets et consomme trop de RAM.  
    *  Les bénéfices apportés par ce patron varient énormément en fonction de son utilisation et de son contexte. Il est surtout utile dans les cas suivants :

        * Votre application demande un grand nombre d’objets similaires.
        * La RAM de l’appareil ciblé est saturée.
        * Les objets contiennent des états identiques qui peuvent être extraits et partagés entre plusieurs objets.  

# Mise en œuvre

* Divisez les attributs d’une classe en deux parties pour les transformer en poids mouche :

      * L’état intrinsèque : les attributs qui contiennent des données invariables, dupliquées dans de nombreux objets.
      * L’état extrinsèque : les attributs qui contiennent des données contextuelles uniques à chaque objet.
* Laissez les attributs de l’état intrinsèque dans la classe, mais empêchez leur modification. Leur valeur initiale ne doit être modifiable qu’à l’intérieur de leur constructeur.

* Parcourez toutes les méthodes qui utilisent les attributs de l’état extrinsèque. Pour chacun de ces attributs, introduisez un nouveau paramètre que vous utiliserez à la place.

* Il est envisageable de créer une fabrique pour gérer une réserve de poids mouches. Elle devra vérifier l’existence du poids mouche avant d’en créer un nouveau. Une fois que la fabrique est en place, les clients doivent obligatoirement passer par elle pour récupérer des poids mouches. Ils doivent donner une description du poids mouche désiré en passant leur état intrinsèque à la fabrique.

 * Le client doit stocker ou calculer les valeurs de l’état extrinsèque (contexte) pour appeler des méthodes du poids mouche. Il est parfois plus pratique de déplacer l’état extrinsèque et l’attribut qui référence le poids mouche dans une classe contexte séparée.  

# Avantages  

* Vous économisez beaucoup de RAM si votre programme est noyé par des tonnes d’objets similaires.  

# inconvénients  

* Vous allez gagner en RAM mais perdre en cycles microprocesseur (CPU) si les données du contexte sont recalculées lors de chaque appel d’une méthode poids mouche.
* Le code devient beaucoup plus compliqué. Les développeurs qui rejoignent l’équipe vont se demander pourquoi les états d’une entité ont été séparés de cette manière.  

