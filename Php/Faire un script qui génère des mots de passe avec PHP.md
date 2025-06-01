Commençons par définir les variables qui vont déterminer comment sera construit notre mot de passe. Par exemple, imaginons que nous souhaitons que notre script génère des mots de passe de 8 caractères. Pour cela, nous allons créer une variable qui indiquera cette valeur :

```php
$passwordLength = 8;
```

Ensuite, on va créer une nouvelle variable que l’on appellera `$characters`. Cette variable contiendra une longue chaîne regroupant tous les caractères possibles que notre mot de passe pourra utiliser. Elle inclura :

1. Des lettres minuscules (de a à z):
```php
$characters = "abcdefghijklmnopqrstuvwxyz";
```
2. Des lettres majuscules (de A à Z):
```php
$characters = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";
```
3. Des chiffres (de 0 à 9):
```php
$characters = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
```
4. Enfin, des caractères spéciaux (!@#$%^&*()_-=+[]{}):
```php
$characters = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()_-=+[]{}";
```

Maintenant, définissons une dernière variable que nous appellerons `$password`. C’est dans cette variable que le mot de passe généré sera stocké.  Au départ, elle sera vide, puisqu’on nous n’avons encore rien généré :
```php
$password = '';
```

À ce stade, le code complet complet de notre script ressemble à ça:
```php
<?php
	$passwordLength = 8;
	$characters = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()_-=+[]{}";
	$password = '';
```

Pour générer notre mot de passe de 8 caractères *(qui est la valeur contenue dans la variable `$passwordLength`)*, on va utiliser une boucle `for` qui sera s’exécutée 8 fois. À chaque tour, on va sélectionner un caractère au hasard dans la chaîne `$characters`, puis l’ajouter à la variable `$password`.

```php
// Cette boucle sera executée 8 fois (La valeur de la variable length)
for ($i = 0; $i < $passwordLength; $i++) {
	// Ici on choisit au hasard un caractère dans la chaîne de la variable $characters
	// et on l’ajoute au mot de passe
}
```
**Pour choisir un caractère dans notre longue chaîne `$characters`, rien de compliqué.**  
En PHP, une chaîne de caractères peut être manipulée **comme un tableau** : on peut accéder à chaque caractère en indiquant son **index** (sa position dans la chaîne).

Par exemple :

- `$characters[0]` donne le **premier** caractère,
- `$characters[1]` donne le **deuxième**,  
- etc.

Par exemple :

- `$characters[0]` donne le premier caractère,
- `$characters[1]` donne le deuxième,
- et ainsi de suite.

**Ce qui nous intéresse ici, c’est de choisir un caractère au hasard à chaque tour de boucle.**  
Et pour cela, on a besoin de **générer un nombre aléatoire** qui servira d’index dans la chaîne `$characters`.

PHP propose une fonction très pratique : `random_int`.  
Elle permet de générer un nombre entier aléatoire entre deux valeurs.

### 👉 Elle prend deux paramètres :

- Le **premier** représente la plus petite valeur possible (dans notre cas : `0`, pour le premier caractère).
- Le **deuxième** représente la plus grande valeur possible (dans notre cas : la **longueur de la chaîne moins 1**).

Pour connaître la longueur d’une chaîne, on utilise la fonction `strlen()` :
```php
strlen($characters)
```
Mais attention : puisque les index commencent à 0, il faut soustraire 1 à cette longueur pour ne pas dépasser.

Donc, notre code pour obtenir un index aléatoire sera :
```php
random_int(0, strlen($characters) - 1)
```
Et pour récupérer le caractère correspondant à cet index dans la chaîne :
```php
$characters[random_int(0, strlen($characters) - 1)]
```
On va stocker ce caractère dans une variable appellée `$randomCharacter` et l'ajouter à `$password`: 
```php
for ($i = 0; $i < $passwordLength; $i++) {
	// Ici on choisit au hasard un caractère dans la chaîne de la variable $characters
	$randomCharacter = $characters[random_int(0, strlen($characters) - 1)];
	// On ajoute ce caractère au mo de passe
	$password .= $randomCharacter;
}
```

Et pour finir, on peut afficher à l'extérieur de la boucle un petit message avec un echo pour indiquer le mot de passe générer
```php
echo "Le mot de passe généré est: " . $password
```
Le code complet du script:
```php
<?php
	$passwordLength = 8;
	$characters = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()_-=+[]{}";
	$password = '';
	$charactersLength = strlen($characters);
	for ($i = 0; $i < $passwordLength; $i++) {
		// Ici on choisit au hasard un caractère dans la chaîne de la variable $characters
		$randomCharacter = $characters[random_int(0, strlen($characters) - 1)];
		// On ajoute ce caractère au mo de passe
		$password .= $randomCharacter;
	}
	echo "Le mot de passe généré est: " . $password
?>
```