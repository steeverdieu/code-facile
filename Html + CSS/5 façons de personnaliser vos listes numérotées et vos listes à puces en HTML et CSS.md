Les listes en HTML sont très utilisées : que ce soit pour afficher des étapes, des menus ou des points importants. On distingue deux grands types de listes :

- **les listes ordonnées** (`<ol>`), numérotées automatiquement,
- **les listes non ordonnées** (`<ul>`), qui affichent des puces (ou "bulles").

Dans cet article, nous allons voir **5 astuces pratiques** pour personnaliser vos listes avec HTML et CSS.
## 1. Changer le numéro de départ d’une liste ordonnée

Par défaut, une liste ordonnée (`<ol>`) commence toujours par le chiffre **1**.  
Si vous voulez qu’elle commence à un autre numéro, utilisez l’attribut **`start`**.
```html
<ol start="5">
  <li>Premier élément</li>
  <li>Deuxième élément</li>
  <li>Troisième élément</li>
</ol>
```
👉 Ici, la liste commencera à **5** au lieu de 1.
## 2. Inverser la numérotation d’une liste

HTML propose aussi l’attribut **`reversed`** pour inverser la numérotation.
```html
<ol reversed>
  <li>Premier élément</li>
  <li>Deuxième élément</li>
  <li>Troisième élément</li>
</ol>
```
👉 La liste commence par le nombre le plus élevé et descend jusqu’à 1.

Vous pouvez même **combiner** `start` et `reversed` :
```html
<ol start="10" reversed>
  <li>Élément A</li>
  <li>Élément B</li>
  <li>Élément C</li>
</ol>
```
👉 Ici, la liste débute à **10** et se décrémente : 10, 9, 8…
## 3. Donner une valeur personnalisée à un item

Chaque élément `<li>` peut recevoir une numérotation **spécifique** grâce à l’attribut **`value`**.
```html
<ol>
  <li value="5">Premier élément</li>
  <li value="10">Deuxième élément</li>
  <li value="50">Troisième élément</li>
</ol>
```

👉 Résultat : le premier élément est numéroté **5**, le deuxième **10**, et le troisième **50**.  
La numérotation continue automatiquement après chaque valeur donnée.
## 4. Changer la couleur des puces d’une liste non ordonnée

Pour les listes à puces (`<ul>`), vous pouvez personnaliser la couleur des bulles avec le pseudo-élément **`::marker`** en CSS.
```css
ul li::marker {
  color: red;
  font-size: 20px;
}
```
👉 Ici, les puces deviennent rouges et plus grandes.
## 5. Remplacer les puces par une icône personnalisée

Vous pouvez aussi **supprimer les puces par défaut** et en ajouter de nouvelles avec `::before`.
```html
<ul class="custom">
  <li>Accueil</li>
  <li>Services</li>
  <li>Contact</li>
</ul>
```

```css
.custom {
  list-style-type: none; /* supprime les puces par défaut */
  padding: 0;
}

.custom li::before {
  content: "✔ "; /* ou une icône personnalisée */
  color: green;
  font-weight: bold;
}
```
👉 Ici, chaque élément de la liste est précédé d’un **check vert** au lieu d’une puce classique.
## Conclusion

En HTML et CSS, il est très simple de **personnaliser vos listes** pour les rendre plus claires et esthétiques.  
Vous pouvez :

1. Modifier le numéro de départ (`start`)
2. Inverser la numérotation (`reversed`)
3. Donner une valeur spécifique à chaque élément (`value`)
4. Changer la couleur et la taille des puces (`::marker`)
5. Remplacer les puces par une icône (`::before`)
