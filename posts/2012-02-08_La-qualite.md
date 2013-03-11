###### 08/02/2012

# La qualité

Un projet est composé de quatre variables :

* le périmètre fonctionnel (quoi),
* la qualité (comment),
* les ressources (qui),
* le temps (quand).

J’ai volontairement classé ces variables dans l’ordre où il me semble qu’elles devraient être définies. Mais nous ne vivons pas dans le monde des Bisounours et c’est pourquoi la qualité est en général la variable qui sert à laisser de la marge aux autres.

Chez [PMSIpilot](http://www.pmsipilot.com) nous avons la chance de pouvoir mettre en place des processus de production permettant d’obtenir la qualité *souhaitée*. Effectivement, le métier d’éditeur de logiciels nous oblige à maintenir un certain niveau de qualité, car la moindre lacune dans ce domaine génère un coût pour l’entreprise et non pas un gain comme pour certaines entreprises de service.

## La qualité organisationnelle

La première possibilité d’amélioration de la qualité est organisationnelle. Elle consiste à suivre scrupuleusement la 5ème [règle de Joel](http://www.joelonsoftware.com/articles/fog0000000043.html) : **corriger tous les bugs existants avant d’écrire de nouvelles fonctionnalités**. Cela parait simple, mais dans la pratique il faut que tous les services soient conscients des impacts. Dans notre équipe cela se traduit par un processus simple mais rigide de gestion des demandes entrantes :

1. La demande est-elle nécessaire pour l’exploitation ?  
Traduction : « l’application n’est-elle plus utilisable par les clients sans cela ? »  
Si oui, on développe rapidement la demande.
2. L’application est-elle stable ?  
Traduction : « il n’y a plus de bug connu et la couverture de test est suffisante ? »  
Si non, on stabilise l’application.
3. Est-ce un besoin réel ?  
Traduction : « plusieurs personnes pensent que cette demande est attendue ? »  
Si oui, les développeurs estiment la durée de développement de la demande.

A la fin de ce processus, nous nous trouvons en position de planifier un ensemble de demandes dont les temps de développement ont été préalablement définis par les développeurs en incluant la marge nécessaire pour maintenir la qualité intrinsèque du code.

## La qualité intrinsèque

Afin d’obtenir la meilleur qualité de code, nous suivons un autre principe simple : **plusieurs cerveaux valent toujours mieux qu’un seul**.

Nous essayons donc d’appliquer ce principe sur chacune des phases composant la réalisation d’une demande :

* Lors de la spécification, toutes les décisions techniques sont prises collégialement par l’équipe. Pour éviter de couper le rythme des développeurs, seuls les volontaires participent aux débats.
* Lors du développement, des périodes de [pair programming](http://fr.wikipedia.org/wiki/Programmation_en_bin%C3%B4me) s’alternent avec des périodes d’isolement *relatif* ([open space oblige](http://www.joelonsoftware.com/items/2006/07/30.html)). Pour communiquer de manière la moins intrusive possible tout en restant ludique, nous utilisons [Campfire](http://campfirenow.com/) avec notre fidèle robot Fubot.
* Enfin pour la vérification, nous réalisons obligatoirement une revue de code avant de le mettre à disposition sur le *master*. De cette manière, au moins une autre personne que celles ayant développées la fonctionnalité est amenée à vérifier le code. Pour simplifier cette étape, nous avons développé un logiciel open source de revue de code : [Crew](http://crew-cr.org/).

## La qualité continue

Le type de projet que nous réalisons (80% d’interface de saisie et 20% de calcul) ainsi que la motivation de l’équipe nous a naturellement dirigés vers l’utilisation intensive et quasiment exclusive de [Behat](http://behat.org/) pour tester nos applications. C’est un framework de test fonctionnel permettant de coder intuitivement des scénarios utilisateurs qui peuvent ensuite être joués sur plusieurs navigateurs différents pour garantir la régularité fonctionnelle cross-navigateurs (IE, Firefox, Chrome, etc.). Cela permet aussi de détecter toute régression des fonctionnalités existantes.

Même si chaque développeur lance l’ensemble des tests sur son poste avant de mettre son nouveau code à disposition sur le master, les interactions complexes qui peuvent surgir lors des merges nécessitent une [intégration continue](http://martinfowler.com/articles/continuousIntegration.html). Nous disposons donc d’un serveur d’intégration continue piloté par [Jenkins](http://jenkins-ci.org/) qui reconstruit une nouvelle version et fait tourner l’ensemble des tests lors de chaque modification du master. **Nous sommes ainsi avertis rapidement lors de l’apparition d’une régression**.

Sachant que nos tests Behat sont déjà composés de plus de 3200 étapes et que cela croît de manière exponentielle, nous avons ajouté un [notifier Campfire](https://github.com/tentacode/BehatCH/blob/master/features/bootstrap/notifiers/CampfireNotifier.php) à notre [bootstrap personnalisé](https://github.com/tentacode/BehatCH) afin d’être avertis de l’échec d’une étape avant la fin de tous les tests.

Réactivité ! ;)

## La qualité ressentie

Comme il apparaît que les tests grandeur nature (avec des gens dedans) [sont bien plus performants](http://kev.inburke.com/kevin/the-best-ways-to-find-bugs-in-your-code/) que n’importe quel système de tests automatisés, nous avons mis en place des instances de nos logiciels accessibles en interne à n’importe quel employé de l’entreprise. Ces instances sont reconstruites dans leur dernières versions toutes les heures / jours / mois. Nous encourageons ainsi tous les employés à utiliser nos applications. Mais en pratique, le résultat est assez mitigé : peu de personnes utilisent spontanément nos logiciels.

Certains managers de l’entreprise ont donc eu la très bonne idée de créer une cellule de test que nous appelons *cellule qualité*. Approximativement une fois par mois, plusieurs personnes de divers secteurs se réunissent (formation, support, métier et développement) et passent 1 ou 2 journées à tester manuellement les logiciels. **Il en ressort toujours un bon nombre de bugs que les développeurs n’avaient pas prévus lors de la création de leur tests automatisés**.

## Améliorations

Outre des bureaux individuels permettant d’[augmenter la productivité](http://www.joelonsoftware.com/articles/FieldGuidetoDevelopers.html) des développeurs, l’axe d’amélioration que j’aimerais étudier concerne le [déploiement continu](http://blog.octo.com/5-bonnes-raisons-de-deployer-en-continu/).

Ce type de déploiement nous permettrait comme certains grands noms du web ([GitHub](http://zachholman.com/talk/how-github-uses-github-to-build-github/) ou [37signals](http://37signals.com/svn/posts/3102-saas-change-starts-easy-and-then-gets-really-hard)), d’être bien plus réactif sur la correction des bugs sans pour autant polluer les utilisateurs avec de nombreuses mises à jour correctives ou même évolutives qui peuvent à terme dégrader l’image de l’entreprise.

Avec le déploiement continu :

* **la stabilité augmente** grâce à la suppression des sauts fonctionnels trop importants,
* **la qualité ressentie par les utilisateurs est meilleure** grâce à la réactivité non intrusive des corrections de bugs.

Actuellement développés sous forme d’intranets cloisonnés dans les SI des hôpitaux, nos logiciels évolueront peut-être un jour vers du [SaaS](http://fr.wikipedia.org/wiki/Logiciel_en_tant_que_service). Cela nous simplifierait alors la mise en place du déploiement continu.
