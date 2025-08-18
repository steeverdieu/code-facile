## 1. Qu’est-ce qu’une convention de nommage ?

Une convention de nommage est un ensemble de règles définissant comment nommer les entités dans le code source. Cela concerne **le nommage des variables, fonctions, classes et autres éléments du code**.

Respecter une convention de nommage n’est pas obligatoire pour qu'un code fonctionne, mais c’est fortement recommandé pour que le code soit lisible et cohérent.

## 2. Principales conventions de nommage

### A) Camel Case (camelCase)
Le **camelCase** commence toujours par une lettre minuscule et on met une lettre majuscule au début de chaque mot suivant, par exemple:
```js
let userName = "Steeve";
function calculateTotalPrice() { }
```

Cette convention de nommage est souvent utilisée pour nommer les variables et les fonctions.

### B) Pascal Case (PascalCase)
Le **PascalCase** commence par une lettre majuscule et on met également une lettre majuscule au début de chaque mot :
```js
class ShoppingCart { }
function GetUserName() { }
```

Cette convention de nommage est souvent utilisée pour nommer **les classes**, **les interfaces** et **les enums**.

### C) Snake Case (sanke_case)
Le **snake_case** sépare les mots par un underscore. Le snake case est généralement en minuscules, mais il arrive de mettre les mots en majuscule :
```js
let user_name = "Steeve"
class calculate_total_price()
const MAX_VALUE = 5
```

Cette convention de nommage est souvent utilisée pour nommer **les variables**, **les fonctions** et **les constantes**.

- P.S: On utilise souvent le snake scase en majuscule pour nommer les constantes

### D) Kebab Case (kebab-case)
Le **snake_case** sépare les mots par un tiret, généralement en minuscules:
```
my-component-name
```
Cette convention de nommage est souvent utilisée pour **les noms de fichiers** et **les URLs**, rarement dans le code directement.