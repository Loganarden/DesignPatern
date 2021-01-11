# Composite

Composite est un patron de conception structurel qui permet d’agencer les objets dans des arborescences afin de pouvoir traiter celles-ci comme des objets individuels.  

# Problème

L’utilisation de ce patron doit être réservée aux applications dont la structure principale peut être représentée sous la forme d’une arborescence.  

# Solution  

Le patron de conception composite vous propose de manipuler les Produits et les Boîtes à l’aide d’une interface qui déclare une méthode de calcul du prix total.

Comment cette méthode peut-elle fonctionner ? Pour un produit, on retourne simplement son prix.  
Pour une boîte, on parcourt chacun de ses objets, on leur demande leur prix, puis on retourne un total pour la boîte.  
Si l’un de ces objets est une boîte plus petite, cette dernière va aussi parcourir son propre contenu et ainsi de suite, jusqu’à ce que tous les prix aient été calculés. Une boîte peut même ajouter des frais supplémentaires, comme le prix de l‘emballage.

La cerise sur le gâteau est que vous n’avez même pas besoin de connaître la classe concrète des objets de l’arborescence.  
Vous n’avez pas besoin de savoir si un objet est un produit tout simple ou une boîte sophistiquée, vous les manipulez de la même manière grâce à une interface commune.  
Lorsque vous faites appel à une méthode, les objets s’occupent de faire transiter la requête en descendant vers les feuilles de l’arbre.
# Possibilités d’application  

* Si vous devez gérer une structure d’objets qui ressemble à une arborescence.

    * Le patron de conception composite vous propose deux éléments de base qui partagent la même interface : des feuilles simples et des conteneurs complexes. Un conteneur peut être composé de feuilles et d’autres conteneurs. Grâce à cela, vous pouvez construire une structure récursive composée d’objets imbriqués qui ressemble à un arbre.

* Si vous voulez que le client interagisse avec les éléments simples aussi bien que complexes de façon uniforme.

    * Tous les éléments définis dans le patron composite partagent une interface commune. En utilisant cette interface, le client n’a pas besoin de connaître la classe concrète des objets qu’il manipule.  


# Mise en œuvre

* Assurez-vous que votre application possède bien la forme d’une arborescence. Décomposez-la en conteneurs et en éléments simples. Rappelez-vous que les conteneurs doivent pouvoir accueillir des éléments simples et d’autres conteneurs.

* Déclarez l’interface composant avec une liste de méthodes qui fonctionnent à la fois avec les composants simples et complexes.

* Créez une classe feuille pour représenter les éléments simples. Un même programme peut avoir plusieurs classes feuille différentes.

* Créez une classe conteneur pour représenter les éléments complexes. Fournissez un attribut de type tableau à cette classe, afin de stocker les références aux sous-éléments. Ce tableau doit pouvoir stocker les feuilles et les conteneurs, assurez-vous donc qu’il est bien déclaré avec le type d’interface du composant.

* Tout en implémentant les méthodes de l’interface composant, gardez en tête que les conteneurs sont censés déléguer la majeure partie du travail à leurs sous-éléments.

* Enfin, définissez des méthodes pour ajouter ou retirer des éléments enfants du conteneur.

* Elles peuvent être placées à l’intérieur de l’interface composant, mais ceci ne respecte pas le principe de ségrégation des interfaces, car la classe feuille contiendra des méthodes vides. L’avantage est que le client pourra traiter ces éléments uniformément, même lorsqu’il construit l’arborescence.

# Avantages

Vous pouvez travailler dans des structures arborescentes complexes plus facilement en utilisant les avantages du polymorphisme et de la récursivité.  

Principe ouvert/fermé. Vous pouvez introduire de nouveaux types d’éléments dans l’application qui pourront directement être intégrés dans l’arborescence, sans avoir à réécrire l’existant.

# Inconvénients

Vous rencontrerez parfois des difficultés pour définir une interface commune à certaines classes dont les fonctionnalités sont trop différentes. Dans certains scénarios, vous devez créer une interface composant bien trop générique, rendant le fonctionnement difficile à comprendre.