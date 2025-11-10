# 📦 Comprendre et utiliser localStorage en JavaScript

## Qu'est-ce que localStorage ?

`localStorage` est une fonctionnalité du navigateur web qui permet de stocker des données (sous forme de texte) directement dans le navigateur de l'utilisateur. Les données restent enregistrées même si on ferme l'onglet ou le navigateur.

- **Capacité** : environ 5 Mo par site
- **Portée** : spécifique à chaque domaine (site)
- **Durée** : persiste tant que l'utilisateur ne vide pas le stockage ou que le site ne les supprime pas

## À quoi ça sert ?

- Garder en mémoire des préférences utilisateur (thème, langue...)
- Se souvenir d'un token d'authentification
- Retrouver un panier d'achat, des brouillons, etc.

## Comment stocker une valeur ?

```js
// Stocker une valeur (toujours sous forme de texte !)
localStorage.setItem("maCle", "maValeur");
```

## Comment lire une valeur ?

```js
// Lire une valeur (ou null si la clé n'existe pas)
const valeur = localStorage.getItem("maCle");
console.log(valeur); // Affiche "maValeur"
```

## Comment supprimer une valeur ?

```js
// Supprimer une valeur
localStorage.removeItem("maCle");
```

## Comment tout vider ?

```js
// Supprimer toutes les données du site
localStorage.clear();
```

## Bonnes pratiques et pièges à éviter

- **Tout est stocké en texte** : pour stocker un objet, il faut utiliser `JSON.stringify` et `JSON.parse`.
  ```js
  // Stocker un objet
  const user = { nom: "Alice", age: 25 };
  localStorage.setItem("utilisateur", JSON.stringify(user));

  // Lire un objet
  const userString = localStorage.getItem("utilisateur");
  const userObj = JSON.parse(userString);
  ```
- **Ne jamais stocker de données sensibles** (mot de passe, numéro de carte, etc.)
- **Attention à la taille** : ne pas stocker de gros fichiers ou images
- **localStorage est synchrone** : évitez d'y faire trop d'accès dans des boucles lourdes

## Exemple concret : retenir le pseudo d'un utilisateur

```js
// Au moment où l'utilisateur saisit son pseudo :
const pseudo = "Bob";
localStorage.setItem("pseudo", pseudo);

// Plus tard, pour le retrouver :
const pseudoSauvegarde = localStorage.getItem("pseudo");
if (pseudoSauvegarde !== null) {
  alert("Bienvenue, " + pseudoSauvegarde + " !");
}
```

## 🔎 Comment consulter le localStorage dans les principaux navigateurs ?

Il est possible de visualiser et modifier le contenu du localStorage directement depuis les outils de développement de votre navigateur. Voici comment faire selon le navigateur utilisé :

### Chrome

1. Ouvrez votre page web.
2. Faites un clic droit puis sélectionnez « Inspecter » ou appuyez sur `F12` pour ouvrir les outils de développement.
3. Allez dans l’onglet **Application**.
4. Dans le menu de gauche, ouvrez la section **Stockage** puis cliquez sur **Local Storage** et sélectionnez votre domaine.
5. Vous verrez la liste des clés/valeurs stockées.

### Firefox

1. Ouvrez votre page web.
2. Faites un clic droit puis sélectionnez « Examiner l’élément » ou appuyez sur `F12`.
3. Rendez-vous dans l’onglet **Stockage**.
4. Dans le panneau de gauche, ouvrez **localStorage** puis sélectionnez votre site.
5. Les données s’affichent dans le panneau principal.

### Edge

1. Ouvrez votre page web.
2. Faites un clic droit puis sélectionnez « Inspecter » ou appuyez sur `F12`.
3. Allez dans l’onglet **Application**.
4. Dans le menu de gauche, ouvrez **Stockage** puis **Local Storage** et choisissez votre domaine.
5. Les données apparaissent à droite.

### Safari

1. Ouvrez Safari puis allez dans les **Préférences** > **Avancées** et cochez « Afficher le menu Développement ».
2. Ouvrez votre page web.
3. Dans la barre de menu, cliquez sur **Développement** > **Afficher l’inspecteur web**.
4. Allez dans l’onglet **Stockage** (ou **Storage** en anglais).
5. Sélectionnez **localStorage** dans la liste de gauche pour voir les données.

---

### 🧪 Exemple de code utilisé pour tester

Vous pouvez utiliser le code suivant pour ajouter des données dans le localStorage, puis les visualiser dans les outils de développement comme expliqué ci-dessus :

```js
localStorage.setItem("pseudo", "John");
localStorage.setItem("age", 20);
localStorage.setItem("isAdmin", true);
localStorage.setItem("lastLogin", new Date().toISOString());
localStorage.setItem("preferences", JSON.stringify({
  theme: "dark",
  language: "fr"
}));
```

Voici à quoi peut ressembler le localStorage dans les outils de développement :

![localStorage](./ressources/assets/demo.png)

## Sécurité et confidentialité

- Les données sont accessibles par **tout le JavaScript du site**
- Elles peuvent être lues par toute personne ayant accès à l'ordinateur (via les outils du navigateur)
- Ne jamais y stocker de secrets ou d'informations confidentielles

---

Pour aller plus loin : [MDN Web Docs - localStorage](https://developer.mozilla.org/fr/docs/Web/API/Window/localStorage) 