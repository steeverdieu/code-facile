Commençons par réorganiser notre générateur de mots de passe en séparant chaque type de caractère dans une variable distincte. Pour rappel, un mot de passe sécurisé doit contenir :
- des lettres minuscules,
- des lettres majuscules,
- des chiffres,
- et des caractères spéciaux.

Nous allons donc découper notre grande chaîne de caractères en quatre groupes, chacun stocké dans sa propre variable :
```php
// On définit les groupes de caractères disponibles
$lowercaseCharacters = "abcdefghijklmnopqrstuvwxyz";
$uppercaseCharacters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
$uppercaseCharacters = "0123456789";
$specialCharacters = "!@#$%^&*()_-=+[]{}";
```
Ensuite, on rassemble tous ces groupes dans une seule variable `$characters`, qui contiendra l’ensemble des caractères utilisables pour générer un mot de passe :
```php
$characters = $lowercaseCharacters . $uppercaseCharacters . $numbers . $specialCharacters;
```
Voici à quoi ressemble notre code pour le moment :
```php
$passwordLength = 8;
$password = '';

// Groupes de caractères
$lowercaseCharacters = "abcdefghijklmnopqrstuvwxyz";
$uppercaseCharacters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
$numbers = "0123456789";
$specialCharacters = "!@#$%^&*()_-=+[]{}";
  
// Concaténation des groupes en une seule chaine
$characters = $lowercaseCharacters . $uppercaseCharacters . $numbers . $specialCharacters;
```
### 🛠 Création d'une fonction pour tirer un caractère aléatoire
Maintenant que nos groupes de caractères sont prêts, nous allons nous assurer de sélectionner **au moins un caractère aléatoire dans chacun d’eux**.  
Autrement dit, nous allons tirer :

- une lettre minuscule depuis la variable `$lowercaseCharacters`,
- une lettre majuscule depuis `$uppercaseCharacters`,
- un chiffre depuis `$numbers`,
- et un caractère spécial depuis `$specialCharacters`.

Pour éviter de dupliquer le même bloc de code à chaque fois, nous allons créer une **fonction réutilisable** appelée `getCharacters`. Cette fonction prendra en paramètre une chaîne de caractères, et renverra un caractère choisi au hasard dans cette chaîne.
```php
function getCharacters($str) {

  // Script pour recuper un caractère au hasard de la chaine passée en paramètre (ici str)

}
```
Pour rappel, dans la version précédente de notre script, pour récupérer un caractère au hasard, on faisait comme suit:
```php
// On choisit un index aléatoire compris entre 0 et la longueur de la chaîne moins 1
$randomIndex = random_int(0, strlen($characters) - 1);
// On récupère ensuite le caractère correspondant à cet index
$randomCharacter = $characters[$randomIndex];
```
Nous allons maintenant **réutiliser ces lignes** dans notre fonction `getCharacters()`, mais cette fois-ci en les appliquant à la chaîne **reçue en paramètre**. Voici le résultat :
```php
function getCharacters($str) {
	// On choisit un index aléatoire entre 0 et la longueur de la chaîne - 1
	$randomIndex = random_int(0, strlen($str) - 1);
	// Ensuite on recupere le caractère qui correspond à cet index
	$randomCharacter = $str[$randomIndex];
	// Et on retourne le caractère récupéré
	return $randomCharacter;

}
```
Voici à quoi ressemble notre code pour le moment :
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
	// On choisit un index aléatoire entre 0 et la longueur de la chaîne - 1
	$randomIndex = random_int(0, strlen($str) - 1);
	// Ensuite on recupere le caractère qui correspond à cet index
	$randomCharacter = $str[$randomIndex];
	// Et on retourne le caractère récupéré
	return $randomCharacter;

}
```
Une fois cette fonction prête, nous disposons de tous les éléments nécessaires pour construire notre mot de passe.  Nous allons commencer par récupérer un caractère dans **chaque groupe** de caractères, puis les concaténer dans la variable `$password` :
```php
// On récupère une lettre minuscule et on l’ajoute au mot de passe
$password .= getCharacters($lowercaseCharacters);
// On récupère une lettre majuscule et on l’ajoute au mot de passe
$password .= getCharacters($uppercaseCharacters);
// On récupère un chiffre et on l’ajoute au mot de passe
$password .= getCharacters($numbers);
// On récupère un caractère spécial et on l’ajoute au mot de passe
$password .= getCharacters($specialCharacters);
```
À ce stade, notre mot de passe contient déjà 4 caractères bien répartis. Si on l'affiche :
```php
echo 'Le mot de passe généré est: ' . $password;
```
on verra un mot de passe de 4 caractères, avec une lettre minuscule, une majuscule, un chiffre et un caractère spécial.
### Compléter le mot de passe
Comme notre objectif est de générer un mot de passe de 8 caractères (***Valeur de la variable passwordLength définie plus haut***), il nous faut en ajouter 4 autres, choisis aléatoirement dans l’ensemble complet `$characters`.

Pour compléter notre mot de passe, nous allons utiliser une boucle qui va récupérer, à chaque itération, un caractère aléatoire parmi l’ensemble des caractères disponibles. Pour cela, nous réutiliserons la fonction `getCharacters()` :
```php
// $passwordLength - 4 (8 - 4) permet de boucler 4 fois pour récupérer les caractères restants

for ($i = 0; $i < $passwordLength - 4; $i++) {
    // À chaque tour, on récupère un caractère aléatoire dans la chaîne complète
    // et on l’ajoute à la variable $password
    $password .= getCharacters($characters);
}
```
Si nous affichons maintenant la variable `$password`, nous obtiendrons un mot de passe de 8 caractères qui contiendra systématiquement au moins une lettre minuscule, une lettre majuscule, un chiffre, ainsi qu’un caractère spécial.
### Petite et dernière correction
Actuellement, tous les mots de passe générés commencent toujours par une lettre minuscule, une lettre majuscule, un chiffre, puis un caractère spécial, car ce sont les quatre premiers caractères que nous avons ajoutés avant les autres.

Pour remédier à ce problème et rendre le début de la chaîne aléatoire, il suffit de **mélanger** les caractères du mot de passe généré à l’aide de la fonction `str_shuffle()`. Cela permettra de repositionner les caractères de manière totalement aléatoire.
```php
$password = str_shuffle($password);
```
## 🧩 Script complet

Voici le générateur complet, prêt à l’emploi :
```php
<?php

$passwordLength = 8;
$password = "";

// Groupes de caractères
$lowercaseCharacters = "abcdefghijklmnopqrstuvwxyz";
$uppercaseCharacters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
$numbers = "0123456789";
$specialCharacters = "!@#$%^&*()_-=+[]{}";

// Chaîne complète
$characters = $lowercaseCharacters . $uppercaseCharacters . $numbers . $specialCharacters;

// Fonction de sélection aléatoire
function getCharacters($str) {
    $randomIndex = random_int(0, strlen($str) - 1);
    return $str[$randomIndex];
}

// Ajout de caractères garantis
$password .= getCharacters($lowercaseCharacters);
$password .= getCharacters($uppercaseCharacters);
$password .= getCharacters($numbers);
$password .= getCharacters($specialCharacters);

// Complément du mot de passe
for ($i = 0; $i < $passwordLength - 4; $i++) {
    $password .= getCharacters($characters);
}

// Mélange final
$password = str_shuffle($password);

echo 'Le mot de passe généré est : ' . $password;

```