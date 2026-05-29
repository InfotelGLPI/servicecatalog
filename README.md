# Plugin Service Catalog for GLPI

Purpose of the plugin : Redirect users to a user-friendly interface allowing them to be directed towards the correct categorization of their ticket (like a service catalog).

Characteristics :

- [X] Access to a fully configurable home page / dashboard
- [X] Display of alerts / scheduled maintenances / information from the Mydashboard plugin
- [X] Display of categories in the manner of a service catalog (5 possible display choices)
- [X] Configuration of comments associated with types and categories
- [X] Ordering of categories
- [X] Choice of logos / colors / description / keywords / restrictions to associate with categories
- [X] Possible link with the Metademands / Formcreator plugin for the creation of complex requests
- [X] Visibility of the links with the Resources, Badges, Consumables plugins, if these are activated.

Visit [https://blogglpi.infotel.com/le-plugin-service-catalog-by-infotel/](https://blogglpi.infotel.com/le-plugin-service-catalog-by-infotel/)

## Access to a Dashboard

![Plugin Service Catalog](https://raw.githubusercontent.com/InfotelGLPI/servicecatalog/master/screenshots/NewNavBar-1024x678.png "Plugin Service Catalog")

## Ticket categories display

![Plugin Service Catalog](https://raw.githubusercontent.com/InfotelGLPI/servicecatalog/master/screenshots/thumbnail3-1024x546.png "Plugin Service Catalog")

## Incident creation form

![Plugin Service Catalog](https://raw.githubusercontent.com/InfotelGLPI/servicecatalog/master/screenshots/create_incident.png "Plugin Service Catalog")

## Example to use with Metademands plugin 

![Plugin Service Catalog](https://raw.githubusercontent.com/InfotelGLPI/servicecatalog/master/screenshots/metademands_navbar-1024x484.png "Plugin Service Catalog")

# Guide utilisateur — Plugin GLPI Service Catalog

**Service Catalog** est un plugin GLPI qui remplace l'interface helpdesk standard par un portail utilisateur complet et personnalisable. Il propose la création de tickets par catégorie, le suivi des tickets, une base de connaissance, des liens utiles, des réservations, un annuaire de contacts, la gestion des équipements et un moteur de recherche fuzzy.

---

## 1. Présentation

### 1.1 Fonctionnalités principales

- **Portail end-user** : interface simplifiée remplaçant la vue helpdesk GLPI, configurable par profil et par entité
- **Création de tickets par catégorie** : arborescence ITIL enrichie avec images, icônes, couleurs, descriptions et mots-clés
- **Suivi des tickets** : vue chronologique (timeline), annulation, validation, ajout d'acteurs
- **Base de connaissance** : FAQ intégrée avec recherche et liaison aux catégories
- **Liens utiles** : liste de liens paramétrables avec visibilité par groupe
- **Favoris** : catégories favorites par utilisateur, groupe ou profil
- **Moteur de recherche fuzzy** (Fuse.js) : recherche sur catégories, articles FAQ et sources externes (Drupal, BookStack)
- **Réservations** : réservation d'équipements avec génération optionnelle d'un ticket
- **Rendez-vous technicien** : planification d'un rendez-vous depuis la timeline d'un ticket
- **Gestion des équipements** : liste des éléments de l'utilisateur (« Mes équipements »)
- **Barre de navigation personnalisable** : menu latéral/haut configurable (titres, icônes, ordre)
- **Mise en page multi-layout** : 10 mises en page de tuiles disponibles
- **Multi-entité** : configuration par entité (logo, en-tête, vue par défaut du portail)
- **Traductions** : tous les champs configurables sont traduisibles par langue

### 1.2 Compatibilité

| Élément | Version |
|---|---|
| Plugin | 3.0.4 |
| GLPI | 11.0.0 – 12.0.0 |
| PHP | = 8.1 |

---

## 2. Gestion des droits

Chemin : `Administration > Profils > onglet Service catalog`

### 2.1 Droits matriciels (LIRE / CRÉER / MODIFIER / PURGER)

| Droit | Objet | Description |
|---|---|---|
| `plugin_servicecatalog_setup` | Configuration, catégories, entités | Accès complet à l'administration du plugin |
| `plugin_servicecatalog_links` | Liens utiles | Gérer les liens utiles affichés dans le portail |
| `plugin_servicecatalog_appliancelinks` | Liens applicatifs | Associer des applications aux utilisateurs |
| `plugin_servicecatalog_contacts` | Contacts | Gérer l'annuaire de contacts du portail |
| `plugin_servicecatalog_myelements` | Mes équipements | Consulter la liste des équipements de l'utilisateur |
| `plugin_servicecatalog_api` | Clients API | Gérer les clients API externes (Drupal, BookStack) |
| `plugin_servicecatalog_favorites` | Favoris | Gérer les catégories favorites |
| `plugin_servicecatalog_shortcuts` | Raccourcis | Créer des raccourcis dans le menu Outils |
| `plugin_servicecatalog_defaultview` | Tableau de bord | Accès au tableau de bord du portail |

### 2.2 Droits à case à cocher (activé / désactivé)

| Droit | Description |
|---|---|
| `plugin_servicecatalog` | Accéder au portail (droit d'usage principal) |
| `plugin_servicecatalog_incidents` | Créer des tickets de type Incident |
| `plugin_servicecatalog_requests` | Créer des tickets de type Demande |
| `plugin_servicecatalog_add_actor` | Ajouter des acteurs à un ticket depuis le portail |
| `plugin_servicecatalog_cancel_ticket` | Annuler son propre ticket |
| `plugin_servicecatalog_ticket_appointment` | Planifier un rendez-vous depuis la timeline d'un ticket |
| `plugin_servicecatalog_redirect_on_menu` | Rediriger vers le menu principal après création d'un ticket |
| `plugin_servicecatalog_hide_menu` | Masquer le menu GLPI standard pour ce profil |
| `plugin_servicecatalog_checkticket` | Vérifier la validité de la catégorie avant création d'un ticket |

> **Conseil** : attribuez `plugin_servicecatalog` à tous les profils helpdesk. Seuls les administrateurs ont besoin de `plugin_servicecatalog_setup`.

---

## 3. Configuration globale

Chemin : `Configuration > Plugins > Service catalog` (nécessite `plugin_servicecatalog_setup` MODIFIER)

### 3.1 Onglets de configuration

| Onglet | Contenu |
|---|---|
| **Configuration plugin** | Tous les paramètres globaux (accordéon) |
| **Widgets** | Visibilité et personnalisation de chaque tuile du portail |
| **Tableau de bord** | Vue par défaut du portail par entité et profil |
| **Ordre du menu** | Glisser-déposer pour ordonner les éléments de la barre de navigation |
| **Ordre des catégories** | Ordre d'affichage des catégories sur le portail |
| **Ordre des champs** | Ordre des champs dans le formulaire de création de ticket |
| **Ordre des boutons** | Ordre des boutons d'action dans le widget d'actions |
| **Ordre des colonnes** | Colonnes et ordre dans les listes de tickets en mode tableau |
| **Traductions** | Traduction de tous les champs configurables par langue |
| **Liens utiles** | Liste des liens utiles affichés dans le portail |
| **Clients API** | Sources externes (Drupal, BookStack) |
| **Outils** | Outils de maintenance et de diagnostic |
| **Vérification schéma** | Intégrité des tables de la base de données |

---

### 3.2 Section : Affichage

| Paramètre | Description |
|---|---|
| Layout des catégories | Mise en page des tuiles : `sly`, `wrapper`, `wrappersly`, `thumbnail`, `thumbnail_wrapper`, `bootstrapped`, `bootstrapped_color`, `shoper`, `circle`, `glpi11` |
| Utiliser les couleurs du plugin | Couleurs personnalisées du plugin ou CSS du cœur GLPI |
| Couleur générale | Couleur principale des tuiles |
| Couleur secondaire (survol) | Couleur au survol des tuiles |
| Couleur de la barre de navigation | Fond de la barre de navigation |
| Couleur de police des titres | Couleur du texte dans les en-têtes de tuiles |
| Couleur de fond des titres | Fond des en-têtes de tuiles |
| Forcer la couleur de fond du titre | Appliquer la couleur de fond même si la catégorie a sa propre couleur |
| Taille des catégories | `Très petite`, `Petite`, `Normale` |
| Afficher la bordure | Bordure autour des tuiles |
| Bords arrondis | Coins arrondis sur les bordures |
| Masquer le menu helpdesk | Supprimer le menu de navigation helpdesk standard |
| Masquer le menu haut | Supprimer la barre supérieure GLPI |
| Rediriger le bouton accueil | Le logo GLPI renvoie vers le portail au lieu de la page d'accueil standard |
| Masquer le sélecteur de langue | Supprimer le bouton de langue dans la barre helpdesk |
| Masquer le bouton d'aide | Supprimer le bouton aide |
| Masquer les recherches sauvegardées | Supprimer les recherches sauvegardées |
| Masquer les préférences | Supprimer le bouton préférences de la barre |
| Masquer le bouton de déconnexion | Supprimer le bouton de déconnexion de la barre |
| Afficher les articles FAQ liés | Afficher les articles liés sur la page de détail d'une catégorie |
| Afficher le lien de détail | Afficher un lien « détails » sur les tuiles de catégorie |
| Afficher le logo dans les détails | Afficher le logo de la catégorie sur sa page de détail |
| Afficher les indicateurs dans l'interface complète | Afficher les indicateurs du portail aux utilisateurs en interface centrale |
| Icône par défaut des catégories | Icône de secours pour les catégories sans icône assignée |
| Couleur par défaut des catégories | Couleur de secours pour les catégories sans couleur assignée |
| Listes de tickets en tableau | Afficher les listes de tickets sous forme de tableau |
| Colonnes utilisées | Colonnes affichées en mode tableau |
| Icône par défaut des catégories mères | Icône de secours pour les catégories parentes |
| Icône par défaut des catégories filles | Icône de secours pour les catégories enfants |
| Nombre de lignes par défaut dans les listes | `3`, `5`, `10`, `25`, `50`, `100` |
| Ajouter un bouton Retour | Afficher un bouton de navigation retour |
| Désactiver le tableau de bord | `Activé` / `Désactivé ? liste incidents` / `Désactivé ? liste demandes` |
| Lignes dans les tickets fermés | `30`, `100`, `200`, `300`, `400`, `Tous` |
| Rediriger le logo vers la sélection d'entités | Cliquer sur le logo GLPI redirige vers la sélection d'entité |
| Mode démo | Activer la barre de sélection de la démo |

---

### 3.3 Section : Plugin

| Paramètre | Description |
|---|---|
| Activer les mots-clés | Recherche par mots-clés sur les catégories et articles FAQ |
| Activer la restriction par groupe | Les catégories restreintes à des groupes appliquent cette restriction à leurs sous-catégories |
| Récursivité de la restriction | La restriction de groupe s'applique aussi aux sous-groupes |

---

### 3.4 Section : Tableau de bord

| Paramètre | Description |
|---|---|
| Titre de la page d'accueil | En-tête principal du portail |
| Titre du widget d'actions | Titre de la tuile des actions rapides |
| Titre de vos tickets ouverts | Label de la section « tickets en cours » |
| Titre de vos incidents ouverts | Label de la section « incidents en cours » |
| Titre de vos incidents + groupe | Label combinant incidents personnels et de groupe |
| Titre de vos demandes ouvertes | Label de la section « demandes en cours » |
| Titre de vos demandes + groupe | Label combinant demandes personnelles et de groupe |
| Titre des tickets à clore | Label pour les tickets résolus en attente de clôture |
| Titre des tickets à valider | Label pour les tickets en attente de validation |
| Sélectionner catégorie incident | Placeholder du sélecteur de catégorie incident |
| Sélectionner catégorie demande | Placeholder du sélecteur de catégorie demande |
| Catégories favorites | Titre de la section favoris |
| Articles FAQ liés | Label des articles liés à une catégorie |
| Niveau de catégories à afficher | Profondeur de l'arborescence ITIL affichée sur le tableau de bord |
| Afficher le Top incidents / Top demandes | Compteurs des catégories les plus utilisées |
| Raison d'en attente pour les indicateurs | Raison d'en attente affichée dans le widget indicateurs (MyDashboard) |

---

### 3.5 Section : Barres de recherche

| Paramètre | Description |
|---|---|
| Utiliser la barre de recherche intégrée | Remplacer la barre de recherche standard |
| Afficher la barre de recherche intégrée | Afficher la barre sans la définir comme barre principale |
| Maximiser la barre de recherche | Étendre la barre à la largeur complète |
| Recherche stricte | Correspondance exacte au lieu de fuzzy |
| Afficher sur le tableau de bord | Afficher la barre sur la page principale |
| Couleur recherche tickets | Couleur des résultats de type ticket |
| Couleur recherche articles FAQ | Couleur des résultats de type article KB |
| Couleur recherche API externe | Couleur des résultats provenant de Drupal/BookStack |
| Titre barre incidents | Placeholder de la barre de recherche incidents |
| Titre barre demandes | Placeholder de la barre de recherche demandes |
| Titre barre articles FAQ | Placeholder de la barre de recherche articles |

---

### 3.6 Section : Barre de navigation

| Paramètre | Description |
|---|---|
| Afficher la navigation entités plugin | Intégrer le plugin `entitiesnavigation` dans la barre |
| Titre du menu principal | Label et icône du menu racine |
| Titre du menu Accueil | Label de l'élément Accueil |
| Titre du menu Tickets | Label générique tickets |
| Titre du menu Incidents | Label du sous-menu incidents |
| Titre du menu Demandes | Label du sous-menu demandes |
| Titre du menu Aide | Label et icône du menu aide |
| Titre du menu Autres | Label et icône du menu divers |
| Mes équipements | Afficher/masquer, label et icône de la rubrique équipements |
| Mes applications | Afficher/masquer, label et icône de la rubrique applications |
| Tickets fermés | Afficher/masquer, label et icône de la rubrique tickets fermés |

---

### 3.7 Section : Formulaire de ticket

| Paramètre | Description |
|---|---|
| Ignorer la sélection de catégorie | Aller directement au formulaire sans passer par le sélecteur |
| Titre de la sélection de catégorie | Label au-dessus du sélecteur |
| Utiliser un assistant (wizard) | Formulaire en plusieurs étapes au lieu d'une page unique |
| Couleur de fond du formulaire | Couleur de fond du formulaire de création |
| Rediriger vers le détail avant création | Afficher la page de détail de la catégorie avant le formulaire |
| Largeur du formulaire | Pourcentage de la largeur de la colonne (70–100 %) |
| Modèle de ticket par défaut — Incident | Modèle appliqué à la création d'un incident |
| Modèle de ticket par défaut — Demande | Modèle appliqué à la création d'une demande |
| Titre de l'urgence | Label personnalisé du champ urgence |
| Commentaire sur l'urgence | Texte d'aide sous le champ urgence |
| Couleurs par niveau d'urgence | Couleur par niveau (1–5, filtrés par le masque GLPI) |
| Titre de l'impact | Label personnalisé du champ impact |
| Commentaire sur l'impact | Texte d'aide sous le champ impact |
| Couleurs par niveau d'impact | Couleur par niveau (1–5) |
| Déployer « Plus d'informations » par défaut | Afficher le bloc additionnel déplié par défaut |
| Titre de la section informations | Label de la section « autres informations » |
| Champs dans le bloc informations | Champs affichés dans le bloc dépliable |
| Autoriser l'ouverture pour d'autres utilisateurs | Ouvrir un ticket au nom d'un autre utilisateur |
| Utilisateurs autorisés pour la délégation | Tous les utilisateurs ou uniquement ceux du même groupe |
| Titre de la délégation | Label du sélecteur de délégation |
| Ajouter le bénéficiaire comme observateur | Ajouter automatiquement l'utilisateur délégué en observateur |
| Titre du menu préférences | Label de l'élément préférences dans la navigation |
| Afficher le champ groupe demandeur | Ajouter un champ groupe demandeur dans le formulaire |
| Titre du groupe demandeur | Label du champ groupe demandeur |
| Titre des observateurs | Label du champ observateurs |
| Titre de la date TTR | Label du champ Date de résolution souhaitée |
| Titre de l'ajout de validation | Label du bouton « Demander une validation » |
| Afficher les éléments liés avec icônes | Icônes de type d'équipement dans le sélecteur d'éléments liés |
| Types d'éléments par défaut dans le formulaire | Types d'équipements GLPI disponibles dans le sélecteur |
| Titre des éléments liés | Label du champ éléments liés |
| Titre de la localisation | Label du champ localisation |
| Afficher le champ téléphone | Champ numéro de téléphone supplémentaire |
| Titre du champ téléphone | Label du champ téléphone |
| Téléphone obligatoire | Rendre le champ téléphone obligatoire |
| Afficher les informations navigateur | Ajouter automatiquement les infos navigateur/client à la description |
| Titre du ticket | Label du champ objet/titre du ticket |
| Titre de la description | Label de la zone de description |
| Placeholder de la description | Texte fantôme dans la zone de description |
| Libellé du bouton de soumission | Texte personnalisé pour le bouton « Envoyer » |
| Masquer le suivi par e-mail | Masquer la case « Me notifier par e-mail » |
| Titre du suivi par e-mail | Label de la case de suivi |
| Ajouter des demandeurs après création | Autoriser l'ajout de demandeurs sur un ticket existant |
| Ajouter des observateurs après création | Autoriser l'ajout d'observateurs sur un ticket existant |
| Utilisateurs pour ajout acteurs | Tous les utilisateurs ou uniquement ceux des groupes |
| Redirection vers sélection d'entité après création | Rediriger vers la sélection d'entité après création du ticket |
| Redirection vers le ticket après création | Rediriger directement vers le ticket créé |
| Utiliser l'onglet « Tous » par défaut | Afficher l'onglet « Tous » par défaut dans les listes de tickets |
| Afficher les tickets liés | Afficher les tickets liés dans la timeline helpdesk |

---

### 3.8 Section : Mise à jour des équipements

| Paramètre | Description |
|---|---|
| Afficher le bouton de mise à jour | Bouton de demande de mise à jour sur la page « Mes équipements » |
| Modèle de ticket pour mise à jour | Modèle appliqué à la demande de mise à jour d'équipement |

---

### 3.9 Section : Mise à jour du profil utilisateur

| Paramètre | Description |
|---|---|
| Utiliser le formulaire de préférences du plugin | Remplacer les préférences GLPI par la page du plugin |
| Modèle de ticket pour la mise à jour | Modèle utilisé pour la demande de mise à jour des informations personnelles |

---

### 3.10 Section : Annulation de ticket

| Paramètre | Description |
|---|---|
| Modèle de solution pour l'annulation | Modèle de solution appliqué lors de l'annulation d'un ticket par l'utilisateur |

---

### 3.11 Section : Réservations

| Paramètre | Description |
|---|---|
| Créer une demande à la réservation | Générer automatiquement un ticket lors d'une réservation |
| Modèle de ticket pour réservation | Modèle appliqué au ticket de réservation |

---

## 4. Configuration des widgets (onglet Widgets)

Chaque widget correspond à une tuile ou une section du portail. Chaque widget dispose des options suivantes :

| Sous-paramètre | Description |
|---|---|
| Afficher dans la barre de navigation | La tuile apparaît dans le menu de navigation |
| Afficher dans le menu haut | La tuile apparaît comme raccourci dans la barre supérieure |
| Afficher dans le widget d'actions | La tuile apparaît dans les actions rapides de la page d'accueil |
| Titre | Label personnalisé de la tuile |
| Commentaire | Description affichée sous le titre (texte enrichi pour la plupart) |
| Image | Image uploadée pour l'icône de la tuile |
| Icône | Sélecteur d'icône FontAwesome / Tabler |

**Widgets configurables :**

| Widget | Barre de navigation | Menu haut | Widget actions |
|---|---------------------|---|---|
| Message de bienvenue | —                   | — | — |
| Créer un incident | Oui                 | Oui | Oui |
| Créer une demande | Oui                 | Oui | Oui |
| Liste des tickets | Oui                 | — | — |
| Liste des incidents | Oui                 | — | — |
| Liste des demandes | Oui                 | — | — |
| FAQ / Base de connaissance | —                   | Oui | — |
| Validation de tickets | —                   | — | — |
| Préférences utilisateur | Oui                 | — | — |
| Liens utiles | Oui                 | Oui | — |
| Réservations | —                   | — | — |

**Options supplémentaires :**

- **Mes équipements** : sélection multiple des états GLPI à exclure de la liste
- **Widget Favoris** : afficher les favoris dans le menu haut
- **Widget Contextes** : afficher le nom complet de l'entité, titre et commentaire de la liste d'entités, titre du sélecteur de contexte ticket

---

## 5. Gestion des catégories ITIL

Le plugin ajoute un onglet **Service catalog** sur chaque fiche de catégorie ITIL.

Chemin : `Assistance > Catégories ITIL > [Catégorie] > onglet Service catalog`

### 5.1 Champs par catégorie

| Champ | Description |
|---|---|
| Hériter la configuration parente | Reprendre les paramètres de la catégorie parente (par défaut : oui) |
| Hériter l'image parente | Reprendre l'image de la catégorie parente |
| Hériter le détail parent | Reprendre le contenu de la page de détail |
| Hériter l'alerte parente | Reprendre le texte d'alerte parent |
| Hériter les types d'éléments parents | Reprendre les types d'équipements du parent |
| Image | Image de la tuile de catégorie |
| Icône | Icône FontAwesome / Tabler |
| Couleur | Couleur de la tuile |
| Contenu de la page de détail | Texte enrichi affiché avant la création du ticket |
| Texte d'alerte | Message d'avertissement affiché sur la tuile |
| Types d'équipements applicables | Types GLPI disponibles dans le formulaire pour cette catégorie |
| Restriction par groupe | Groupes autorisés à voir et utiliser cette catégorie |
| Nom simplifié incident | Label alternatif en mode incident |
| Nom simplifié demande | Label alternatif en mode demande |

### 5.2 Sous-onglets de catégorie

| Onglet | Contenu |
|---|---|
| **Traductions** | Traduire les champs texte par langue |
| **Mots-clés** | Mots-clés de recherche associés à la catégorie |
| **Favoris** | Gérer les favoris liés à cette catégorie (nécessite `plugin_servicecatalog_favorites`) |

### 5.3 Ordre des catégories

L'onglet **Ordre des catégories** dans la configuration globale permet de réordonner les catégories par glisser-déposer, par type de ticket (incident / demande) et par niveau.

---

## 6. Interface portail

### 6.1 Page d'accueil

La page d'accueil du portail (`main.form.php`) affiche :
- Le **widget d'actions rapides** (créer incident, créer demande, liens utiles, etc.)
- Les **catégories ITIL** organisées en tuiles selon la mise en page choisie
- Les **tickets ouverts** de l'utilisateur (incidents, demandes, tickets à valider, à clore)
- Les **favoris** de l'utilisateur
- La **barre de recherche fuzzy** (si activée)
- Les **indicateurs MyDashboard** (si le plugin mydashboard est actif et l'option activée)

> **Note** : la mise en page et les sections visibles dépendent des droits du profil et des paramètres de configuration.

### 6.2 Création de ticket

Chemin de création :

1. **Sélection de la catégorie** (`choosecategory.form.php`) — arborescence ITIL enrichie
2. *(Optionnel)* **Page de détail** (`categorydetail.form.php`) — contenu riche, alerte, articles FAQ liés
3. **Formulaire de ticket** (`newticket.form.php`) — formulaire complet ou assistant (wizard)

Options du formulaire :
- Champs configurables : objet, description, urgence, impact, localisation, groupe demandeur, observateurs, éléments liés, téléphone, date TTR, demande de validation
- Mode délégation : ouvrir un ticket au nom d'un autre utilisateur
- Bloc « Plus d'informations » dépliable
- Ajout automatique des informations navigateur
- Redirection après création : vers le ticket, vers la sélection d'entité, ou vers le menu principal

### 6.3 Suivi des tickets

Page de ticket (`ticket.form.php`) :
- **Timeline** : suivi des followups, tâches, solutions, validations
- **Annulation** : bouton disponible si le droit `plugin_servicecatalog_cancel_ticket` est attribué, le ticket n'est pas résolu et n'a pas de followup/tâche
- **Ajout d'acteurs** : demandeurs et observateurs si les droits correspondants sont attribués
- **Tickets liés** : affichés si l'option est activée
- **Rendez-vous** : planification avec un technicien si le droit `plugin_servicecatalog_ticket_appointment` est attribué

Listes de tickets :
- Incidents ouverts / demandes ouvertes / tous les tickets
- Tickets à valider, résolus, fermés
- Mode tableau configurable (colonnes, nombre de lignes)

### 6.4 FAQ / Base de connaissance

Page `faq.php` — affiche les articles de la base de connaissance GLPI. Les articles peuvent être liés à des catégories ITIL pour apparaître sur la page de détail de la catégorie. La recherche fuzzy inclut les articles FAQ.

### 6.5 Liens utiles

Page `link.php` — liste des liens configurés par l'administrateur. La visibilité peut être limitée par groupe (`Linkgroup`). Les liens peuvent apparaître dans la barre de navigation ou sur la page d'accueil.

### 6.6 Réservations

Page `reservation.php` — consultation et réservation d'équipements GLPI. La création d'une réservation peut déclencher automatiquement la création d'un ticket si l'option est activée.

### 6.7 Mes équipements

Page `usercard.php` — liste des équipements GLPI assignés à l'utilisateur. Un bouton « Demander une mise à jour » peut être affiché (génère un ticket avec le modèle configuré). Les états GLPI à exclure sont paramétrables dans le widget.

### 6.8 Mes applications

Rubrique « Mes applications » — liste des applications GLPI (`Appliance`) liées à l'utilisateur via le mécanisme `ApplianceLink`.

### 6.9 Préférences utilisateur

Page `preference.php` — formulaire de mise à jour des informations personnelles (nom, e-mail, téléphone). Si un modèle de ticket est configuré, la modification génère une demande de ticket au lieu d'une modification directe.

---

## 7. Barre de navigation

La barre de navigation du portail remplace la barre helpdesk GLPI standard.

### 7.1 Structure par défaut

| Secteur | Éléments |
|---|---|
| **Accueil** | Page d'accueil du portail |
| **Tickets** | Créer un incident (si droit `plugin_servicecatalog_incidents`) |
| **Tickets** | Créer une demande (si droit `plugin_servicecatalog_requests`) |
| **Aide** | FAQ, base documentaire |
| **Autres** | Liens utiles, réservations, liens directs, mes équipements, mes applications, préférences, plugins tiers |

### 7.2 Personnalisation

- **Titres et icônes** : configurables par widget dans l'onglet Widgets
- **Ordre** : configurable par glisser-déposer dans l'onglet Ordre du menu
- **Visibilité** : chaque élément peut être masqué via son widget

---

## 8. Favoris

Les utilisateurs peuvent marquer des catégories ITIL comme favorites (étoile sur la tuile).

- **Affichage** : section prioritaire sur la page d'accueil du portail
- **Portée** : personnalisable par utilisateur, par groupe (`Favorite_Group`) ou par profil (`Favorite_Profile`)
- **Menu haut** : option pour afficher les favoris dans la barre de navigation haut

---

## 9. Moteur de recherche fuzzy

Le plugin intègre [Fuse.js](https://fusejs.io/) pour une recherche instantanée et tolérante aux fautes.

### 9.1 Sources de recherche

| Source | Contenu indexé |
|---|---|
| Catégories ITIL | Nom, description, mots-clés |
| Articles FAQ | Titre, contenu, résumé |
| API externe | Contenu Drupal ou BookStack |

### 9.2 Modes de recherche

- **Fuzzy** (par défaut) : trouve les résultats proches même sans correspondance exacte
- **Strict** : correspondance exacte uniquement (option `Recherche stricte`)

### 9.3 Clients API externes

Chemin : `Configuration > Plugins > Service catalog > onglet Clients API`

Deux types de sources externes sont supportées :

| Type | Protocole |
|---|---|
| Drupal | Authentification Basic ou par token |
| BookStack | Authentification Basic ou par token |

---

## 10. Gestion par entité

Un onglet **Service catalog** est ajouté sur chaque fiche Entité GLPI.

| Contenu | Description |
|---|---|
| Images et logos spécifiques | En-tête et logo propres à cette entité dans le portail |
| Options d'affichage | Surcharges des options d'affichage globales |
| Tableau de bord (onglet Dashboard) | Vue par défaut du portail pour cette entité, par profil |

---

## 11. Intégration MyDashboard

Lorsque le plugin MyDashboard est actif, Service Catalog contribue un widget **Indicateurs** dans le tableau de bord MyDashboard.

Ce widget affiche :
- Tickets ouverts par l'utilisateur
- Tickets en attente (selon la raison d'en attente configurée)
- Tickets en attente de validation

---

## 12. Intégration avec les formulaires GLPI natifs

Un onglet **Service catalog** est ajouté sur chaque formulaire GLPI natif (Forms GLPI 11). Il permet d'exposer un formulaire natif comme point d'entrée d'une catégorie du portail.

---

## 13. Bonnes pratiques

### 13.1 Configuration initiale

1. Aller dans `Configuration > Plugins > Service catalog`
2. Choisir un **layout** adapté (recommandé : `glpi11` pour une intégration moderne)
3. Définir les **couleurs** selon la charte graphique de votre organisation
4. Configurer le **modèle de ticket par défaut** pour les incidents et les demandes
5. Activer la **barre de recherche** si l'arborescence de catégories est large

### 13.2 Gestion des catégories

1. Créer les catégories ITIL dans `Assistance > Catégories ITIL`
2. Sur chaque catégorie, aller dans l'onglet **Service catalog** pour ajouter une image, une icône, une couleur et une description
3. Activer `is_helpdeskvisible` sur la catégorie ITIL pour qu'elle apparaisse dans le portail
4. Utiliser l'**Ordre des catégories** pour prioriser les catégories les plus utilisées

### 13.3 Gestion des droits

1. Attribuer `plugin_servicecatalog` (READ) à tous les profils qui doivent accéder au portail
2. Attribuer `plugin_servicecatalog_incidents` et/ou `plugin_servicecatalog_requests` selon les types de tickets autorisés
3. Réserver `plugin_servicecatalog_setup` (UPDATE) aux administrateurs uniquement

### 13.4 Performance

> Le plugin met en cache la liste des catégories pendant **3600 secondes**. Toute modification d'une catégorie ITIL ou d'une catégorie Service Catalog invalide automatiquement ce cache. En cas de doute, utilisez les **Outils** dans la configuration du plugin pour forcer la réinitialisation du cache.

### 13.5 Multi-entité

- Configurez une vue par défaut du portail par entité via l'onglet **Tableau de bord** sur la fiche Entité
- Les logos et images peuvent être surchargés par entité via l'onglet **Service catalog** de l'entité

---

*Documentation générée pour Service Catalog v3.0.4 — GLPI 11.x*
