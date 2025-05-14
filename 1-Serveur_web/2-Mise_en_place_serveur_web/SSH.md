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
## Sécurisation de la configuration SSH
Désormais nous allons améliorer la sécurité du SSH. Pour commencer nous allons modifier son fichier de configuration de la manière suivante. vim /etc/ssh/sshd_config.  
Nous modifions deux paramètres :  
- Le port que l'on passe au port 5789  
- Le PermitRootLogin que l'on mets en no (pour que personne ne se connecte avec root)  
= ces deux modifications nous permettent une plus grande sécurité.  
![image](https://github.com/user-attachments/assets/ead732f7-5a14-438a-8f4e-0c7c1e370b8f)  
Pour quitter la modification 'echap' et ':x'  
On redémarre désormais SSH de la manière suivante : sudo service ssh restart  
![image](https://github.com/user-attachments/assets/dae17e92-b30d-45a3-a61f-5e7fd8dabec5)  
On retourne désormais sur VirtualBox pour ajouter nos modifications dans la 'Redirection de ports'.  
![image](https://github.com/user-attachments/assets/aed4c90a-3497-4898-b87c-6e24f576d0d5)  

## Connexion avec un système de clés
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
On récupère d'abord la clé publique :  
- on va dans .ssh (cd .shh) puis on ouvre le fichier créé précédement avec la commande vim id_rsa.pub  
![image](https://github.com/user-attachments/assets/5e9a6f1c-eb83-46be-bff0-86633f1c47b6)  
- puis on copie la clé publique avec la commande 5yy  
![image](https://github.com/user-attachments/assets/1d5116ec-e653-40ab-95f9-985e108cc735)  
- enfin on colle cette clé avec la commande p après être revenu dans authorized_keys (pour cela faire :q! pour quitter id_rsa.pub puis faire vim authorized_keys qui créera automatiquement ce fichier et rentrera dedans)  
![image](https://github.com/user-attachments/assets/f09cec53-faef-4fcc-b3e5-558c634335fd)  
Pour quitter ce fichier et le sauvegarder on fait :wq. Ensuite on modifie les autorisations sur le fichier  
![image](https://github.com/user-attachments/assets/f86ac605-6fd1-4aed-a49f-283f9fb85a53)  
Maintenant si on se reconnecte, on ne nous demande plus le mot de passe mais la passphrase.  
![image](https://github.com/user-attachments/assets/62a79a8a-dd87-4469-bff0-580efbf5966d)  
  
On peut maintenant modifier la configuration ssh en faisant :  
sudo vim /etc/ssh/sshd_config  
On trouve la ligne PasswordAuthentication (on peut taper /PasswordAuthentication pour arriver directement sur la ligne), on se mets en mode insertion et on remplace le yes par no. Puis on quitte avec :wq.  
![image](https://github.com/user-attachments/assets/d0593bfd-a499-4623-8a33-5f799c463425)  
Puis je peux redémarrer ssh avec sudo service ssh restart. Je fais exit  
⚠️ ATTENTION à ne pas supprimer id_rsa.pub ni à le renommer sinon on ne peux plus se connecter !  
Une mauvaise configuration du SSH peut nous bloquer du serveur il faut donc faire très attention lorsqu'on le paramètre.  
