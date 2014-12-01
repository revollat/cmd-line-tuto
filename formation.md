
# UN peu d'histoire

- UNIX : créé en 1969. Nombreux petits outils, chacun doté d'une mission spécifique.
- Projet GNU commencé en 1984. Première version des outils en 1992 utilisant le noyau Linux (créer par un étudiant finlandais un an plus tôt)

## La philosophie UNIX 

- Écrivez des programmes qui effectuent une seule chose et qui le font bien.
- Écrivez des programmes qui collaborent.
- Écrivez des programmes pour gérer des flux de texte, car c'est une interface universelle.

### Citations

> Ceux qui ne comprennent pas Unix sont condamnés à le ré-inventer.
>  – Henry Spencer

> Unix n'a pas été conçu pour empêcher ses utilisateurs de commettre des actes stupides, car cela les empêcherait aussi de réaliser des choses ingénieux.
>  – Doug Gwyn

# Les commandes de base

Il y a les commandes "de base" des OS UNIX-like et il y a les commandes "additionnels" spécifiques aux logiciels installés (par exemple ligne de commande pour vider un cache varnish). Ces outils additionnels suivent en général la "philosophie Unix".

## Fichiers

```ls``` Lister vos fichiers

```ls -l``` version long format

```ls -lah```

```ls -ltr``` date dernière modification en ordre inverse

```ls --help``` pour l'aide concise et ```man ls``` pour l'aide complète

```less filename``` visualiser un ficheir, page par page. Utilisez ```/pattern``` pour rechercher un mot

```tail filename.txt```

```tail -f log-file```

```mv filename1 filename2```

```cp filename1 filename2```

```rm filename```

```diff filename1 filename2```

```wc filename``` compter les caractères, mots lignes d'un fichier

```chmod options filename```

```chmod 665 file.txt```

```chmod ug+rwx file.txt```

```chmod g-rwx file.txt```

```chown oracle:dba dbora.sh```

```gzip filename```

```gunzip filename```

## Dossiers

pwd

```mkdir dirname```

```mkdir des/sous/repetoires```

```cd /home/test```

```cd ../../dossier/test```

```cd dossier/relatif```

```cd -``` naviguer entre 2 dossiers


## Rechercher

```grep string filename```

```grep -i "the" demo_file``` insensible à la case

```grep -r --include=*.twig "prod\.nice\.fr" .```

```find / -name "*the*"```

```find . -type f``` fichiers régulier seulement, pas les dossiers, liens symboliques,binaires...

```find . -type f -exec sed -i 's/www.nice.fr/ancien.nice.fr/g' {} \;```

## Divers

whoami

date

cal

ps u

kill PID

ftp hostname

ssh hostname

wget

# Redirection et pipe

## Pour rediriger la sortie d'une commande

```ps ax >processes.txt```

```ps ax >>processes.txt```

```ls -l > foo```

## Redigier entrée d'une commande

```less < foo```

## Pipe

au lieu d'écrire ces 2 commandes

```
ls -l > foo
less < foo
```

On peut écrire : ```ls -l | less```

Autres exemples :

```ps ax | grep java```

```php -m | grep intl```

# Quelques exemples de commandes

```grep -RE '[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}' . > /tmp/ip_dur```

```du -s * | sort -nr > $HOME/user_space_report.txt```

```mysql -h host -u user -ppass base_de_donnees > fichier_dump```

```mysql -h host -u user -ppass base_de_donnees < fichier_dump```

```echo 'GET / HTTP/1.1\r\nHost: www.perdu.com\r\nConnection: close\r\n\r\n' | nc www.perdu.com 80```

```docker ps -a --filter 'status=exited' | grep torbox | awk '{print $1}' | xargs --no-run-if-empty docker rm```

```:(){ :|:& };:``` fork bomb, warning : n'essayez pas ça à la maison :)

```seq -f '4/%g' 1 2 99999 | paste -sd-+ | bc -l``` valeur approchée de pi

```tr -c "[:digit:]" " " < /dev/urandom | dd cbs=$COLUMNS conv=unblock | GREP_COLOR="1;32" grep --color "[^ ]"``` maxtix en ligne de commande

```find -not -empty -type f -printf "%s\n" | sort -rn | uniq -d | xargs -I{} -n1 find -type f -size {}c -print0 | xargs -0 md5sum | sort | uniq -w32 --all-repeated=separate``` trouver des fichiers en doulons basé sur contenu (md5)

PLeins d'exemples marrant là :http://www.commandlinefu.com/commands/browse/sort-by-votes

# Pour aller plus loin

Les scripts bash/zsh

# Aide

man wget

wget -h

apropos wget

Tip of the day :

```echo "Le saviez-vous ?" ; whatis $(ls /bin | shuf -n 1)```


# Easter egg 

```apt-get moo```

```nc towel.blinkenlights.nl 23```

# Référence

http://linuxcommand.org/

http://ss64.com/bash/

http://www.commandlinefu.com/


