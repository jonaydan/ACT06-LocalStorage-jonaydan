# 🛡️ Gestion des erreurs avec try/catch

## Pourquoi gérer les erreurs ?

En programmation, des erreurs peuvent survenir à tout moment. Sans gestion d'erreurs, votre application peut "planter" et l'utilisateur ne comprendra pas ce qui s'est passé. La gestion d'erreurs permet de :

- **Éviter les crashes** de l'application
- **Informer l'utilisateur** de ce qui ne va pas
- **Continuer l'exécution** même en cas de problème
- **Déboguer** plus facilement

## Structure try/catch

```js
try {
  // Code qui peut générer une erreur
  const resultat = operationRisquee();
} catch (error) {
  // Code exécuté si une erreur se produit
  console.error("Une erreur s'est produite:", error);
}
```

## Exemples concrets

### 1. Gestion des erreurs localStorage

```js
function sauvegarderDonnees(donnees) {
  try {
    // Tentative de sauvegarde dans le localStorage
    localStorage.setItem("mesDonnees", JSON.stringify(donnees));
    console.log("Données sauvegardées avec succès !");
  } catch (error) {
    // Si une erreur se produit (ex: quota dépassé)
    console.error("Erreur lors de la sauvegarde:", error);
    alert("Impossible de sauvegarder les données. Vérifiez l'espace disponible.");
  }
}
```

### 2. Validation de données

```js
function ajouterFavori(url, titre) {
  try {
    // Vérification des données
    if (!url || !titre) {
      throw new Error("URL et titre sont obligatoires");
    }
    
    if (!url.startsWith("http://") && !url.startsWith("https://")) {
      throw new Error("L'URL doit commencer par http:// ou https://");
    }
    
    // Ajout du favori
    const favori = { url, titre, date: new Date().toISOString() };
    favoris.push(favori);
    
  } catch (error) {
    console.error("Erreur lors de l'ajout du favori:", error.message);
    alert(`Erreur: ${error.message}`);
  }
}
```

### 3. Lecture de données JSON

```js
function chargerDonnees() {
  try {
    // Tentative de lecture et parsing JSON
    const donneesBrutes = localStorage.getItem("mesDonnees");
    const donnees = JSON.parse(donneesBrutes);
    return donnees;
  } catch (error) {
    // Si le JSON est invalide ou si localStorage échoue
    console.error("Erreur lors du chargement:", error);
    return []; // Retourne un tableau vide par défaut
  }
}
```

## Types d'erreurs courantes

### 1. Erreurs localStorage

```js
try {
  localStorage.setItem("cle", "valeur");
} catch (error) {
  if (error.name === "QuotaExceededError") {
    alert("L'espace de stockage est plein. Supprimez des données.");
  } else {
    alert("Erreur de stockage: " + error.message);
  }
}
```

### 2. Erreurs de parsing JSON

```js
try {
  const donnees = JSON.parse(chaineJSON);
} catch (error) {
  if (error instanceof SyntaxError) {
    alert("Format de données invalide");
  } else {
    alert("Erreur inconnue: " + error.message);
  }
}
```

### 3. Erreurs de validation

```js
function validerEmail(email) {
  try {
    if (!email.includes("@")) {
      throw new Error("L'email doit contenir un @");
    }
    if (!email.includes(".")) {
      throw new Error("L'email doit contenir un point");
    }
    return true;
  } catch (error) {
    alert(error.message);
    return false;
  }
}
```

## Bonnes pratiques

### ✅ À faire
- **Toujours** utiliser try/catch pour les opérations risquées
- **Informer l'utilisateur** avec des messages clairs
- **Logger les erreurs** dans la console pour le débogage
- **Fournir des valeurs par défaut** quand c'est possible

### ❌ À éviter
- Ne pas laisser les erreurs "silencieuses"
- Ne pas afficher les détails techniques à l'utilisateur
- Ne pas ignorer les erreurs localStorage
- Ne pas faire de try/catch pour tout (seulement les opérations risquées)

## Exemple complet dans un exercice

```js
// Dans l'exercice 5 (Gestionnaire de favoris)
function ajouterAuxFavoris(url, titre) {
  try {
    // Validation des données
    if (!url || !titre) {
      throw new Error("Veuillez remplir tous les champs");
    }
    
    if (!url.startsWith("http://") && !url.startsWith("https://")) {
      throw new Error("L'URL doit commencer par http:// ou https://");
    }
    
    // Vérification des doublons
    const existeDeja = favoris.find(fav => fav.url === url);
    if (existeDeja) {
      throw new Error("Ce site est déjà dans vos favoris");
    }
    
    // Ajout du favori
    const nouveauFavori = {
      url: url,
      titre: titre,
      date: new Date().toISOString()
    };
    
    favoris.unshift(nouveauFavori);
    
    // Sauvegarde dans localStorage
    localStorage.setItem("favoris", JSON.stringify(favoris));
    
    // Message de succès
    alert("Favori ajouté avec succès !");
    
  } catch (error) {
    // Gestion de l'erreur
    console.error("Erreur:", error);
    alert(`Erreur: ${error.message}`);
  }
}
```

## Structure try/catch/finally (optionnel)

```js
try {
  // Code qui peut générer une erreur
  const donnees = chargerDonnees();
} catch (error) {
  // Gestion de l'erreur
  console.error("Erreur:", error);
} finally {
  // Code toujours exécuté (succès ou erreur)
  console.log("Opération terminée");
}
```

---

**Ressource suivante :** [Manipulation des tableaux en JavaScript](./4-manipulation-des-tableaux-en-javascript.md) 