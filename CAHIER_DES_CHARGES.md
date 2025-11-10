# 📋 Cahier des Charges - ACT06 LocalStorage

## 📌 Informations du projet

- **Projet** : ACT06 - LocalStorage Exercices
- **Auteur** : jonaydan
- **Date de création** : 10 novembre 2025
- **Formation** : O'Clock - Falun
- **Objectif** : Maîtriser l'utilisation du localStorage en JavaScript

---

## 🎯 Objectifs pédagogiques

### Compétences visées
- ✅ Comprendre le fonctionnement du localStorage
- ✅ Sauvegarde et récupération de données
- ✅ Manipulation de données JSON (stringify/parse)
- ✅ Gestion d'événements JavaScript
- ✅ Manipulation du DOM dynamique
- ✅ Persistance des données côté client

---

## 📦 Structure du projet

```
ACT06-LocalStorage-jonaydan/
├── README.md
├── CAHIER_DES_CHARGES.md
├── exercices/
│   ├── exercice-1.html       # Premiers pas avec localStorage
│   ├── exercice-2.html       # Gestionnaire de préférences
│   ├── exercice-3.html       # Todo List persistante
│   ├── exercice-4.html       # Panier d'achat
│   └── css/
│       └── pico.min.css      # Framework CSS
└── ressources/
    ├── 1-introduction-au-localstorage.md
    ├── 2-gestion-des-dates-en-javascript.md
    ├── 3-gestion-des-erreurs-avec-try-catch.md
    └── 4-manipulation-des-tableaux-en-javascript.md
```

---

## 🔧 Exercices réalisés

### Exercice 1 : Premiers pas avec localStorage
**Objectif** : Comprendre les opérations de base du localStorage

**Fonctionnalités** :
- ✅ Sauvegarder une valeur texte
- ✅ Charger une valeur sauvegardée
- ✅ Effacer une valeur
- ✅ Validation des champs (vérification valeur vide)
- ✅ Messages de confirmation utilisateur

**Technologies** :
- JavaScript (ES6)
- localStorage API
- querySelector()
- addEventListener()

---

### Exercice 2 : Gestionnaire de préférences utilisateur
**Objectif** : Manipuler différents types de données et sauvegarde automatique

**Fonctionnalités** :
- ✅ Formulaire de préférences multi-champs
  - Nom (input text)
  - Couleur préférée (select)
  - Langue (select)
  - Mode sombre (checkbox)
- ✅ Sauvegarde automatique à chaque changement
- ✅ Chargement automatique au démarrage
- ✅ Stockage en JSON

**Technologies** :
- JSON.stringify() / JSON.parse()
- Événement `change`
- Gestion des différents types d'input
- Gestion des valeurs par défaut

---

### Exercice 3 : Todo List persistante
**Objectif** : Travailler avec des tableaux et objets complexes

**Fonctionnalités** :
- ✅ Ajouter une tâche
- ✅ Marquer une tâche comme terminée
- ✅ Réactiver une tâche
- ✅ Supprimer une tâche
- ✅ Affichage dynamique des tâches
- ✅ Persistance complète des données
- ✅ Génération d'ID uniques (timestamp)
- ✅ Stockage de la date de création

**Structure des données** :
```javascript
{
  texte: "Nom de la tâche",
  terminee: false,
  id: 1699622400000,
  dateCreation: "2025-11-10T12:00:00.000Z"
}
```

**Technologies** :
- Tableaux d'objets JavaScript
- Array.forEach()
- Array.splice()
- createElement() et manipulation du DOM
- Gestion d'événements dynamiques

---

### Exercice 4 : Panier d'achat
**Objectif** : Gérer des données complexes avec calculs en temps réel

**Fonctionnalités** :
- ✅ Catalogue de produits (4 produits disponibles)
  - Pomme - 0.50 €
  - Banane - 0.30 €
  - Pain - 1.20 €
  - Lait - 0.80 €
- ✅ Ajouter un produit au panier
- ✅ Gestion automatique des quantités
- ✅ Augmenter la quantité (+1)
- ✅ Supprimer un produit du panier
- ✅ Calcul automatique du total
- ✅ Persistance du panier

**Structure des données** :
```javascript
{
  id: 1,
  nom: "Pomme",
  prix: 0.50,
  quantity: 2
}
```

**Technologies** :
- Array.find() pour recherche
- Array.forEach() pour affichage
- Calculs mathématiques (prix × quantité)
- toFixed(2) pour formatage des prix
- Gestion d'événements sur boutons dynamiques

---

## 🔄 Traçabilité Git

### Dépôts Git
Le projet est synchronisé sur **deux dépôts Git** :

1. **O-clock-Falun** (dépôt principal de formation)
   - URL : `git@github.com:O-clock-Falun/ACT06-LocalStorage-jonaydan.git`
   - Remote : `origin`
   - Branche : `master`

