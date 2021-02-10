# Objectif du document

Il s’agit de décrire les différentes fonctionnalités du plugin Catalogue de service.

# Description générale

Le plugin catalogue de service permet de rediriger les utilisateurs vers une interface conviviale permettant de les orienter vers la bonne catégorisation de leur ticket.

**Nouvelle interface pour l’utilisateur final :**
![sc_interface_helpdesk.png](/uploads/service-catalog/sc_interface_helpdesk.png)

# Installation du plugin


Le plugin est contenu dans un dossier intitulé « **servicecatalog** ».
L’installation sur GLPI se fait en copiant ce dossier dans le répertoire « plugins » de GLPI.

Il faut ensuite se connecter sur l’interface de GLPI et aller dans l’interface des plugins « **Configuration > Plugins** ».

![7 D 5734 Ad 1 F 340 F 5836617638481 F 1153](/uploads/service-catalog/7d5734ad1f340f5836617638481f1153.png "7 D 5734 Ad 1 F 340 F 5836617638481 F 1153")

Ensuite appuyer sur le bouton « **Installer** » près du nom du plugin, puis « **Activer** ».

Le plugin est alors en état de fonctionner sur GLPI et est disponible dans le menu « **Plugins** ».

# Gestion des droits

Différents droits sont à définir pour l’utilisation du plugin :

Il suffit pour cela, d'aller dans le menu « **Administration > Profils** », de sélectionner le profil que l'on souhaite modifier, puis dans l'onglet « **Catalogue de service** » définir les options que l’on souhaite.

![sc-profile-helpdesk.png](/uploads/service-catalog/sc-profile-helpdesk.png)

