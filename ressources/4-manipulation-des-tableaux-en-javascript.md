# 📋 Manipulation des tableaux en JavaScript

## Qu'est-ce qu'un tableau ?

Un tableau (array) est une structure de données qui permet de stocker plusieurs valeurs dans une seule variable. C'est très utile pour gérer des listes d'éléments comme des tâches, des favoris, ou des produits.

```js
// Tableau simple
const couleurs = ["rouge", "vert", "bleu"];

// Tableau d'objets
const utilisateurs = [
  { nom: "Alice", age: 25 },
  { nom: "Bob", age: 30 }
];
```

## Méthodes essentielles

### 1. Ajouter des éléments

```js
const fruits = ["pomme", "banane"];

// Ajouter à la fin
fruits.push("orange");
console.log(fruits); // ["pomme", "banane", "orange"]

// Ajouter au début
fruits.unshift("kiwi");
console.log(fruits); // ["kiwi", "pomme", "banane", "orange"]
```

### 2. Supprimer des éléments

```js
const nombres = [1, 2, 3, 4, 5];

// Supprimer le dernier élément
nombres.pop();
console.log(nombres); // [1, 2, 3, 4]

// Supprimer le premier élément
nombres.shift();
console.log(nombres); // [2, 3, 4]

// Supprimer à un index spécifique
nombres.splice(1, 1); // Supprime 1 élément à partir de l'index 1
console.log(nombres); // [2, 4]
```

### 3. Rechercher des éléments

```js
const etudiants = [
  { id: 1, nom: "Alice", note: 15 },
  { id: 2, nom: "Bob", note: 12 },
  { id: 3, nom: "Charlie", note: 18 }
];

// Trouver un élément
const alice = etudiants.find(etudiant => etudiant.nom === "Alice");
console.log(alice); // { id: 1, nom: "Alice", note: 15 }

// Trouver l'index d'un élément
const indexBob = etudiants.findIndex(etudiant => etudiant.nom === "Bob");
console.log(indexBob); // 1
```

### 4. Parcourir un tableau

```js
const fruits = ["pomme", "banane", "orange"];

// Méthode forEach
fruits.forEach((fruit, index) => {
  console.log(`${index + 1}. ${fruit}`);
});

// Méthode map (créer un nouveau tableau)
const fruitsMajuscules = fruits.map(fruit => fruit.toUpperCase());
console.log(fruitsMajuscules); // ["POMME", "BANANE", "ORANGE"]

// Méthode filter (filtrer les éléments)
const fruitsLongs = fruits.filter(fruit => fruit.length > 5);
console.log(fruitsLongs); // ["banane", "orange"]
```

## Exemples pratiques dans nos exercices

### 1. Gestion FIFO (First In, First Out)

```js
// Dans l'exercice 5 (Gestionnaire de favoris)
const favoris = [];

function ajouterFavori(nouveauFavori) {
  // Ajouter au début (plus récent en premier)
  favoris.unshift(nouveauFavori);
  
  // Limiter à 10 éléments (FIFO)
  if (favoris.length > 10) {
    favoris.splice(10); // Supprime les éléments après l'index 10
  }
}
```

### 2. Suppression d'éléments

```js
// Dans l'exercice 3 (Todo List)
function supprimerTache(idTache) {
  // Trouver l'index de la tâche
  const index = taches.findIndex(tache => tache.id === idTache);
  
  if (index !== -1) {
    // Supprimer la tâche
    taches.splice(index, 1);
  }
}
```

### 3. Recherche et modification

```js
// Dans l'exercice 4 (Panier d'achat)
function ajouterAuPanier(produit) {
  // Chercher si le produit existe déjà
  const produitExistant = panier.find(item => item.id === produit.id);
  
  if (produitExistant) {
    // Augmenter la quantité
    produitExistant.quantity += 1;
  } else {
    // Ajouter un nouveau produit
    panier.push({
      id: produit.id,
      nom: produit.nom,
      prix: produit.prix,
      quantity: 1
    });
  }
}
```

### 4. Calculs sur les tableaux

```js
// Calculer le total du panier
const total = panier.reduce((somme, item) => {
  return somme + (item.prix * item.quantity);
}, 0);

console.log(`Total: ${total.toFixed(2)} €`);
```

## Méthodes avancées

### 1. reduce() - Réduire un tableau à une valeur

```js
const notes = [15, 12, 18, 14, 16];

// Calculer la moyenne
const moyenne = notes.reduce((somme, note) => somme + note, 0) / notes.length;
console.log(moyenne); // 15
```

### 2. slice() - Extraire une portion

```js
const nombres = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// Garder seulement les 5 premiers
const premiers = nombres.slice(0, 5);
console.log(premiers); // [1, 2, 3, 4, 5]
```

### 3. includes() - Vérifier si un élément existe

```js
const couleurs = ["rouge", "vert", "bleu"];

if (couleurs.includes("vert")) {
  console.log("La couleur verte est disponible");
}
```

## Bonnes pratiques

### ✅ À faire
- Utilisez `push()` pour ajouter à la fin
- Utilisez `unshift()` pour ajouter au début
- Utilisez `find()` pour rechercher un élément
- Utilisez `filter()` pour filtrer
- Utilisez `map()` pour transformer

### ❌ À éviter
- Ne modifiez pas un tableau pendant que vous le parcourez
- N'oubliez pas que `findIndex()` retourne -1 si rien n'est trouvé
- Ne confondez pas `splice()` et `slice()`

## Exemple complet

```js
// Gestionnaire de tâches
let taches = [];

function ajouterTache(texte) {
  const nouvelleTache = {
    id: new Date().getTime(),
    texte: texte,
    terminee: false,
    date: new Date().toISOString()
  };
  
  taches.push(nouvelleTache);
  afficherTaches();
}

function supprimerTache(id) {
  const index = taches.findIndex(tache => tache.id === id);
  if (index !== -1) {
    taches.splice(index, 1);
    afficherTaches();
  }
}

function marquerTerminee(id) {
  const tache = taches.find(tache => tache.id === id);
  if (tache) {
    tache.terminee = !tache.terminee;
    afficherTaches();
  }
}

function afficherTaches() {
  const tachesTerminees = taches.filter(tache => tache.terminee);
  const tachesEnCours = taches.filter(tache => !tache.terminee);
  
  console.log(`Tâches en cours: ${tachesEnCours.length}`);
  console.log(`Tâches terminées: ${tachesTerminees.length}`);
}
```

---

**Ressource suivante :** [Validation des données en JavaScript](./5-validation-des-donnees-en-javascript.md) 