# Guide d'installation : Windows 11 sur PC non compatible

Ce tutoriel explique étape par étape l'installation et la configuration de Windows 11 sur un ordinateur qui ne répond pas aux exigences matérielles officielles de Microsoft. 

L'objectif de ce guide est de permettre à n'importe qui de donner une seconde vie à un ancien ordinateur en contournant facilement ces restrictions à l'aide de l'outil **Rufus**.

---

## Sommaire
- [1. Téléchargement de l'ISO officiel de Windows 11 et de Rufus](#1-Téléchargement-de-l'ISO-officiel-de-Windows-11-et-de-Rufus)
- [2. Configuration de Rufus et activation du bypass des restrictions](#2-Configuration-de-Rufus-et-activation-du-bypass-des-restrictions)
- [3. Démarrage sur la clé USB, formatage et configuration initiale](#3-Démarrage-sur-la-clé-USB,-formatage-et-configuration-initiale)
- [4. Conseils pour l'activation et les clés de produit](#4-Conseils-pour-l'activation-et-les-clés-de-produit)

---

## 1. Téléchargement de l'ISO officiel de Windows 11 et de Rufus

1. Rendez-vous sur la page officielle de Microsoft : [Télécharger Windows 11](https://www.microsoft.com/fr-ca/software-download/windows11).
2. Dans la section **Téléchargement de l'image disque (ISO) de Windows 11**, sélectionnez l'option ISO multi-éditions.

> [!CAUTION]
> **Attention à l'architecture de votre processeur :**
> Assurez-vous de télécharger la version pour processeurs **x64 (64 bits - Intel/AMD)**. Ne choisissez **pas** la version **ARM64**, sous peine d'avoir un message d'erreur d'incompatibilité au démarrage de la clé USB.

![image1](images/01-telecharger-windows.png)

3. Rendez-vous sur le site officiel de Rufus : [rufus.ie](https://rufus.ie/fr/) et téléchargez la dernière version du logiciel.

![image2](images/02-telecharger-rufus.png)

---

## 2. Configuration de Rufus et activation du bypass des restrictions

> [!WARNING]
> **Sauvegarde de la clé USB :**
> L'utilisation de Rufus effacera l'intégralité des données présentes sur la clé USB sélectionnée. Assurez-vous qu'elle ne contient aucun fichier important.

1. Insérez une clé USB d'au moins **8 Go** dans votre ordinateur.
2. Lancez le logiciel **Rufus**.
3. Dans la liste déroulante **Périphérique**, sélectionnez votre clé USB.
4. Dans la section **Type de démarrage**, cliquez sur **SÉLECTION** et choisissez le fichier ISO de Windows 11 (`.iso`) téléchargé précédemment.
5. Sélectionnez le **Schéma de partition** approprié :
   - **GPT** : Si l'ordinateur cible utilise un BIOS récent (**UEFI**).
   - **MBR** : Si l'ordinateur cible est plus ancien et utilise un BIOS hérité (**Legacy/CSM**).

![image3](images/03-options-rufus.png)

6. Cliquez sur **DÉMARRER**.
7. Une fenêtre **Personnalisation de l'installation de Windows** apparaît alors.
8. Cochez impérativement la case :
   - `Supprimer le besoin de 4 Go+ de RAM, Secure Boot et TPM 2.0`
9. Configurez les autres options selon vos préférences (par exemple : sauter l'obligation de créer un compte Microsoft ou désactiver la collecte de données).

![image4](images/04-experience-rufus.png)

10. Validez en cliquant sur **OK** et patientez jusqu'à la fin de la création du support bootable.

## 3. Démarrage sur la clé USB, formatage et configuration initiale

1. Après avoir créé un USB bootable, vous devez d'abord modifier l'ordre de démarrage. La première étape consiste à désactiver Secure Boot :

2. Redémarrez votre appareil et entrer dans le BIOS. la maniere d'entrer dans le bios depend de la marque que vous avez, vous pouvez consulter ce site http://www.auditiait.es/en/list-of-keys-to-access-to-bios/

3. Naviguez vers Sécurité, puis Secure Boot.

4. Accédez à Secure Boot et appuyez sur la touche Entrée pour désactiver.

5. Quitter le BIOS & enregistrer les modifications.

6. Redémarrez votre appareil et entrer entrer dans le Menu de Démarrage. vous pouvez consulter ce site http://www.auditiait.es/en/list-of-keys-to-access-to-bios/ pour savoir quel touche pour rentrer dans le menu de demarrage. 

7. Utilisez les touches flèches pour naviguer vers votre USB bootable et appuyez sur Entrée pour sélectionner.

## 4. Conseils pour l'activation et les clés de produit 

1. Pour faire une installation propre de Windows 11 (ce qui est recommandé lors d'un changement de système), la meilleure méthode est de supprimer toutes les partitions du Disque 0 pour réinstaller sur un disque totalement propre.

2. Obtenir une clé de produit Windows 11
Avant d'en acheter une neuve, vérifiez si vous en avez réellement besoin :

Réutilisation d'une ancienne clé (Windows 7 / 8 / 10) :

Si l'ordinateur tourne actuellement sous Windows 10 et qu'il était déjà activé, l'activation sera automatique dès qu'il sera connecté à Internet après l'installation de Windows 11 (licence numérique liée à la carte mère).

Les anciennes clés de licence physiques de Windows 7 ou 8 collées sur un autocollant sous l'ordinateur portable ou sur le boîtier PC fonctionnent également dans la plupart des cas.

ce que moi j'ai fait: 
Appuyez sur les touches Windows + S pour ouvrir la recherche.Tapez PowerShell, faites un clic droit dessus et choisissez Exécuter en tant d'administrateur.Copiez et collez la commande suivante, puis appuyez sur Entrée :(Get-CimInstance -ClassName SoftwareLicensingService).OA3xOriginalProductKeyLa clé s'affiche à l'écran si elle est enregistrée dans le BIOS/UEFI de votre carte mère.

