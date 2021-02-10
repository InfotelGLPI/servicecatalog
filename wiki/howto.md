# Objectif du document

Il s�agit de d�crire les diff�rentes fonctionnalit�s du plugin Catalogue de service.

# Description g�n�rale

Le plugin catalogue de service permet de rediriger les utilisateurs vers une interface conviviale permettant de les orienter vers la bonne cat�gorisation de leur ticket.

**Nouvelle interface pour l�utilisateur final :**
![sc_interface_helpdesk.png](/uploads/service-catalog/sc_interface_helpdesk.png)

# Installation du plugin


Le plugin est contenu dans un dossier intitul� � **servicecatalog** �.
L�installation sur GLPI se fait en copiant ce dossier dans le r�pertoire � plugins � de GLPI.

Il faut ensuite se connecter sur l�interface de GLPI et aller dans l�interface des plugins � **Configuration > Plugins** �.

![7 D 5734 Ad 1 F 340 F 5836617638481 F 1153](/uploads/service-catalog/7d5734ad1f340f5836617638481f1153.png "7 D 5734 Ad 1 F 340 F 5836617638481 F 1153")

Ensuite appuyer sur le bouton � **Installer** � pr�s du nom du plugin, puis � **Activer** �.

Le plugin est alors en �tat de fonctionner sur GLPI et est disponible dans le menu � **Plugins** �.

# Gestion des droits

Diff�rents droits sont � d�finir pour l�utilisation du plugin :

Il suffit pour cela, d'aller dans le menu � **Administration > Profils** �, de s�lectionner le profil que l'on souhaite modifier, puis dans l'onglet � **Catalogue de service** � d�finir les options que l�on souhaite.

![sc-profile-helpdesk.png](/uploads/service-catalog/sc-profile-helpdesk.png)

