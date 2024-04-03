> BIMONT Maxime

> E-mothep

> Intégrateur webmethods

# Semaine du 26 février au 1 mars

## Ce que j'ai fait

Retour en entreprise après 2 mois d'absence. Plusieurs choses ont changé dans mon projet, notamment sur le stockage de mes données qui ont été migrées vers une base de données MySQL. Mon application angular a été mise sur un dépôt GIT et configuré pour travailler en toute autonomie et faciliter la mise en production prévue à l'avenir. Le dossier webmethods du projet à été déplacé dans le workspace de tous les projets interne de l'entreprise et à besoin d'être restructuré pour une meilleur organisation et sécurité. Ma mission était donc de reconnecter les adapters, les flows et les API entre-eux. Lundi en début d'après-midi, j'ai un eu point avec mon MA et mon chef d'équipe pour faire un point sur mon évaluation sur la moitié de la période de mon alternance et de rappeler les objectifs et deadlines du projet. Sur ce dernier, plusieurs améliorations ont été présentées pour une meilleur ergonomie et différents retours fait durant mon absence. J'ai fini la journée en restructurant le dossier du projet dans webmethods.

J'ai commencé par reconnecter tous les adapters au flows services et ces derniers au API. Ensuite j'ai changé les url obsolètes des API dans les appels fetch ou http côté front. J'ai continué en modifiant la partie de front de sorte à ravoir le même rendu qu'à l'origine. Il m'a fallu supprimé certains appel d'API et revoir l'envoi de données pour d'autres. Le dernier point était les fichiers joints. Ces derniers n'ayant plus d'appel API à eux même côté back ont été rattachés dans la création de note. 

Ensuite il m'a fallut modifier mes flows services pour prendre en compte les apports effectuer côté front. J'ai donc insérer dans la création de la note, l'insertion des fichiers dans la db et dans le serveur. A la fin de cette semaine je pouvais donc insérer et récupérer des fichiers lors de la création et visualiation de note. 

## Ce que j'ai appris

Durant cette semaine je n'ai pas aprris de nouvelles choses, j'ai surtout eu un rappel de ce que j'avais vu et appris les semaines précédentes que ca soit côté front ou back.

## Ce que j'ai ressenti

J'ai heurté sur un problème de multi-origine lors d'appel de plusieurs url en simultané ( 1 pour l'API et 1 pour l'application ). Pour palier à ce problème il m'a fallut configuer le serveur webmethods en ajoutant certains paramètres dans les `Settings > Extends`. 

J'ai eu beaucoup de mal avec le type que devait prendre mes fichiers côté front pour que le back puisse les récupérer avec toutes les données qu'ils comportaient. Après d'innombrable essaie pour envoyer la liste de fichiers vers le back j'ai trouvé le moyen, assez simple, de le faire. Il suffisait d'encoder les fichiers en base64 et de les envoyer tel quel vers le back.

Un problème est survenue lorsque je souhaitais récupérer mes fichiers depuis le serveur. Le type de retour qui devait être un InputStream était en fait un string, donc inutilisable pour mon code. Le problème c'est révélé être que si le nom du fichier comportait un espace, la méthode `client.sftp:get` n'interprétait pas correctement ce charactère et envoyer un message d'erreur

Une des difficultés à été mon manque de compétence en Angular pour travailler rapidement.

## Ce qui est prévu pour la semaine prochaine 

Dans 2 semaines, j'ajouterais :
- la visualisation côté front 
- l'ajout des fichiers lors de l'insertion de commentaire dans les notes.
- le téléchargement et la lecture des fichiers

# Semaine du 11 mars au 15 mars

## Ce que j'ai fait

J'ai commencé cette semaine en apportant des modifications sur les documents type tel que 'comments' ou 'files' pour avoir les mêmes noms de paramètres entre le back et le front. J'ai réussi à obtenir un résultat satisfaisant avec les fichiers insérer dans les commentaires et les notes et non uniquement regroupés dans la note. 

J'ai été demandé des conseils à Aymeric Henouille, un membre de l'équipe Front pour m'aider sur certains aspect du projet côté front. Je savais déjà que la partie front présentait quelques problèmes puisque j'ai récupéré un projet déjà existant et que j'ai peu de compétence en angular. J'ai pu de ce fait améliorer certains points en therme d'optimisation. 

J'ai par la suite, améliorer mes flows webmethods car je me suis rendu compte que mes appels API prenaient du temps (beaucoup trop de temps). Avec mon MA on a donc observé quels flows étaient utilisés dans d'autres et refractor certains pour optimiser le temps d'appel API. 

Sur un conseil donné par un membre de l'équipe front, j'ai voulu mettre à jour les dépendances de mon projet côté front comme par exemple `@angular/core` et `@angular/cli`. Mais cette action à amené plus de problèmes qu'autre chose.

Cette semaine à plus été sujet à des améliorations de l'existant et des conseils côté front pour améliorer le projet dans sa globalité

## Ce que j'ai appris

J'ai fini par faire des exercices sur le type Observable et sur la librairie RJSX d'angular donné par Aymeric Henouille. Cela m'a beaucoup aidé pour améliorer mes appels APi, refractor mes fonctions et nettoyer un peu mon code.

