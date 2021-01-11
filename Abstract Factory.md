# le pattern Abstract Factory  

* Le pattern Abstract Factory est classé dans la catégorie des Design Patterns de création.

Le pattern Abstract Factory va nous permettre d’instancier des familles de produits dépendant les uns des autres sans qu’il soit nécessaire de préciser leur type concret (je ne suis pas sûr qu’on soit plus avancé …)  

Factory : En développement orienté objet, une Factory (Fabrique) est un bout de code dédié qui a pour fonction de construire des objets : d’où son nom “Fabrique.  

Abstract : l’abstraction en développement objet permet de regrouper des comportements communs à une famille d’objets.  
 Par exemple, un carré, un rectangle et un triangle vont hériter d’une classe “abstraite” “Forme Géométrique” qui contient un nombre de cotés, une superficie, etc.

Le pattern abstract Factory permet de rassembler des méthodes communes à des familles d’objets différents dans une classe commune :  
la fabrique abstraite, afin d’éviter au client d’appeler des méthodes différentes (concrètes) par famille d’objets.

# Quand l’utiliser ?

Le pattern Abstract Factory peut être intéressant dans les cas suivants :

* Quand on veut faire cohabiter des familles d’objets ayant des comportements  
* communs (ce qui arrive très souvent).  
* Quand je ne veux pas rendre accessible l’implémentation concrète d’une famille   d’objets (le client aura accès qu’aux interfaces).

# Possibilités d’application 

* si votre code a besoin de manipuler des produits d’un même thème, mais que vous ne voulez pas qu’il dépende des classes concrètes de ces produits — soit vous ne les connaissez pas encore, soit vous voulez juste rendre votre code évolutif.

    * La fabrique abstraite fournit une interface qui permet de créer des objets pour chaque classe de la famille de produits. Tant que votre code utilise cette interface pour créer ses objets, il prendra systématiquement les bonnes variantes des produits disponibles dans votre application. 


# Exemple concret d’utilisation :

J’implémente une application de gestion d’assemblage de voitures destinées aux marchés européen et américain. Dans les 2 cas, j’effectue les mêmes tâches comme, par exemple, monter le moteur et les roues.  
Cependant, j’ai des spécificités pour chacun des marché : 
* par exemple pour le marché français j’utilise un moteur de 110ch 
* pour le marché américain un moteur de 200ch.  

Dans ce cas de figure, je souhaiterais simplifier l’implémentation car j’effectue des tâches communes (assembler des voitures) sur des produits de mêmes familles (des voitures) et qui présentent des caractéristiques différentes (donc des implémentations différentes).  
Ce cas de figure est un candidat idéal pour l’Abstract Factory.

# Que retenir ?

On retrouve à travers le pattern Abstract Factory des concepts fondamentaux et très utilisés en POO : l’héritage, les interfaces et les fabriques : ce qui fait de l’Abstract Factory un très bon exemple de pattern à connaitre.

