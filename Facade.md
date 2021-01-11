# Design Patterns - Facade  

Façade est un patron de conception structurel qui procure une interface offrant un accès simplifié à une librairie, un framework ou à n’importe quel ensemble complexe de classes.  

# Problème  

Imaginez que vous devez adapter votre code pour manipuler un ensemble d’objets qui appartiennent à une librairie ou à un framework assez sophistiqué.  
D’ordinaire, vous initialisez tous ces objets en premier, gardez la trace des dépendances et appelez les méthodes dans le bon ordre, etc.

Par conséquent, la logique métier de vos classes devient fortement couplée avec les détails de l’implémentation des classes externes, rendant cette logique difficile à comprendre et à maintenir.  

# Solution

Une façade est une classe qui procure une interface simple vers un sous-système complexe de parties mobiles.   
Les fonctionnalités proposées par la façade seront plus limitées que si vous interagissiez directement avec le sous-système, mais vous pouvez vous contenter de n’inclure que les fonctionnalités qui intéressent votre client.

Une façade se révèle très pratique si votre application n’a besoin que d’une partie des fonctionnalités d’une librairie sophistiquée parmi les nombreuses qu’elle propose.

Par exemple, une application qui envoie des petites vidéos de chats comiques sur des réseaux sociaux peut potentiellement utiliser une librairie de conversion vidéo professionnelle.  
Mais la seule chose dont vous ayez réellement besoin, c’est d’une classe dotée d’une méthode encoder(fichier, format).  
Après avoir créé cette classe et intégré la librairie de conversion vidéo, votre façade est opérationnelle.  
# Possibilités d’application 

* Si vous avez besoin d’une interface limitée mais directe à un sous-système complexe.

    * Souvent, les sous-systèmes gagnent en complexité avec le temps et mettre en place un patron de conception implique de créer de nouvelles classes. Dans de nombreux contextes, un sous-système peut se révéler plus souple et facile à réutiliser, mais la quantité de travail pour configurer et écrire le code de base ne fait que croitre. La façade tente de remédier à ce problème en fournissant un raccourci aux fonctionnalités du sous-système qui sont adaptées au besoin du client.

* Si vous voulez structurer un sous-système en plusieurs couches.

    * Créez des façades pour définir des points d’entrée à chaque niveau d’un sous-système. Vous pouvez réduire le couplage entre plusieurs sous-systèmes en les obligeant à communiquer au travers de façades.  


#  Mise en œuvre  

* Vérifiez s’il est possible de fournir une interface plus simple que ce qu’un sous-système vous propose. Si cette interface peut découpler le code client des nombreuses classes du sous-système, vous êtes sur la bonne voie !

* Déclarez et implémentez cette interface en tant que nouvelle façade. Elle doit rediriger les appels du code client aux objets appropriés du sous-système. Elle doit également être responsable de l’initialisation du sous-système et gérer son cycle de vie, sauf si le code client s’en occupe déjà.

* Pour exploiter au maximum les avantages de la façade, toute communication du code client avec le sous-système doit passer par elle. Cette manipulation protège le code client de tout effet de bord que des modifications apportées au sous-système pourraient provoquer. Si un sous-système est mis à jour, vous n’aurez besoin que de modifier le code de la façade.

* Si la façade devient trop grande, vous devriez envisager de transférer une partie de ses comportements vers une nouvelle façade plus spécialisée.  
  
# Avantages  

* Vous pouvez isoler votre code de la complexité d’un sous-système.  

# inconvénients  

* Une façade peut devenir un objet omniscient couplé à toutes les classes d’une application.

