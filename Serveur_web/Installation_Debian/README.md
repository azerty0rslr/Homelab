## ISO Debian à installer pour Windows
https://www.debian.org/download.fr.html

## Configuration de la VM sur VirtualBox
Dans la partie ISO mettre l'ISO de Debian nouvellement installée.
Mémoire vive : 2048 MB  
Processors : 2 CPU  
Create a Virtual Hard Disk Now : 20Gio (ne pas pré-allouer l'espace)
Finish

## Installation de Debian sur la VM

![image](https://github.com/user-attachments/assets/2801824a-b649-4c9d-a80a-e4fe2e358884)
Pour les langages (Région, clavier, langue utilisé pour la configuration de Debian) sélectionner : French, France, Français
![image](https://github.com/user-attachments/assets/592134ee-398b-46ca-b079-99592f6d52c9)
Par simplicté pour ce premier serveur web nous ne modifierons pas les paramètres suivants : nom de machine, domaine
![image](https://github.com/user-attachments/assets/1f09f8ad-745e-4f33-b22c-7a55cf2ba30c)
![image](https://github.com/user-attachments/assets/e7443eec-dfe7-4e8b-baa7-17bec85c2fc8)
Nous n'utiliserons pas le superutilisateur, ce sera le premier compte qui récupèrera les privilèges avec la commande "sudo", donc nous laissons le champs vide.
![image](https://github.com/user-attachments/assets/9ac5ae62-f581-4da1-9ba6-5035146d9292)
Choisissez ensuite un nom d'utilisateur puis son mot de passe.
![image](https://github.com/user-attachments/assets/99ec60fa-e617-4c87-962b-3c1cc67263ff)

### Partition des disques
Nous laisserons tout le partitionnement des disques par défaut.
![image](https://github.com/user-attachments/assets/0eb01778-7f05-4902-893e-371f82244cb5)
![image](https://github.com/user-attachments/assets/7e09fe86-5b9d-4bd7-b06f-1816fd14ca72)
![image](https://github.com/user-attachments/assets/7d6ff798-8645-40e9-8d11-94a151941a63)  

Puisque nous n'avions qu'un seul disque à installer pour Debian il faudra mettre non à l'option suivante :
![image](https://github.com/user-attachments/assets/071a8a51-65bc-463c-a5c6-389b5a19ea09)
Pour le point de réseau, choisissez l'endroit où est localisé votre réseau
![image](https://github.com/user-attachments/assets/274442a1-412c-4378-9d51-a9698adbed46)
Puis laissez la sélection sur deb.debian.org
![image](https://github.com/user-attachments/assets/2bbad3b8-5f20-467d-b323-dc39a0d7d625)
Si vous avez un **proxy** indiquez le sur cette étape
![image](https://github.com/user-attachments/assets/9c952a08-dcd1-48b4-8d51-2193735a22cb)
Par soucis de sécurité, il peut être préférable de sélectionner "Non" à l'étude statistique sur l'utilisation des données
![image](https://github.com/user-attachments/assets/486d020b-55e0-46da-8e05-1a4049c78b1c)
Dans notre cas, pour la sélection des logiciels, sélectionnez les paramètres suivants avec la touche *espace* pour ajouter ou supprimer un élément.
![image](https://github.com/user-attachments/assets/f153eb15-ebb3-4c0b-9861-33ba40f4947c)


### GRUM
Nous installons donc GRUM.
![image](https://github.com/user-attachments/assets/75c9896a-d63b-4a6e-a972-27669762bcfa)
Sur le périphérique que nous propose la VM.
![image](https://github.com/user-attachments/assets/0cd219b3-01ff-4a15-b773-bbfb50df52de)

Notre installation se termine ...
![image](https://github.com/user-attachments/assets/f0f38527-acf4-414d-9a73-507de2a5cbd0)
Rentrez le nom d'utilisateur choisi plus tôt ainsi que le mot de passe.



![image](https://github.com/user-attachments/assets/ddbda36f-16db-42c7-b837-f0d891b689e8)

Et voilà Debian est désormais installé sur notre VM !
![image](https://github.com/user-attachments/assets/a9cbfecd-40de-4390-ae3e-751cee9ea35f)
