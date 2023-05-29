# Workshop_clem-ju
Workshop_epitech


Objectif: découvrir Angular et les appels aux bases de données.

**INSTALATION**: 

```npm install -g @angular/cli```

**PROJET**: Créer une application Angular qui affiche des données à partir d'une base de données JSON simulée.

**Etape 1: Initialisation**

1- Ouvrez votre terminal ou votre invite de commandes et créez un nouveau dossier pour votre projet.​

2- Accédez au dossier du projet et exécutez la commande suivante pour créer une nouvelle application Angular : ```ng new angular-database-app​```

3- ```cd angular-database-app​```

4- **Installez** la dépendance json-server qui nous permettra de simuler une base de données JSON : ```npm install json-server​```

5- Créez un fichier JSON nommé database.json à la racine de votre projet et ajoutez quelques données fictives. Par exemple : ​
```
{​

  "users": [​

      { "id": 1, "name": "John" },​

      { "id": 2, "name": "Jane" },​

      { "id": 3, "name": "Bob" }​

  ]​

}​
```

**Étape 2: Création des composants Angular​**

1- Créez un composant Angular : https://angular.fr/composants/ecrire-un-composant.html

2- Ouvrez le fichier ***src/app/user-list/user-list.component.html***

  2a - Ajoutez un titre : https://developer.mozilla.org/fr/docs/Web/HTML/Element/Heading_Elements

3- Ouvrez le fichier ***src/app/user-list/user-list.component.ts***

  - 3a - Créez une variable ***users***
  - 3b - Ajoutez un ngOnInit : https://angular.fr/composants/untitled.html
  - 3c - Dans le ngOnInit, ajoutez une méthode get qui récupère les users : https://jasonwatmore.com/fr/post/2019/09/06/angular-les-exemples-des-requetes-http-get#:~:text=Une%20requ%C3%AAte%20HTTP%20GET%20avec%20gestion%20des%20erreurs,par%20l'appel%20%C3%A0%20http.

3- Ouvrez le fichier ***src/app/app.module.ts*** et verifiez qu'il y a bien cette importation nécessaire au début du fichier : ```import { HttpClientModule } from '@angular/common/http';​```

4- Ajoutez également HttpClientModule à la liste des imports du module :```imports: [ HttpClientModule ]```

**Étape 3: Configuration du service JSON Server​**

1- À la racine de votre projet, créez un fichier ***server.js*** et ajoutez le code suivant : ​
```
const jsonServer = require('json-server');
const server = jsonServer.create();
const router = jsonServer.router('database.json');
const middlewares = jsonServer.defaults();

server.use(middlewares);
server.use(router);
server.listen(3000, () => {
  console.log('JSON Server is running');
});

```
2- Démarrez le serveur JSON

**Étape 4: Affichage des données dans l'application Angular​**

1 - Affichez les données du composant dans l'application web Angular
  - 1a - Ouvrez le fichier ***src/app/app.component.html***

2- Verifiez que dans la section des déclarations du module il y ait bien ***UserListComponent***

3- Lancez votre projet

***Etape 5: Créez une application de gestion des tâches (to-do list) en utilisant Angular et une API RESTful.***

0- Créez le service ***task.service.ts***

1- Dans ce service, importez HttpClient et implémentez les méthodes nécessaires pour effectuer les requêtes HTTP suivantes :

- Récupérer toutes les tâches (GET)
- Ajouter une nouvelle tâche (POST)
- Mettre à jour une tâche existante (PUT)
- Supprimer une tâche (DELETE)

2- Dans le composant principal de l'application ***(app.component.ts)***, injectez le service TaskService et utilisez-le pour afficher la liste des tâches et implémentez les fonctionnalités d'ajout, de mise à jour et de suppression des tâches.

3- Dans le fichier HTML du composant principal ***(app.component.html)***, affichez les tâches récupérées depuis le service et ajoutez des fonctionnalités pour créer, mettre à jour et supprimer des tâches.

4- Déployez une API RESTful, vous pouvez utiliser une fausse API comme JSONPlaceholder ou créez votre propre API en utilisant des outils tels que Express pour gérer les requêtes HTTP de votre application :

  - 4a - Créez un nouveau répertoire pour votre API et allez-y depuis votre terminal.
  - 4b - Installez les dépendances nécessaires pour votre API: ```npm install express body-parser```
  - 4c - Créez un fichier index.js dans votre répertoire pour l'API.
  - 4d - Dans le fichier index.js, importez les modules nécessaires et configurez Express pour écouter sur un port spécifique.
  - 4e - Ajoutez les routes nécessaires pour gérer les requêtes HTTP du projet.
  - 4f - ```node index.js```

5- Testez votre application en ajoutant, mettant à jour et supprimant des tâches, en vous assurant que les modifications sont reflétées à la fois dans l'application et dans l'API.

- VOILA FINIT PTDR
