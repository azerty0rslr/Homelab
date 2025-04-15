~ : dossier perso  
cd : change directory  
cd .. : remonter juste avant  
- cd /home : chemin absolut  
- cd dossier/ : chemin relatif  
- cd ./ : part du dossier courant  
ls : liste les dossiers  
- ls -a : voit les dossiers cachés  
- ls -l : affiche les options supplémentaires  
- ls -R : affiche de manière récursive  
- ls -t : organise par date de modification (et non paar nom)  
- ls -F : mets des / à la fin des dossiers  
nom_commande --help : affiche la page de manuel  
mkdir nom_dossier : créer un dossier  
rmdir nom_dossier : retire un dossier (on ne peut pas supprimer un dossier remplit)  
touch nom_fichier : créer un fichier  
rm nom_fichier : supprime un fichier  
- rm -r nom_dossier : supprime de manière récursive (supprime ce qu'il y a à l'intérieur puis le dossier)  
- :warning: rm -r / : va essayer de tout supprimer à partir de la racine  
mv nom_fichier nom_dossier/ : déplace un fichier  
mv nom_fichier nouveau_nom : renomme un fichier  
cp nom_fichier nom_copie : copie un fichier  
ln -s nom_fichier dossier/nom_du_lien : créer un lien symbolique  (fichier est mit en rouge, le lien se détaille en faisant ls -l)  

## Permissions
chmod g+w nom_fichier : pour modifier les permissions  
chmod 750 nom_fichier : pour modifier les permissions (r 4pts, w 2pts, x 1pts, 0pts rien)  
chown nom:autre_nom nom_fichier : permet de changer l'appartenance d'un fichier/dossier  

clear : nettoyer

## Dossiers à la racine
bin et sbin : les executables (sont aussi présent dans le dossier usr pour les exécutables des utilisateurs)  
etc : les configurations logiciels  
mnt et media : pour les disques durs, les clés usb ...  
root : correspond à l'administrateur (root sur linux)  
srv : serveur  
lost + found : lorsque le système à des ratés  
opt : (=optional) stock ce qui ne rentre pas dans la structure linux (logiciels propriétaires notamment)  
var : contient tout les fichiers qui vont être modifiés (notamment le log pour aller chercher les erreurs)  


sudo -s : pour être admin (root)
exit : pour quitter sudo
ctrl + c : arrêter exécution d'une commande
ctrl + x : pour quitter l'éditeur

## Gestionnaire d'applications
apt-get : pour obtenir le gestionnaire d'applications  
apt-get -h : pour avoir l'aide  
apt-get install nom_paquet : pour installer un paquet  
apt-get update : mets à jour la liste des dépots (mais pour modifier le gestionnaire des paquets il faut être en administrateur donc bien mettre sudo avant la commande)  
apt-get upgrade : mets à jour la distribution  
ls /etc/apt : pour connaître la liste des dépôts  
sudo nano /etc/apt/sources.list : pour éditer la liste  
