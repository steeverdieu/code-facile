En JavaScript, il existe plusieurs façons de parcourir un objet pour récupérer ses **clés** et **valeurs**. Dans cet article, nous allons voir quatre méthodes différentes, avec des exemples concrets. Nous allons utiliser l'objet ci-dessous pour les demonstrations:
```js
const obj = { 
  A: 1, 
  B: 2, 
  C: 3 
};

```
## 1 - Utiliser une boucle `for...in`
La boucle `for...in` permet de parcourir toutes les **propriétés énumérables** d’un objet, y compris celles héritées du prototype.
```js
for (let key in obj) {
  console.log(key);       // Clés : A, B, C
  console.log(obj[key]);  // Valeurs : 1, 2, 3
}
```
#### Attention au prototype

Si des propriétés sont ajoutées au prototype, elles seront aussi parcourues :
```js
Object.prototype.d = 4;

for (let key in obj) {
  console.log(key, obj[key]);
}
// Affiche : A 1, B 2, C 3, d 4
```
Pour ne récupérer que les **clés propres à l’objet**, il faut ajouter une condition :
```js
for (let key in obj) {
  if (obj.hasOwnProperty(key)) {
    console.log(key, obj[key]); 
  }
}
// Affiche : A 1, B 2, C 3
```
## 2 - Utiliser `Object.keys()`

`Object.keys(obj)` retourne **un tableau contenant toutes les clés propres** de l’objet.
```js
const keys = Object.keys(obj);
console.log(keys); // ["A", "B", "C"]

keys.forEach(key => {
  console.log(key, obj[key]);
});
// Affiche : A 1, B 2, C 3
```
- Avantage : seules les clés propres à l’objet sont récupérées.
- Utile si on veut traiter **uniquement les clés**
## 3 - Utiliser `Object.values()`

`Object.values(obj)` retourne **un tableau contenant toutes les valeurs propres** de l’objet.
```js
const values = Object.values(obj);
console.log(values); // [1, 2, 3]

values.forEach(value => {
  console.log(value);
});
// Affiche : 1, 2, 3
```
Pratique si vous voulez travailler **uniquement avec les valeurs**, sans vous soucier des clés.
## 4 - Utiliser `Object.entries()`

`Object.entries(obj)` retourne un **tableau de paires `[clé, valeur]`**, ce qui permet de traiter les clés et valeurs en même temps.
```js
const entries = Object.entries(obj);
console.log(entries); 
// [["A", 1], ["B", 2], ["C", 3]]

for (const [key, value] of Object.entries(obj)) {
  console.log(key, value);
}
// Affiche : A 1, B 2, C 3
```
- Très pratique pour parcourir **simultanément clés et valeurs**.
- La syntaxe de **destructuration** `[key, value]` rend le code lisible et compact.