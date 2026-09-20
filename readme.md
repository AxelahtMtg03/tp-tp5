### Question 1.1
Liste des en-têtes de la réponse HTTP du serveur :

- Status : 200 OK
- connection: keep-alive
- date: Sat, 19 Sep 2026 07:05:13 GMT
- keep-alive: timeout=5
- transfer-encoding: chunked

### Question 1.2
En-têtes qui ont changé depuis la version précédente :

- **Content-Type** : est passé de `text/html` (implicite par défaut) 
  à `application/json`

Le reste (Date, Connection, Keep-Alive, Transfer-Encoding) est inchangé.

### Question 1.3
Le client ne reçoit aucune réponse (la requête reste en attente puis 
expire). En effet, la méthode `fs.readFile` échoue car le fichier 
`index.html` n'existe pas

### Question 1.4
L'erreur affichée dans la console est :
`Error: ENOENT: no such file or directory, open 'C:\Users\axela\OneDrive\Documents\univ\S4\Dev\Js\tp-tp5\index.html'`

Le code d'erreur est **ENOENT** (Error NO ENTry).

ENOENT signifie : "No such file or directory" — le fichier demandé n'existe pas.

### Question 1.5
Code de requestListener() modifié avec gestion d'erreur en async/await

### Question 1.6
Les commandes `npm install cross-env --save` et 
`npm install nodemon --save-dev` ont modifié le projet de la façon suivante :

1. **Ajout de `nodemon` dans `devDependencies`** 
   (dépendance de développement : utile seulement en local)
2. **Création du dossier `node_modules/`** contenant tous les paquets installés
3. **Création du fichier `package-lock.json`** qui verrouille les versions exactes
4. J'ai aussi créé un fichier **`.gitignore`** pour exclure `node_modules/` 
   du dépôt Git

### Question 1.7
Différences entre les scripts `http-dev` et `http-prod` :

- **`http-dev`** lance le serveur avec nodemon, qui **surveille les fichiers** 
  et **redémarre automatiquement** le serveur à chaque modification. 
  `NODE_ENV` est fixé à `development`.
- **`http-prod`** lance le serveur avec node classique, **sans redémarrage automatique**. 
  `NODE_ENV` est fixé à `production`.

Les deux utilisent `cross-env` pour définir la variable `NODE_ENV` de façon 
portable.

### Question 1.8
Codes HTTP reçus pour chacune des pages :

- http://localhost:8000/index.html → **200 OK**
- http://localhost:8000/random.html → **200 OK**
- http://localhost:8000/ → **404 NOT FOUND**
- http://localhost:8000/dont-exist → **404 NOT FOUND**

### Question 2.1
URLs des documentations des modules installés :

- **express** : https://expressjs.com/
- **http-errors** : https://github.com/jshttp/http-errors
- **loglevel** : https://github.com/pimterry/loglevel
- **morgan** : https://github.com/expressjs/morgan

### Question 2.2
Les trois routes fonctionnent :

- `GET /` → renvoie la page `index.html` 
- `GET /index.html` → renvoie la page `index.html` 
- `GET /random/5` → renvoie une page HTML avec une liste de 5 nombres 
  aléatoires 
Les trois routes fonctionnent donc bien.

### Question 2.3
En-têtes renvoyés par Express (observés sur http://localhost:8000/) :

- `accept-ranges: bytes`
- `cache-control: public, max-age=0`
- `connection: keep-alive`
- `content-length: 335`
- `content-type: text/html; charset=utf-8`
- `date: Sun, 20 Sep 2026 11:39:51 GMT`
- `etag: W/"14f-1a0bc3cb2e7"`
- `keep-alive: timeout=5`

**Nouveaux par rapport au serveur HTTP natif :**

- `accept-ranges: bytes` → indique que le serveur supporte les requêtes 
  partielles (utile pour le téléchargement/reprise de gros fichiers).
- `cache-control: public, max-age=0` → directives de cache pour le navigateur.
- `etag: W/"..."` → identifiant de version de la ressource (cache navigateur).

### Question 2.4
L'événement `listening` est déclenché quand le serveur a démarré et commence à écouter sur le port

