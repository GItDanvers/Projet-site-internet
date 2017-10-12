# Projet-site-internet
Travail effectué pour création site internet
utilisation des langages de programmation suivants :
PHP/Mysql
HTML5 CSS3
JAVASCRIPT JQUERY (en cours) 

Partie Graphique faite avec Photoshop

PHP/Mysql - Connexion à la BD LilleBioKarine

<?php

// connexion à la Bdd LillebioKarine

try {

	$bdd = new PDO('mysql:host=localhost;dbname=LillebioKarine;charset=utf8','root','root',array(PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION));
	
} catch (Exception $e) {
	die('Erreur : ' . $e->getMessage());	
}

// on vérifie si les variables existent et si elles ne sont pas vides

if (isset($_POST['nom']) AND isset($_POST['mail']) AND !empty($_POST['nom']) AND !empty($_POST['mail']))

{
	# code...
	// on renomme les variables pour que cela soit plus sympa à lire, le htmlspecialchars va sécuriser $nom et $email
	$nom=htmlspecialchars($_POST['nom']);
	$mail=htmlspecialchars($_POST['mail']);

// requête préparée
$insertmsg = $bdd->prepare('INSERT INTO client(nom,mail) VALUES(?, ?)');
// Permet d'insérer des données dans la BD sous forme de tableau
$insertmsg->execute(array($nom,$mail));

}
 ?>

