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
4. Le fichier requirements contient les dépendances python installées dans l'image docker pyth (surtout avec les bonnes versions et le bon ordre de chaque package).

torch==1.7.1  
torchvision==0.8.2  
torchaudio==0.7.2  
allennlp  
h5py==2.10.0  
numpy==1.19.5  
elmoformanylangs  
PyOpenGL  
Tensorflow==2.4.1  
keras==2.4.3  
overrides  
matplotlib==3.3.4  
pandas==1.1.3  
gensim==3.8.3  
python-Levenshtein  

### Installation
1. Créer un fichier raw.txt dans votre repertoire de travail et Metter une phrase à analyser par exemple: 
*L'analyseur syntaxique et sémantique du français à large échelle GRAIL a été développé par Richard Moot.*
3. Télécharger le fichier [script.sh] (https://github.com/aminamaiga/Grail/blob/main/script.sh)
4. Exécuter la commande ./script.sh (Elle prend du temps pour la première fois, en effet 4 images Docker vont être téléchargées depuis le dockerHub)
  * Image du code source + le model (environ 4Go). Le DockerFile est disponible pour créer votre propre image [DockerFile] (https://github.com/aminamaiga/Grail/blob/main/Dockerfile)
  * Image Swipl
  * Image Tclsh
  * Pdflatex
6. Vous allez voir des traces sur la console pour toutes les actions exécutées:  
  * La création du conteneur 1 pour le code source  
  * La création du conteneur 2 pour le tclsh  
  * La création du conteneur 3 pour le swipl  
  * La création du conteneur 4 pour le pdflatex

Si vous obtenez le message *"Containers run succeeded"*, bravo! vos images et conteneurs ont été bien téléchargés et exécutés.  
S'en suit le message *"Tokenisation succeeded".*
S'en suit les messages *"Tagging succeeded"*  
                       *"conversion in prolog succeeded"*  
                       
                       
                       
Le bash de la machine Swipl s'ouvre, tapez manuellement les commandes suivantes pour la lémmatisation:  
une par une  
##### *swipl -s /app/lefff.pl -g "lemmatize(['/app/superpos_nolem.pl'])." -t halt.*  
##### *swipl -s /app/load.pl -g "chart_parse_all." -t halt.*  
##### *exit pour sortir du bash*  
##### *docker exec -it container4 bash -c 'pdflatex /app/semantics.tex'*  
##### *X* pour exit
##### *docker cp container4:/semantics.pdf .*
##### *docker cp container4:/proof.tex .*


![alt text](https://github.com/aminamaiga/Grail/blob/main/G3.PNG)
![alt text](https://github.com/aminamaiga/Grail/blob/main/G1.PNG)
![alt text](https://github.com/aminamaiga/Grail/blob/main/G4.PNG)
![alt text](https://github.com/aminamaiga/Grail/blob/main/G2.PNG)
![alt text](https://github.com/aminamaiga/Grail/blob/main/G5.PNG)





