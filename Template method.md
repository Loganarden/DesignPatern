# Template Method  

Patron de Méthode est un patron de conception comportemental qui permet de mettre le squelette d’un algorithme dans la classe mère, mais laisse les sous-classes redéfinir certaines étapes de l’algorithme sans changer sa structure.  

Le patron de méthode vous propose de découper un algorithme en une série d’étapes, de transformer ces étapes en méthodes et de mettre l’ensemble des appels à ces méthodes dans une seule méthode socle, le patron de méthode.  
Les étapes peuvent être abstraites ou avoir une implémentation par défaut.  
Pour utiliser l’algorithme, le client doit fournir sa propre sous-classe, implémenter toutes les étapes abstraites et redéfinir certaines d’entre elles si besoin (mais pas la méthode socle elle-même).  

# Possibilités d’application  

* Utilisez le patron de méthode si vous voulez que vos clients puissent étendre des étapes spécifiques d’un algorithme, mais pas l’algorithme entier ou sa structure.

    * Le patron de méthode vous permet de transformer un algorithme monolithique en une série d’étapes individuelles qui peuvent être facilement étendues par des sous-classes, tout en gardant intacte la structure établie dans une classe mère.

* Utilisez ce patron si vous avez plusieurs classes qui contiennent des algorithmes presque identiques, avec seulement quelques différences mineures. Par conséquent, vous risqueriez de devoir retoucher toutes les classes lorsque vous modifiez l’algorithme.

    * Lorsque vous transformez un tel algorithme en un patron de méthode, vous pouvez également remonter les étapes dotées d’implémentations similaires dans la classe mère, afin d’éviter la duplication de code. Vous pouvez laisser le reste du code dans les sous-classes.  

# Mise en œuvre  

* Analysez l’algorithme ciblé pour voir si vous pouvez le décomposer en étapes. Déterminez les étapes communes à toutes les sous-classes et celles qui sont uniques.

* Créez une classe de base abstraite et déclarez le patron de méthode et un ensemble de méthodes abstraites pour représenter les opérations de l’algorithme. Faites une ébauche de la structure de l’algorithme dans ce patron de méthode en appelant les opérations correspondantes. Rendez ce patron final pour empêcher les sous-classes de la redéfinir.

* Cela ne pose aucun problème si toutes les opérations sont abstraites, mais une implémentation par défaut bénéficierait à certaines opérations. Les sous-classes n’ont pas besoin d’implémenter ces méthodes.

* Pensez à ajouter des crochets entre les étapes cruciales de votre algorithme.

* Pour chaque variante de l’algorithme, créez une nouvelle sous-classe. Elle doit implémenter toutes les opérations abstraites, mais peut également redéfinir les opérations facultatives.  

# Avantages 

* Vous permettez aux clients de redéfinir certaines parties d’un grand algorithme. Elles sont ainsi moins affectées par les modifications apportées aux autres parties de l’algorithme.

* Vous pouvez remonter le code dupliqué dans la classe mère.  

# inconvénients  

* Certains clients peuvent être limités à cause du squelette de l’algorithme.  
  
* Vous ne respectez pas le Principe de substitution de Liskov, si vous supprimez l’implémentation d’une étape par défaut dans une sous-classe.  
  
* Plus vous avez d’étapes, plus le patron de méthode devient difficile à maintenir.  

