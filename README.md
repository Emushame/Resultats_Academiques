Proclamation par répondant automatique (Telegram)
Introduction
Ce projet a pour objectif de créer une API Flask permettant de gérer et d'afficher les résultats académiques des étudiants, intégration avec un bot Telegram pour faciliter la consultation des résultats.
Les utilisateurs (étudiants) peuvent ainsi accéder aux résultats académiques via le bot Telegram en envoyant simplement leur matricule.
Mais avant tout, parlons de « Bot »
1.	Définition du Bot
Un bot intelligent est un programme informatique conçu pour interagir avec les utilisateurs de manière naturelle et automatisée. Ces bots utilisent des technologies avancées telles que l'intelligence artificielle (IA) et le traitement du langage naturel (NLP) pour comprendre et répondre aux requêtes des utilisateurs.

a.	Description d'un bot intelligent
Un bot intelligent peut être intégré dans diverses plateformes comme les sites web, les applications mobiles, et les messageries instantanées (par exemple, Telegram). Il est capable de mener des conversations, de fournir des informations, d'exécuter des tâches spécifiques, et même d'apprendre de ses interactions pour s'améliorer au fil du temps.

b.	Caractéristiques d'un bot intelligent
1.	Compréhension du langage naturel (NLP) : Capacité à comprendre et interpréter le langage humain de manière contextuelle.
2.	Réponses automatisées : Fournit des réponses précises et rapides aux questions des utilisateurs.
3.	Apprentissage automatique (Machine Learning) : Améliore ses performances en apprenant des interactions passées.
4.	Personnalisation : Adapte ses réponses en fonction des préférences et du comportement de l'utilisateur.
5.	Multicanal : Peut être utilisé sur différentes plateformes et appareils.
6.	Intégration avec d'autres systèmes : Peut se connecter à des bases de données, des CRM, et d'autres systèmes pour fournir des informations pertinentes.
7.	Sécurité et confidentialité : Assure la protection des données des utilisateurs.
2. Objectifs du Projet
Le projet comprend plusieurs objectifs fonctionnels et techniques :
•	Développement d'une API RESTful avec Flask : Cette API permet de récupérer les résultats d'un étudiant à partir de son matricule, ainsi que d'autres informations académiques.
•	Création d'un Bot Telegram : Ce bot permet aux utilisateurs de consulter les résultats académiques en interagissant avec un bot via la plateforme Telegram.
•	Sécurisation et gestion des erreurs : Le système gère les erreurs liées à l'API et offre une sécurité de base pour les connexions à la base de données(securité standard, un username et un password pour se connecter).
3. Architecture du Projet
3.1. API Backend avec Flask
L'API est construite à l'aide du framework Flask, qui permet de créer des routes HTTP pour gérer les requêtes. Elle interagit avec une base de données MySQL pour récupérer et afficher les informations des étudiants et leurs résultats académiques.
L'API offre les fonctionnalités suivantes :
•	Route pour récupérer les résultats d'un étudiant : En utilisant le matricule, cette route renvoie les résultats académiques d'un étudiant (moyenne générale, mention, appréciation, etc.).
•	Route pour récupérer les résultats de tous les étudiants : Cette route permet de récupérer la liste des étudiants et leurs résultats respectifs.
Principes de conception :
•	Connexion à la base de données : La base de données MySQL est utilisée pour stocker les informations des étudiants, les résultats académiques et les délibérations, etc.
•	Gestion des erreurs : L'API gère les erreurs de manière claire avec des messages adaptés pour l'utilisateur.
•	Sécurité : Bien que basique, l'API utilise une connexion sécurisée à la base de données, et des mécanismes de gestion des erreurs pour éviter toute divulgation d'information sensible.
3.2. Bot Telegram
Le bot Telegram est développé pour permettre aux utilisateurs de consulter les résultats académiques via la plateforme de messagerie Telegram. Il interagit avec l'API Flask pour obtenir les résultats en fonction du matricule fourni par l'utilisateur.
Le bot offre les fonctionnalités suivantes :
•	Commande /start : Le bot envoie un message d'accueil à l'utilisateur pour expliquer son utilisation.
•	Commande /resultat : L'utilisateur peut envoyer son matricule pour obtenir ses résultats académiques. Le bot fait une requête à l'API Flask, récupère les résultats et les affiche sous forme de message.
Le bot est conçu pour fournir une interface simple, où l'utilisateur n'a qu'à entrer un matricule et recevoir une réponse immédiate.
4. Détails du Développement
4.1. API Backend - Flask
•	Connexions à la base de données : L'API utilise mysql-connector-python pour se connecter à la base de données MySQL et effectuer des requêtes SQL afin de récupérer les informations des étudiants et leurs résultats.
•	Gestion des erreurs : Chaque fonction d'API dispose de mécanismes de gestion des erreurs, qui capturent les exceptions liées aux erreurs de base de données ou à des requêtes incorrectes. En cas d'erreur, l'API renvoie un message d'erreur clair à l'utilisateur et génère un fichier de logging que l’on peut consulter du coté Backend.
•	Routage de l'API : L'API expose deux principales routes :
o	Une pour obtenir les résultats d'un étudiant spécifique via son matricule.
o	Une autre pour récupérer tous les résultats des étudiants (utile pour des administrateurs ou pour générer des rapports).
4.2. Bot Telegram
Le bot utilise la bibliothèque python-telegram-bot pour interagir avec Telegram et gérer les commandes utilisateur. Il envoie des requêtes HTTP à l'API Flask pour récupérer les résultats. La gestion des commandes est simple : une commande de démarrage (/start) pour saluer l'utilisateur, et une commande (/resultat <matricule>) pour obtenir les résultats académiques d'un étudiant via son matricule.
Le bot gère aussi les erreurs en cas de matricule non valide ou de problème de communication avec l'API.
5. Tests
Le projet a été testé en plusieurs étapes pour garantir le bon fonctionnement de chaque composant :
•	Test de l'API : L'API a été testée en utilisant des outils comme Postman et en vérifiant les réponses renvoyées pour différents matricules et scénarios d'erreur 
•	Test du Bot Telegram : Le bot a été testé pour s'assurer qu'il répond correctement aux commandes et interagit correctement avec l'API.
 
