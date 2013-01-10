###### 26/04/2012
## Tester la dernière version de Git

[Git](http://git-scm.com/) c'est bien.

Mais Git est en constante évolution. C'est pourquoi il peut être utile de tester les dernières évolutions qui pourraient potentiellement nous simplifier la vie.

Git ayant un miroir sur [GitHub](https://github.com/gitster/git) (sans gestion des PullRequests), il est facile de se brancher sur le master :

```shell
$ cd /tmp
$ git clone git://github.com/gitster/git.git
```

Ensuite il suffit de lancer quelques commandes pour générer le programme :

```shell
$ cd /tmp/git
$ autoreconf
$ ./configure --prefix=/chemin/vers/nouveaugit
$ make install
```

Afin de pouvoir utiliser cette version de Git nouvellement installée avec une autre commande que `git`, il est possible de créer un alias `gitdev` :

```shell
$ vi ~/.bashrc
```

Ajouter la ligne `alias gitdev="/chemin/vers/nouveaugit/bin/git"` puis recharger le fichier pour pouvoir en profiter tout de suite :

```shell
$ source ~/.bashrc
```
    
Si tout fonctionne bien, les numéros de version des deux commandes doivent être différents :

```shell
$ git --version
git version 1.7.4.1
$ gitdev --version
git version 1.7.10.334.gf9d99
```

Et voilà.
