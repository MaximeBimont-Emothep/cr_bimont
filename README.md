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

# Semaine du 01 avril au 05 avril

## Ce que j'ai fait

Cette semaine on m'a confié une tâche sur le gros projet interne de la boîte. L'objectif était de rajouter la gestion d'erreur sur les 130 appels API du projet pour personnaliser le message de retour d'erreur et faciliter le débogage. Après une réunion m'expliquant mon travail et les outils mis à ma disposition, j'ai pu m'atteler à ma tâche. Pour la gestion d'erreur voici quelques précisions : 

Chaque appel API devaient avoir un retour d'erreur `400 - Bad Request`
Les appels POST devaient avoir en plus `403 - Already Exist`
Les appels DELETE devaient avoir en plus : 
    - `404 - Not Found`
    - `403 - In Use`
Les appels PUT devaient avoir en plus : 
    - `404 - Not Found`
    - `403 - Already Exist`

Pour les retours 400, il fallait modifier les paramètres `Required` et `Allow null` pour tous les champs en input des appels.
Pour les retours 404, un autre membre de l'entreprise à créé un service permettant de vérifier le contenu du message d'erreur et à l'aide d'une table en bdd contenant des filtres de messages d'erreur capable de détecter le type d'erreur. De ce fait pour les retours 404, il nous fallait ajouter ce service et modifier la requete SQL pour ajouter le retour de l'id de l'élément supprimé ou modifié grâce à `returning id` sur postgreSQL car ce service nécesitte ce dernier paramètre.
Pour les retours 403, il fallait modifier les paramètres de suppression et des contraintes de clés unique dans les tables de la base de données.

Du côté de mon projet base de connaissances, j'ai réaliser les documentations techniques et d'utilisateurs. J'ai aussi eu une réunion avec d'autres membres de l'entreprise pour organiser la mise en production du projet. J'ai donc initialisé un dépot git pour le back et le front. Un changement de serveur pour la recette et la mise en place d'un serveur de production qui sera utilisé par tout le monde dans la boite.

## Ce que j'ai appris

J'ai beaucoup appris sur la gestion des projets dans git avec Webmethods, ainsi que les différentes étapes pour partager son travail sur un projet qui est développé par une dizaine d'employés. 

## Ce que j'ai ressenti

J'ai failli engendré un problème car au lieu de faire une `pull request` sur git, j'ai directement publié mon travail sur l'environment de recette. Heuresement l'erreur était minime est j'ai pu rapidement fixer l'erreur avant de créer de gros problèmes.

## Ce qui est prévu pour la semaine prochaine 

Pour la semaine prochaine, je compte :
- Finir l'implémentation de la gestion d'erreur
- Réaliser les points définies dans la réunion de mise en production pour le projet base de connaissance.

# Semaine du 08 avril au 12 avril

## Ce que j'ai fait

Cette semaine j'ai terminé l'implémentation de la gestion d'erreur sur toutes les APIs du projet. 

On m'a donc confié une nouvelle tâche qui était d'automatiser la sauvegarde de facture généré par l'entreprise. Pour cela je devais récupérer depuis le front, une facture sous un format de PDF ainsi que les paramètres de date et du nom de l'entité associé à cette facture. Ensuite lorsque j'ai récupérée cette facture côté back, il me fallait l'envoyé dans un serveur distant à l'aide d'un protocole SFTP. Cette tâche à été assez facile car j'avais déjà réalisé un travail de ce style sur le projet base de connaissances. J'avais aussi comme demande de trier les factures par entité et par date sous format (MM-yy). 

Vendredi en fin de journée, on m'a donnée une nouvelle tâche qui était de générer un fichier SEPA sous format XML. Comme il me restait peu de temps avant la fin de la journée que j'ai juste pris connaisance de la documentation et réfléchie à comment implémenter mes différents services et quels jeux de données utilisés. 

## Ce que j'ai appris

Pas de nouvelles fonctionnalités apprises cette semaine mais des bonnes pratiques webmethods révisées. 

## Ce que j'ai ressenti

Tous c'est très bien passé durant cette semaine.

## Ce qui est prévu pour la semaine prochaine 

Pour la semaine prochaine, je compte :
- Finir l'implémentation de la génération des fichiers XML SEPA
- Faire le point sur certains cas de la gestion d'erreur

