## 1. Qu’est-ce qu’une convention de nommage ?

Une convention de nommage est un ensemble de règles définissant comment nommer les entités dans le code source. Cela concerne **le nommage des variables, fonctions, classes et autres éléments du code**.

Respecter une convention de nommage n’est pas obligatoire pour qu'un code fonctionne, mais c’est fortement recommandé pour que le code soit lisible et cohérent.

## 2. Principales conventions de nommage

### A) Camel Case (camelCase)
Les éléments en **camelCase** commencent toujours par une lettre minuscule, suivie d'une lettre majuscule au début de chaque mot suivant, par exemple :
```js
let userName = "Steeve"; // deux mots : [user (minuscule)] [Name (N majuscule)]
function calculateTotalPrice() { } // trois mots : [calculate] [Total] [Price]
```

Cette convention est souvent utilisée pour nommer **les variables** et **les fonctions**, car elle rend les noms longs facilement lisibles.

### B) Pascal Case (PascalCase)
Les éléments en **PascalCase** commencent toujours par une lettre majuscule et chaque mot commence également par une majuscule :

```js
class ShoppingCart { }
function GetUserName() { }
```

Cette convention est souvent utilisée pour nommer **les classes**, **les interfaces**, **les enums** etc...

### C) Snake Case (sanke_case)
En **snake_case**, les mots sont séparés par un underscore. Les mots sont généralement en minuscules, mais il est courant de mettre les constantes en majuscule :
```js
let user_name = "Steeve"
class calculate_total_price()
const MAX_VALUE = 5 // En majuscule
```

Cette convention est souvent utilisée pour nommer **les variables**, **les fonctions** et **les constantes**.

- P.S. : Le snake_case en majuscules est une norme pour les constantes.

### D) Kebab Case (kebab-case)
Le **kebab-case** sépare les mots par un tiret, généralement en minuscules :

```
my-component-name
```
Cette convention est souvent utilisée pour **les noms de fichiers** et **les URLs**, rarement directement dans le code.