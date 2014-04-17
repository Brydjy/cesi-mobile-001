TP découverte AngularJS
=======================

Introduction
------------

Au travers de ce TP vous allez créer une application type "Checklist" (todoList) afin de vous familiariser avec AngularJS et Bootstrap  

Fonctionnalités
---------------

Une fois terminée l'application permettra :  

- De lister un ensemble de Checklist (liste de course, A faire demain, A faire aujourd'hui, etc.)
- D'ajouter une nouvelle Checklist avec autant de tâches que souhaitées
- Lors du clic sur une des Checlist présentes, on pourra accéder à une page listant les tâches pour la Checklist concernée
- Sur la Checklist donnée, on pourra éditer la Checklist en cours

Requirements
------------

- Un serveur web d'installé (apache par exemple)
- Un navigateur assez récent pour bien gérer l'HTML5 (chrome, safari, firefox)
- Un éditeur de texte
- Des bases en javascript

Etapes
------

### Etape 1 : Installation

- Prendre connaissance de la documentation du projet github [angular-seed](https://github.com/angular/angular-seed)
- Cloner le projet github [angular-seed](https://github.com/angular/angular-seed) ou téléchargez-le au format zip.
- Veiller à bien télécharger / ajouter la lib AngularJS dans votre projet. (Attention, de base il est programmé avec Bower)
- Copier le répertoire **app** dans votre serveur web (Vous pouvez aussi utiliser le serveur nodejs fournit)
- **conseil** : gardez une copie du répertoire **app**, afin de vous en servir en tant que modèle pour la suite du TP
- Supprimer toutes les balises du body dans le fichier index.html tout en conservant les balises script
- Supprimer tous les fichiers du dossier **partials**
- Supprimer les 3 lignes (routeProvider) du callback de la fonction **config** dans le fichier *app.js*
- Supprimer les 2 controllers dans le fichier *js/controllers.js*
- Télécharger une version de [twitter bootstrap](http://twitter.github.io/bootstrap/) (ou [la dernière version](http://getbootstrap.com/)) et placer le dossier **bootstrap** dans la répertoire *lib* de votre projet
- Inclure dans le fichier *index.html* la feuille de style *boostrap.min.css*

### Etape 2 : Création de la première page

- Dans le fichier *index.html*, ajouter dans le body la directive **ng-view** (dans une balise div)
- Créer un nouveau fichier *list.html* dans le répertoire *partials* et y ajouter le texte suivant :  page liste
- Ajouter le controller **ListController** dans le fichier *controllers.js* (ne pas oublier de passer $scope dans le constructeur)
- Dans le fichier *app.js*, configurer la route vers l'url "checklists" avec en template la page *list.html* et en controller **ListController**
- Ajouter la page **checklists** en chemin par défault

### Etape 3 : Navbars

- Au début du fichier *list.html*, ajouter une navbar (bootstrap) avec un titre "Checklists"
- Ajouter dans cette navbar un lien en forme de bouton avec une icone "+"

### Etape 4 : Deuxième page

- Créer un nouveau fichier *view.html* dans le dossier **partials**
- Ajouter une navbar avec "Checklist 1" en guise de titre et un bouton back poitant vers la page de listing des checklists (*list.html*)
- Ajouter dans le contenu le texte temporaire suivant : "Les tâches de la checklist 1"
- Ajouter le controller **ViewController** dans *controllers.js* (passer $scope et $routeParams en paramètre du constructeur)
- Dans *app.js*, créer la route pour accéder à cette page sous la forme "checklist/:checklistId"
- Dans la page *list*, créer un lien vers la nouvelle page (vers checklist/1 par exemple)

### Etape 5 : Page List

- Dans le fichier *list.html*, ajouter une liste temporaire de trois checklists différentes (aujourd'hui, demain, plus tard) en "nav tabs stacked" (pour donner un effet liste mobile)
- Les liens de la liste doivent pointer vers la page *view*
- Dans les liens de la liste, ajouter une icon-chevron-right avec la class pull-right(pour la mettre à droite)

### Etape 6 : Page View

- Dans le fichier *view.html*, ajouter une liste en nav-stacked
- Dans le header, ajouter à droite une bouton pour éditer la checklist avec un icon-pencil (Pour un affichage plus propre, utiliser le fluid grid system de bootstrap)
- Ajouter dans les liens à droite des "icon-ok" et "icon-remove" (bootstrap)

### Etape 7 : Page Formulaire

- Créer une page affichant un formulaire avec 2 chemins (routes) mais un seul controller
  - Route pour l'ajout le chemin est **checklist/add**
  - Route pour l'édition le chemin est **checklist/edit/:checkListsId**
- Ajouter un header avec un titre
- Créer le formulaire avec :  
  - Un input text pour le nom de la checklist
  - Une liste d'input text pour les tâches
  - Un bouton permettant d'ajouter des champs pour de nouvelles tâches

### Etape 8 : Page list dynamique

- Ajouter un controller **AppController** au body (directive ngController).
- Ajouter un attribut checklists à l'objet **$scope** qui contiendra les données de la checklist.
- Dans le fichier *list.html*, supprimer le contenu de la liste (les li)
- Ajouter une balise li avec la directive **ng-repeat** pour parcourir l'object *checklists*
  - Mettre en label du lien le nom de la checklist
  - Mettre en URL du lien le chemin vers la page *view* avec le bon ID de checklist

Exemple de structure de l'objet checklists:

    $scope.checklists = [
	  {
	    name: 'checklist1',
		id: 1,
		tasks: [
		  {name: 'Tâche 1', done: true},
		  {name: 'Tâche 2', done: false},
		  {name: 'Tâche 3', done: false},
		]
	  },
	  {
	    name: 'checklist2',
		id: 2,
		tasks: [
		  {name: 'Tâche 1', done: true},
		  {name: 'Tâche 2', done: false},
		  {name: 'Tâche 3', done: false},
		]
	  },
	  {
	    name: 'checklist3',
		id: 3,
		tasks: [
		  {name: 'Tâche 1', done: true},
		  {name: 'Tâche 2', done: false},
		  {name: 'Tâche 3', done: false},
		]
	  },
	];
	
Exemple de structure JSON de l'objet checklists:

    [
	  {
	    "name": "checklist1",
		"id": 1,
		"tasks": [
		  {"name": "Tâche 1", "done": true},
		  {"name": "Tâche 2", "done": false},
		  {"name": "Tâche 3", "done": false}
		]
	  },
	  {
	    "name": "checklist2",
		"id": 2,
		"tasks": [
		  {"name": "Tâche 1", "done": true},
		  {"name": "Tâche 2", "done": false},
		  {"name": "Tâche 3", "done": false}
		]
	  },
	  {
	    "name": "checklist3",
		"id": 3,
		"tasks": [
		  {"name": "Tâche 1", "done": true},
		  {"name": "Tâche 2", "done": false},
		  {"name": "Tâche 3", "done": false}
		]
	  }
	]


### Etape 9 : Filtre page list

- Ajouter un champ input de type text avec la class "search-query", en lui ajoutant le ng-model "query.name"
- Ajouter le filtre dans le ng-repeat pour filtrer la liste

### Etape 10 : Page view dynamique

- Récupérer l'id de la checklist à l'aide du paramètre $routeParams et ajouter la checklist dans le scope
- Stocker l'id dans le scope
- Dans le fichier *view.html*, changer le titre de la page par le nom de la checklist
- Ajouter le bouton edit dans le header pointant vers le formulaire d'édition
- Afficher la liste de tâches de la checklist à l'aide de la directive **ng-repeat**
- Afficher l'icon-ok si l'attribut done est à true ou icon-remove si done est à false (Indice: ng-show, ng-hide)
- Dans le lien de la tâche, ajouter la directive "**ng-click**" avec en paramètre une fonction pour mettre à jour la tâche (updateTask par exemple), en lui passant en paramètre l'index de la tâche
- Dans le controller **ViewController**, ajouter dans le scope la méthode **updateTask** qui changera l'état de l'attribut "done" de la tâche référencés par l'index passé en paramètre

### Etape 11 : Page form

- Récupérer l'id de la checklist à l'aide du paramètre **$routeParams** et ajouter la checklist dans le scope
- Si il n'y a pas d'id
  - Créer un nouvel objet checklist
  - Ajouter le nouvel objet aux autres checklists
  - Récupérer l'id du nouvel objet
- Sinon, stocker l'id dans le scope
- Puis, changer le titre par "Edit <Nom de la checklist>"
- Ajouter un bouton back pointant vers la page view avec l'id
- Dans le input text du nom, ajouter le ng-model pour qu'il pointe sur le nom de la checklist
- Ajouter un ng-repeat et ajouter un input pour chaque tâche avec comme **ng-model** la tâche courante
- Dans le bouton, ajouter une directive ng-click avec en paramètre une méthode pour ajouter une tâche
- Dans le controller, ajouter la méthode d'ajout de tâche au scope

### Etape 12 : Le stockage

- Dans le controller **AppController**, remplir l'object checklists avec les données du localstorage avec la clé "checklists"
- Lors de chaque action sur l'object checklists, sauvegarder les changement dans le localstorage avec la clé checklist


Ressources
----------

### Angular

- [AngularJS] (http://angularjs.org/)
- [Directives](http://docs.angularjs.org/guide/directive)
- [Controllers](http://docs.angularjs.org/guide/dev_guide.mvc.understanding_controller)
- [Routes](http://docs.angularjs.org/tutorial/step_07)
- [Model & Scope](http://docs.angularjs.org/tutorial/step_02)
- [Filtres](http://docs.angularjs.org/tutorial/step_03)

### Bootstrap

- [Navbars](http://twitter.github.io/bootstrap/components.html#navbar)
- [Buttons](http://twitter.github.io/bootstrap/base-css.html#buttons)
- [Icons](http://twitter.github.io/bootstrap/base-css.html#icons)
- [Navs](http://twitter.github.io/bootstrap/components.html#navs)
- [Grid system](http://twitter.github.io/bootstrap/scaffolding.html#gridSystem)
- [Forms](http://twitter.github.io/bootstrap/base-css.html#forms)

### Autre

- [Localstorage](http://www.lafermeduweb.net/billet/le-stockage-local-en-html5-localstorage-942.html)
- [Localstorage](http://www.alsacreations.com/article/lire/1402-web-storage-localstorage-sessionstorage.html)
- [Module AngularJS - LocalStorage] (https://github.com/grevory/angular-local-storage)
- Pour vider son local storage sous Chrome : Paramètre --> Onglet "Paramètres" --> "Afficher les paramètres avancés" --> sous "Confidentialité", cliquer sur "Paramètres de contenu", puis cliquer sur "Cookier et données de site...", faites le ménage;
