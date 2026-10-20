# Série N°1 : Premiers pas, types et conditions

> **Durée TD :** 40 min | **Durée TP :** 80 min  
> **Chapitre couvert :** Sections 1 à 3 (Premiers pas, variables et types, opérateurs et conditions)  
> **Outils :** DartPad ([dartpad.dev](https://dartpad.dev)) pour le TD ; Dart SDK + VS Code (`dart run`) pour le TP.

---

## 🎯 Objectifs
À la fin de cette série, vous saurez :
- Écrire et exécuter un programme Dart.
- Choisir le bon **type** de donnée.
- Utiliser les **opérateurs**.
- Lire une saisie clavier et prendre des décisions avec `if`, `switch` et l'opérateur ternaire.

---

## 📝 Partie A -- TD (Papier / Réponses écrites) — *40 min*

### Exercice 1 : Prédire les résultats (*10 min*)
*Donnez le résultat affiché par chaque instruction (écrivez `erreur` si le code est refusé).*

| N° | Instruction(s) | Votre réponse |
| :---: | :--- | :--- |
| **1** | `print(10 / 4);` | 2.5 |
| **2** | `print(10 ~/ 4);` | 2 |
| **3** | `print(10 % 4);` | 2|
| **4** | `print('Dart' + ' ' + 'MST');` |  Dart MST |
| **5** | `print('2' + '3');` | 23 |
| **6** | `print(2 + 3 * 4 - 1);` | 13 |
| **7** | `int x = 5; x += 3; x *= 2; print(x);` | 16 |
| **8** | `print(5 > 3 && 2 > 4);` | FALSE|
| **9** | `print(!(5 == 5) \|\| 3 < 4);` |  true |
| **10**| `String? s; print(s ?? 'vide');` | vide |

---

### Exercice 2 : Quel type pour quelle valeur ? (*7 min*)
*Indiquez le type Dart le plus adapté (`int`, `double`, `String`, `bool`) pour chaque valeur ou expression.*

| Valeur / Expression | Votre réponse | Valeur / Expression | Votre réponse |
| :--- | :--- | :--- | :--- |
| `42` | int | `'42'` | string |
| `3.14` | double | `10 / 2` | double |
| `true` | bool | `10 ~/ 2` | int |
| `"Settat"` | string | `7 > 3` | bool |

---

### Exercice 3 : Chasse aux erreurs (*8 min*)
*Le programme suivant contient **6 erreurs**. Repérez-les, indiquez la ligne, le type d'erreur (syntaxe, type, logique) et la correction.*

```dart
1: void main() {
2:   int age = 'vingt';
3:   double prix = 12,5;
4:   String nom = 'Sara";
5:   const tva = 0.2
6:   tva = 0.25;
7:   print('Age : ' + age);
8: }
```

#### Vos réponses :

| Ligne | Type d'erreur | Problème identifié | Correction proposée |
| :---: | :--- | :--- | :--- |
| **2** | Type | on doit affecter un string dans la variable int | `int age = 20;` |
| **3** | Syntaxe | on doit mettre un point au lieu de la virgule |  prix=12.5; |
| **4** | Syntaxe | guillemets| sring nom='sara'; |
| **5** |Syntaxe | on doit mettre ";"| const tva=0.2 ;|
| **6** | Type/Logique | on ne peut pas re-declarer ou modifier const | var tva = 0.2 ;|
| **7** | Type| on ne peut pas concatener string + INT  | print('Age :  $age);  |

---

### Exercice 4 : Conditions (*15 min*)

#### a) Trace de code
*Donnez le résultat des appels suivants selon la fonction ci-dessous :*

```dart
String mention(double m) {
  if (m >= 16) {
    return 'Très bien';
  } else if (m >= 14) {
    return 'Bien';
  } else if (m >= 12) {
    return 'Assez bien';
  } else if (m >= 10) {
    return 'Passable';
  } else {
    return 'Insuffisant';
  }
}
```

| Appel | `mention(17)` | `mention(13.99)` | `mention(10)` | `mention(9.5)` |
| :--- | :---: | :---: | :---: | :---: |
| **Résultat** | très bien | assez bien| passable | insuffisant |

#### b) Expressions booléennes
*Écrivez en Dart la condition qui vaut `true` lorsque :*

1. `a` est compris entre 10 et 20 (bornes incluses) :
```dart
a>=10 && a<=20;
```

2. `n` est un entier **pair et strictement positif** :
```dart
n>0 && n%2==0;
```

3. `annee` est une année **bissextile** (divisible par 4 mais pas par 100, ou divisible par 400) :
```dart
(annee % 4==0 && annee%100 !=0)||(annee%400==0);
```

#### c) Réécriture
*Réécrivez la structure `if/else` suivante avec l'opérateur ternaire :*

```dart
String statut;
if (age >= 18) {
  statut = 'majeur';
} else {
  statut = 'mineur';
}
```

**Votre réécriture :**
```dart
strin statut =age>=18?'majeur':'mineur';
```

---

## 💻 Partie B -- TP (Sur machine) — *80 min*

> 💡 **Consigne :** Créez un dossier `tp1` et enregistrez chaque exercice dans un fichier séparé (`tp1_ex1.dart`, etc.). Exécution : `dart run tp1_ex1.dart`.  
> *Note : Les exercices TP3 à TP5 utilisent `stdin` (non compatibles avec DartPad).*

---

### TP 1 : Environnement et premier programme (*10 min*)

1. **Version installée :**
   ```bash
   # Collez le résultat de `dart --version` ici
   Dart SDK version: 3.13.5 (stable) (Tue Sep 29 01:00:52 2026 -0700) on "windows_x64"

2. **Code de la carte de visite (`tp1_ex1.dart`) :**
```dart
void main(){
String nom='misbahi';
String filière='SIOC';
String ville='monaco';

print('carte visite');
print('nom :  $nom');
print('filière :  $filiere');
print('ville :  $ville');

}
```

3. **Remarque sur l'erreur de syntaxe testée :**
   * compileNewDDC
main.dart:9:24: Error: Expected ';' after this.
print('ville :  $ville')       il apparait un erreur de syntaxe que determine qu'on a oublié ";"

### TP 2 : Calcul d'une facture (*15 min*)

- **Code source (`tp1_ex2.dart`) :**
```dart
void main{
const tva=0.2;
double prixHT=250;
double montantTVA = prixHT*tva;
double prixTTC = prixHT+montantTVA;
print('Prix HT  : ${prixHT.toStringAsFixed(2)} DH');
  print('TVA (20%): ${montantTVA.toStringAsFixed(2)} DH');
  print('Prix TTC : ${prixTTC.toStringAsFixed(2)} DH');
}
```

- **Question :** Pourquoi utiliser `const` plutôt que `var` pour la TVA ?
  > **Réponse :  il empêche toute modification accidentelle du taux au cours de l'exécution et indique une valeur immuable définie dès la compilation

---

### TP 3 : Moyenne et mention (*15 min*)

- **Code source (`tp1_ex3.dart`) :**
```dart
// Collez votre code Dart ici
import 'dart:io';

void main() {
  stdout.write('Nom : ');
  String nom = stdin.readLineSync() ?? 'Inconnu';

  stdout.write('Note 1 : ');
  double? n1 = double.tryParse(stdin.readLineSync() ?? '');
  
  stdout.write('Note 2 : ');
  double? n2 = double.tryParse(stdin.readLineSync() ?? '');

  if (n1 == null || n2 == null) {
    print('invalide.Entrer des nombres valides.');
    return;
  }

  double moy = (n1 + n2) / 2;
  String mention;

  if (moy >= 16) {
    mention = 'Très bien';
  } else if (moy >= 14) {
    mention = 'Bien';
  } else if (moy >= 12) {
    mention = 'Assez bien';
  } else if (moy >= 10) {
    mention = 'Passable';
  } else {
    mention = 'Insuffisant';
  }

  print('$nom : ${moy.toStringAsFixed(2)} ($mention)');
}
```

---

### TP 4 : Calculatrice à deux opérandes (*20 min*)

- **Code source (`tp1_ex4.dart`) :**
```dart
// Collez votre code Dart ici
```import 'dart:io';

void main() {
  stdout.write('a = ');
  double? a = double.tryParse(stdin.readLineSync() ?? '');

  stdout.write('Opérateur (+ - * /) : ');
  String op = stdin.readLineSync() ?? '';

  stdout.write('b = ');
  double? b = double.tryParse(stdin.readLineSync() ?? '');

  if (a == null || b == null) {
    print('Nombres invalides.');
    return;
  }

  switch (op) {
    case '+':
      print('Résultat : ${a + b}');
      break;
    case '-':
      print('Résultat : ${a - b}');
      break;
    case '*':
      print('Résultat : ${a * b}');
      break;
    case '/':
      if (b == 0) {
        print('Erreur : Division par zéro impossible.');
      } else {
        print('Résultat : ${a / b}');
      }
      break;
    default:
      print('Erreur');
  }
}

- **Bonus : Année bissextile (`tp1_ex4_bonus.dart`) :**


import 'dart:io';

void main() {
  stdout.write('Année : ');
  int? annee = int.tryParse(stdin.readLineSync() ?? '');

  if (annee == null) {
    print('Année invalide.');
    return;
  }

  bool bissextile = (annee % 4 == 0 && annee % 100 != 0) || (annee % 400 == 0);
  print('$annee : ${bissextile ? "bissextile" : "non bissextile"}');
}
---

### TP 5 : Conversion d'une durée (*20 min*);

- **Code source (`tp1_ex5.dart`) :**

import 'dart:io';

void main() {
  stdout.write('Saisir une durée en secondes : ');
  int total = int.parse(stdin.readLineSync()!);

  int n = total ~/ 3600;
  int reste = total % 3600;
  int m = reste ~/ 60;
  int s = reste % 60;

  print('$total s = $n n $m min $s s');
}


// Version Défi (sans unités nulles) ;

import 'dart:io';

void main() {
  stdout.write('Saisir une durée en secondes : ');
  int total = int.parse(stdin.readLineSync()!);

  List<String> parties = [];

  int n = total ~/ 3600;
  int m = (total % 3600) ~/ 60;
  int s = total % 60;

  if (n > 0) parties.add('$n n');
  if (m > 0) parties.add('$m min');
  if (s > 0) parties.add('$s s');

  print(parties.isEmpty ? '0 s' : parties.join(' '));
}





## 📦 Livrable
Cochez les éléments à remettre :
- [ ] Le présent fichier Markdown complété
- [ ] Les 5 fichiers `.dart` dans le dossier `tp1`
- [ ] Une capture d'écran d'exécution du **TP3**