- **Catalogue de service** : cette partie sert pour la configuration du plugin, il est donc possible de refuser l�acc�s � la configuration du plugin ou de l�autoriser en pr�cisant l�option � **Mettre � jour** �, � **Cr�er** � et � **Purger** �.
- **Liens utiles** : cette partie permet de donner les droits sur la configuration des liens utiles qui seront d�taill�s par la suite.
- **Utiliser la v�rification de la cat�gorisation des tickets** : cette partie sera d�taill�e par la suite, les utilisateurs qui auront ce droit verront une [popup](#recategorisation) sur tous les nouveaux tickets leur demandant de confirmer la cat�gorie du ticket
- **Mettre � jour la vue par d�faut** : ce droit permet de donner la possibilit� de mettre � jour la vue par d�faut.
- **Mettre � jour sa vue** : ce droit permet de mettre � jour sa propre vue.
- **Redimensionner les tableaux de bord** : ce droit permet de redimensionner les widgets du dashboard.
- **Favoris** : ces droits permettent de visualiser et/ou de cr�er des cat�gories favorites.
- **Utiliser le plugin** : ce droit permet la visualisation du catalogue de service pour les utilisateurs de ce profil.


**Exemple de  droits � configurer pour un profil qui aura uniquement acc�s au catalogue de service depuis l'interface simplifi�e :**

![profile_user.png](/uploads/service-catalog/profile_user.png)


# Description de l'utilisation du plugin par l'utilisateur final / principe de fonctionnement

## Choix du contexte

Lorsqu'un utilisateur a la visibilit� sur plusieurs entit�s, la premi�re action est la s�lection de l'entit� de destination de cr�ation de ticket.
![Sc Context](/uploads/service-catalog/sc-context.png "Sc Context")

Dans l'interface suivante, une ic�ne "Changer de contexte" permet de revenir � la s�lection de l'entit�

> Vous pouvez bien sur customiser les logos et textes / commentaires dans la configuration du plugin.
{.is-info}

## Choix du type de l�action

Une premi�re interface permet de choisir l�action qu�il veut effectuer, certaines actions sont pr�sentes dans l�interface selon la configuration du plugin, d�autres suivant les droits du profil ou suivant les plugins qui sont activ�s.

-   **Cr�er un incident** : ce choix permet de cr�er un ticket de type incident et permet de choisir la cat�gorie par la suite.
-   **Cr�er une demande** : ce choix permet de cr�er un ticket de type demande et permet de choisir la cat�gorie par la suite.
-   **Voir vos incidents** : cette interface permet d�avoir un raccourci pour visualiser la liste de vos incidents.
-   **Voir vos demandes** : cette interface permet d�avoir un raccourci pour visualiser la liste de vos demandes.
-   **Voir vos tickets** : cette interface permet d�avoir un raccourci pour visualiser la liste de vos tickets.
-   **Essayer de trouver une solution ?** : ce choix permet d��tre rediriger vers la foire aux questions.
-   **G�rer les validations de ticket** : (Visible lorsque l�utilisateur a un profil de validation de ticket). Cette interface permet d�avoir un raccourci pour visualiser la liste des tickets qui sont en attente de validation de votre part.
-   **G�rer les ressources humaines** : Ce choix permet d��tre redirig� vers le menu de Ressources humaines.
> Visible lorsque le plugin Ressources humaines est activ� et que l�utilisateur a les droits
{.is-warning}
-   **G�rer les badges temporaires** : Cette interface permet d��tre rediriger vers une interface de demande de badge d�acc�s.
> Visible lorsque le plugin Badges est activ� et que l�utilisateur a les droits
{.is-warning}

**Interface pour le choix de l�action � effectuer :**
![Sc Interface Helpdesk](/uploads/service-catalog/sc_interface_helpdesk.png "Sc Interface Helpdesk")

**Interface avec les plugins pour le choix de l�action :**

![Sc Interface Helpdesk With Plugins](/uploads/service-catalog/sc_interface_helpdesk_with_plugins.png "Sc Interface Helpdesk With Plugins")

## Choix de la cat�gorie

Lorsque l�utilisateur choisit de cr�er soit un incident ou une demande, il sera alors orient� vers la s�lection de la cat�gorie du ticket.

L�interface lui permet donc de naviguer dans l�ensemble de l�arborescence des cat�gories et de revenir en arri�re si besoin.

**Interface de s�lection de la cat�gorie :**

![sc-wrapper.png](/uploads/service-catalog/sc-thumbnail.png)


Lors de la s�lection d�une cat�gorie, le d�tail de la cat�gorie apparait avec toutes les sous-cat�gories. Lors du choix de la cat�gorie, l�utilisateur sera alors redirig� vers la cr�ation de ticket.

Ainsi que les diff�rents articles de la FAQ existants li�s � cette cat�gorie.

Lors de la s�lection d�une cat�gorie qui contient plusieurs sous-cat�gories, lors du clic sur la cat�gorie, une nouvelle interface apparaitra avec toutes les sous-cat�gories.

## Recherche de la cat�gorie


De plus, il aura acc�s � un moteur de recherche qui lui permettra de directement choisir la bonne cat�gorie de ticket ainsi qu�aux articles de la FAQ li�s � la cat�gorie choisie.

![Sc Interface Category](/uploads/service-catalog/sc_interface_category.png "Sc Interface Category")

## Cr�ation du ticket

Une fois la cat�gorie choisie, l�utilisateur sera donc redirig� vers le formulaire de cr�ation de ticket.

Si lors de la configuration du plugin, vous avez choisi � **Montrer les autres informations par d�faut � la cr�ation du ticket** �, tous les champs du ticket seront affich�s.

Dans le cas contraire, seulement les champs obligatoires seront affich�s par d�faut, les champs restants seront visibles en cliquant sur � **Autres informations** �.

**Cr�ation d�un ticket :**
![Sc Create Ticket](/uploads/service-catalog/sc-create-ticket.png "Sc Create Ticket")

## Interface des liens utiles


Si des liens sont visibles par un des groupes dont je fais partie, le bouton � **Liens utiles** � apparait sur la page d�accueil.

**Page d�accueil avec le bouton � Liens utiles � :**
![Links](/uploads/service-catalog/links.png "Links")

Lors de la s�lection � **Liens utiles** �, vous �tes redirig�s vers l�ensemble des liens utiles qui sont pr�sents.

Dans l�exemple ci-dessous, deux liens sont pr�sents :

-   SITE 1 qui est configur� sans ic�ne et un commentaire d�informations compl�mentaires
-   SITE 2 qui est configur� avec une image comme on peut le voir dans l�image ci-dessous.

**Liste des liens utiles :**
![List Links](/uploads/service-catalog/list-links.png "List Links")

Lorsqu�un lien est configur� avec le param�tre � **Afficher sur la page d�accueil** �, le lien sera visible au m�me niveau que le bouton � Liens utiles �.

**Bouton avec redirection vers le site1 :**
![Link 1](/uploads/service-catalog/link-1.png "Link 1")


# Configuration du plugin


> Avant toute utilisation du plugin, une configuration du plugin est requise.
{.is-info}

## Onglet Configuration

### Configuration de l'affichage

![sc-setup-display.png](/uploads/service-catalog/sc-setup-display.png)

Il est possible de configurer l'affichage du catalogue de service selon plusieurs param�tres : 

- **Disposition** : Il est possible de choisir la disposition / th�me g�n�ral des vignettes li�es aux cat�gories. Il existe cinq dispositions diff�rentes.

- **sly**

![sc-sly-.png](/uploads/service-catalog/sly.png)
Possibilit� de "slider" la liste sur les c�t�s.

- **wrapper-sly**

![sc-wrappersly.png](/uploads/service-catalog/wrappersly.png)

- **wrapper**

![sc-wrapper.png](/uploads/service-catalog/wrapper.png)

- **thumbnail**

![sc-wrapper.png](/uploads/service-catalog/sc-thumbnail.png)

- **thumbnail_wrapper**

![sc-wrapper.png](/uploads/service-catalog/sc-thumbnail-wrapper.png)

{.is-warning} 
- **Couleur g�n�rale** : Il est possible de choisir la couleur principale de l'interface du catalogue de service.
- **Couleur secondaire (hover)** : Il est possible de choisir la couleur secondaire li�e aux boutons de l'interface.
> TODO Infotel - d�crire l'option : Taille des cat�gories
{.is-warning}
- **Supprimer la barre de menu pour l'utilisateur final** : Cette option permet de supprimer la barre de menu pour l'utilisateur final.
- **Supprimer le pied de page pour l'utilisateur final** : Cette option permet de supprimer le pied de page de l'interface pour l'utilisateur final.
- **Bouton de redirection vers l'accueil de Service catalogue** : Il est possible de rediriger le lien du bouton "Accueil" pr�sent dans la barre de menu vers l'accueil du plugin. 
- **Supprimer le choix de langue pour l'utilisateur final** : Cette option permet de supprimer le bouton de choix de langue pour l'utilisateur final. (*)
- **Supprimer le bouton d'aide pour l'utilisateur final** : Cette option supprime le bouton d'aide dans l'interface pour l'utilisateur final. (*)
- **Supprimer le bouton de recherches sauvegard�es pour l'utilisateur final** : Cette option supprime le bouton de recherches sauvegard�es pr�sent dans l'interface pour l'utilisateur final. (*)
- **Supprimer le bouton de pr�f�rences pour l'utilisateur final** : Cette option supprime le bouton de pr�f�rences pr�sent dans l'interface pour l'utilisateur final. (*)
- **Supprimer le bouton de deconnexion pour l'utilisateur final** : Cette option supprime le bouton de deconnexion pr�sent dans l'interface pour l'utilisateur final. (*)
- **Afficher les articles de la FAQ Disponibles** : Il est possible d'afficher ou non les articles de la FAQ disponibles li�s aux cat�gories.
- **Montrer le lien vers les d�tails de la cat�gorie** : Permet d'afficher un lien vers des d�tails compl�mentaires (configurable sur une cat�gorie).
- **Afficher le logo dans les d�tails des cat�gories** : Il est possible de choisir d'afficher ou non le logo des cat�gories.
- **Ic�ne par d�faut pour les cat�gories** : Il est possible de configurer le logo par d�faut pour les cat�gories o� aucun logo n'a �t� d�fini.
- **Icone Retour** : Il est possible de choisir l'icone du bouton retour pr�sent dans la barre de navigation lors du choix de la cat�gorie du ticket.

(*) *barre de menu, en haut � droite*


### Configuration du plugin

![sc-setup-comment.png](/uploads/service-catalog/sc-setup-comment.png)

- **Activer les mots cl�s** : Il est possible d'afficher dans les vignettes des cat�gories les mots cl�s / commentaires pr�d�finis, visible ou non pour l'utilisateur final et de les utiliser dans le moteur de recherche.
- **Activer la restriction par groupe** : Il est possible de choisir si les groupes auront acc�s aux cat�gories enfants m�me si les parents de ces enfants leurs sont restreints.
- **Activer la r�cursivit� de la restriction par groupe** : m�me chose que pour la restriction par groupe, mais cela s'applique aux enfants des enfants li�s aux parents.



### Tableau de bord

Afin de guider l�utilisateur pour la cr�ation du ticket, diff�rents commentaires sont � remplir dans cette configuration, ces commentaires permettent d�aiguiller l�utilisateur.

![sc-dashboard-config.png](/uploads/service-catalog/sc-dashboard-config.png)

- **Niveau de cat�gories � afficher** : Il est possible de choisir dans les widgets listant les tickets en cours / � clore sur l'interface simplifi�e le niveau de l'arborescence des cat�gories affich�es : ici 2 (Parent > enfant) : 

![levelcat.png](/uploads/service-catalog/levelcat.png)

- **Voir le top incidents / demandes** : Il est possible d'afficher ou non la liste des cat�gories les plus utilis�es

> Uniquement en mode thumbnail / thumbnail_wrapper
{.is-warning}



### Barre de recherche du plugin

![sc-searchbar-config.png](/uploads/service-catalog/sc-searchbar-config.png)

Afin de guider l'utilisateur dans sa recherche, il est possible d'ins�rer un commentaire dans les barres de recherche pour aider l'utilisateur final.

![sc-searchbar-exemple.png](/uploads/service-catalog/sc-searchbar-exemple.png) 


### Formulaire

Il est possible de personnaliser certains labels du formulaire de cr�ation de ticket. 

![sc-form-config.png](/uploads/service-catalog/sc-form-config.png)

- ~~**Plus utilis� - Remplacer le formulaire de cr�ation de ticket** : Il est possible de choisir si le plugin remplace le formulaire de cr�ation de ticket.~~
- **Remplacer le formulaire de mise � jour de ticket** : Il est possible de choisir si le plugin remplace le formulaire de ticket standard de GLPI par celui du plugin.
- **Montrer les autres informations par d�faut � la cr�ation du ticket** : Cette option permet de choisir lors de la cr�ation du ticket d�afficher tous les champs du ticket si elle est activ�e. 
    Dans le cas contraire, elle affiche seulement les champs obligatoires � la cr�ation du ticket. Les champs qui ne sont pas obligatoires seront affich�s en cliquant sur le lien � Autres informations �.
- **Titre de la liste d�roulante des observateurs** : Il est possible de changer le titre de la liste d�roulante des observateurs.
- **Montrer le champ Num�ro de t�l�phone � la cr�ation du ticket** : Il est possible d'afficher un champ permettant de choisi un num�ro pour joindre l'utilisateur - les informations saisies seront ajout�es � la fin de la description du ticket.

![telephone_form.png](/uploads/service-catalog/telephone_form.png)

- **Titre du champ Num�ro de t�l�phone** : Permet de d�finir le titre du bloc T�l�phone : dans l'exemple ci-dessus : "Comment vous joindre ?"

- **Titre du ticket** : Il est possible de changer le label au dessus du champ de renseignement du titre du ticket.
- **Titre de la description du ticket** : Il est possible de changer le label au dessus du champ de renseignement de la description du ticket.
- **Titre du bouton de validation du ticket** : Il est possible de changer le titre du bouton de validation dans le formulaire de cr�ation de ticket.
- **Masquer le suivi par mail** : Permet de supprimer visuellement les notifications de suivi par mail des acteurs concern�s du ticket cr��.
> TODO Infotel - d�crire l'option : Permettre l'ajout de demandeurs sur le ticket
{.is-warning}

> TODO Infotel - d�crire l'option : Permettre l'ajout d'observateurs sur le ticket
{.is-warning}
- **Redirection vers la s�lection des entit�s apr�s la cr�ation d'un ticket** : il est possible de configurer la redirection vers l'�cran des entit�s apr�s la cr�ation du ticket (Ecran du choix du contexte du ticket).

> TODO Infotel - d�crire l'option : Utiliser l'onglet tous par d�faut dans les tickets
{.is-warning}


### Configuration pour la mise � jour des informations personnelles de l'utilisateur

![sc-form-personal.png](/uploads/service-catalog/sc-form-personal.png)

> TODO Infotel - d�crire l'option : Gabarit de ticket associ� � la mise � jour des informations personnelles de l'utilisateur
{.is-warning}


> Il faut au pr�alable avoir activ� l'option � **Voir les informations personnelles lors de la cr�ation d'un ticket (interface simplifi�e)** �, disponible dans le menu Configuration g�n�rale, onglet Assistance.
{.is-warning}

Une fois l'option activ�e :  

- un nouveau widget est disponible dans l'interface de cr�ation de ticket de service catalogue.
- Un nouvel encadrement permet de v�rifier ses informations personnelles avant la soumission d'un ticket.

Si les informations personnelles ne sont plus d'actualit�s, cliquer sur "�diter". Un formulaire reprends les informations existantes, autorise la modification et soumet un ticket sur les champs � modifier.


## Onglet widgets

![config_widgets.png](/uploads/service-catalog/config_widgets.png)

- **Widget de bienvenue** : Personnalisation du titre du message et du commentaire de bienvenue pour l'�cran d'interface de cr�ation de ticket du service catalogue.


- **Widget d'incidents** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de cr�ation d'un ticket de type incident. 


- **Widget de demandes** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de cr�ation d'un ticket de type demande.


- **Widget de la liste des tickets** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de la liste des tickets en cours concernant l'utilisateur connect�. 


- **Widget de la liste des incidents** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de la liste des tickets en cours de type incident concernant l'utilisateur connect�. 


- **Widget de la liste des demandes** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de la liste des tickets en cours de type demande concernant l'utilisateur connect�.

- **Widget de la Faq** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de la Faq.

- **Widget de la validation des tickets** : Personnalisation du titre, commentaire, l'image ou l'icone du widget des tickets en cours de validation concernant l'utilisateur connect�.


- **Widget de mise � jour des informations personnelles** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de mise � jour des informations personnelles.

> Il faut au pr�alable avoir activ� l'option "Voir les informations perrsonnelles lors de la cr�ation d'un ticket (interface simplifi�e), disponible dans le menu Configuration g�n�rale de GLPI, onglet Assistance.
{.is-warning}

- **Widget de la liste des liens utiles** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de la liste des liens utiles. N�cessite l'ajout de liens utiles.


- **Widget de r�servation** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de r�servation de mat�riel.

- **Widget de contexte** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de contexte de la liste des entit�s.

- **Widget de la base documentaire** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de la base documentaire.

![config_widget_incidents.png](/uploads/service-catalog/config_widget_incidents.png)

> Pour chaque widget, il est possible selon le widget de choisir si l'on souhaite afficher le bouton dans le menu d'interface de cr�ation de ticket de l'interface service catalogue, et  d'afficher l'icone sous forme de miniature raccourcie dans le menu sup�rieur
{.is-info}

![menu_superieur.png](/uploads/service-catalog/menu_superieur.png)

- **Afficher le bouton de cr�ation d'incident / d'une demande / de la liste des tickets / de la liste des incidents / de la liste des demandes** : Il est possible de choisir les diff�rents boutons que l'on souhaite afficher sur l'interface centrale.

- **Afficher dans le menu sup�rieur** : Il est possible de choisir d'afficher l'icone sous forme de miniature raccourcie dans le menu sup�rieur lors du choix de la cat�gorie de ticket.

## Onglet Ordonnancement des cat�gories de ticket

![Sc Category Order](/uploads/service-catalog/sc-category-order.png "Sc Category Order")

Par d�faut lors de l�affichage des diff�rentes cat�gories de niveau 1, les cat�gories sont tri�es sur le nom.

Il est possible d�ordonnancer les cat�gories par d�ordre d�importance dans cette interface.

> Il faut que les cat�gories soient visibles dans l'interface simplifi�e pour pouvoir les ordonnancer 
{.is-warning}

L�ordonnancement des cat�gories s�effectue suivant le type du ticket et l�entit�.

Dans cette interface lors de la premi�re consultation, il faut tout d�abord charger toutes les cat�gories depuis GLPI via le lien � **Charger les cat�gories depuis GLPI** �. La liste des cat�gories apparaitra, pour les ordonnancer il vous suffit de les d�placer.

Lors de l�ajout de nouvelles cat�gories dans GLPI, pour ne pas perdre tout ordonnancement d�j� effectu�, vous pouvez ajouter seulement les nouvelles cat�gories via le lien � **Ajouter des nouvelles cat�gories depuis GLPI** �.

> Il faut configurer ce tri pour les deux types de tickets. 
{.is-warning}

## Onglet Ordonnancement des champs de tickets

![sc-orderingfields.png](/uploads/service-catalog/sc-orderingfields.png)

Par simple glisser/d�poser, Il est possible d'ordonner les champs du formulaire de cr�ation de ticket. 

## Onglet Ordonnancement des boutons du widget principal

> TODO Infotel - Ajouter une image
{.is-warning}

Par simple glisser/d�poser, Il est possible d'ordonner les boutons pr�sents dans le widget principal


## Onglet Traductions

Comme pour les diff�rents intitul�s de GLPI, il est possible de proposer une traduction pour les titres et commentaires du plugin.

![Sc Setup Translate](/uploads/service-catalog/sc-setup-translate.png "Sc Setup Translate")

## Onglet Liens utiles

Cette partie permet de configurer diff�rents liens pour permettre � l�utilisateur d�avoir une interface avec des raccourcis vers diff�rentes url.

Lors de l�ajout d�un lien utile, ces champs sont pr�sents :

-   **Nom** du lien qui sera utilis� comme titre dans l�interface de redirection.
-   **Image** il est possible de changer l�ic�ne pour l�utilisateur final.
-   **URL** qui permet de rediriger l�utilisateur vers un site par le biais de cette url.
-   **Ouvrir dans une nouvelle fen�tre** : ce param�tre permet de configurer lors du clic de l�utilisateur sur le lien si la redirection se passe dans la m�me fen�tre ou dans une nouvelle fen�tre.
-   **Afficher sur la page d�accueil** : ce param�tre s�il est activ� permet d�avoir ce raccourci sur la page d�accueil.
-   **Commentaires** : informations compl�mentaires sur le lien qui est visible pour l�utilisateur final.

![Sc Links](/uploads/service-catalog/sc_links.png "Sc Links")

Il sera aussi possible de traduire les diff�rents champs qui sont visibles pour l�utilisateur final, un onglet est d�di� � cette configuration.

Pour limiter la visualisation de ces liens, un onglet � **Droit des groupes** � est pr�sent.

Il est possible d�ajouter diff�rents groupes qui seront autoris�s � voir les liens. Seules les personnes qui feront partie de ces groupes verront le lien.

**Configuration des groupes ayant acc�s au lien :**
![Sc Setup Translate Group](/uploads/service-catalog/sc_setup_translate_group.png "Sc Setup Translate Group")


# Configuration des entit�s


## Onglet Catalogue de service

Pour chaque entit� de GLPI, il sera possible d'ajouter un logo et des commentaires compl�mentaires.

Ces informations seront visibles pour les utilisateurs lorsqu'ils devront choisir l'entit� de destination du ticket.
![Sc Entity](/uploads/service-catalog/sc-entity.png "Sc Entity")

> Il sera possible de d�finir des contacts pour l'entit�. Ces contacts seront visibles dans un widget "Contactez-nous".
{.is-info}

## Onglet Dashboard Catalogue de service 

Il est possible de personnaliser la vue par d�faut de l'utilisateur final et de choisir les widgets qui seront affich�s.

![Sc Dashboard Interface](/uploads/service-catalog/sc-dashboard-interface.png "Sc Dashboard Interface")

**Diff�rents widgets sont disponibles :**

- **Widget d'affichage du titre** : ce widget permet d'afficher du texte personnalis� par le biais du champ "Commentaire du message" dans la configuration du plugin.

- **Widget d'affichage des statistiques** : Ce module permet d'ajouter des statistiques sur le suivi des tickets.

- **Widget d'affichage des contacts** : Ce widget permet d'ajouter les coordonn�es de contacts qui sont configur�s dans les entit�s.

- **Vos incidents en cours** : Liste de vos incidents en cours.

- **Vos demandes en cours** : Liste de vos demandes en cours.

- **Vos tickets en cours** : Liste de l'ensemble des tickets en cours.

- **Vos tickets � clore** : Liste de vos tickets � clore.

- **Vos tickets en cours par statut** : Ce widget permet d'afficher un graphe en forme de camembert de l'ensemble de vos tickets par statut.

- **Alertes r�seau** : Il permet d�indiquer � l�utilisateur un �ventuel probl�me comme une alerte r�seau pour ainsi �viter la cr�ation de ticket sur ce m�me probl�me. Pour ajouter une alerte, il faut cr�er une note GLPI et la configurer en tant qu'alerte dans l'onglet "Alertes dashboard". (*)

- **Maintenances planifi�es pr�vues** : Au m�me titre que "Alertes r�seau", ce widget permet d'indiquer � l'utilisateur une maintenance planifi�e. Pour le configurer, il faut r�aliser les m�mes �tapes que pr�c�demment, en indiquant "Maintenance planifi�e pr�vue" dans la configuration de la note. (*)

- **Informations** : Ce widget permet d'indiquer diff�rentes informations. (*)

> (*) Visible lorsque le plugin MyDashboard est activ�. 
{.is-warning}


# Configuration des cat�gories

## Onglet Catalogue de service 

![Sc Category Detail](/uploads/service-catalog/sc_category_detail.png "Sc Category Detail")

Pour chaque cat�gorie de GLPI, il sera possible d�ajouter un logo pour la repr�senter dans l�interface du catalogue de service.

Il sera possible d�y ajouter un commentaire pour d�crire cette cat�gorie aux utilisateurs.

Ainsi que diff�rents mots cl�s qui permettront par la suite de retrouver cette cat�gorie par le biais d�une barre de recherche.

Il sera aussi possible d'indiquer diff�rentes informations compl�mentaires sur la cat�gorie.

Il suffit pour cela, d'aller dans le menu � **Configuration > Intitul�s > Cat�gories de ticket** �, de s�lectionner la cat�gorie que l'on souhaite modifier.

Lors de l�ajout du logo de la cat�gorie, il est conseill� d�utiliser un fichier png de taille 145px sur 75px. Dans le cas contraire, l�image sera redimensionn�e en respectant cette taille.

## Onglet Favoris

Si l'on souhaite avoir des cat�gories acc�ssibles plus facilement dans l'interface, il sera possible de param�trer des favoris.

Apr�s avoir s�l�ctionn� un profil (Administration->Profils) auquel vous voulez activer l'utilisation de favoris, une nouvelle ligne "Favoris" fait son apparition dans l'onglet Catalogue de service afin de g�rer les droits d'acc�s, de modifications et de suppressions des favoris.

![sc-favorites-add-rights.png](/uploads/service-catalog/sc-favorites-add-rights.png) 

L'administrateur pourra choisir les favoris qu'il souhaite rendre acc�ssible � une entit�, un groupe, profil ou utilisateur particulier (ou plusieurs des cas cit�s). 

Pour se faire, la cr�ation d'un favori se fait dans l'onglet "intitul�s" dans le menu Configuration,
puis choisir "cat�gories de ticket".

Il faut s�l�ctionner une cat�gorie qui n'est pas niveau 1 et se rendre dans l'onglet favoris.

![sc-favorites-admin-add.png](/uploads/service-catalog/sc-favorites-admin-add.png)

La cat�gorie ITIL li�e est celle ou l'on souhaite afficher le favori. La visibilit� permet de choisir qui peut acc�der aux favoris.

L'utilisateur pourra �galement choisir ses propres favoris en plus de ceux qui seront configur�s par l'administrateur (� condition qu'il est les droits). 

Note : Il faut se placer dans les incidents ou les demandes pour voir appara�tre le menu de gestion des favoris utilistaurs.

![sc-nav-fav.png](/uploads/service-catalog/sc-nav-fav.png)

![sc-add-favorites-user.png](/uploads/service-catalog/sc-add-favorites-user.png)

Il pourra de la m�me mani�re choisir dans quelles cat�gories il souhaite les ajouter, supprimer ceux qu'il aura cr�� pour lui et les trier.


# Options compl�mentaires et informations diverses

## Modification du formulaire de cr�ation de ticket pour l'interface standard ##

En plus des champs d�j� pr�sents dans l'interface simplifi�e pour le formulaire de cr�ation de ticket, il est possible d'ajouter 3 champs en fonction du gabarit de ticket : 
-   Impact
-   Temps de r�solution
-   Demande de validation

La configuration s'effectue dans un nouvel onglet dans chaque gabarit de ticket : 
![Sc Tickettemplate](/uploads/service-catalog/sc-tickettemplate.png "Sc Tickettemplate")

Dans l'interface du ticket, les champs seront affich�s de cette fa�on :
![Sc Tickettemplate Ticket](/uploads/service-catalog/sc-tickettemplate-ticket.png "Sc Tickettemplate Ticket")

## <a name="recategorisation"></a>Re-cat�gorisation 

Cette fonctionnalit� permet de proposer la re-cat�gorisation des tickets lors de leur �dition cot� interface compl�te � ceci afin de requalifier si besoin le ticket et de v�rifier les cat�gories choisies par les utilisateurs.

![52 B 077 Cafdd 78 B 3362385611 De 8 Cd 777](/uploads/service-catalog/52b077cafdd78b3362385611de8cd777.png "52 B 077 Cafdd 78 B 3362385611 De 8 Cd 777")

Cette pop-up est affich�e lors de la premi�re consultation du ticket. Lors de la validation ou du changement de la cat�gorie via cette pop-up, la pop-up ne s�affichera pas lors des prochaines �ditions du ticket.


## Utilisation avec le plugin Metademands

Le plugin Service Catalog est utilisable avec le plugin Metademands :

https://github.com/InfotelGLPI/metademands

Il suffit de modifier la configuration du plugin Metademands : 

**Activer la transformation d'un ticket en m�ta-demande**


Ceci vous permettra de lier une cat�gorie � un formulaire Metademande et donc de rediriger l'utilisateur lors de la s�lection de la cat�gorie depuis Service Catalog. 

## Utilisation avec le plugin Formcreator

Dans l�archive du plugin ServiceCatalog, vous avez un dossier **plugins** dans lequel vous avez un dossier **formcreator**.

A l�int�rieur se trouve un fichier *servicecatalog.class.php* qu�il faut placer dans l�arborescence du plugin formcreator (dans le dossier **inc**).

A partir de ce moment-l� vous aurez un onglet suppl�mentaire � Catalogue de Service � depuis la configuration de votre formulaire Formcreator.

Ceci vous permettra de lier une cat�gorie � un formulaire FormCreator � une cat�gorie de ticket. 
