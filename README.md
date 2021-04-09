# FastInstallGrailDocker
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
4. Le fichier requirements contient les dépendants pyth

- PyOpenGL
- Tensorflow
- keras
- torch==1.7.1
- h5py
- matplotlib
- numpy
- pandas
- elmoformanylangs
- gensim!
