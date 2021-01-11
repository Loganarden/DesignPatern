# Strategy 

Stratégie est un patron de conception comportemental qui permet de définir une famille d’algorithmes, de les mettre dans des classes séparées et de rendre leurs objets interchangeables.  

Le patron de conception stratégie vous propose de prendre une classe dotée d’un comportement spécifique mais qui l’exécute de différentes façons, et de décomposer ses algorithmes en classes séparées appelées stratégies.  

# Possibilités d’application  

* Si vous voulez avoir différentes variantes d’un algorithme à l’intérieur d’un objet à disposition, et pouvoir passer d’un algorithme à l’autre lors de l’exécution.

    * Ce patron vous permet de modifier indirectement le comportement de l’objet lors de l’exécution, en l’associant avec différents sous-objets qui peuvent accomplir des sous-tâches spécifiques de différentes manières.

* Si vous avez beaucoup de classes dont la seule différence est leur façon d’exécuter un comportement.

    * Ce patron vous permet d’extraire des variantes d’un comportement dans une hiérarchie de classes séparées et de combiner les classes originales dans une seule, évitant de dupliquer du code.

* isoler la logique métier d’une classe, de l’implémentation des algorithmes dont les détails ne sont pas forcément importants pour le contexte.

    * Ce patron vous permet de séparer le code, les données internes et les dépendances des divers algorithmes du reste du code. Une interface toute simple permet aux clients d’exécuter les algorithmes et d’en changer lors de l’exécution.

 * Si votre classe possède un gros bloc conditionnel qui choisit entre différentes variantes du même algorithme.

    * La stratégie vous débarrasse de toutes ces conditions en extrayant tous les algorithmes dans des classes séparées, et ces dernières implémentent toutes la même interface. L’objet original délègue l’exécution à l’un de ces objets, au lieu d’implémenter toutes les variantes de l’algorithme.  

# Mise en œuvre 

* Dans la classe contexte, identifiez un algorithme qui varie souvent. Il peut s’agir d’un gros bloc conditionnel qui sélectionne une variante du même algorithme lors de l’exécution.

* Déclarez l’interface stratégie commune à toutes les variantes de l’algorithme.

* Extrayez tous les algorithmes un par un et mettez-les dans leurs propres classes. Elles doivent toutes implémenter l’interface stratégie.

* Ajoutez un attribut pour garder une référence vers un objet stratégie dans la classe contexte. Créez un setter pour modifier le contenu de cet attribut. Le contexte ne doit manipuler l’objet stratégie qu’au travers de l’interface stratégie. Le contexte peut définir une interface qui laisse la stratégie accéder à ses données.

* Les clients d’un contexte doivent l’associer avec une stratégie adaptée au comportement attendu.  

# Avantages  
* Vous pouvez permuter l’algorithme utilisé à l’intérieur d’un objet à l’exécution.  
  
* Vous pouvez séparer les détails de l’implémentation d’un algorithme et le code qui l’utilise.  
  
* Vous pouvez remplacer l’héritage par la composition.  
  
* Principe ouvert/fermé. Vous pouvez ajouter de nouvelles stratégies sans avoir à modifier le contexte.  

# inconvénients  

* Si vous n’avez que quelques algorithmes qui ne varient pas beaucoup, nul besoin de rendre votre programme plus compliqué avec les nouvelles classes et interfaces qui accompagnent la mise en place du patron.  
  
* Les clients doivent pouvoir comparer les différentes stratégies et choisir la bonne.
  
* De nombreux langages de programmation modernes gèrent les types fonctionnels et vous permettent d’implémenter différentes versions d’un algorithme à l’intérieur d’un ensemble de fonctions anonymes. Vous pouvez ensuite utiliser ces fonctions exactement comme vous le feriez pour des objets stratégie, sans encombrer votre code avec des classes et interfaces supplémentaires.  

