###### 11/03/2013

# Service web d'analyse de code PHP

## Les services web

Les services web, c'est bien. A la fois parce qu'ils sont au coeur de la [plateformisation](https://plus.google.com/112678702228711889851/posts/eVeouesvaVX) mais aussi parce qu'ils facilitent les méthodes d'amélioration continue. C'est pourquoi je m'acharne à en développer (trop) régulièrement.


## La qualité

La qualité est aussi un [sujet qui m'intéresse](https://github.com/KuiKui/Blog/blob/master/posts/2012-02-08_La-qualite.md#la-qualit) même si je ne suis pas toujours satisfait de mon propre travail dans ce domaine.

Parmi tous les processus de qualité, la revue de code à rapidement attiré mon attention de par l'humilité qu'elle impose. Il apparait de plus, qu'elle est [un des facteurs les plus importants](http://www.codinghorror.com/blog/2006/01/code-reviews-just-do-it.html) de l'amélioration de la qualité ([plus que les tests unitaires?](http://kev.inburke.com/kevin/the-best-ways-to-find-bugs-in-your-code/)).

C'est pourquoi, avec feu la Team-Fusion (big up!), nous avons développé [Crew](http://crew-cr.org/), un outil open-source de revue de code, actuellement [intensivement](https://twitter.com/srogier/status/288248643331444736) utilisé chez notre [ancien employeur](http://pmsipilot.com/).


## Le 'One Week POC'

Il y quelques mois, avec [Adrien Gallou](https://twitter.com/agallou) et [Julien Bianchi](https://twitter.com/jubianchi), nous avons développé Coconut CI, un service web d'intégration continue pour concurrencer [Travis CI](https://travis-ci.org). Effectivement à cette époque malgré sa domination sans partage, Travis CI restait fortement couplé à GitHub et ne permettait pas d'utiliser des repositories privés, ce qui était notre besoin.

Bref, pendant 3 mois nous avons développé un [MVP](http://www.dinkypage.com/the-makingof-our-mvp) que nous avons ensuite [présenté à quelques développeurs](http://lyon.afup.org/2012/09/18/aperophp-jeudi-27-septembre-a-19h/). Deux mois après nous fermions ce service. Aucun utilisateur n'avait lancé le moindre test. *Epic Fail*.

Une des conclusions de cette expérience est évidente : 3 mois de développement avant d'avoir des retours utilisateurs, c'est trop. Voilà pourquoi j'ai décidé d'essayer un nouveau format : faire le POC d'un nouveau service web complet en une semaine. Pas un jour de plus.

![](http://img171.imageshack.us/img171/1496/premiercommit.png)

## Phakir

Voici donc la première itération de [Phakir](http://phakir.com/), une plateforme en ligne d'analyse de code PHP.

[Phakir](http://phakir.com/) vous permet d'analyser vos projets GitHub à l'aide de [PHP Mess Detector](http://phpmd.org/) et d'afficher les résultats dans une page dédiée. Les règles actuellement utilisée sont [celles par défaut](http://phpmd.org/rules/index.html). Grâce aux liens directs sur GitHub vous pouvez visualiser rapidement le code incriminé par chaque violation.

[Phakir](http://phakir.com/) ne propose dans un premier temps, aucune configuration. Les résultats sont ainsi visibles directement sans autres action que le lancement manuel d'un *check*.

## La concurrence

L'idée de [Phakir](http://phakir.com/) est intégralement tirée de [Code Climate](https://codeclimate.com/). Aucune originalité mise à part le simple et étonnant fait que cela n'existe pas pour les projets PHP.

Ou plutôt, *n'existait pas*. Car au deuxième jour de mon *One Week POC*, je découvre [Scrutinizer](https://scrutinizer-ci.com/). Je suis alors [très impressionné](https://twitter.com/dondouny/status/309276005929988096). Pourtant je continue de développer [Phakir](http://phakir.com/). D'abord parceque je veux [terminer ce que j'ai commencé](http://gettingreal.37signals.com/ch06_Done.php). Ensuite par ce que la *killer feature* que j'attends n'existe pas encore sur Scrutinizer.


## La viabilité du projet

Je continue de développer des fonctionnalités, tout en étant conscient que la vie d'un projet ne dépend que de son abilité à résoudre les problèmes du plus grand nombre. 

N'hésitez donc pas à me contacter par [Twitter](https://twitter.com/dondouny) si vous pensez que [Phakir](http://phakir.com/) peut potentiellement vous aider à résoudre certains problèmes.