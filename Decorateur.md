# LE DESIGN PATTERN DECORATOR

Décorateur est un patron de conception structurel qui permet d’affecter dynamiquement de nouveaux comportements à des objets en les plaçant dans des emballeurs qui implémentent ces comportements.

# Problème

Imaginez que vous travaillez sur une librairie qui permet aux programmes d’envoyer des notifications à leurs utilisateurs lorsque des événements importants se produisent.  
Au bout d’un certain temps, vous vous rendez compte que les utilisateurs de la librairie veulent plus que les notifications qu’ils reçoivent sur leur boîte mail.  
Ils sont nombreux à vouloir recevoir des SMS lorsque leurs applications rencontrent des problèmes critiques. Certains voudraient être prévenus sur Facebook et les employés de certaines entreprises adoreraient recevoir des notifications Slack.  
Vous devez structurer vos classes de notification différemment pour ne pas trop les multiplier, sinon vous allez vous retrouver dans le livre Guinness des records.

# Solution

La première chose qui nous vient à l’esprit lorsque l’on veut modifier le comportement d’un objet, c’est d’étendre sa classe.  
Cependant, voici quelques mises en garde concernant l’héritage :

* L’héritage est statique. Vous ne pouvez pas modifier le comportement d’un objet au moment de l’exécution. Vous ne pouvez que remplacer la totalité de l’objet par un autre, généré grâce à une sous-classe différente.  
* Les sous-classes ne peuvent avoir qu’un seul parent. Dans la majorité des langages de programmation, vous ne pouvez hériter que d’une seule classe à la fois.  

Une des solutions pour contourner ce problème consiste à utiliser l’aggrégation ou la composition  à la place de l’héritage.  
Ces alternatives fonctionnent à peu près de la même façon :   
* un objet possède une référence à un autre objet et lui délègue une partie de son travail.   
Avec l’héritage, l’objet est capable de faire le travail tout seul en héritant du comportement de sa classe mère.

Grâce à cette nouvelle approche, il est facile de remplacer l’objet référencé par un autre, ce qui modifie le comportement du conteneur au moment de l’exécution.    
Un objet peut utiliser le comportement de diverses classes, posséder des références à de nombreux objets et leur déléguer toutes sortes de tâches.  
L’agrégation et la composition sont des principes clés dans le décorateur, tout comme dans de nombreux autres patrons. Sur ces belles paroles, revenons à nos moutons.  

Le décorateur est également appelé « emballeur » ou « empaqueteur ». Ces surnoms révèlent l’idée générale derrière le concept.  
Un emballeur est un objet qui peut être lié par un objet cible. L’emballeur possède le même ensemble de méthodes que la cible et lui délègue toutes les demandes qu’il reçoit. Il peut exécuter un traitement et modifier le résultat avant ou après avoir envoyé sa demande à la cible.
# Possibilités d’application 

* Si vous avez besoin d’ajouter des comportements supplémentaires au moment de l’exécution sans avoir à altérer le code source de ces objets.

    * Le décorateur vous permet de structurer votre logique métier en couches, de créer un décorateur pour chacune de ces couches et de décorer les objets avec différentes combinaisons au moment de l’exécution. Le code client peut traiter les objets uniformément puisqu’ils implémentent la même interface.

* Si l’héritage est impossible ou peu logique pour étendre le comportement d’un objet.

    * De nombreux langages de programmation permettent l’utilisation du mot clé final pour interdire l’héritage une classe. Le seul moyen d’étendre le comportement d’une telle classe est de l’emballer en utilisant un décorateur.  


# Mise en œuvre

* Assurez-vous que votre domaine peut être représenté sous la forme d’un composant principal recouvert par plusieurs couches facultatives.

* Déterminez les méthodes communes entre le composant principal et les couches facultatives. Créez l’interface du composant et déclarez-y ces méthodes.

* Créez une classe concrète pour le composant et définissez son comportement de base.

* Créez une classe de base décorateur. Elle doit inclure un attribut qui va permettre de stocker la référence à un objet emballé. Cet attribut doit être déclaré avec le type de l’interface du composant, afin de le relier aux composants concrets et aux décorateurs. Le décorateur de base doit déléguer tout le travail à l’objet emballé.

* Assurez-vous que les classes implémentent l’interface du composant.

* Créez des décorateurs concrets en les implémentant à partir du décorateur de base. Un décorateur concret doit exécuter son comportement avant ou après l’appel à la méthode de son parent (qui délègue toujours la tâche à l’objet emballé).

* Le code client doit être responsable de la création des décorateurs et de leur agencement en fonction des besoins du client.  
  
# Avantages 

Vous pouvez étendre le comportement d’un objet sans avoir recours à la création d’une nouvelle sous-classe.  

Vous pouvez ajouter ou retirer dynamiquement des responsabilités à un objet au moment de l’exécution.  

Vous pouvez combiner plusieurs comportements en emballant un objet dans plusieurs décorateurs.  

Principe de responsabilité unique. Vous pouvez découper une classe monolithique qui implémente plusieurs comportements différents en plusieurs petits morceaux.  

# inconvénients

* Retirer un emballeur spécifique de la pile n’est pas chose aisée.
* Il n’est pas non plus aisé de mettre en place un décorateur dont le comportement ne varie pas en fonction de sa position dans la pile.
* Le code de configuration initial des couches peut avoir l’air assez moche.  

