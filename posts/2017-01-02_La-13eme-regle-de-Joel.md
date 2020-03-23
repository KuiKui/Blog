###### 02/01/2017

# La 13ème règle de Joel

Lorsque certains de mes mentors m’ont fait prendre conscience il y a quelques années de l’importance de la [qualité](https://github.com/KuiKui/Blog/blob/master/posts/2012-02-08_La-qualite.md#la-qualit%C3%A9) au sens large, un [article de Joel Spolsky](https://www.joelonsoftware.com/2000/08/09/the-joel-test-12-steps-to-better-code/) cristalisait tout ce que nous pensions alors de la valeur d’une équipe de développement.


Avec son évaluation en 12 étapes, Joel nous propose de chiffrer la qualité de notre environnement de travail : en partant de l’infrastructure jusqu’au recrutement en passant par les processus de travail.


Le temps ayant passé depuis l’écriture de cet article fondateur qui devrait toujours faire foi dans chaque entrerprise créant des programmes, il me semble cependant manquer un aspect qui a pris de plus en plus d’ampleur ces dernières années : la disparité croissante et l’évolution rapide des outils de développement.


Voilà pourquoi j’ajouterais bien une nouvelle question au test de Joel :


>  13. Can you setup a dev env in one step?


Le nombre de distributions viables et répandues d’OS est maintenant bien plus grand qu’à l’époque où Joel écrivait ses 12 règles : entre Windows, MacOSX, Debian, RedHat ou encore ArchLinux, il y a largement de quoi perdre la tête en essayant d’installer et de configurer exactement de la même manière un serveur web, un serveur de base de données, un gestionnaire de cache, un système de queuing ou tout simplement les bonnes versions des languages utilisés dans la _stack_ technique, sur plusieurs machines différentes.


De la même manière, du fait du nombre croissant d’outils de développement, la configuration de l’application pour fonctionner dans un environnement de dev peut être sujette à perte de temps : qui n’a jamais cherché quel nom devait porter la base de données ? Puis apprendre quelques jours plus tard, qu’il en fallait en réalité une seconde pour que des logs spécifiques fonctionnent ? Ou qu’il était nécessaire d’ajouter une règle spécifique dans un fichier de configuration caché ?


## Rapidité

Avec la mise en place d’un environnement de dev fonctionnel en une commande, les developpeurs ne perdent plus de temps à installer les composants systèmes nécessaires ni à paramétrer l’application : ils peuvent commencer à travailler rapidement et à produire du code pour corriger un bug mineur par exemple, afin de le déployer dans la foulée pour réaliser un [premier déploiement lors de sa première journée de travail](http://blog.crowdcast.io/engineers-ship-code-on-day-1/) sur le projet.


## Simplicité

Lorsque le projet est accessible en développement de la même manière chez tout les développeurs, les échanges s’en trouvent simplifiés : les url permettant d’accéder aux pages de démonstration ou contenant des erreurs à corriger peuvent être échangées facilement sur la messagerie instantanée et on s’y retrouve plus rapidement lorsque l’on [travaille sur le poste d’un collègue](https://developer.atlassian.com/blog/2015/05/try-pair-programming/).


## Documentation

Il est aussi facile à un nouvel arrivant de découvrir l’infrastructure utilisée en parcourant simplement les scripts d’installation de l’environnement de développement. Comme ces scripts sont certainement contenus dans la base de code versionnée de l’application, il est aussi possible de découvrir les évolutions de la _stack_ technique utilisée sur le projet.


## Mise en place

Afin de bénéficier de tous ces avantages, nous avons décidé chez Wizaplace de mettre en place un environnement de développement partagé à l’aide de [Vagrant](https://www.vagrantup.com/).


Voici un extrait du README de notre projet :


![](https://user-images.githubusercontent.com/748924/77312613-9a0b1080-6d02-11ea-8898-8891b94e0e4f.png)


Nous avons pris le parti de laisser les développeurs installer les deux logiciels nécessaires sur leur machine : Vagrant et VirtualBox.


![](https://user-images.githubusercontent.com/748924/77312615-9aa3a700-6d02-11ea-8662-76856d671b62.png)


Comme nous essayons toujours d’avoir une [approche rationnelle](http://mnapoli.fr/approaching-coding-style-rationally/), nous n’avons pas imposé ce fonctionnement aux membres de l’équipe ayant déjà un environnement de développement fonctionnel.


Mais notre équipe technique étant en phase d’expension importante, les prochains arrivants bénéficieront du confort, de la rapidité et de la sécurité d’une installation d’un environnement de développement fonctionnel en (presque) une commande.


## Métriques

Lors de la réception de mon nouveau MBP 15” fraichement réinstallé avec la dernière version de MacOS, il m’a fallu exactement 20 minutes pour disposer de mon environnement de dev fonctionnel me permettant d’accéder à l’application à l’adresse prévue et de lancer la suite de tests.


En clair, tout le nécessaire pour commencer à travailler !


![](https://user-images.githubusercontent.com/748924/77311949-68457a00-6d01-11ea-890c-653025137ec1.gif)

