Lorsque l'on travaille sur un serveur, nous n'avons pas accès directement à la machine pour pouvoir taper nos différentes commandes. Il va donc nous falloir utiliser un protocole particulier pour communiquer avec cette dernière : SSH. Normalement SSH est installé par défaut sur la machine. Si ce n'est pas le cas il suffit d'utiliser : sudo apt-get install ssh. 

# Redirection de ports
Si nous utilisons VirtualBox il faudra réaliser une étape intermédiaire avant de pouvoir procéder. Il faut donc modifier les paramètres réseaux de la manière suivante. 
![image](https://github.com/user-attachments/assets/ca74e5ab-8c8d-4e31-b24e-1e81aa9c6c62)
Une fois sur réseau, cliquez sur "Redirection de ports"
![image](https://github.com/user-attachments/assets/1edf496f-0ad5-48be-84c4-9b9a1c9f9779)
Pour rediriger l'IP nous aurons besoin de connaître l'IP machine. Pour cela sur votre serveur faites : ip a  
L'IP se trouve au niveau de enp0s3 à côté de inet. Ici l'IP est celui par défaut : 10.0.2.15 (à adapter en fonction de son propre ip)  
L'IP local sur la machine est au niveau de lo. Ici c'est : 127.0.0.1
![image](https://github.com/user-attachments/assets/89f2730c-3659-404e-805f-b076a1d5a95c)
On ajoute donc les nouvelles règles de redirection que l'on paramètre de la manière suivante sur VirtualBox. Puis on redémarre la machine virtuelle.
![image](https://github.com/user-attachments/assets/ca41e9ca-7d9d-4239-b136-0cf481a7f29a)
Pour se connecter à la machine. Faites : ssh (login de votre machine donc ici dev + @ + l'ip de votre machine donc l'ip local puisqu'on a fait une redirection des ports) dev@127.0.0.1. On peut modifier le port par défaut (ici 22) qu'on va modifier pour le port 2222 de la manière suivante :
ssh dev@127.0.0.1 -p 2222.  
Dans ma situation la commande ne marchait pas puisqu'aucun port n'étais configuré sur 2222 j'ai donc retiré la partie -p 2222. Pour que cela fonctionne nous aurions dû (sur windows) installer PuTTY pour utiliser le port 2222.
![image](https://github.com/user-attachments/assets/143201eb-79a2-473f-9453-df3a08ab7dce)

# Amélioration sécurité
Désormais nous allons améliorer la sécurité du SSH. Pour commencer nous allons modifier son fichier de configuration de la manière suivante. vim /etc/ssh/sshd_config.
Nous modifions deux paramètres : 
- Le port que l'on passe au port 5789
- Le PermitRootLogin que l'on mets en no
= ces deux modifications nous permettent une plus grande sécurité.
![image](https://github.com/user-attachments/assets/ead732f7-5a14-438a-8f4e-0c7c1e370b8f)
Pour quitter la modification 'echap' et ':x'
On redémarre désormais SSH de la manière suivante : sudo service ssh restart
![image](https://github.com/user-attachments/assets/dae17e92-b30d-45a3-a61f-5e7fd8dabec5)
On retourne désormais sur VirtualBox pour ajouter nos modifications dans la 'Redirection de ports'.
![image](https://github.com/user-attachments/assets/aed4c90a-3497-4898-b87c-6e24f576d0d5)

Pour plus d'amélioration de sécurité, nous allons empêcher les utilisateurs de se connecter avec un mot de passe afin d'utiliser un système de clés.
Pour cela nous allons générer une clée de la manière suivante.
ssh-keygen -t rsa -b 4096 -C "azerty0rslr@gmail.com"
-t rsa : pour le type de clé (rsa ou dsa)
-b 4096 : pour le nombre de bytes (on considère sécurisé au delà de 2000)
-C "azerty0rslr@gmail.com" : adresse mail de contact à qui appartient la clé
On fait 'entrer' dans la partie où la clé sera sauvegardée.
Puis il faut entrer une "passphrase", une phrase à entrer pour utiliser la clé : ici on utilise demodemo
![image](https://github.com/user-attachments/assets/35b54976-2617-4d51-a7c2-92f3553ee071)
On se reconnecte ensuite à notre serveur, puis on créer un dossier à la racine. 
![image](https://github.com/user-attachments/assets/de35d0c1-6d35-403e-8475-d17710c7dfb7)


![image](https://github.com/user-attachments/assets/1d5116ec-e653-40ab-95f9-985e108cc735)
3yy
