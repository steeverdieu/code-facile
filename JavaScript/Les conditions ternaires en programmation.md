Les **conditions ternaires** sont un principe en programmation qui permet de **simplifier un bloc `if...else`** afin de le rendre **plus court et plus lisible**.
## Syntaxe générale d'une condition ternaire
La syntaxe suit cette structure :
```
(condition) ? valeur_si_vrai : valeur_si_faux;
```
- On commence par écrire la **condition** entre parenthèses.
- Puis on ajoute un **point d’interrogation (`?`)**.
- Ensuite, on écrit la **valeur à exécuter si la condition est vraie**.
- Puis on ajoute **deux-points (`:`)**.
- Et enfin, la **valeur à exécuter si la condition est fausse**.
## 💡 Exemple concret
Prenons l'exemple suivant en JavaScript :
```js
let age = 20;
let message = "";

if (age >= 18) {
    message = "Majeur";
} else {
    message = "Mineur";
}

console.log(message);

```
On peut réécrire ce bloc en une seule ligne avec une **condition ternaire** :
```js
message = ($age >= 18) ? "Majeur" : "Mineur";
```
### 🔍 Explication
La variable `message` attend une valeur.  
Mais cette valeur dépend du résultat de la condition `(age >= 18)` :
- Si la condition est **vraie**, `message` recevra `"Majeur"`.
- Si la condition est **fausse**, `message` recevra `"Mineur"`.
## Les conditions ternaires imbriquées
En plus des conditions ternaires simples, il est aussi possible d’**imbriquer plusieurs conditions ternaires**, comme on le ferait avec un `if...else if...else`.  
Cela permet de **gérer plusieurs cas**, tout en gardant une écriture compacte.
## 💡 Exemple concret
Prenons un exemple avec une condition qui permet de vérifier si un nombre est **positif**, **négatif** ou **nul** :
```js
let n = 15;
let message = "";

if (n > 0) {
    message = "Ce nombre est positif";
} else if (n < 0) {
    message = "Ce nombre est négatif";
} else {
    message = "Ce nombre est nul";
}

console.log(message);

```
On peut réécrire ce code avec une **condition ternaire imbriquée** :
```js
let message = (n > 0)
    ? "Ce nombre est positif"
    : (n < 0)
        ? "Ce nombre est négatif"
        : "Ce nombre est nul";

console.log(message);

```
### 🧠 Explication

- On commence par tester si `n > 0`.
    - Si c’est vrai → le message sera **"Ce nombre est positif"**.
- Sinon, on passe à une **autre condition** imbriquée : `n < 0`.
    - Si c’est vrai → **"Ce nombre est négatif"**.
    - Sinon (donc le nombre est égal à 0) → **"Ce nombre est nul"**.

👉 Pour chaque `else if`, on peut écrire : `: (condition) ? valeur_si_vrai : valeur_si_faux;`
### ⚠️ Attention à la lisibilité
Même si c’est possible d’enchaîner plusieurs conditions ternaires, **ce n’est pas toujours une bonne idée**.  Plus il y a de cas, plus le code devient **difficile à lire**. Dans ces situations, il est **souvent préférable d’utiliser un `if...else if...else` classique** pour garder le code clair.