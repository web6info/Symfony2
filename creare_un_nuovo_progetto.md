Creare un nuovo progetto
========

####Riferimenti
- [Symfony2 doc](http://symfony.com/it/doc/current/book/installation.html)

####HowTo
Installare *composer* seguendo la guida descritta [qui](https://github.com/web6info/Composer/blob/master/install-global.md#installazione-globale). Posizioniamoci nella directory del progetto:
```
$ cd /dir/del/progetto
```
Da ora in poi supporremo di lanciare i comandi dalla posizione `/dir/del/progetto`. Per creare il progetto lanciare il seguente comando:
```
$ composer create-project symfony/framework-standard-edition /percorso/del/mioprogetto 2.4.*
```
Impostare i permessi alle directory app/cache e app/logs:
```
$ APACHEUSER=`ps aux | grep -E '[a]pache|[h]ttpd' | grep -v root | head -1 | cut -d\  -f1`
$ sudo setfacl -R -m u:$APACHEUSER:rwX -m u:`whoami`:rwX app/cache app/logs
$ sudo setfacl -dR -m u:$APACHEUSER:rwX -m u:`whoami`:rwX app/cache app/logs
```
Successivamente, quando si vorrà aggiornare il progetto basterà lanciare il seguente comando:
```
$ composer update
```
