### Titre :  Role du controller dans une architecture MV


###  Objectif pédagogique

#### A l'isssue de ce chapitre vous sere capable :
##### - Découvrir la notion de MVC
##### - Définir le role du controlleur dans l'architecture MVC
##### - Tester son application

### 1. L'architecture MVC
### 2. Role du controlleur
### 3. Structure d'un projet MVC

### A retenir


## 1.  Architecture MVC (Modele-Vue-Contrôleur)

####  Il s'agit d'abord d'un acronyme, signifiant "**Model View Controller**", ou "Modèle Vue Contrôleur" en français.

#### Il s'agit surtout d'une **structure** que nous donnons à nos projets pour **séparer clairement les principaux composants** de notre application.

#### En utilisant une **structure MVC**, nous allons **séparer** les requêtes en **base de données** de notre **code HTML** et de toute "l'**intelligence**" de l'application.

#### En d'autres termes, l'architecture _Modèle/Vue/Contrôleur_ (MVC) est une façon d'organiser une interface graphique d'un programme. Elle consiste à distinguer trois entités distinctes qui sont, le _modèle_, la _vue_ et le _contrôleur_ ayant chacun un rôle précis dans l'interface.

#### L'organisation globale d'une interface graphique est souvent délicate. Bien que la façon MVC d'organiser une interface ne soit pas la solution miracle, elle fournit souvent une première approche qui peut ensuite être adaptée. Elle offre aussi un cadre pour structurer une application.

#### Dans l'architecture MVC, les rôles des trois entités sont les suivants.

#### -   modèle : données (accès et mise à jour)
#### -   vue : interface utilisateur (entrées et sorties)
#### -   contrôleur : gestion des événements et synchronisation

### Le routeur

#### Dans la structure MVC, un seul et unique fichier est le point d'entrée de l'application, quelle que soit la page affichée. Il est systématiquement appelé, et envoie la demande au bon contrôleur. Il est chargé de trouver le bon chemin pour que l'utilisateur récupère la bonne page, d'où le nom de routeur.

#### Voici un schéma qui récapitule tout ceci:
![[d538ebe865ce5e6faae82369dcdbc680.jpeg]]

### 2. Role du controleur

#### Le rôle du contrôleur  peut se traduire de la manière suivante:

##### Le contrôleur est chargé de la synchronisation du modèle et de la vue. Il reçoit tous les événements de l'utilisateur et enclenche les actions à effectuer. Si une action nécessite un changement des données, le contrôleur demande la modification des données au modèle et ensuite avertit la vue que les données ont changé pour que celle-ci se mette à jour. Certains événements de l'utilisateur ne concerne pas les données mais la vue. Dans ce cas, le contrôleur demande à la vue de se modifier.

##### Dans le cas d'une base de données des emplois du temps. Une action de l'utilisateur peut être l'entrée (saisie) d'un nouveau cours. Le contrôleur ajoute ce cours au modèle et demande sa prise en compte par la vue. Une action de l'utilisateur peut aussi être de sélectionner une nouvelle personne pour visualiser tous ses cours. Ceci me modifie pas la base des cours mais nécessite simplement que la vue s'adapte et offre à l'utilisateur une vision des cours de cette personne.

##### Le contrôleur est souvent scindé en plusieurs parties dont chacune reçoit les événements d'une partie des composants. En effet si un même objet reçoit les événements de tous les composants, il lui faut déterminer quelle est l'origine de chaque événement. Ce tri des événements peut s'avérer fastidieuse et peut conduire à un code pas très élégant (un énorme switch). C'est pour éviter ce problème que le contrôleur est réparti en plusieurs objets.  

##### De façon factuelle, lorsqu'un client ouvre son navigateur internet, et qu'il entre une adresse du site internet qu'il veut consulter sur la barre d'adresse, sans le savoir, il fait appelle au contrôleur. Le contrôleur est assimilable au chef d'orchestre dans la mesure où c'est lui qui dirige les opérations nécessaires pour retrouver ou pas la ressource demandée. Une fois contacté, le contrôleur se charge d'appeler le modèle qui est l'entité de l'architecture mvc chargé de dialoguer avec la base de données pour retourner au contrôleur enfin les données sollicitées. Ensuite, le contrôleur affiche les données provenant du modèle dans la troisième entité de l'architecture mvc qui n'est autre que la Vue. La vue représente tout ce qu'il y a à afficher dans le navigateur en réponse à la requête entrée au début par le client dans le navigateur web. Il peut s'agir d'une simple page web, d'un formulaire html etc.


### 3. Structure d'un projet MVC

![[structureprojetMVC.jpeg]]

###### Voici l'utilité des différents dossiers et fichiers

-   **.htaccess et index.php** : ces fichiers seront notre routeur
-   **app** : ce dossier contiendra le coeur de l'application
-   **controllers** : contiendra, comme son nom l'indique, les contrôleurs, dont le nom commencera par une majuscule, par convention.
-   **models** : contiendra nos modèles, leur nom commencera également par une majuscule
-   **views** : contiendra nos fichiers de vues, dans des dossiers, un dossier par contrôleur.

## Le point d'entrée : le routeur

###### Comme indiqué précédemment, le point d'entrée de l'application  le **routeur**.

###### Il s'agit "tout simplement" de notre fichier **index.php** situé à la **racine publique de notre projet**.

###### Ce routeur va nous servir à identifier quel contrôleur doit être utilisé pour générer la page demandée.

##### Exemple de routeur simple, qui comprend les adresses comme ci-dessous.

```http
http://url_du_site/controleur/methode
```

###### Cette url permettra à notre routeur de comprendre qu'il doît pointer vers le contrôleur mentionné en premier paramètre et la méthode de ce contrôleur mentionnée en deuxième paramètre.

## A retenir 

####  1. Lorsqu’un projet augmente, le besoin de s’organiser et de permettre plus de réutilisabilité et de lisibilité demande une certaine méthode. MVC = Modèle Vue Controleur peut être une solution intéressante.

#### 2. L'architecture qui constitue une façon d'organiser une interface graphique d'un programme permet de  distinguer trois entités distinctes ayant chacun un rôle précis dans l'interface, à savoir : le _modèle_, la _vue_ et le _contrôleur_ .

#### 3. Le contrôleur est chargé de la synchronisation du modèle et de la vue. Il reçoit tous les événements de l'utilisateur et enclenche les actions à effectuer. 
