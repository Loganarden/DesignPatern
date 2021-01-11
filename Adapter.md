# LE DESIGN PATTERN ADAPTER

Le pattern “Adapter” permet de faire rentrer des ronds dans des carrés, de ranger les torchons avec les serviettes et de mélanger les choux et les carottes.  
A peu près.  
L’objectif est de faire dialoguer un élément hétérogène de notre système avec des éléments homogènes. Et ce, sans perturber le fonctionnement du reste de l’application.

Prenons un cas concret:  

Nous sommes un grossiste et vendons des articles à de grandes enseignes de la grande distribution.  
Nous avons une application mise à disposition de ces clients pour acheter nos articles.  
Tous nos clients sont homogènes, car ils implémentent l’interface IUtilisateur.  
Cette application est également ouverte à nos salariés qui souhaitent se fournir directement chez nous, sans passer par la grande distribution.

Un jour, nous avons eu à faire évoluer une fonctionnalité de notre application :  
lister l’ensemble de nos clients, mais cette fois en indiquant pour les employés leur poste actuel.

Notre problème est le suivant :  
Nous avons une gestion identique des clients et des salariés et nous ne voulons pas refaire entièrement la gestion des utilisateurs et souhaitons que cette évolution ne perturbe pas le fonctionnement actuel de l’application.

Pour y répondre, nous faisons le choix d’utiliser le pattern “Adapter”, pour que l’appel de la méthode “AfficherUtilisateur” nous affiche le nom du client, et dans le cas d’un employé son nom suivi de son poste actuel.

Nous avons créé une application console pour illustrer ce cas. Elle crée une liste de clients et, pour chacun d’eux, appelle la méthode “AfficherUtilisateur”.  
S’il s’agit d’un client, on affiche son nom, s’il s’agit d’un employé, son nom suivi de son poste.
# Possibilités d’application  

* si vous avez besoin d’une classe existante, mais que son interface est incompatible avec votre code.

    * L’adaptateur permet de créer une classe faisant office de couche intermédiaire. Cette couche sert de convertisseur entre votre code et une classe héritée ou externe, ou n’importe quelle classe avec une interface incongrue.

* si vous désirez réutiliser plusieurs sous-classes existantes à qui il manque des fonctionnalités communes qui ne peuvent pas être remontées dans la classe mère.

    * Vous pourriez étendre chaque sous-classe et mettre la fonctionnalité manquante dans les nouvelles sous-classes. En revanche, vous allez devoir dupliquer le code dans ces nouvelles classes, ce qui n’est pas terrible.  


# CONCLUSION

Dans le cadre de vos développements, vous avez probablement déjà été confronté à une de ces situations où :

* une classe implémentée et utilisée dans diverses parties de votre application doit avoir, à un endroit bien précis, un comportement différent sans pour autant en modifier son comportement initial,

* vous ne voulez pas développer toutes les méthodes d’une interface dont vos classes héritent.

L’implémentation du pattern “Adapter” est une des solutions possibles permettant de répondre à ces problématiques.