- **Catalogue de service** : cette partie sert pour la configuration du plugin, il est donc possible de refuser l’accès à la configuration du plugin ou de l’autoriser en précisant l’option « **Mettre à jour** », « **Créer** » et « **Purger** ».
- **Liens utiles** : cette partie permet de donner les droits sur la configuration des liens utiles qui seront détaillés par la suite.
- **Utiliser la vérification de la catégorisation des tickets** : cette partie sera détaillée par la suite, les utilisateurs qui auront ce droit verront une [popup](#recategorisation) sur tous les nouveaux tickets leur demandant de confirmer la catégorie du ticket
- **Mettre à jour la vue par défaut** : ce droit permet de donner la possibilité de mettre à jour la vue par défaut.
- **Mettre à jour sa vue** : ce droit permet de mettre à jour sa propre vue.
- **Redimensionner les tableaux de bord** : ce droit permet de redimensionner les widgets du dashboard.
- **Favoris** : ces droits permettent de visualiser et/ou de créer des catégories favorites.
- **Utiliser le plugin** : ce droit permet la visualisation du catalogue de service pour les utilisateurs de ce profil.


**Exemple de  droits à configurer pour un profil qui aura uniquement accès au catalogue de service depuis l'interface simplifiée :**

![profile_user.png](/uploads/service-catalog/profile_user.png)


# Description de l'utilisation du plugin par l'utilisateur final / principe de fonctionnement

## Choix du contexte

Lorsqu'un utilisateur a la visibilité sur plusieurs entités, la première action est la sélection de l'entité de destination de création de ticket.
![Sc Context](/uploads/service-catalog/sc-context.png "Sc Context")

Dans l'interface suivante, une icône "Changer de contexte" permet de revenir à la sélection de l'entité

> Vous pouvez bien sur customiser les logos et textes / commentaires dans la configuration du plugin.
{.is-info}

## Choix du type de l’action

Une première interface permet de choisir l’action qu’il veut effectuer, certaines actions sont présentes dans l’interface selon la configuration du plugin, d’autres suivant les droits du profil ou suivant les plugins qui sont activés.

-   **Créer un incident** : ce choix permet de créer un ticket de type incident et permet de choisir la catégorie par la suite.
-   **Créer une demande** : ce choix permet de créer un ticket de type demande et permet de choisir la catégorie par la suite.
-   **Voir vos incidents** : cette interface permet d’avoir un raccourci pour visualiser la liste de vos incidents.
-   **Voir vos demandes** : cette interface permet d’avoir un raccourci pour visualiser la liste de vos demandes.
-   **Voir vos tickets** : cette interface permet d’avoir un raccourci pour visualiser la liste de vos tickets.
-   **Essayer de trouver une solution ?** : ce choix permet d’être rediriger vers la foire aux questions.
-   **Gérer les validations de ticket** : (Visible lorsque l’utilisateur a un profil de validation de ticket). Cette interface permet d’avoir un raccourci pour visualiser la liste des tickets qui sont en attente de validation de votre part.
-   **Gérer les ressources humaines** : Ce choix permet d’être redirigé vers le menu de Ressources humaines.
> Visible lorsque le plugin Ressources humaines est activé et que l’utilisateur a les droits
{.is-warning}
-   **Gérer les badges temporaires** : Cette interface permet d’être rediriger vers une interface de demande de badge d’accès.
> Visible lorsque le plugin Badges est activé et que l’utilisateur a les droits
{.is-warning}

**Interface pour le choix de l’action à effectuer :**
![Sc Interface Helpdesk](/uploads/service-catalog/sc_interface_helpdesk.png "Sc Interface Helpdesk")

**Interface avec les plugins pour le choix de l’action :**

![Sc Interface Helpdesk With Plugins](/uploads/service-catalog/sc_interface_helpdesk_with_plugins.png "Sc Interface Helpdesk With Plugins")

## Choix de la catégorie

Lorsque l’utilisateur choisit de créer soit un incident ou une demande, il sera alors orienté vers la sélection de la catégorie du ticket.

L’interface lui permet donc de naviguer dans l’ensemble de l’arborescence des catégories et de revenir en arrière si besoin.

**Interface de sélection de la catégorie :**

![sc-wrapper.png](/uploads/service-catalog/sc-thumbnail.png)


Lors de la sélection d’une catégorie, le détail de la catégorie apparait avec toutes les sous-catégories. Lors du choix de la catégorie, l’utilisateur sera alors redirigé vers la création de ticket.

Ainsi que les différents articles de la FAQ existants liés à cette catégorie.

Lors de la sélection d’une catégorie qui contient plusieurs sous-catégories, lors du clic sur la catégorie, une nouvelle interface apparaitra avec toutes les sous-catégories.

## Recherche de la catégorie


De plus, il aura accès à un moteur de recherche qui lui permettra de directement choisir la bonne catégorie de ticket ainsi qu’aux articles de la FAQ liés à la catégorie choisie.

![Sc Interface Category](/uploads/service-catalog/sc_interface_category.png "Sc Interface Category")

## Création du ticket

Une fois la catégorie choisie, l’utilisateur sera donc redirigé vers le formulaire de création de ticket.

Si lors de la configuration du plugin, vous avez choisi « **Montrer les autres informations par défaut à la création du ticket** », tous les champs du ticket seront affichés.

Dans le cas contraire, seulement les champs obligatoires seront affichés par défaut, les champs restants seront visibles en cliquant sur « **Autres informations** ».

**Création d’un ticket :**
![Sc Create Ticket](/uploads/service-catalog/sc-create-ticket.png "Sc Create Ticket")

## Interface des liens utiles


Si des liens sont visibles par un des groupes dont je fais partie, le bouton « **Liens utiles** » apparait sur la page d’accueil.

**Page d’accueil avec le bouton « Liens utiles » :**
![Links](/uploads/service-catalog/links.png "Links")

Lors de la sélection « **Liens utiles** », vous êtes redirigés vers l’ensemble des liens utiles qui sont présents.

Dans l’exemple ci-dessous, deux liens sont présents :

-   SITE 1 qui est configuré sans icône et un commentaire d’informations complémentaires
-   SITE 2 qui est configuré avec une image comme on peut le voir dans l’image ci-dessous.

**Liste des liens utiles :**
![List Links](/uploads/service-catalog/list-links.png "List Links")

Lorsqu’un lien est configuré avec le paramètre « **Afficher sur la page d’accueil** », le lien sera visible au même niveau que le bouton « Liens utiles ».

**Bouton avec redirection vers le site1 :**
![Link 1](/uploads/service-catalog/link-1.png "Link 1")


# Configuration du plugin


> Avant toute utilisation du plugin, une configuration du plugin est requise.
{.is-info}

## Onglet Configuration

### Configuration de l'affichage

![sc-setup-display.png](/uploads/service-catalog/sc-setup-display.png)

Il est possible de configurer l'affichage du catalogue de service selon plusieurs paramètres : 

- **Disposition** : Il est possible de choisir la disposition / thème général des vignettes liées aux catégories. Il existe cinq dispositions différentes.

- **sly**

![sc-sly-.png](/uploads/service-catalog/sly.png)
Possibilité de "slider" la liste sur les côtés.

- **wrapper-sly**

![sc-wrappersly.png](/uploads/service-catalog/wrappersly.png)

- **wrapper**

![sc-wrapper.png](/uploads/service-catalog/wrapper.png)

- **thumbnail**

![sc-wrapper.png](/uploads/service-catalog/sc-thumbnail.png)

- **thumbnail_wrapper**

![sc-wrapper.png](/uploads/service-catalog/sc-thumbnail-wrapper.png)

{.is-warning} 
- **Couleur générale** : Il est possible de choisir la couleur principale de l'interface du catalogue de service.
- **Couleur secondaire (hover)** : Il est possible de choisir la couleur secondaire liée aux boutons de l'interface.
> TODO Infotel - décrire l'option : Taille des catégories
{.is-warning}
- **Supprimer la barre de menu pour l'utilisateur final** : Cette option permet de supprimer la barre de menu pour l'utilisateur final.
- **Supprimer le pied de page pour l'utilisateur final** : Cette option permet de supprimer le pied de page de l'interface pour l'utilisateur final.
- **Bouton de redirection vers l'accueil de Service catalogue** : Il est possible de rediriger le lien du bouton "Accueil" présent dans la barre de menu vers l'accueil du plugin. 
- **Supprimer le choix de langue pour l'utilisateur final** : Cette option permet de supprimer le bouton de choix de langue pour l'utilisateur final. (*)
- **Supprimer le bouton d'aide pour l'utilisateur final** : Cette option supprime le bouton d'aide dans l'interface pour l'utilisateur final. (*)
- **Supprimer le bouton de recherches sauvegardées pour l'utilisateur final** : Cette option supprime le bouton de recherches sauvegardées présent dans l'interface pour l'utilisateur final. (*)
- **Supprimer le bouton de préférences pour l'utilisateur final** : Cette option supprime le bouton de préférences présent dans l'interface pour l'utilisateur final. (*)
- **Supprimer le bouton de deconnexion pour l'utilisateur final** : Cette option supprime le bouton de deconnexion présent dans l'interface pour l'utilisateur final. (*)
- **Afficher les articles de la FAQ Disponibles** : Il est possible d'afficher ou non les articles de la FAQ disponibles liés aux catégories.
- **Montrer le lien vers les détails de la catégorie** : Permet d'afficher un lien vers des détails complémentaires (configurable sur une catégorie).
- **Afficher le logo dans les détails des catégories** : Il est possible de choisir d'afficher ou non le logo des catégories.
- **Icône par défaut pour les catégories** : Il est possible de configurer le logo par défaut pour les catégories où aucun logo n'a été défini.
- **Icone Retour** : Il est possible de choisir l'icone du bouton retour présent dans la barre de navigation lors du choix de la catégorie du ticket.

(*) *barre de menu, en haut à droite*


### Configuration du plugin

![sc-setup-comment.png](/uploads/service-catalog/sc-setup-comment.png)

- **Activer les mots clés** : Il est possible d'afficher dans les vignettes des catégories les mots clés / commentaires prédéfinis, visible ou non pour l'utilisateur final et de les utiliser dans le moteur de recherche.
- **Activer la restriction par groupe** : Il est possible de choisir si les groupes auront accès aux catégories enfants même si les parents de ces enfants leurs sont restreints.
- **Activer la récursivité de la restriction par groupe** : même chose que pour la restriction par groupe, mais cela s'applique aux enfants des enfants liés aux parents.



### Tableau de bord

Afin de guider l’utilisateur pour la création du ticket, différents commentaires sont à remplir dans cette configuration, ces commentaires permettent d’aiguiller l’utilisateur.

![sc-dashboard-config.png](/uploads/service-catalog/sc-dashboard-config.png)

- **Niveau de catégories à afficher** : Il est possible de choisir dans les widgets listant les tickets en cours / à clore sur l'interface simplifiée le niveau de l'arborescence des catégories affichées : ici 2 (Parent > enfant) : 

![levelcat.png](/uploads/service-catalog/levelcat.png)

- **Voir le top incidents / demandes** : Il est possible d'afficher ou non la liste des catégories les plus utilisées

> Uniquement en mode thumbnail / thumbnail_wrapper
{.is-warning}



### Barre de recherche du plugin

![sc-searchbar-config.png](/uploads/service-catalog/sc-searchbar-config.png)

Afin de guider l'utilisateur dans sa recherche, il est possible d'insérer un commentaire dans les barres de recherche pour aider l'utilisateur final.

![sc-searchbar-exemple.png](/uploads/service-catalog/sc-searchbar-exemple.png) 


### Formulaire

Il est possible de personnaliser certains labels du formulaire de création de ticket. 

![sc-form-config.png](/uploads/service-catalog/sc-form-config.png)

- ~~**Plus utilisé - Remplacer le formulaire de création de ticket** : Il est possible de choisir si le plugin remplace le formulaire de création de ticket.~~
- **Remplacer le formulaire de mise à jour de ticket** : Il est possible de choisir si le plugin remplace le formulaire de ticket standard de GLPI par celui du plugin.
- **Montrer les autres informations par défaut à la création du ticket** : Cette option permet de choisir lors de la création du ticket d’afficher tous les champs du ticket si elle est activée. 
    Dans le cas contraire, elle affiche seulement les champs obligatoires à la création du ticket. Les champs qui ne sont pas obligatoires seront affichés en cliquant sur le lien « Autres informations ».
- **Titre de la liste déroulante des observateurs** : Il est possible de changer le titre de la liste déroulante des observateurs.
- **Montrer le champ Numéro de téléphone à la création du ticket** : Il est possible d'afficher un champ permettant de choisi un numéro pour joindre l'utilisateur - les informations saisies seront ajoutées à la fin de la description du ticket.

![telephone_form.png](/uploads/service-catalog/telephone_form.png)

- **Titre du champ Numéro de téléphone** : Permet de définir le titre du bloc Téléphone : dans l'exemple ci-dessus : "Comment vous joindre ?"

- **Titre du ticket** : Il est possible de changer le label au dessus du champ de renseignement du titre du ticket.
- **Titre de la description du ticket** : Il est possible de changer le label au dessus du champ de renseignement de la description du ticket.
- **Titre du bouton de validation du ticket** : Il est possible de changer le titre du bouton de validation dans le formulaire de création de ticket.
- **Masquer le suivi par mail** : Permet de supprimer visuellement les notifications de suivi par mail des acteurs concernés du ticket créé.
> TODO Infotel - décrire l'option : Permettre l'ajout de demandeurs sur le ticket
{.is-warning}

> TODO Infotel - décrire l'option : Permettre l'ajout d'observateurs sur le ticket
{.is-warning}
- **Redirection vers la sélection des entités après la création d'un ticket** : il est possible de configurer la redirection vers l'écran des entités après la création du ticket (Ecran du choix du contexte du ticket).

> TODO Infotel - décrire l'option : Utiliser l'onglet tous par défaut dans les tickets
{.is-warning}


### Configuration pour la mise à jour des informations personnelles de l'utilisateur

![sc-form-personal.png](/uploads/service-catalog/sc-form-personal.png)

> TODO Infotel - décrire l'option : Gabarit de ticket associé à la mise à jour des informations personnelles de l'utilisateur
{.is-warning}


> Il faut au préalable avoir activé l'option « **Voir les informations personnelles lors de la création d'un ticket (interface simplifiée)** », disponible dans le menu Configuration générale, onglet Assistance.
{.is-warning}

Une fois l'option activée :  

- un nouveau widget est disponible dans l'interface de création de ticket de service catalogue.
- Un nouvel encadrement permet de vérifier ses informations personnelles avant la soumission d'un ticket.

Si les informations personnelles ne sont plus d'actualités, cliquer sur "éditer". Un formulaire reprends les informations existantes, autorise la modification et soumet un ticket sur les champs à modifier.


## Onglet widgets

![config_widgets.png](/uploads/service-catalog/config_widgets.png)

- **Widget de bienvenue** : Personnalisation du titre du message et du commentaire de bienvenue pour l'écran d'interface de création de ticket du service catalogue.


- **Widget d'incidents** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de création d'un ticket de type incident. 


- **Widget de demandes** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de création d'un ticket de type demande.


- **Widget de la liste des tickets** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de la liste des tickets en cours concernant l'utilisateur connecté. 


- **Widget de la liste des incidents** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de la liste des tickets en cours de type incident concernant l'utilisateur connecté. 


- **Widget de la liste des demandes** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de la liste des tickets en cours de type demande concernant l'utilisateur connecté.

- **Widget de la Faq** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de la Faq.

- **Widget de la validation des tickets** : Personnalisation du titre, commentaire, l'image ou l'icone du widget des tickets en cours de validation concernant l'utilisateur connecté.


- **Widget de mise à jour des informations personnelles** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de mise à jour des informations personnelles.

> Il faut au préalable avoir activé l'option "Voir les informations perrsonnelles lors de la création d'un ticket (interface simplifiée), disponible dans le menu Configuration générale de GLPI, onglet Assistance.
{.is-warning}

- **Widget de la liste des liens utiles** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de la liste des liens utiles. Nécessite l'ajout de liens utiles.


- **Widget de réservation** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de réservation de matériel.

- **Widget de contexte** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de contexte de la liste des entités.

- **Widget de la base documentaire** : Personnalisation du titre, commentaire, l'image ou l'icone du widget de la base documentaire.

![config_widget_incidents.png](/uploads/service-catalog/config_widget_incidents.png)

> Pour chaque widget, il est possible selon le widget de choisir si l'on souhaite afficher le bouton dans le menu d'interface de création de ticket de l'interface service catalogue, et  d'afficher l'icone sous forme de miniature raccourcie dans le menu supérieur
{.is-info}

![menu_superieur.png](/uploads/service-catalog/menu_superieur.png)

- **Afficher le bouton de création d'incident / d'une demande / de la liste des tickets / de la liste des incidents / de la liste des demandes** : Il est possible de choisir les différents boutons que l'on souhaite afficher sur l'interface centrale.

- **Afficher dans le menu supérieur** : Il est possible de choisir d'afficher l'icone sous forme de miniature raccourcie dans le menu supérieur lors du choix de la catégorie de ticket.

## Onglet Ordonnancement des catégories de ticket

![Sc Category Order](/uploads/service-catalog/sc-category-order.png "Sc Category Order")

Par défaut lors de l’affichage des différentes catégories de niveau 1, les catégories sont triées sur le nom.

Il est possible d’ordonnancer les catégories par d’ordre d’importance dans cette interface.

> Il faut que les catégories soient visibles dans l'interface simplifiée pour pouvoir les ordonnancer 
{.is-warning}

L’ordonnancement des catégories s’effectue suivant le type du ticket et l’entité.

Dans cette interface lors de la première consultation, il faut tout d’abord charger toutes les catégories depuis GLPI via le lien « **Charger les catégories depuis GLPI** ». La liste des catégories apparaitra, pour les ordonnancer il vous suffit de les déplacer.

Lors de l’ajout de nouvelles catégories dans GLPI, pour ne pas perdre tout ordonnancement déjà effectué, vous pouvez ajouter seulement les nouvelles catégories via le lien « **Ajouter des nouvelles catégories depuis GLPI** ».

> Il faut configurer ce tri pour les deux types de tickets. 
{.is-warning}

## Onglet Ordonnancement des champs de tickets

![sc-orderingfields.png](/uploads/service-catalog/sc-orderingfields.png)

Par simple glisser/déposer, Il est possible d'ordonner les champs du formulaire de création de ticket. 

## Onglet Ordonnancement des boutons du widget principal

> TODO Infotel - Ajouter une image
{.is-warning}

Par simple glisser/déposer, Il est possible d'ordonner les boutons présents dans le widget principal


## Onglet Traductions

Comme pour les différents intitulés de GLPI, il est possible de proposer une traduction pour les titres et commentaires du plugin.

![Sc Setup Translate](/uploads/service-catalog/sc-setup-translate.png "Sc Setup Translate")

## Onglet Liens utiles

Cette partie permet de configurer différents liens pour permettre à l’utilisateur d’avoir une interface avec des raccourcis vers différentes url.

Lors de l’ajout d’un lien utile, ces champs sont présents :

-   **Nom** du lien qui sera utilisé comme titre dans l’interface de redirection.
-   **Image** il est possible de changer l’icône pour l’utilisateur final.
-   **URL** qui permet de rediriger l’utilisateur vers un site par le biais de cette url.
-   **Ouvrir dans une nouvelle fenêtre** : ce paramètre permet de configurer lors du clic de l’utilisateur sur le lien si la redirection se passe dans la même fenêtre ou dans une nouvelle fenêtre.
-   **Afficher sur la page d’accueil** : ce paramètre s’il est activé permet d’avoir ce raccourci sur la page d’accueil.
-   **Commentaires** : informations complémentaires sur le lien qui est visible pour l’utilisateur final.

![Sc Links](/uploads/service-catalog/sc_links.png "Sc Links")

Il sera aussi possible de traduire les différents champs qui sont visibles pour l’utilisateur final, un onglet est dédié à cette configuration.

Pour limiter la visualisation de ces liens, un onglet « **Droit des groupes** » est présent.

Il est possible d’ajouter différents groupes qui seront autorisés à voir les liens. Seules les personnes qui feront partie de ces groupes verront le lien.

**Configuration des groupes ayant accès au lien :**
![Sc Setup Translate Group](/uploads/service-catalog/sc_setup_translate_group.png "Sc Setup Translate Group")


# Configuration des entités


## Onglet Catalogue de service

Pour chaque entité de GLPI, il sera possible d'ajouter un logo et des commentaires complémentaires.

Ces informations seront visibles pour les utilisateurs lorsqu'ils devront choisir l'entité de destination du ticket.
![Sc Entity](/uploads/service-catalog/sc-entity.png "Sc Entity")

> Il sera possible de définir des contacts pour l'entité. Ces contacts seront visibles dans un widget "Contactez-nous".
{.is-info}

## Onglet Dashboard Catalogue de service 

Il est possible de personnaliser la vue par défaut de l'utilisateur final et de choisir les widgets qui seront affichés.

![Sc Dashboard Interface](/uploads/service-catalog/sc-dashboard-interface.png "Sc Dashboard Interface")

**Différents widgets sont disponibles :**

- **Widget d'affichage du titre** : ce widget permet d'afficher du texte personnalisé par le biais du champ "Commentaire du message" dans la configuration du plugin.

- **Widget d'affichage des statistiques** : Ce module permet d'ajouter des statistiques sur le suivi des tickets.

- **Widget d'affichage des contacts** : Ce widget permet d'ajouter les coordonnées de contacts qui sont configurés dans les entités.

- **Vos incidents en cours** : Liste de vos incidents en cours.

- **Vos demandes en cours** : Liste de vos demandes en cours.

- **Vos tickets en cours** : Liste de l'ensemble des tickets en cours.

- **Vos tickets à clore** : Liste de vos tickets à clore.

- **Vos tickets en cours par statut** : Ce widget permet d'afficher un graphe en forme de camembert de l'ensemble de vos tickets par statut.

- **Alertes réseau** : Il permet d’indiquer à l’utilisateur un éventuel problème comme une alerte réseau pour ainsi éviter la création de ticket sur ce même problème. Pour ajouter une alerte, il faut créer une note GLPI et la configurer en tant qu'alerte dans l'onglet "Alertes dashboard". (*)

- **Maintenances planifiées prévues** : Au même titre que "Alertes réseau", ce widget permet d'indiquer à l'utilisateur une maintenance planifiée. Pour le configurer, il faut réaliser les mêmes étapes que précédemment, en indiquant "Maintenance planifiée prévue" dans la configuration de la note. (*)

- **Informations** : Ce widget permet d'indiquer différentes informations. (*)

> (*) Visible lorsque le plugin MyDashboard est activé. 
{.is-warning}


# Configuration des catégories

## Onglet Catalogue de service 

![Sc Category Detail](/uploads/service-catalog/sc_category_detail.png "Sc Category Detail")

Pour chaque catégorie de GLPI, il sera possible d’ajouter un logo pour la représenter dans l’interface du catalogue de service.

Il sera possible d’y ajouter un commentaire pour décrire cette catégorie aux utilisateurs.

Ainsi que différents mots clés qui permettront par la suite de retrouver cette catégorie par le biais d’une barre de recherche.

Il sera aussi possible d'indiquer différentes informations complémentaires sur la catégorie.

Il suffit pour cela, d'aller dans le menu « **Configuration > Intitulés > Catégories de ticket** », de sélectionner la catégorie que l'on souhaite modifier.

Lors de l’ajout du logo de la catégorie, il est conseillé d’utiliser un fichier png de taille 145px sur 75px. Dans le cas contraire, l’image sera redimensionnée en respectant cette taille.

## Onglet Favoris

Si l'on souhaite avoir des catégories accéssibles plus facilement dans l'interface, il sera possible de paramétrer des favoris.

Après avoir séléctionné un profil (Administration->Profils) auquel vous voulez activer l'utilisation de favoris, une nouvelle ligne "Favoris" fait son apparition dans l'onglet Catalogue de service afin de gérer les droits d'accès, de modifications et de suppressions des favoris.

![sc-favorites-add-rights.png](/uploads/service-catalog/sc-favorites-add-rights.png) 

L'administrateur pourra choisir les favoris qu'il souhaite rendre accéssible à une entité, un groupe, profil ou utilisateur particulier (ou plusieurs des cas cités). 

Pour se faire, la création d'un favori se fait dans l'onglet "intitulés" dans le menu Configuration,
puis choisir "catégories de ticket".

Il faut séléctionner une catégorie qui n'est pas niveau 1 et se rendre dans l'onglet favoris.

![sc-favorites-admin-add.png](/uploads/service-catalog/sc-favorites-admin-add.png)

La catégorie ITIL liée est celle ou l'on souhaite afficher le favori. La visibilité permet de choisir qui peut accèder aux favoris.

L'utilisateur pourra également choisir ses propres favoris en plus de ceux qui seront configurés par l'administrateur (à condition qu'il est les droits). 

Note : Il faut se placer dans les incidents ou les demandes pour voir apparaître le menu de gestion des favoris utilistaurs.

![sc-nav-fav.png](/uploads/service-catalog/sc-nav-fav.png)

![sc-add-favorites-user.png](/uploads/service-catalog/sc-add-favorites-user.png)

Il pourra de la même manière choisir dans quelles catégories il souhaite les ajouter, supprimer ceux qu'il aura créé pour lui et les trier.


# Options complémentaires et informations diverses

## Modification du formulaire de création de ticket pour l'interface standard ##

En plus des champs déjà présents dans l'interface simplifiée pour le formulaire de création de ticket, il est possible d'ajouter 3 champs en fonction du gabarit de ticket : 
-   Impact
-   Temps de résolution
-   Demande de validation

La configuration s'effectue dans un nouvel onglet dans chaque gabarit de ticket : 
![Sc Tickettemplate](/uploads/service-catalog/sc-tickettemplate.png "Sc Tickettemplate")

Dans l'interface du ticket, les champs seront affichés de cette façon :
![Sc Tickettemplate Ticket](/uploads/service-catalog/sc-tickettemplate-ticket.png "Sc Tickettemplate Ticket")

## <a name="recategorisation"></a>Re-catégorisation 

Cette fonctionnalité permet de proposer la re-catégorisation des tickets lors de leur édition coté interface complète – ceci afin de requalifier si besoin le ticket et de vérifier les catégories choisies par les utilisateurs.

![52 B 077 Cafdd 78 B 3362385611 De 8 Cd 777](/uploads/service-catalog/52b077cafdd78b3362385611de8cd777.png "52 B 077 Cafdd 78 B 3362385611 De 8 Cd 777")

Cette pop-up est affichée lors de la première consultation du ticket. Lors de la validation ou du changement de la catégorie via cette pop-up, la pop-up ne s’affichera pas lors des prochaines éditions du ticket.


## Utilisation avec le plugin Metademands

Le plugin Service Catalog est utilisable avec le plugin Metademands :

https://github.com/InfotelGLPI/metademands

Il suffit de modifier la configuration du plugin Metademands : 

**Activer la transformation d'un ticket en méta-demande**


Ceci vous permettra de lier une catégorie à un formulaire Metademande et donc de rediriger l'utilisateur lors de la sélection de la catégorie depuis Service Catalog. 

## Utilisation avec le plugin Formcreator

Dans l’archive du plugin ServiceCatalog, vous avez un dossier **plugins** dans lequel vous avez un dossier **formcreator**.

A l’intérieur se trouve un fichier *servicecatalog.class.php* qu’il faut placer dans l’arborescence du plugin formcreator (dans le dossier **inc**).

A partir de ce moment-là vous aurez un onglet supplémentaire « Catalogue de Service » depuis la configuration de votre formulaire Formcreator.

Ceci vous permettra de lier une catégorie à un formulaire FormCreator à une catégorie de ticket. 
