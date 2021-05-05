# FastInstallGrailWithDocker
> L'analyseur syntaxique et sémantique du français à large échelle GRAIL a été développé par Richard Moot. La plateforme Grail analyse une ou plusieurs phrases du français et produit automatiquement une formule logiques représentant le sens de la phrase analysée --- en cas d'ambiguïté Grail en produit plusieurs.   
Moot, R. (2015), A Type-Logical Treebank for French, Journal of Language Modelling 3(1), pp. 229-265.

### Installer docker  
[Docker] (https://docs.docker.com/get-docker/)
Vérifier l'installation sur votre ligne de commande avec la commande __docker -v__

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Organisation
Le projet est constitué:
1. du dossier model (ElmostForManyLangs)
2. du dossier GrailLight (code python Tcl Pl)
3. du dossier elmo_superpos
4. Le fichier requirements contient les dépendances python installées dans l'image docker pyth.

- PyOpenGL
- Tensorflow
- keras
- torch==1.7.1
- h5py
- matplotlib
- numpy
- pandas
- elmoformanylangs
- gensim

### Installation
1. Créer un fichier raw.txt dans votre repertoire de travail et Metter une phrase à analyser par exemple: 
*L'analyseur syntaxique et sémantique du français à large échelle GRAIL a été développé par Richard Moot.*
3. Télécharger le fichier [script.sh] (https://github.com/aminamaiga/Grail/blob/main/script.sh)
4. Exécuter la commande ./script.sh (Elle prend du temps pour la première fois, en effet 3 images Docker vont être téléchargées depuis le dockerHub)
  * Image du code source (environ 6Go). Le DockerFile est disponible pour créer votre propre image [DockerFile] (https://github.com/aminamaiga/Grail/blob/main/Dockerfile)
  * Image Swipl
  * Image Tclsh
6. Vous allez voir des traces sur la console pour toutes les actions exécutées:  
  * La création du conteneur 1 pour le code source  
  * La création du conteneur 2 pour le tclsh  
  * La création du conteneur 3 pour le swipl  

Si vous obtenez le message *"Containers run succeeded"*, bravo! vos images et conteneurs ont été bien téléchargés et exécutés.  
S'en suit le message *"Tokenisation succeeded".*
S'en suit les messages *"Tagging succeeded"*  
                       *"conversion in prolog succeeded"*  
                       
                       
                       
Le bash de la machine Swipl s'ouvre, tapez manuellement les commandes suivantes pour la lémmatisation:  
une par une  
##### *swipl -s /app/lefff.pl -g "lemmatize(['/app/superpos_nolem.pl'])." -t halt.*  
##### *swipl -s /app/grail_light_nd.pl -g "compile('./app/GrailLight/superpos')." -t halt.*  
##### *swipl -s /app/grail_light_nd.pl -g "chart_parse_all." -t halt.*  
##### *exit pour sortir du bash*  


![alt text](https://github.com/aminamaiga/Grail/blob/main/G1.PNG)
![alt text](https://github.com/aminamaiga/Grail/blob/main/G2.PNG)
![alt text](https://github.com/aminamaiga/Grail/blob/main/G3.PNG)
![alt text](https://github.com/aminamaiga/Grail/blob/main/G4.PNG)








