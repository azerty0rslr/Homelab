# Mise en place de l'éditeur VIM
Nous allons donc installer un éditeur plus puissant que l'éditeur par défaut (nano) afin de gagner du temps par la suite.  
Pour cela nous allons essayer VI (version moins puissante que VIM mais présente par défaut) en tapant vi chemin/accès/fichier  
En mode naviguation les touches JKLM ainsi que les flèches directionnelles permettent de naviguer dans le fichier.  
Pour passer en mode insertion il faut taper 'i' et pour sortir il faut taper sur 'echap'.  
L'avantage majeur de l'éditeur est son nombre conséquent de raccourcis : https://www.atmos.albany.edu/daes/atmclasses/atm350/vi_cheat_sheet.pdf  
**Exemples :**  
- dupliquer une ligne - faire 'yy' sur la ligne puis 'p' pour copier  
- supprimer une ligne - 'd'  
Pour quitter VI il faut être en mode navigation et taper ':q'  
  
Pour installer la version suppérieure de VI (=> VIM) il faut l'installer avec la commande suivante : sudo apt-get install vim  
Par la suite pour utiliser VIM, les commandes sont les mêmes en revanche pour accéder au fichier il faut entrer : vim chemin/accès/fichier  
![image](https://github.com/user-attachments/assets/a8b107a0-cfea-4849-8416-9be754d4325b)  
Pour voir la syntaxe il suffit de taper ':syntax on'  
  
![image](https://github.com/user-attachments/assets/aeef6a03-77bf-4a71-9570-3b50460d77e8)  

## Créer un fichier de configuration
Pour configurer le comportement de VIM, pour qu'il reste identique.  
Tout d'abord il faut se rendre dans son dossier personnel (cd ~)  
Puis créer un fichier .vimrc (vi .vimrc)  
Exemple pour mettre la syntaxe obligatoirement sur VIM :  
![image](https://github.com/user-attachments/assets/6d2884c3-feb5-440d-89f2-d1ca40d351cf)  
  
Pour quitter en sauvegardant les modifications ajoutées ':wq'  
Pour quitter sans sauvegarder les modifications ajoutées ':q!'  
