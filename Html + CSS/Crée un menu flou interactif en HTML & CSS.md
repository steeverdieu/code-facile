Dans cet article, je vais te montrer comment flouter du texte à l’aide de HTML et CSS, tout en construisant un joli petit menu flou. Voici un exemple de ce que nous allons faire ensemble :
![Aperçu du menu flou](assets/blurry-menu.gif)

### Prérequis

Pour reproduire ce menu, tu n’as besoin que de deux choses :
- Les bases du **HTML**
- Les bases du **CSS**

### La partie HTML

La partie HTML est très simple :

```html
<nav class="menu">
  <a href="#">Home</a>
  <a href="#">About</a>
  <a href="#">Services</a>
  <a href="#">Contact</a>
</nav>
```

Comme tu peux le voir, j’ai créé un élément `<nav>` auquel j’ai donné la classe `"menu"`. Cet élément est utilisé pour insérer tous les éléments de navigation.

**P.S.** : J’aurais pu utiliser un `<div>` à la place du `<nav>`, le résultat visuel aurait été le même. Mais pour respecter une structure HTML sémantique, il est plus logique d’utiliser `<nav>` pour indiquer que cet élément représente un menu de navigation.

### La partie CSS

Commençons par mettre l’arrière-plan de la page en noir :

```css
body {
  background-color: #3c3c3c;
}
```

Ensuite, plaçons tous les éléments au centre de la page à l’aide de flexbox, et donnons une largeur à notre élément `<nav class="menu">`.

Tu peux choisir la largeur que tu veux. Ensuite, stylisons les éléments du menu :

```css
body {
  background-color: #3c3c3c;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.menu {
  display: flex;
  gap: 30px;
}

.menu a {
  font-size: 2em;
  font-weight: bold;
  text-decoration: none;
  color: transparent;
  text-shadow: 0 0 8px rgba(255, 255, 255, 0.5);
}
```

### Comment rendre le texte flou ?

Pour flouter le texte, on va utiliser la propriété **`text-shadow`**. Pour rappel, cette propriété prend 4 paramètres :

```css
text-shadow: distance-horizontale distance-verticale rayon-de-flou couleur;
```

- **distance-horizontale** : décalage horizontal de l’ombre
- **distance-verticale** : décalage vertical
- **rayon-de-flou** _(optionnel)_ : plus il est élevé, plus l’ombre est floue
- **couleur** : la couleur de l’ombre

Ce qui nous intéresse ici, c’est le **rayon-de-flou**, car c’est lui qui va nous permettre de créer l’effet de flou sur le texte.

Mais attention ! Si tu appliques cette ombre à un texte **blanc**, tu ne verras pas bien l’effet. Pour que le flou soit visible, il faut que la **couleur du texte soit transparente**.

Donc on applique ça dans notre CSS :

```css
.menu a {
  color: transparent;
  text-shadow: 0 0 8px rgba(255, 255, 255, 0.5);
}
```

Et voilà ! 🤩

### La dernière étape

Maintenant, on veut que **lorsqu’on passe la souris sur un lien du menu**, le texte devienne lisible. On va donc modifier la couleur du texte et enlever le flou quand il y a un **hover** :

```css
.menu a:hover {
  color: white;
  text-shadow: none;
}
```

Et pour rendre la transition douce entre le texte flou et le texte net, on ajoute simplement une **transition** :

```css
.menu a {
  transition: all 0.3s ease;
}
```

### Et voilà, c’est terminé ! 😊

Tu viens de créer un menu à effet de flou stylé en HTML/CSS. Bravo !

Et voici le **code CSS complet**:

```css
/* Style global de la page */
body {
  background-color: #3c3c3c;
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  font-family: sans-serif;
}

/* Menu */
.menu {
  display: flex;
  gap: 40px;
}

/* Liens du menu */
.menu a {
  font-size: 2em;
  font-weight: bold;
  text-decoration: none;
  color: transparent;
  text-shadow: 0 0 8px rgba(255, 255, 255, 0.5);
  transition: all 0.3s ease;
  cursor: pointer;
}

/* État au survol */
.menu a:hover {
  color: white;
  text-shadow: none;
}
```