# Semaine du 15 avril au 19 avril

## Ce que j'ai fait

Lundi et mardi, j'ai travaillé sur la génération de fichiers SEPA des notes de frais. Les paramètres d'entrée étaient :
- Une période (un mois et une année)
- Une liste d'entités
- Une liste de types de notes de frais

Pour m'aider, j'ai reçu une documentation expliquant tous les champs de ce fichier, ainsi que les normes et contraintes à respecter. Je vous ai fourni cette documentation.

Ensuite, le travail a été simple : j'ai importé le fichier XML de la documentation directement dans WebMethods pour créer la structure du fichier côté back.

J'ai utilisé des adaptateurs SQL pour récupérer mes jeux de données dans la base de données en deux étapes. D'abord, je récupérais les données d'une entité grâce à son ID :
```sql
SELECT 
    c.name AS entity_name, 
    c.siret AS entity_siret, 
    bc.iban AS entity_iban, 
    bc.swift AS entity_swift
FROM 
    entity AS e
INNER JOIN 
    company AS c ON e.company_id = c.id
INNER JOIN 
    bank_account AS bc ON c.id = bc.company_id
WHERE
    e.id = ?
AND 
    bc.main_account = true
GROUP BY 
    c.name, 
    c.siret, 
    bc.iban, 
    bc.swift;
```

Ensuite je récupère les notes de frais d'une entité aussi grâce à son id mais en respectant le type de note de frais passé en paramètre :
```sql
SELECT 
    e.amount_ati as amount_ati, 
    ert.name as type_name, 
    c2.firstname || ' ' || c2.lastname as collaborator_name, 
    c1.iban as collaborator_iban, 
    c1.bic as collaborator_swift
FROM 
    expense_report as e 
INNER JOIN 
    expense_report_type as ert ON ert.id = e.expense_report_type_id
INNER JOIN 
    collaborator as c1 ON e.collaborator_id = c1.id
INNER JOIN 
    contact as c2 ON c2.id = c1.contact_id
WHERE 
    ert.id IN (${expenseReportTypeIdList}) 
AND 
    c1.entity_id = ?
AND 
    EXTRACT(YEAR FROM e.date) = ? 
AND 
    EXTRACT(MONTH FROM e.date) = ?
AND 
    e.tp_expense_report_status_id = 2
GROUP BY 
    e.amount_ati, 
    ert.name, 
    c2.lastname, 
    c2.firstname, 
    c1.iban, 
    c1.bic;
```

Enfin, il ne me restait plus qu'à relier les données entre elles pour enrichir le fichier SEPA et ajouter dans l'API existante un appel pour envoyer le ou les fichiers SEPA générés dans un zip.

Les autres jours je suis intervenues sur des points à régler par ci et par la :
- Modifier les jointures sql en `LEFT JOIN` pour la récupération des données dans les méthodes `GET`.
- Ajouter une surcouche sur un flow webMethod existant pour gérer les erreurs en cas d'élément null.
- Ajouter des cas de gestion d'erreur spécifiques.
- Régler des soucis de code manquant causé lors d'un pull request d'autres membres sur git ou lors du déploiement sur le serveur de recette.

## Ce que j'ai appris

J'ai appris comment travailler avec des fichiers XML sur webMethod.

## Ce que j'ai ressenti

J'ai effectué avec mon responsable mon évaluation professionnelle et annuelle. Cette dernière permettait de savoir : 
- mon ressenti sur l'entreprise 
- ce que j'avais réalisé
- faire le bilan de mes compétences acquises
- mes perspective d'évolution

J'ai donc fait part de mon envie de me diriger vers une voie qui inclut plus de gestion de projet, comme TechLead. De ce fait, jeudi et vendredi prochain, mon responsable m'a confié la gestion des tâches des stagiaires. Je devrais donc faire le point sur ce qu'ils ont appris pendant leur semaine de formation, leur confier des tâches, préparer des points d'avancement et répondre à leurs besoins. Je suis donc très satisfait qu'on me laisse tester de nouvelles perspectives.

## Ce qui est prévu pour la semaine prochaine 

Pour la semaine prochaine, je compte :
- Réaliser différents point sur le projet de refonte des projets internes
- Continuer la refonte de la partie Front du projet BDC que j'ai commencé sur mon temps perso
- Encadrer les stagiaires sur le projet BDC.