a.	Lancement du bot sur telegram 
 

  
6. Sécurité et Gestion des Erreurs
•	Sécurisation des connexions : Bien que le projet n'intègre pas d'authentification complexe, l'API Flask est configurée pour se connecter de manière sécurisée à la base de données en utilisant des bonnes pratiques de gestion des connexions.
•	Gestion des erreurs : Chaque composant (API, Bot Telegram) gère les erreurs de manière claire pour l'utilisateur, offrant des messages d'erreur utiles en cas de problème.


Exemple : Matricule introuvable dans la base des données
 
7. Conclusion
Ce projet a permis de créer une solution complète de gestion des résultats académiques, intégrant une API backend, un bot Telegram pour l'accès aux résultats via la messagerie. Le système est conçu pour être évolutif et peut être amélioré avec des fonctionnalités telles que l'authentification des utilisateurs ou des rapports détaillés pour les administrateurs, ainsi que l’integration du chargement de la grille de deliberation directement pour rendre les résultats disponibles. 


a.	Consulter les résultats 
 
b.	Et le relevé des côtes, une fois ouvert au format PDF 
 
c.	Schéma de base de données
1. Table etudiants
Cette table contient les informations personnelles et académiques des étudiants inscrits.
•	Champs :
o	id (INT, clé primaire) : Identifiant unique de chaque étudiant.
o	matricule (VARCHAR(50), unique) : Numéro d'identification unique de l'étudiant.
o	nom_complet (VARCHAR(255)) : Nom complet de l'étudiant.
o	promotion (VARCHAR(50)) : Promotion ou niveau d'étude de l'étudiant.
o	filiere (VARCHAR(250)) : Filière académique de l'étudiant.
o	moyenne_annuelle (DECIMAL(5,2)) : Moyenne générale annuelle de l'étudiant.
o	credits_valides (INT) : Nombre total de crédits validés par l'étudiant.
o	mention (VARCHAR(50)) : Mention obtenue par l'étudiant (par exemple, « Bien », « Très Bien »).
o	appreciation (VARCHAR(100)) : Remarques générales sur les performances de l'étudiant.
o	decision (VARCHAR(50)) : Décision académique concernant l'étudiant (exemple : « Admis », « Ajourné »).
o	notes (DOUBLE) : Informations supplémentaires (à préciser selon le contexte).
o	poids (TEXT) : Champs libre pour des valeurs spécifiques.
o	moyenne_ponderee (VARCHAR(250)) : Moyenne pondérée des résultats de l'étudiant.
o	pourcentage (VARCHAR(250)) : Pourcentage de réussite.
2. Table cours
Cette table décrit les informations relatives aux cours disponibles dans l'établissement.
•	Champs :
o	id (INT, clé primaire) : Identifiant unique de chaque cours.
o	code_cours (VARCHAR(50), unique) : Code unique pour identifier un cours.
o	nom_cours (VARCHAR(255)) : Nom du cours.
o	credit (INT) : Nombre de crédits associés à ce cours.
________________________________________
3. Table resultats
Cette table lie les étudiants aux cours et enregistre leurs résultats.
•	Champs :
o	id (INT, clé primaire) : Identifiant unique de chaque enregistrement.
o	matricule (VARCHAR(50), clé étrangère vers etudiants.matricule) : Matricule de l'étudiant.
o	code_cours (VARCHAR(50), clé étrangère vers cours.code_cours) : Code du cours.
o	moyenne (DECIMAL(5,2)) : Moyenne obtenue par l'étudiant dans le cours.
o	total (DECIMAL(5,2)) : Total des points obtenus dans le cours.
4. Table deliberations
Cette table enregistre les résultats des délibérations académiques pour chaque étudiant.
•	Champs :
o	matricule (VARCHAR(10), clé étrangère vers etudiants.matricule) : Matricule de l'étudiant.
o	annee (VARCHAR(10)) : Année académique concernée.
o	decision (VARCHAR(2)) : Décision prise lors des délibérations (exemple : « A » pour admis, « R » pour recalé).
Relations :
•	La table resultats est liée à :
o	La table etudiants via le champ matricule.
o	La table cours via le champ code_cours.
•	La table deliberations est liée à la table etudiants via le champ matricule.
 

