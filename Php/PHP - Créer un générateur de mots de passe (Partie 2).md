Commençons par organiser notre générateur de mots de passe en séparant chaque type de caractère dans une variable distincte. Pour rappel, un mot de passe sécurisé doit contenir :
- des lettres minuscules,
- des lettres majuscules,
- des chiffres,
- et des caractères spéciaux.
Nous allons donc découper notre longue chaîne de caractères en quatre groupes, chacun stocké dans sa propre variable :
```php
// On définit les groupes de caractères disponibles dans leur propre variable

$lowercaseCharacters = "abcdefghijklmnopqrstuvwxyz";
$uppercaseCharacters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
$uppercaseCharacters = "0123456789";
$specialCharacters = "!@#$%^&*()_-=+[]{}";
```
Ensuite, rassemblons tous les groupes de caractères que nous avons définis précédemment pour reconstruire notre chaîne initiale. L'idée est de les combiner dans une seule variable, que nous appellerons `$characters`. Cette variable contiendra donc l’ensemble des caractères utilisables pour générer un mot de passe sécurisé :
```php
$characters = $lowercaseCharacters . $uppercaseCharacters . $numbers . $specialCharacters;
```
Notre code complet pour l'instant ressemble à ceci:
```php
$passwordLength = 8;
$password = '';

// On définit les groupes de caractères disponibles dans leur propre variable

$lowercaseCharacters = "abcdefghijklmnopqrstuvwxyz";
$uppercaseCharacters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
$numbers = "0123456789";
$specialCharacters = "!@#$%^&*()_-=+[]{}";
  
// On rassemble tous les groupes de caractères en une seule chaine
$characters = $lowercaseCharacters . $uppercaseCharacters . $numbers . $specialCharacters;
```
Une fois ce travail fait, on va s'assurer de prendre au hasard un caractère dans chaque groupe de chaine. C'est à dire, on va extraire au hasard une lettre minuscule dans la variable `$lowercaseCharacters`, une lettre majuscule dans la variable `$uppercaseCharacters`, un chiffre dans la variable `$uppercaseCharacters` et un caractère spécial dans la variable `$specialCharacters`. Pour éviter de se répeter, on va definir une fonction qui fera pour nous ce travail. On l'appellera `getCharaters` et prendra en paramettre la chaine en question.
```php
function getCharacters($str) {

  // Script pour recuper un caractère au hasard de la chaine passée en paramètre (ici str)

}
```
Pour rappel, dans la version précedente de notre script, pour récuperer un caractère au hasard d'une chaine on fasait comme suit:
```php
// On choisit un index compris entre zero et la longueur de la chaine
$randomIndex = random_int(0, strlen($characters) - 1);
// Ensuite on recupere le caractère qui correspond à l'index en question
$randomCahracters = $characters[$randomIndex];
```
On va reutiliser ces lignes dans notre fonction `getCharacters`, mais en les appliquant a la variable passée en paramètre:
```php
function getCharacters($str) {

	// Script pour recuper un caractère au hasard de la chaine passée en paramètre (ici str)
	
	// On choisit un index compris entre zero et la longueur de la chaine passé en paramètre ($str)
	
	$randomIndex = random_int(0, strlen($str) - 1);
	// Ensuite on recupere le caractère qui correspond à l'index en question
	$randomCahracters = $str[$randomIndex];
	// Et on retourne le caractère récupéré
	return $randomCahracters;

}
```
Notre code complet ressemble à ça pour l'instant:
```php
$passwordLength = 8;
$password = '';

// On divise chaque groupe de caractères

$lowercaseCharacters = "abcdefghijklmnopqrstuvwxyz";
$uppercaseCharacters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
$numbers = "0123456789";
$specialCharacters = "!@#$%^&*()_-=+[]{}";

$characters = $lowercaseCharacters . $uppercaseCharacters . $numbers . $specialCharacters;


function getCharacters($str) {

	// Script pour recuper un caractère au hasard de la chaine passée en paramètre (ici str)
	
	// On choisit un index compris entre zero et la longueur de la chaine passé en paramètre ($str)
	
	$randomIndex = random_int(0, strlen($str) - 1);
	// Ensuite on recupere le caractère qui correspond à l'index en question
	$randomCahracters = $str[$randomIndex];
	// Et on retourne le caractère récupéré
	return $randomCahracters;

}
```
Une fois qu'on a ca, on a tous les elements necessaires pour constituer noptre mot de passe. On va commencer par recuperer un caractere de chaques groupe, en les concatenant a la variable `$password`:
```php
// On recupere une lettre misuscule et l'ajoute a la variable password

$password .= getCharacters($lowercaseCharacters);

// On recupere une lettre majuscule et l'ajoute a la variable password
$password .= getCharacters($uppercaseCharacters);
// On recupere un chiffre et l'ajoute a la variable password
$password .= getCharacters($numbers);
// On recupere un caractère spécial et l'ajoute a la variable password
$password .= getCharacters($specialCharacters);
```
Si on affiche notre mot de passe pour l'instant, on verra bien qu'il est constitué de quatre caractères, et comprend bien une lettre minuscule, une lettre majuscule, un chiffre et un caractère special:
```php
echo 'Le mot de passe généré est: ' . $password;
```
Maintenant, ce qu'il nous reste, c'est recuperer le reste des caracteres, que l'on va puiser au hasard de la longue chaine characters qu'on definit plus haut. Pour cela, on va faire un boucle, et reutiliser la fonction getCharacters. Puisqu'on a deja recuperer 4 caracteres, le nombre de caracteres qu'il nous reste  a recuperer est 4, qui est la longueur de la password (la valeur de la varibale `$passwordLength` qui est 8, moins le nombre de caractere deja recuperer qui est `4`). Notre boucle va ressembler à ceci:
```php
// $passwordLength - 4 (8 -4) permet de boucler 4 fois pour recuperer le nombre de caractères restant

for ($i = 0; $i < $passwordLength - 4; $i++) {

	// On recupère à chaque tour de boucle un nouveau caractère de la longue characteres
	// Et l'ajoute à la variable password
	$password .= getCharacters($characters);

}
```
Maintenant si on affiche notre password, on aura bien un mot de passe de 8 caractères, qui contiendra à tous les coups au moins une lettre minuscule, une lettre majuscule, un chiffre et un caractère scpecial.
### Petite et derniere correction
Si on regarde bien, tous les mots de passe qu'on genere debute systematiquement par une lettre minuscule, une lettre majuscule, un chiffre et un caractère scpecial. Ce seront à tous les coups les quatre premiers caracteres qui s'afficheront puis qu'on les a recuperer avant tous les autres. Pour corriger ce probleme et faire en sorte que le debut de la chaine soit aleatoire, on peut shuffle le password générer, ce qui permettra de repositionner les characteres de la chaine. ce qu'on  doit faire est d'utiliser la methode `str_shuffle`:
```php
$password = str_shuffle($password);
```
Et voici notre script complet:
```php
<?php
$passwordLength = 8;
$password = "";

// On divise chaque groupe de caractères
$lowercaseCharacters = "abcdefghijklmnopqrstuvwxyz";
$uppercaseCharacters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
$numbers = "0123456789";
$specialCharacters = "!@#$%^&*()_-=+[]{}";

$characters = $lowercaseCharacters . $uppercaseCharacters . $numbers . $specialCharacters;

function getCharacters($str) {

	// Script pour recuper un caractère au hasard de la chaine passée en paramètre (ici str)
	
	// On choisit un index compris entre zero et la longueur de la chaine passé en paramètre ($str)
	
	$randomIndex = random_int(0, strlen($str) - 1);
	// Ensuite on recupere le caractère qui correspond à l'index en question
	$randomCahracters = $str[$randomIndex];
	// Et on retourne le caractère récupéré
	return $randomCahracters;

}

// On recupere une lettre misuscule et l'ajoute a la variable password
$password .= getCharacters($lowercaseCharacters);
// On recupere une lettre majuscule et l'ajoute a la variable password
$password .= getCharacters($uppercaseCharacters);
// On recupere un chiffre et l'ajoute a la variable password
$password .= getCharacters($numbers);
// On recupere un caractère spécial et l'ajoute a la variable password
$password .= getCharacters($specialCharacters);

// $passwordLength - 4 (8 -4) permet de boucler 4 fois pour recuperer le nombre de caractères restant
for ($i = 0; $i < $passwordLength - 4; $i++) {

	// On recupère à chaque tour de boucle un nouveau caractère de la longue characteres
	// Et l'ajoute à la variable password
	$password .= getCharacters($characters);
}

$password = str_shuffle($password);

echo 'Le mot de passe généré est: ' . $password;
```