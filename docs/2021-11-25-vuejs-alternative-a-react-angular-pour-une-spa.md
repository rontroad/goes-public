---
title: "VUeJS alternative crédible pour un développement d'une SPA industrielle"
---
# Introduction
Dans les architectures logicielles modernes, hormis contraintes spécifiques du client, il y a quelque chose qui ne fait pas débat, en tout cas vue du point de vue du chef de projet, c'est la mise en place de solution « Single Page Application » (SPA) et de Micro-Services (MS). Cette association gagnante permet à l’ère du cloud et du DevOps d’apporter l’atomicité et la souplesse pour délivrer de manière continue nos projets, petits ou gros.

Une fois ceci dit, se posent de vastes questions sur le choix des composants logiciels, de la cible cloud, de son api management, de son service mesh, du meilleur pattern de micro-service pour notre besoin, de la meilleure solution de persistance, distribué ou non, managé ou non, etc... Tous ces sujets sont importants et nous pouvons compter sur nos architectes pour y apporter les meilleures réponses.

Parmi ces choix à faire, il y a celui du framework sur lequel bâtir notre SPA. Les réponses traditionnelles sont Angular et React. Ces deux solutions sont en soi de bons choix, chacune d’entre-elles soutenues par son GAFA et largement adoptées dans les communautés. Je voudrais m’attarder ici sur une troisième solution [VueJS](https://vuejs.org) sur laquelle je souhaite faire un retour d’expérience.

Alors, c’est le moment de prendre connaissance de cette importante note de la rédaction :
> L’auteur est un chef de projet informatique, certes avec un historique de développement logiciel solide, auquel les hasards de la vie professionnelle l’ont amené à avoir une (1) expérience SPA réalisée en VueJS et n’a aucune connaissance d’autres framework SPA (ni Angular, ni React).

Ca peut faire peur sur la profondeur de la suite de l’article, mais pourtant, c’est justement le point principal qui m’a poussé à le faire : la simplicité avec laquelle un développeur, sans expérience du développement « front », peut rentrer sur la technologie et réaliser une application relativement complexe de manière industrielle.

Un collègue chargé de réaliser une comparaison des framework SPA a identifié cette analyse de marché : https://blog.dyma.fr/quel-framework-choisir-en-2020-angular-vue-js-ou-react/. Il y a deux points principaux qui militent pour l’utilisation de VueJS :
* La **courbe d’apprentissage** : VueJS est significativement plus simple à prendre en main, pour toutes les activités, de la découverte de la technologie jusqu’à la mise en production d’une application « pour de vrai »
* La **productivité** : si pour les utilisateurs avancés dans chaque technologie la productivité est équivalente, celle de vue est significativement supérieure pour les utilisateurs débutants ou intermédiaires.

Je peux personnellement témoigner de ces 2 premiers points et en tant que chef de projet, j’y vois un intérêt pour la réalisation de nos projets. Le marché du développement informatique étant sous tension, nous sommes amenés à embarquer dans nos équipes des ressources pas forcément expérimentées ou avec le background technique permettant d’être rapidement à l’aise avec des technologies complexes. Il faut également faire avec le turn-over et les contingences économiques : une ressource experte coutera surement plus cher qu’un débutant. 

**Le positionnement de VueJS sur la courbe d’apprentissage et la productivité est selon moi démarquant dans la réalité du métier du développement informatique du moment**. Je trouve aussi que le positionnement du framework exclusivement côté front (pas côté serveur) est un avantage dans le découplage et au final l’évolutivité de nos solutions. A noter que la solution NuxtJS apporte justement ces capacités de rendu côté serveur, ce qui ont le SEO en contrainte forte devront probablement passer par là.

Alors, bien sûr, tous ces avantages sont à mitiger. Certains évoqueront le risque de pérennité, mais VueJS n’est pas sans soutiens dans les communautés ou les entreprises (Google, BMW, Louis Vuitton, GitLab, …). Un argument fort remonté par l’étude de marché, c’est une « employabilité » plus forte avec Angular ou React, beaucoup plus d’offre d’emploi donc un intérêt surement supérieur pour nos ressources dans la perspective de leur développement professionnel.

En conclusion, un argument béton, c’est avant tout hyper fun et gratifiant en tant que développeur de voir qu’on peut proprement, de manière industrielle, créer des composants et des sites très rapidement et bien sûr cloud ready !

Pour ceux que ça intéresse, je vais compléter cette introduction par 3 articles un peu plus concrets :
* La mise en place d’un projet VueJS, compter 30 minutes si vous voulez faire les manips de votre côté
* Une illustration de l’approche par composant, de la réactivité et du store VueX, compter 2 heures
* Une projection sur un Système d’Information Géographique (SIG), compter surement plutôt 1 jour
