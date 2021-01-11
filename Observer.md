# Observer 

L’Observateur est un patron de conception comportemental qui permet de mettre en place un mécanisme de souscription pour envoyer des notifications à plusieurs objets, au sujet d’événements concernant les objets qu’ils observent.  

# Possibilités d’application  

* Quand des modifications de l’état d’un objet peuvent en impacter d’autres, et que l’ensemble des objets n’est pas connu à l’avance ou qu’il change dynamiquement.

    * Ce problème est souvent rencontré lorsque l’on travaille sur des classes d’une interface utilisateur graphique. Par exemple, si vous créez des classes bouton personnalisées et que vous voulez que les clients puissent y ajouter du code déclenché par le clic d’un utilisateur.  
    L’observateur permet à tous les objets qui suivent l’interface souscripteur de s’inscrire aux notifications des événements des objets diffuseur. Vous pouvez ajouter le mécanisme de souscription à tous vos boutons et laisser les clients mettre leur code personnalisé dans des classes souscripteur personnalisées.  

* Quand certains objets de votre application doivent en suivre d’autres, mais seulement pendant un certain temps ou dans des cas spécifiques.

    * La liste d’inscription est dynamique, les souscripteurs peuvent donc rejoindre ou quitter la liste quand ils le désirent.  

# Mise en œuvre  

* Passez en revue votre logique métier et découpez-la en deux parties : la fonctionnalité principale (indépendante du reste du code) prendra le rôle du diffuseur ; le reste va être transformé en classes souscripteur.

* Déclarez l’interface souscripteur. Elle doit au moins contenir une méthode update.

* Déclarez l’interface diffuseur et écrivez des méthodes qui permettent d’ajouter et de retirer des objets souscripteur de la liste. Rappelez-vous que les diffuseurs doivent manipuler les souscripteurs uniquement en passant par l’interface des souscripteurs.

* Décidez où vous allez mettre la liste de souscription ainsi que l’implémentation des méthodes de souscription. En général, ce code est presque identique pour tous les types de diffuseurs. Le mieux est donc de le mettre dans une classe abstraite directement dérivée de l’interface diffuseur. Les diffuseurs concrets étendent cette classe et héritent du comportement de la souscription.

* Si vous implémentez ce patron dans une hiérarchie de classes existante, pensez à la composition : mettez la logique de souscription dans un objet séparé et faites en sorte que les diffuseurs l’utilisent.

* Créez les classes concrètes Diffuseur. Chaque fois que quelque chose d’important se produit chez un diffuseur, il doit prévenir ses souscripteurs.

* Implémentez les méthodes de notifications (update) dans les classes concrètes Souscripteur. La majorité des souscripteurs va vouloir des données du contexte qui concernent l’événement en question. Vous pouvez les envoyer en paramètre de la méthode de notification.

* Mais il y a une autre possibilité. Lors de la réception d’une notification, le souscripteur peut aller chercher les données directement dans la notification. Dans ce cas, le diffuseur doit s’envoyer lui-même en paramètre de la méthode update. On peut également lier un diffuseur à un souscripteur de manière permanente dans le constructeur, mais cette possibilité est moins flexible.

* Le client doit créer tous les souscripteurs nécessaires et les enregistrer auprès des diffuseurs.  

# Avantages 

* Principe ouvert/fermé. Vous pouvez ajouter de nouvelles classes souscripteur sans avoir à modifier le code du diffuseur (et inversement si vous avez une interface diffuseur).
* Vous pouvez établir des relations entre les objets lors du lancement de l’application.  

# inconvénients  

* Les souscripteurs sont avertis dans un ordre aléatoire.  

