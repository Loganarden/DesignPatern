# Design pattern : Builder

# Qu’est-ce que le design pattern builder ?

Le pattern Builder est utilisé pour la création d’objets complexes dont les différentes parties doivent être créées suivant un certain ordre ou algorithme spécifique.  
Une classe externe contrôle l’algorithme de construction.

On a également le rôle de ce design pattern :

Dissocier la construction d’un objet de sa représentation, afin que le même processus de construction ait la possibilité de créer des représentations différentes.

Typiquement, ce design pattern sera préconisé dans les situations où au moins :

* l’objet final est imposant, et sa création complexe.  
* beaucoup d’arguments doivent être passés à la construction de l’objet, afin d’avoir un design lisible.  
* certains de ces arguments sont optionnels (par ex. : un bateau n’a pas forcément de capitaine, mais toujours une taille), ou ont plusieurs variations (la taille peut par exemple être passée en mètres ou en pieds).  

Le modèle Builder suggère que vous extrayiez le code de construction d’objet de sa propre classe et le déplacez vers des objets distincts appelés constructeurs.  

Certaines des étapes de construction peuvent nécessiter une mise en œuvre différente lorsque vous avez besoin de construire diverses représentations du produit. Par exemple, les murs d’une cabane peuvent être construits en bois, mais les murs du château doivent être construits avec de la pierre.

Dans ce cas, vous pouvez créer plusieurs classes de constructeur différentes qui implémentent le même ensemble d’étapes de construction, mais d’une manière différente. Ensuite, vous pouvez utiliser ces constructeurs dans le processus de construction (c.-à-d., un ensemble ordonné d’appels aux étapes du bâtiment) pour produire différents types d’objets.  

Par exemple, imaginez un constructeur qui construit tout à partir de bois et de verre, un second qui construit tout avec de la pierre et du fer et un troisième qui utilise de l’or et des diamants. En appelant le même ensemble d’étapes, vous obtenez une maison régulière du premier constructeur, un petit château de la seconde et un palais de la troisième. Toutefois, cela ne fonctionnerait que si le code client qui appelle les étapes du bâtiment est capable d’interagir avec les constructeurs à l’aide d’une interface commune.
# Possibilités d’application  

* Afin de vous débarrasser d’un « constructeur télescopique ».

    * Prenons un constructeur avec dix paramètres facultatifs. Faire un appel à cette monstruosité n’est pas très pratique : vous surchargez le constructeur avec plusieurs petites versions, mais avec moins de paramètres. Ces constructeurs font toujours référence au constructeur principal en donnant des valeurs par défaut aux paramètres optionnels. 
  
 * pour rendre votre code capable de créer différentes représentations de produits (par exemple des maisons en pierre et en bois).

    *Le monteur est utile lorsque les étapes de la construction des différentes représentations du produit se ressemblent (seuls quelques détails diffèrent).L’interface de base du monteur définit toutes les étapes possibles de la construction. Les monteurs concrets implémentent les étapes pour construire les représentations particulières du produit. Le directeur quant à lui s’occupe de gérer l’ordonnancement des différentes étapes de construction.  

* *afin de construire une arborescence composite ou d’autres objets complexes.

    * Le monteur vous permet de construire des produits étape par étape. Vous pouvez déléguer l’exécution de certaines étapes sans endommager le produit final. Vous pouvez même appeler les étapes de manière récursive, ce qui est très pratique dans le cas de la construction d’un objet composite.

# Comment mettre en œuvre

* Assurez-vous que vous pouvez définir clairement les étapes de construction communes pour la construction de toutes les représentations de produits disponibles. Sinon, vous ne serez pas en mesure de procéder à la mise en œuvre du modèle.

* Déclarez ces étapes dans l’interface du constructeur de base.

* Créez une classe de constructeur de béton pour chacune des représentations de produit et mettez en œuvre leurs étapes de construction.

* N’oubliez pas de mettre en œuvre une méthode pour obtenir le résultat de la construction. La raison pour laquelle cette méthode ne peut pas être déclarée à l’intérieur de l’interface du constructeur est que divers constructeurs peuvent construire des produits qui n’ont pas d’interface commune.  
Par conséquent, vous ne savez pas quel serait le type de retour pour une telle méthode. Toutefois, si vous traitez avec des produits d’une hiérarchie unique, la méthode d’extraction peut être ajoutée en toute sécurité à l’interface de base.

* Pensez à créer une classe de réalisateurs. Il peut encapsuler différentes façons de construire un produit en utilisant le même objet constructeur.

* Le code client crée à la fois les objets du constructeur et du directeur. Avant le début de la construction, le client doit transmettre un objet constructeur au directeur.  
Habituellement, le client ne le fait qu’une seule fois, via les paramètres du constructeur du directeur.  
Le directeur utilise l’objet constructeur dans toute autre construction. Il ya une approche alternative, où le constructeur est passé directement à la méthode de construction du directeur.

* Le résultat de construction ne peut être obtenu directement auprès du directeur que si tous les produits suivent la même interface. Dans le cas contraire, le client doit aller chercher le résultat du constructeur.

# Avantages

Vous pouvez construire des objets étape par étape, reporter les étapes de construction ou exécuter des étapes de manière récursive.  

Vous pouvez réutiliser le même code de construction lors de la construction de diverses représentations de produits.  

Principe de responsabilité unique. Vous pouvez isoler le code de construction complexe de la logique commerciale du produit.

# inconvénients

La complexité globale du code augmente puisque le modèle nécessite la création de plusieurs nouvelles classes.