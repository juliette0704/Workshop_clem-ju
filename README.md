# Workshop_clem-ju
Workshop_epitech


Objéctif: découvrir Angular et les appels aux bases de données.​

**INSTALATION**: 

```npm install -g @angular/cli```

**PROJET**: Créé une application Angular qui affiche des données à partir d'une base de données JSON simulée.​

**Etape 1: Initialisation**​

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

1- Créez un composant user-list en exécutant la commande suivante : ```ng generate component user-list```

2- Ouvrez le fichier ***src/app/user-list/user-list.component.ts*** et remplacez le contenu par le code suivant:​

```
import { Component, OnInit } from '@angular/core';
import { HttpClient } from '@angular/common/http';

@Component({
  selector: 'app-user-list',
  template: `
    <h2>User List</h2>
    <ul>
      <li *ngFor="let user of users">{{ user.name }}</li>
    </ul>
  `
})
export class UserListComponent implements OnInit {
  users!: any[];

  constructor(private http: HttpClient) {}

  ngOnInit() {
    this.http.get<any[]>('http://localhost:3000/users')
      .subscribe(users => this.users = users);
  }
}
```

3- Ouvrez le fichier ***src/app/app.module.ts*** et ajoutez les importations nécessaires au début du fichier : ```import { HttpClientModule } from '@angular/common/http';​```

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

2- Dans votre terminal, exécutez la commande suivante pour démarrer le serveur JSON : ```node server.js​```

**Étape 4: Affichage des données dans l'application Angular​**

1- Ouvrez le fichier ***src/app/app.component.html*** et remplacez le contenu par le code suivant :​

```<div> <app-user-list></app-user-list> </div>​```

​

2- Dans la section des déclarations du module, ajoutez le composant ***UserListComponent*** : ​
```
 declarations: [ UserListComponent ]​
```
​
```
4- ng serve
```