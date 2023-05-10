# Workshop_clem-ju
Workshop_epitech


Objéctif: découvrir Angular et les appels aux bases de données.​

**INSTALATION**: 

```npm install -g @angular/cli```

**PROJET**: Créé une application Angular qui affiche des données à partir d'une base de données JSON simulée.​

**Etape 1: Initialisation**​

1- Ouvrez votre terminal ou votre invite de commandes et créez un nouveau dossier pour votre projet.​

2- Accédez au dossier du projet et exécutez la commande suivante pour créer une nouvelle application Angular : ng new angular-database-app​

3- cd angular-database-app​

4- Installez la dépendance json-server qui nous permettra de simuler une base de données JSON : npm install json-server​

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