Je me suis beaucoup améliorer dans l'utilisation de GIT avec la création de branche pour chaque problème ou ajout de features et les merges sur la branche principale. Cela me permet maintenant de limiter les erreurs et de ne pas impacter la solution viable du projet.

## Ce que j'ai ressenti

Un problème est apparu lors du téléchargement du fichier, ce dernier était mal encodé et donc illisible. Après plusieurs tests j'ai trouvé que l'erreur survient entre le moment ou je récupère mon fichier depuis le serveur distant et lorsque je l'envoi vers le front via WebMethods. Le problème venait du fait que je ne précisais pas le type d'encodage `utf-8` lorsque j'encodais ou décodais mes fichiers dans webmethods.

Le problème qu'à entrainer la mise à jour des dépendances est que d'autres dépendances n'héritaient plus de certaines et que donc certaines méthodes dans mon projet ne fonctionnait plus entraînant une incapacité à compiler mon projet. Pour résoudre ce problème j'ai récupérer une backUp qui datait de décembre et apportait les modificatios nécessaires pour revenir un résultat optimal du projet.

## Ce qui est prévu pour la semaine prochaine 

Pour la semaine prochaine, je compte essayer de faire : 
- Un nettoyage côté front 
- Continuer l'optimisation des flows services
- Régler quelques soucis mineur d'affichage

# Semaine du 18 mars au 22 mars

## Ce que j'ai fait

L'objectif de cette semaine était d'améliorer ce qui était déjà sur le projet et non d'ajouter de nouvelles fonctionnalités dans l'idée de réaliser une première mise en production à la fin de la semaine suivante. J'ai commencé par optimiser mes flows services côté Back en essayant de les rendre plus concis, rapides et structurés. Pour cela mon maître d'apprentissage m'a guidé en me donnant des points à améliorer et quelques tips sur webmethods. Ensuite côté front, il y avait plusieurs légers bugs d'affichage et quelques fonctionnalités à réparer comme la pagination, la barre de recherche et le système de filtrage. J'ai aussi ajouté une icone dans la colonne des fichiers si la note possédait, ou non, un ou plusieurs fichiers.

## Ce que j'ai appris

Je suis en constant apprentissage dans webmethods et en Angular par le biais d'ajout de fonctionnalité ou d'optimisation de code.

## Ce que j'ai ressenti

J'ai rencontré un problème, lorsque j'ai souhaité régler un soucis sur ma barre de navigation. La position de l'indice qui indique la page dans quelle on se situe ne changeait pas, même en naviguant sur d'autres. Le problème vient probablement de la définition des routes du projet. Je dis probablement, car j'ai demandé de l'aide à un membre de l'équipe front mais même avec son expertise le problème persistait. Ce dernier vient peut-être d'une autre source mais comme ce n'est pas moi qui ai créé le projet je n'arrive pas à mettre la main sur l'origine du problème. Après discussion avec mon chef d'équipe, nous avons décidé de retirer cet indice pour la future mise en production puisqu'un titre de page informe l'utilisateur sur quelle page il se situe.

Aussi sur la pause du jeudi, l'entreprise à organiser un Spring Break, donc un évènement qui marque l'arrivée du printemps et dans lequel tous les membres de la boîte se sont réunis pour partager un repas. Un quiz a été organisé qui faisait affronter les membres de la boîte en équipes sur différentes questions qui portaient sur le printemps.

## Ce qui est prévu pour la semaine prochaine 

Pour la semaine prochaine, je compte :
- Tester le zippage de fichiers pour tenter d'optimiser le projet (à voir l'efficacité)
- Retirer l'appel css de FontAwesome qui est une feature trop gourmande pour le projet
- Ajouter un loader CSS pour les appels API.

# Semaine du 25 mars au 29 mars

## Ce que j'ai fait

Cette semaine à été plus légère en termes d'ajout de gros fonctionnalités. Avec pour objectif de préparer la mise en production, on m'a demandé de perfectionner l'existant pour avoir un rendu utilisable lors de la mise en production. J'ai donc commencé par corriger les différents bugs sur l'application. J'ai ensuite fais le tour des différents employés de l'entreprise pour leur faire tester l'application et avoir leurs retours. J'ai de ce fait ajouté ou modifié certains aspect pour perfectionner le rendu.

## Ce que j'ai appris

Toujours en plein apprentissage des techniques et bonnes pratiques d'Angular. J'ai toute fois utilisé pour la première fois un outil git qui est "BackLog". Une sorte de Trello qui m'a permis de voir l'avancement des différentes features à ajouter ou des bugs à modifier. Cet outil est très pratique car il me mettai dans un bon état d'esprit comme je voyais que j'avançais bien sur le projet.

## Ce que j'ai ressenti

Pas vraiment de problèmes rencontrés cette semaine.

## Ce qui est prévu pour la semaine prochaine 

Pour la semaine prochaine, je compte :
- Rédiger les différentes documentations pour le projet
- Aider l'autre projet interne sur l'aspect de la gestion d'erreur de leurs retours d'appels API
- Entretien avec un membre de l'entreprise pour organiser et faire les pré-requis pour la mise en production