2. **jonaydan** (dépôt personnel)
   - URL : `git@github.com:jonaydan/ACT06-LocalStorage-jonaydan.git`
   - Remote : `jonaydan`
   - Branche : `master`

### Workflow Git utilisé

```bash
# 1. Ajouter les fichiers modifiés
git add .

# 2. Créer un commit avec message descriptif
git commit -m "Description des modifications"

# 3. Pousser vers O-clock-Falun
git push origin master

# 4. Pousser vers jonaydan
git push jonaydan master
```

### Commits principaux

| Date | Commit | Description |
|------|--------|-------------|
| 10/11/2025 | deaac18 | Exercice 4 complet: Panier d'achat avec gestion des produits, quantités et persistance localStorage |
| 10/11/2025 | 9e00d91 | Exercice 3 complet: Todo List persistante avec localStorage et gestion complète des tâches |
| 10/11/2025 | 54d6c44 | Exercice 2 complet: Sauvegarde et chargement automatique des préférences avec localStorage |
| 10/11/2025 | 0c9eaa2 | Exercice 2: Ajout du formulaire de préférences et sélection des éléments |

---

## 🛠️ Technologies utilisées

### Frontend
- **HTML5** : Structure sémantique
- **CSS** : Framework Pico CSS (design minimaliste)
- **JavaScript (ES6+)** : Logique applicative

### APIs Web
- **localStorage API** : Stockage côté client
- **DOM API** : Manipulation du document
- **Event API** : Gestion des événements

### Outils
- **Git** : Contrôle de version
- **GitHub** : Hébergement des dépôts
- **VS Code** : Éditeur de code
- **DevTools** : Débogage et inspection

---

## ✅ Tests et validation

### Tests fonctionnels effectués

#### Exercice 1
- ✅ Sauvegarder une valeur
- ✅ Rafraîchir la page et charger la valeur
- ✅ Effacer la valeur
- ✅ Vérifier dans DevTools (Application > Local Storage)

#### Exercice 2
- ✅ Modifier chaque champ et vérifier la sauvegarde automatique
- ✅ Rafraîchir la page et vérifier la restauration
- ✅ Vérifier le format JSON dans localStorage

#### Exercice 3
- ✅ Ajouter plusieurs tâches
- ✅ Marquer des tâches comme terminées
- ✅ Supprimer des tâches
- ✅ Rafraîchir la page et vérifier la persistance

#### Exercice 4
- ✅ Ajouter des produits au panier
- ✅ Augmenter les quantités
- ✅ Vérifier le calcul du total
- ✅ Supprimer des produits
- ✅ Rafraîchir la page et vérifier la persistance

---

## 📊 Bonnes pratiques appliquées

### JavaScript
- ✅ Utilisation de `const` et `let` (pas de `var`)
- ✅ Fonctions nommées et réutilisables
- ✅ Séparation des responsabilités
- ✅ Commentaires explicatifs
- ✅ Gestion des cas limites (valeurs null, tableaux vides)

### localStorage
- ✅ Vérification de l'existence des données avant utilisation
- ✅ Utilisation de JSON pour structures complexes
- ✅ Noms de clés clairs et cohérents
- ✅ Sauvegarde après chaque modification

### Git
- ✅ Messages de commit descriptifs
- ✅ Commits réguliers et atomiques
- ✅ Synchronisation sur deux dépôts
- ✅ Respect de la nomenclature des branches

---

## 🎓 Compétences acquises

### Techniques
- ✅ Maîtrise du localStorage (setItem, getItem, removeItem)
- ✅ Sérialisation/désérialisation JSON
- ✅ Manipulation avancée du DOM
- ✅ Gestion d'événements JavaScript
- ✅ Travail avec des structures de données complexes

### Méthodologiques
- ✅ Décomposition d'un problème en fonctions
- ✅ Tests et validation du code
- ✅ Documentation du code
- ✅ Gestion de version avec Git
- ✅ Workflow de développement structuré

---

## 🔗 Liens utiles

- [Documentation localStorage - MDN](https://developer.mozilla.org/fr/docs/Web/API/Window/localStorage)
- [Pico CSS](https://picocss.com/)
- [Git Documentation](https://git-scm.com/doc)

---

## 📝 Notes finales

Ce projet a permis de :
1. Comprendre le fonctionnement du stockage côté client
2. Appliquer les concepts de persistance de données
3. Créer des applications web interactives
4. Pratiquer Git avec plusieurs remotes
5. Documenter et tracer le travail effectué

**Tous les exercices sont fonctionnels et testés.**

---

**Projet réalisé dans le cadre de la formation O'Clock - Promotion Falun**

*Dernière mise à jour : 10 novembre 2025*
