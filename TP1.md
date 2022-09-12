8 Septembre 2022
TP 1 
Installation D’Ubuntu Server et prise en main du Shell



Exercice 2 : Prise en main de l’interpréteur de commandes

Manuel 

A l’aide du manuel, identifiez le rôle de la commande which 

Le Linux which command identifie l'exécutable binaire qui se lance lorsque vous émettez une commande vers le shell, cela signifie que la commande which produit le chemin complet des commandes du Shell.  
Quand on consulte une page du manuel, comment peut-on rechercher un terme (par exemple, chercher le terme option dans la page de manuel de which ? 

man -k printf ou apropos printf , permet de consulter un page du manuel en cherchant un terme précis. 
Comment quitte-t-on le manuel ? 

Pour quitter le manuel, il suffit de taper « q » 
Chaque section du manuel a une première page, qui présente le contenu de la section. Aﬀicher la première page de la section 6 ; de quoi parle cette section ?  
La section 6 du manuel décrit les jeux et petits programmes disponible sur le système.

Navigation dans l’arborescence des fichiers 

allez dans le dossier /var/log
cd /var/log

remontez dans le dossier parent (/var) en utilisant un chemin relatif 
cd ..

retournez dans le dossier personnel
cd

revenez au dossier précédent (/var) sans utiliser de chemin
cd -

essayez d’accéder au dossier /root ; que se passe-t-il ?
Permission denied, car l’utilisateur na pas n’est pas admin

essayez la commande sudo cd /root ; que se passe-t-il ? Expliquez 
La commande sudo est inconnu, car elle na pas était installé

à partir de votre dossier personnel, créez l’arborescence suivante :  
revenez dans votre dossier personnel ; à l’aide de la commande rm, essayez de supprimer Fichier1, puis Dossier1 ; que se passe-t-il ? 

On ne peut pas supprimer le fichier_1 depuis le dossier personnel. On ne peut pas supprimer le dossier_1 car la commande rm permet uniquement de supprimer les fichiers. 
quelle commande permet de supprimer un dossier ? 
rmdir 
que se passe-t-il quand on applique cette commande à Dossier2 ? 
Cela ne supprimera pas le dossier_2 car il n’est pas vide, et la commande ne supprime que les dossier vide. 
comment supprimer en une seule commande Dossier2 et son contenu ? 
rm -r permet de supprimer un dossier et son contenu

Commandes importantes 

Quelle commande permet d’afficher l’heure ? A quoi sert la commande time ? 
La commande date permet d’afficher l’heure, time est un chronomètre pour l’exécution d’un logiciel. 
Dans votre dossier personnel, tapez successivement les commandes ls puis la ; que peut-on en déduire sur les fichiers commençant par un point ? 
Ce sont les fichiers cachés. 
Où se situe le programme ls? 
Dans le dossier /usr/bin/ls 
Essayez la commande ll. Existe-t-il une entrée de manuel pour cette commande ? Utilisez les commandes alias ou alias pour en savoir plus sur la nature de cette commande. 
ll permet d’afficher les droit de chaque utilisateur. La commande manuel de ll est ls-alF. 
Quelle commande permet d’afficher les fichiers contenus dans le dossier/bin? 
ls /bin 
Que fait la commande ls .. ? 
Affiche les dossier et fichier parent 
Quelle commande donne le chemin complet du dossier courant ? 
pwd 
Que fait la commande echo 'bip' > plop exécutée 2 fois ? 
Ne créer qu’une seule fois le fichier plop 
Que fait la commande echo 'bip' >> plop exécutée 2 fois ? 
Cela affiche plusieurs fois le texte ‘bip’, dans le fichier plop. car. >> n’écrase pas ce qui existe déjà. 
Interprétez le comportement de la commande sleep 10 | echo 'toto' ? 
Cela affiche toto et met en veille le terminal pendant 10 secondes. 
A quoi sert la commande file? Essayez la sur des fichiers de types différents. 
détermine le type d’un fichier, indépendamment de son extension.

Créez un fichier original qui contient la chaîne Hello Toto ! ; créer ensuite un lien lien_phy vers ce fichier avec la commande ln original lien_phy. Modifiez à présent le contenu de original et aﬀichez le contenu de lien_phy : qu’observe-t-on ? Supprimez le fichier original ; quelle conséquence cela a-t-il surlien_phy? 

Cela a aussi modifier le lien_phy. Supprimer origan ne supprime pas le lien_phy
 
Créez àp résent un lien symbolique lien_sym sur lien_phy avec lac ommande ln -s. lien_phy lien_sym. Modifiez le contenu delien_phy; quelle conséquence pourlien_sym? Et inversement? Supprimez le fichier lien_phy; quelle conséquence cela a-t-il surlien_sym? 
Lorsque l’on modifie le lien_phy le lien_sym est aussi modifier. Cependant lorsque l’on supprime lien_phy, le lien_sym est cassé et n ‘est plus consultable. 
Aﬀichez à l’écran le fichier /var/log/syslog. Quels raccourcis clavier permettent d’interrompre et reprendre le défilement à l’écran ? 
Le raccourcis Ctrl+C. 
Aﬀichez les 5 premières lignes du fichier /var/log/syslog, puis les 15 dernières, puis seulement les lignes 10 à 20. 
Les 5 premières head -5 syslog, tail -15 syslog pour les 15 dernières, cat syslog | tail -n +10 | head -n 10 pour afficher les lignes 10 à 20. 
Que fait la commande dmesg | less ? 
Cela affiche les Logs dans un lecteur de fichier. 
Aﬀichez à l’écran le fichier /etc/passwd ; que contient-il ? Quelle commande permet d’aﬀicher la page de manuel de ce fichier ? 
Il contient la liste de tous les utilisateurs. man -5 passwd. 
Aﬀichez seulement la première colonne triée par ordre alphabétique inverse 
cat /etc/passwd | awk '{ print $1 }' | sort -r 
Quelle commande nous donne le nombre d’utilisateurs ayant un compte sur cette machine (pas seule- ment les utilisateurs connectés) ?  
cat /etc/passwd | wc -l
Combien de pages de manuel comportent le mot-clé conversion dans leur description ?  
Man -k conversion | wc -l
A l’aide de la commande find, recherchez tous les fichiers se nommant passwd présents sur la machine   
Find / -name passwd
Modifiez la commande précédente pour que la liste des fichiers trouvés soit enregistrée dans le fichier ~/list_passwd_files.txt et que les erreurs soient redirigées vers le fichier spécial /dev/null 
Find / -name passed 2>/dev /null > ˜/list_passwd_files.txt
Dans votre dossier personnel, utilisez la commande grep pour chercher où est défini l’alias ll vu précédemment  
Grep « alias ll=«  -r ˜, il se trouve dans «˜/.bashrc »
Utilisez la commande locate pour trouver le fichier history.log.  
Impossible d’installer locate
Créerunfichierdansvotredossierpersonnelpuisutilisezlocatepourletrouver.Apparaît-il?Pourquoi? 
Impossible d’installer locate 
Exercice 3

1. Touch log.txt pour créer le fichier. Puis cp /var/log/syslog log.txt. Et on peut l’ouvrir nano log.txt 2. Remplacer le mot kernel par noyau on fait : Ctrl \ kernel noyau A 3. Alt + A puis Ctrl + K et en bas du fichier on fait Ctrl + U
4. Alt U permet d’annuler l’action précédente

Exercice 4

\A[\033[01;35m] - \u@\h\[\033[32m]:\[\033[01;34m\]\w\[\033[36m\]\$