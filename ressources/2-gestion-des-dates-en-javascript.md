# 📅 Gestion des dates en JavaScript

## Qu'est-ce que l'objet Date ?

L'objet `Date` en JavaScript permet de travailler avec les dates et les heures. Il est très utile pour enregistrer quand un événement s'est produit, comme l'ajout d'une tâche ou d'un favori.

## Créer une nouvelle date

```js
// Date actuelle
const maintenant = new Date();
console.log(maintenant); // Affiche la date et l'heure actuelles

// Date spécifique
const dateSpecifique = new Date("2024-01-15");
console.log(dateSpecifique); // 15 janvier 2024
```

## Obtenir un timestamp unique

Un **timestamp** est un nombre qui représente le nombre de millisecondes écoulées depuis le 1er janvier 1970. C'est très utile pour créer des identifiants uniques !

```js
// Timestamp actuel (nombre de millisecondes)
const timestamp = new Date().getTime();
console.log(timestamp); // Exemple : 1703123456789

// Version plus courte
const timestampCourt = Date.now();
console.log(timestampCourt); // Même résultat
```

## Formater une date pour l'affichage

```js
const date = new Date();

// Format français
const dateFrancaise = date.toLocaleString("fr-FR");
console.log(dateFrancaise); // "15/12/2024, 14:30:25"

// Format ISO (pour le stockage)
const dateISO = date.toISOString();
console.log(dateISO); // "2024-12-15T13:30:25.123Z"
```

## Exemples pratiques dans nos exercices

### 1. Créer un ID unique pour une tâche

```js
// Dans l'exercice 3 (Todo List)
const nouvelleTache = {
  id: new Date().getTime(),        // ID unique basé sur le timestamp
  text: "Ma nouvelle tâche",
  completed: false,
  date: new Date().toISOString()   // Date de création au format ISO
};
```

### 2. Afficher la date d'ajout d'un favori

```js
// Dans l'exercice 5 (Gestionnaire de favoris)
const dateAjout = new Date(favori.timestamp);
const dateFormatee = dateAjout.toLocaleString("fr-FR");
console.log(`Ajouté le : ${dateFormatee}`);
```

### 3. Créer un nom de fichier avec la date

```js
// Pour l'export de données
const nomFichier = `donnees-${new Date().toISOString().split('T')[0]}.json`;
console.log(nomFichier); // "donnees-2024-12-15.json"
```

## Méthodes utiles de l'objet Date

| Méthode | Description | Exemple |
|---------|-------------|---------|
| `getTime()` | Timestamp en millisecondes | `1703123456789` |
| `toISOString()` | Format ISO pour stockage | `"2024-12-15T13:30:25.123Z"` |
| `toLocaleString()` | Format local pour affichage | `"15/12/2024, 14:30:25"` |
| `getFullYear()` | Année | `2024` |
| `getMonth()` | Mois (0-11) | `11` (décembre) |
| `getDate()` | Jour du mois | `15` |
| `getHours()` | Heure | `14` |
| `getMinutes()` | Minutes | `30` |

## Bonnes pratiques

### ✅ À faire
- Utilisez `new Date().getTime()` pour créer des IDs uniques
- Stockez les dates au format ISO avec `toISOString()`
- Affichez les dates avec `toLocaleString("fr-FR")` pour l'utilisateur

### ❌ À éviter
- Ne créez pas de dates avec des chaînes de caractères ambiguës
- N'oubliez pas que `getMonth()` retourne 0-11 (pas 1-12)
- Ne confondez pas timestamp et date ISO

## Exemple complet

```js
// Créer un événement avec date
const evenement = {
  id: new Date().getTime(),
  titre: "Réunion importante",
  dateCreation: new Date().toISOString(),
  dateAffichage: new Date().toLocaleString("fr-FR")
};

console.log(evenement);
// {
//   id: 1703123456789,
//   titre: "Réunion importante",
//   dateCreation: "2024-12-15T13:30:25.123Z",
//   dateAffichage: "15/12/2024, 14:30:25"
// }
```

---

**Ressource suivante :** [Gestion des erreurs avec try/catch](./3-gestion-des-erreurs-avec-try-catch.md) 