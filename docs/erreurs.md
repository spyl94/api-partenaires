# Gestion des retours erreurs 💥

## API Partenaires
Chaque erreur est accompagnée d’un code unique et d’un message essayant de vous guider au mieux dans la résolution de l’erreur. La propriété “**details**” servira si besoin à nos équipes à tracer et identifier la source du problème en interne.

```json
{
    "error": {
        "code": "ERR-INTERNAL",
        "message": "Internal Server Error",
        "details": {
            "url": "https://app.myunisoft.fr/api/v1/key/create",
            "method": "POST",
            "requestedAt": "09 Mar 2021, 21:09:24",
            "correlationId": "09347205-7de2-4efe-aa68-f0f24a378029"
        }
    }
}
```

La propriété message est en ce qui la concerne vouée à évoluer à travers le temps. **Nous vous recommandons de ne pas l’utiliser comme référentiel pour automatiser une gestion d’erreur au sein de vos implémentations**.

L’API n’a pour le moment aucune gestion d’un **retour de multiple** “erreurs” mais il n’est pas exclu que cela soit le cas dans le futur. Tout retour HTTP n’ayant pas un statut code en 2xx retournera donc forcément un JSON avec une propriété racine “error”.

> ⚠️ Attention nous ne parlons pas des erreurs qui sont retournées sur les routes qui ne sont que des passerelles vers d’autres API internes.⚠️

# Codes d'erreur

Les codes d’erreurs (unique) sont les suivants;
- **ERR-ANY**
- **ERR-HTTP**
- **ERR-INVALID-AUTH-HEADER** (l’en-tête http “Authorization” doit être préfixé du mot clé Bearer).
- **ERR-INVALID-JWT** (Le jeton Utilisateur ou API n’est pas valide).
- **ERR-INVALID-USER-JWT**
- **ERR-INVALID-API-JWT**
- **ERR-USER-TOKEN-NOT-FOUND** (le token n’existe pas ou est expiré).
- **ERR-API-TOKEN-NOT-FOUND** (le token n’existe pas ou est révoqué).
- **ERR-SECRET-NOT-CONFIGURED**
- **ERR-SECRET-HEADER-NOT-SET** (l’en-tête X-Third-Party-Secret est manquante).
- **ERR-INVALID-SECRET** (l’en-tête X-Third-Party-Secret n’est pas valide).
- **ERR-MISSING-RULE**
- **ERR-FORBIDDEN-ROUTE** (vous n’avez pas les droits d’accès pour la route).
- **ERR-SOCIETY-DOESNT-EXIST** (la société cible n’existe pas).
- **ERR-THIRD-PARTY-DOESNT-EXIST** (le groupe/schéma cible n’existe pas).
- **ERR-USER-DOESNT-EXIST** (l’utilisateur n’existe pas… n’arrive jamais sauf si le JWT est signé par un autre acteur que le Service auth MyUnisoft).
- **ERR-USER-UNEXPECTED-TYPE** (l’utilisateur générant la clé n’a pas les droits nécessaires sur le schéma).
- **ERR-API-TOKEN-GENERATION-FAILED** (la génération du token a échoué… merci de prendre contact avec nous si cela se produit).

## Proxy

| **code** | **message** | **http_statuscode** |
|---|---|---|
| ABSENCE1 | Type absence invalide | 400 |
| ABSENCE2 | Statut absence invalide | 400 |
| ABSENCE3 | Des absences sont en cours sur la période renseignée | 400 |
| ABSENCE4 | Les heures ne peuvent être renseignée que sur un congé sans solde d'un jour | 400 |
| ABSENCE5 | Impossible de renseigner un congé dans le passé | 400 |
| ABSENCE6 | Impossible de saisir 2 demi-journée pour 1 jour, veuillez décocher les demi-journées | 400 |
| ABSENCE7 | Mise à jour impossible de la société | 400 |
| ABSENCE8 | Impossible d'ajouter le solde repos du salarié | 400 |
| ABSENCE9 | Impossible d'annuler l'absence à moins de 30 jours | 400 |
| ANALYT001 | erreur de repartition sur l'axe %1 | 400 |
| ANALYT002 | La somme des répartition de la clé n'est pas égale à 100% | 500 |
| ANALYT003 | Interdit de ventiler de l'analytique sur un autre compte que le 6 et 7 | 400 |
| ASSOCIE1 | Veuillez renseigner un nombre de part. | 400 |
| ASSOCIE2 | Vous essayer d'ajouter %1 parts alors qu'il n' y a que %2 parts disponible sur la société. | 400 |
| ASSOCIE3 | Il n'y a pas assez de part disponible sur la société. | 400 |
| ASSOCIE4 | Il n'y a aucune part renseignée sur la société "%1". | 400 |
| ASSOCIE5 | Veuillez renseigner un nombre de part sur la société. | 400 |
| AXE1 | Impossible de supprimer l'axe car des sections lui sont associées | 400 |
| AXE2 | l'axe %1 n'a pas été trouvé | 400 |
| BIC1 | BIC invalide | 400 |
| BIC2 | BIC: Le code pays ne correspond pas au pays renseigné | 400 |
| CB1 | Erreur lors de la création du crédit bail | 400 |
| CB2 | Le numéro de contrat renseigné dans le flag crédit bail est déjà existant. Celui-ci doit être unique. | 400 |
| CLOTURE1 | journal ou exercice cloturé | 400 |
| COMMENT1 | Le commentaire ne peut être vide. | 400 |
| COMMENT2 | Une erreur s'est produite lors du traitement du commentaire. | 400 |
| COMPTE 13  | Le compte doit commencer par 40 ou 41 | 400 |
| COMPTE1 | Le compte est invalide. | 400 |
| COMPTE10 | Le compte doit commencer par 41 | 400 |
| COMPTE11 | Le compte doit commencer par 67 ou 77, mais pas par 672 et 772. | 400 |
| COMPTE12 | Le compte doit commencer par 672 et 772. | 400 |
| COMPTE14 | Impossible de supprimer le compte car il est lié a une écriture. | 400 |
| COMPTE15 | Impossible de supprimer ce caractère | 400 |
| COMPTE16 | Impossible de changer le compte car il est lié à des écritures lettrées. | 400 |
| COMPTE17 | Impossible de générer les OD de paie car le compte %1 paramétré sur SILAE est invalide | 400 |
| COMPTE18 | Impossible de changer le numéro de compte car il est lié à des écritures cloturées | 400 |
| COMPTE19 | Info_compte_tiers n'existe pas | 400 |
| COMPTE2 | Le compte n'existe pas. | 400 |
| COMPTE20 | Impossible de diminuer la taille des comptes car au moins un de vos comptes dépasse cette limite. | 400 |
| COMPTE21 | Veuillez sélectionner au moins un compte. | 400 |
| COMPTE22 | Impossible de supprimer le compte car il est lié au dossier de révision. | 400 |
| COMPTE23 | Veuillez sélectionner un code TVA. | 400 |
| COMPTE24 | Vous ne pouvez affecter un code TVA que sur les comptes 2/6/7 | 400 |
| COMPTE25 | Ce compte a été validé par le cabinet. Il n’est pas modifiable | 400 |
| COMPTE26 | Ce compte a été validé par le RM. Il n’est pas modifiable | 400 |
| COMPTE27 | Attention ce compte a déjà été validé, voulez vous quand même modifier ce compte? La validation sera automatiquement supprimée | 400 |
| COMPTE28 | Impossible de supprimer le caractère numéro %1 car la liste de numéro de compte suivante sera en doublon: %2 | 400 |
| COMPTE29 | Impossible de fermer le compte, il est toujours en cours d'utilisation (%1) | 400 |
| COMPTE3 | Veuillez saisir un numéro de compte. | 400 |
| COMPTE30 | Le compte %1 est invalide | 400 |
| COMPTE31 | Le compte %1 doit commencer par %2 | 400 |
| COMPTE32 | Le compte est fermé | 400 |
| COMPTE4 | Veuillez saisir un intitulé pour le compte. | 400 |
| COMPTE5 | Le compte n'appartient pas à la société. | 400 |
| COMPTE6 | Le premier caractère du numéro de compte doit être compris entre 1 et 8. | 400 |
| COMPTE7 | Le numéro de compte saisi ne doit pas dépasser 20 caractères. | 400 |
| COMPTE8 | Les comptes de contrepartie autorisées pour les comptes 40 doivent commencer par 2 ou 6. | 400 |
| COMPTE9 | Les comptes de contrepartie autorisées pour les comptes 41 doivent commencer par 7. | 400 |
| CONNECTEUR1 | Un connecteur de ce type existe déjà. | 400 |
| CONNECTEUR2 | Connecteur inconnu | 400 |
| CONNECTEUR3 | Impossible de créer votre connecteur, les informations saisies sont invalides. | 400 |
| COORD1 | Le type de coordonnée n'est pas valide | 400 |
| DADP1 | La diligence est déja validé | 500 |
| DADP2 | Impossible de créer une situation avec les mêmes dates qu'un bilan | 403 |
| DATE1 | le format de la date %1 est invalide | 403 |
| DATE2 | La date de mise au rebut ne peut pas etre avant sa mise en service | 403 |
| DATE3 | Date debut > date fin | 400 |
| DBPERF1 | Impossible de supprimer ce paramètre, il est utilisé | 400 |
| DBPERF2 | Un des paramétres n'existe pas | 400 |
| DEADLINE1 | Vous ne pouvez pas saisir une date inférieur à la date de l'écheance. | 400 |
| DILIGENCE1 | Impossible de créer ou de trouver la diligence | 400 |
| DISCU1 | Impossible de se positionner sur le dossier de discussion du dossier | 500 |
| DISCU2 | Impossible de se positionner sur la conversation des flux divers | 500 |
| DOCUMENT1 | Une erreur s'est produite lors de la création du fichier | 500 |
| DOCUMENT10 | L'extension du fichier n'est pas acceptée. Seuls les fichiers .dat et .txt au format CFONB sont autorisés. | 400 |
| DOCUMENT11 | Le type de document n'est pas autorisé | 400 |
| DOCUMENT2 | L'extension du fichier n'est pas acceptée. Les extensions de fichiers autorisées sont : %1 | 400 |
| DOCUMENT3 | Erreur lors de la lecture du fichier | 500 |
| DOCUMENT4 | Veuillez saisir le nom du fichier | 400 |
| DOCUMENT5 | Une erreur s'est produite lors de la création du document sur le cloud | 500 |
| DOCUMENT6 | Une erreur sur la pièce jointe à été détectée. | 400 |
| DOCUMENT7 | Document non trouvé | 400 |
| DOCUMENT8 | Impossible de supprimer le document | 400 |
| DOCUMENT9 | L'extension du fichier n'est pas acceptée. | 400 |
| DOSSIERREV1 | Le dossier révision n'a pas été trouvé | 400 |
| DOSSIERREV2 | Option non disponible pour ce type de dossier de révision | 400 |
| DOSSIERREV3 | Type de dossier de revision inconnu | 400 |
| DOTATION1 | Impossible de supprimer cette écriture car elle est lié à une dotation d'amortissement | 400 |
| DR1 | Impossible, le dossier de révision a été visé. | 403 |
| DROIT1 | Vous n'avez pas accès à cette société | 403 |
| DROIT2 | Vous n'avez pas les droits. | 403 |
| DROIT3 | Cette fonctionnalité est reservé aux super administreurs | 403 |
| DROIT4 | Vous n'avez pas le droit e modifier l'email de l'utilisateur. | 403 |
| DROIT5 | Echec d'authentification | 401 |
| DROIT6 | Impossible de supprimer la société car le mot de passe renseigné n'est pas valide. | 400 |
| DSN1 | Aucun dossier de révision renseigné | 400 |
| DSN2 | Le dossier de révision n'est pas rattaché à cette société | 400 |
| DSN3 | Aucun ID DSN renseigné | 400 |
| ECR1 | Impossible de valider une écriture possédant un total débit différent du total crédit | 400 |
| ECR10 | La date de l'écriture n'appartient à aucun exercice. | 400 |
| ECR11 | Une erreur s'est produite lors de la création de l'écriture. | 400 |
| ECR12 | Une erreur s'est produite lors de l'enregistrement de l'écriture. | 400 |
| ECR13 | Une erreur s'est produite lors de la suppression des ecritures existantes | 400 |
| ECR14 | Ecriture déséquilibrée | 400 |
| ECR15 | Ecriture clôturée | 400 |
| ECR16 | Impossible de lettrer des écritures sur une plage interdite. | 400 |
| ECR17 | Impossible de créer une écriture de type %1 | 400 |
| ECR18 | Impossible de supprimer une écriture qui possède une ligne lettrée. | 400 |
| ECR19 | Impossible de modifier le journal d'une écriture extournée | 400 |
| ECR2 | Les valeurs débit et crédit sont invalides. | 400 |
| ECR20 | Impossible de supprimer une écriture générée par une feuillle de travail | 400 |
| ECR21 | le montant est vide | 400 |
| ECR22 | L'écriture a une ligne liée à un lettrage sur N-1. Elle ne peut pas être supprimée | 400 |
| ECR23 | Envoi EDI réussi mais une erreur est survenue lors de la génération des OD | 400 |
| ECR24 | Une erreur est survenue lors de la génération de l'OD DECLARATION FISCALE. | 400 |
| ECR25 |  %1 n'ont pas été basculer car elles ne respectent pas les règles. | 400 |
| ECR26 | Impossible de modifier une écriture d'A nouveaux. | 400 |
| ECR27 | Impossible de renseigner une valeur au débit et au crédit. | 400 |
| ECR28 | Impossible de supprimer une écriture qui possède une ligne pointée. | 403 |
| ECR29 | Impossible de modifier le débit ou le crédit d'une écriture lettrée. | 400 |
| ECR30 | Source de l'écriture inconnue | 400 |
| ECR31 | Impossible de supprimer une écriture d'A nouveaux | 400 |
| ECR32 | already_generated | 400 |
| ECR33 | Impossible de générer les A nouveaux car il y a une anomalie dans la comptabilité | 400 |
| ECR34 | Impossible de modifier le débit, le crédit ou le compte d'une écriture pointée | 400 |
| ECR4 | L'écriture est invalide | 400 |
| ECR5 | La date de début de période est invalide. | 400 |
| ECR6 | La date pièce est invalide. | 400 |
| ECR7 | La date de fin de période est invalide. | 400 |
| ECR8 | already_reversed | 400 |
| ECR9 | Impossible de saisir dans un exercice cloturé. | 400 |
| EDI1 | Impossible d'envoyer le message EDI, numéro de siret de la société vide. | 500 |
| EDI10 | Veuillez renseigner un montant pour le paiement. | 400 |
| EDI11 | Impossible d'envoyer le fichier EDI, merci de vérifier le login et mot de passe paramétré dans la fiche cabinet pour jedeclare.com. | 400 |
| EDI12 | Le couple login/mot de passe semble invalide. | 400 |
| EDI13 | Impossible d'envoyer le fichier EDI, adresse ou siret du Centre de Gestion invalide. | 400 |
| EDI14 | ROF invalide , %1 , la ROF doit commencer par %2 | 400 |
| EDI15 | %1 | 400 |
| EDI2 | Impossible d'envoyer le message EDI, numéro de siret du cabinet invalide. | 400 |
| EDI3 | Impossible d'envoyer le message EDI, l'adresse de la société est invalide. | 500 |
| EDI4 | Impossible d'envoyer le message EDI, l'adresse du cabinet est invalide. | 500 |
| EDI5 | Impossible d'envoyer le message EDI, le code adhérent de la société est invalide. | 500 |
| EDI6 | Impossible d'envoyer le message EDI, millésime invalide. | 500 |
| EDI7 | Impossible d'envoyer le message EDI, numéro d'agrément invalide. | 500 |
| EDI8 | Impossible d'envoyer le message EDI, aucun formulaire disponible. | 500 |
| EDI9 | Veuillez renseigner un RIB pour le paiement. | 400 |
| EMPRUNT_1 | Impossible de supprimer cet emprunt car il existe des ecritures sur au mois une des échéances. | 400 |
| EMPRUNT_2 | L'emprunt est terminé, il ne peut plus être modifié | 400 |
| EMPRUNT_3 | Il y a un soucis avec les fichiers contenu dans l'archive.<br>Fichier Emprunt_xxx.csv manquant" (et/ou) Fichier Echéances_xxx.csv manquant | 400 |
| EMPRUNT_4 | Au moins une des échéances n'appartient pas à l'emprunt en question. | 400 |
| ENTMOD1 | Aucun type n'a été renseigné | 400 |
| ENTMOD2 | Aucun label renseigné | 400 |
| ENTMOD3 | Date invalide ou passée | 400 |
| ENVOIEDI1 | Un envoi EDI est déja en cours de traitement. | 400 |
| ENVOIEDI2 | Un envoi edi a déja été validé et payé | 400 |
| ENVOIEDI3 | Un envoi edi a déja été validé mais le paiement a été rejeté. | 400 |
| ENVOIEDI4 | Un envoi edi a déja été validé. | 400 |
| ENVOIEEDI5 | Impossible d'envoyer la déclaration car aucun compte EDI n'a été sélectionné pour cette société. | 400 |
| ETAB1 | Seul un etablissement secondaire peut etre ferme | 400 |
| ETAB2 | L'etablissement est deja ferme | 400 |
| ETAB3 | L'etablissement n'appartient pas a la societe en cours | 400 |
| ETAB4 | Le SIREN de l'etablissement principal et secondaire doivent etre identique | 400 |
| ETAB5 | Impossible de modifier le type d'etablissement d'un etablissement secondaire | 400 |
| ETALON_TIERS1 | Ce siren est déja utilisé | 400 |
| ETALON1 | Cet étalon n'est pas modifiable. | 400 |
| ETALON2 | Impossible de supprimer cet étalon car il est lié à une ou plusieurs sociétés. | 400 |
| ETALON3 | Impossible de supprimer %1. | 400 |
| ETALON4 | Impossible de supprimer cet élément. | 400 |
| ETAT1 | filtre non autorisé sur les balances agées | 400 |
| ETAT2 | Pas de données | 400 |
| ETAT3 | On ne peut pas comparer avec les annees precedentes si on saisit des dates manuellement | 403 |
| EXC1 | Exception levee | 500 |
| EXERCICE1 | Aucun exercice n'a été trouvé sur cette période | 400 |
| EXERCICE10 | Exercice inexistant | 400 |
| EXERCICE11 | Impossible de comparer 2 exercices de plus de 12 mois en période équivalente (chevauchement de date) | 400 |
| EXERCICE12 | Methode de lettrage inconnue | 400 |
| EXERCICE2 | La période est à cheval sur plusieurs exercices, veuillez sélectionner qu’un seul exercice. | 400 |
| EXERCICE3 | Cette date appartient déja à un exercice. | 400 |
| EXERCICE4 | Impossible d'avoir un écart entre 2 exercices. | 400 |
| EXERCICE5 | Impossible de créer un exercice avec une date infèrieure à la date d'immatriculation de la société | 403 |
| EXERCICE6 | Exercice déjà cloturé | 400 |
| EXERCICE7 | Impossible de supprimer cet exercice, car il est lié à une ou plusieurs ecritures | 400 |
| EXERCICE8 | L'exercice n'est pas cloturé | 400 |
| EXERCICE9 | Impossible d'effectuer l'import tant que les exercices n'auront pas été renseignés | 400 |
| EXPENSE1 | Tranche kilométrique inexistante. | 400 |
| EXPENSE2 | L'identifiant du paramétrage est invalide | 400 |
| FACT1 | Le paramètre %1 doit être compris entre %2  et %3 | 400 |
| FEC1 | Impossible d'exporter un FEC sur une période à cheval sur 2 exercices. | 400 |
| FEC10 | FEC non équilibré | 400 |
| FEC2 | Une date contenu dans la colonne ecriture_date n'est pas valide. | 400 |
| FEC3 | Une date contenu dans la colonne piece_date n'est pas valide. | 400 |
| FEC4 | Une date contenu dans la colonne piece_date est en dehors de l'exercice. | 400 |
| FEC5 | Impossible de mettre à jour le libellé des comptes | 400 |
| FEC6 | Votre FEC contient au moins une écriture en dehors des bornes de l'exercice, vous devriez peut-être utilisé l'import FEC COALA ? | 400 |
| FEC7 | Export FEC non équilibré | 400 |
| FEC8 | Ecriture non équilibrée (attention : chaque écriture appartenant à un jour donnée doit être équilibré. Les centralisations ne sont pas acceptées dans le FEC) | 400 |
| FEC9 | Votre FEC contient une majorité d'écriture en dehors de l'exercice selectionné. Import annulé. | 400 |
| FLAG1 | Merci de renseigner le paramétrage de compte pour ce type de feuille de travail | 400 |
| FLAG2 | la date de mise en service d'une immobilisation ne peut être antérieure à la date d'achat | 400 |
| FLAG3 | Type de flag inconnu | 400 |
| FLAG4 | impossible de flaguer un véhicule sans flag immo ou crédit bail | 400 |
| FLAG5 | parametres manquants sur le flag crédit bail | 400 |
| FLAG6 | chemin crédit bail non trouvé | 500 |
| FLAG7 | Impossible d'utiliser ce compte car il est déjà lié à un emprunt | 400 |
| FORMAT1 | Les comptes de la section ne sont pas au bon format. Ex : (60;61;-611) | 400 |
| G_MEMBRE1 | Le SIREN renseigné est déjà utilisé par un autre cabinet. | 400 |
| GBL1 | Une erreur est survenue lors du traitement | 500 |
| GBL10 | Le paramètre %1 est manquant ou invalide | 400 |
| GBL11 | Le mail existe déja. | 400 |
| GBL12 | Le format de l'adresse mail est invalide | 400 |
| GBL13 | Veuillez saisir une adresse mail. | 400 |
| GBL14 | Le champ %1 doit contenir %2 caractères. | 400 |
| GBL15 | Erreur lors de la récupération ou de la lecture du token | 500 |
| GBL16 | La société n'a pas de nom | 400 |
| GBL17 | Association impossible | 400 |
| GBL18 | le parametre %1 ne peut etre etre vide | 400 |
| GBL19 | Aucun exercice trouvé à la date courante | 400 |
| GBL2 | Date saisie invalide | 400 |
| GBL20 | Impossible de se connecter au compte.
| GBL21 | Aucune date de début | 400 |
| GBL22 | Aucune date de fin | 400 |
| GBL23 | Une erreur a été rencontrée lors de la récupération du paramétrage du mail. | 400 |
| GBL24 | Il y a déja un compte par defaut pour ce membre. | 400 |
| GBL25 | Le libellé ne doit pas être vide. | 400 |
| GBL26 | La date %1 n'est pas dans la période du %2 au %3. | 400 |
| GBL27 | Paramètre manquant | 400 |
| GBL28 | Aucune donnée %1 | 400 |
| GBL29 | Origine inconnue | 400 |
| GBL3 | Vous devez saisir une date | 400 |
| GBL30 | Erreur SQL | 400 |
| GBL31 | Erreur création du répertoire | 400 |
| GBL4 | Une erreur est survenue lors de la requête au serveur | 400 |
| GBL5 | Le champ %1 ne peut excéder %2 caractères | 400 |
| GBL6 | Cet élément existe déjà. | 400 |
| GBL7 | Pas de données | 400 |
| GBL8 | Aucun ID n'a été envoyé | 400 |
| GBL9 | Une erreur a été rencontrée lors de l'envoi du mail. | 500 |
| IBAN1 | IBAN invalide | 400 |
| IMMEUBLE1 | Veuillez saisir un nom pour cet immeuble. | 400 |
| IMMEUBLE2 | Veuillez sélectionner un numéro d'ordre. | 400 |
| IMMEUBLE3 | Veuillez sélectionner un régime/déduction. | 400 |
| IMMEUBLE4 | Ce numéro d'ordre est déja utilisé | 400 |
| IMMEUBLE5 | Veuillez choisir la nature de l'immeuble. | 400 |
| IMMEUBLE6 | Ce numéro d'ordre n'appartient pas à la société. | 400 |
| IMMEUBLE7 | Cete section est déja utilisé. | 400 |
| IMMEUBLE8 | Cette section n'appartient pas à la société. | 400 |
| IMMO1 | Le type d'amortissement ne peut etre que linéaire ou dégréssif | 500 |
| IMMO2 | Pour un amortissement degressif la durée doit etre un multiple de 12 et etre également supérieur à 12 (24,36,48,60,...) | 403 |
| IMMO3 | Impossible de supprimer le compte car il est lié a une immo. | 400 |
| IMMO4 | merci de créer l'exercice antérieur car il y a des immo avec amortissement antérieur | 400 |
| IMMO5 | Une immobilisation non amortissable n'a pas de durée | 400 |
| IMMO6 | La date d'achat ne peut pas etre supérieure à la date de mise en service | 400 |
| IMMO7 | la durée minimum d'une immobilisation est de 12 mois | 400 |
| IMMO8 | Impossible de générer les dotations car il n'y a pas de journal configuré pour les écritures de dotations.<br> Pour le configurer, dans la fiche société -> comptabilité -> Immobilisation -> Journal OD pour les dotations | 400 |
| IMMO9 | Impossible de créer l'immobilisation car la date renseignée est supérieure à la date des exercices renseignés dans la fiche société | 400 |
| IMPORT1 | Vous n'appartenez pas au membre renseigné | 403 |
| IMPORT10 | Impossible de supprimer l'archive | 400 |
| IMPORT11 | Extension non supportée : %1 | 400 |
| IMPORT12 | Impossible de trouver le fichier de données | 400 |
| IMPORT13 | Le total du débit et différent du total du crédit | 400 |
| IMPORT14 | Le fichier est vide | 400 |
| IMPORT15 | Aucun flux bancaire trouvé, votre fichier est-il au format CFONB ? Ou les flux ont déjà été importés | 400 |
| IMPORT16 | Les types d'amortissements autorisés sont:<br>Linéaire<br>Dégressif<br>Non amortissable | 400 |
| IMPORT17 | Impossible d'ajouter des écritures d'A nouveaux dans un exercice qui en contient déjà | 400 |
| IMPORT18 | Le fichier semble mal formaté | 400 |
| IMPORT19 | la date d'achat n'est pas valide pour l'immo %1 | 400 |
| IMPORT2 | Accès refusé pour ce membre | 403 |
| IMPORT20 | Le fichier est vide ou toutes les configurations sont déjà existantes | 400 |
| IMPORT3 | Le nom de la société que vous voulez importer n'est pas renseigné. | 400 |
| IMPORT4 | Les écritures ne sont pas équilibrées sur au moins un exercice | 400 |
| IMPORT5 | Impossible d'effectuer l'import car il y a des écritures sur l'exercice. | 400 |
| IMPORT6 | Une erreur à été détecté lors de l'import. | 400 |
| IMPORT7 | Aucune immobilisation n'a été trouvée dans le fichier d'import | 400 |
| IMPORT8 | Impossible d'ouvrir l'archive | 400 |
| IMPORT9 | Impossible d'extraire l'archive | 400 |
| JDC1 | Connexion impossible à Jedeclare.com, merci de vérifier vos informations de connexion. | 403 |
| JOURNAL1 | Vous devez sélectionner un journal | 400 |
| JOURNAL10 | Ce journal est utilisé dans la fiche société -> comptabilité -> Journaux OCR. Veuillez d'abord modifier ce paramétrage. | 400 |
| JOURNAL11 | %1 | 400 |
| JOURNAL12 | Ce journal est utilisé dans la fiche société -> comptabilité -> Journal OD pour les dotations aux amortissements. Veuillez d'abord modifier ce paramétrage. | 400 |
| JOURNAL13 | Impossible d'envoyer une écriture dans un journal de type "À-Nouveaux" | 400 |
| JOURNAL14 | Impossible de changer le type d'un journal AN mouvementé | 400 |
| JOURNAL15 | Attention le journal %1 est utilisé dans le paramétrage %2 et ne peut pas être fermé. Merci de Modifier le paramétrage avant de fermer le journal | 400 |
| JOURNAL2 | Impossible d'ajouter une écriture dans un journal clôturé | 400 |
| JOURNAL3 | Le journal est invalide. | 400 |
| JOURNAL4 | Aucun journal de type '%1' n'a été détecté | 400 |
| JOURNAL5 | Un journal avec ce type existe déjà. | 400 |
| JOURNAL6 | Saisie d'un code journal obligatoire. | 400 |
| JOURNAL7 | Impossible de générer la contrepartie car aucun compte n'est paramétré sur ce journal.  | 400 |
| JOURNAL8 | Impossible d'affecter ce compte car il est déjà affecté à un autre journal. | 400 |
| JOURNAL9 | Impossible de saisir dans un journal qui n'a pas de type | 400 |
| JUSTIF1 | opérateur inconnu | 400 |
| JUSTIF2 | La justification n'appartient pas à la société | 400 |
| JUSTIF3 | La ligne de justification n'appartient pas à la justification | 400 |
| LENTMOD1 | On ne peut pas saisir débit et crédit sur une même ligne | 400 |
| LENTMOD2 | Un abonnement doit comporter des montants | 400 |
| LETAUTO1 | L'écart maximum ne peut excéder 5€ | 400 |
| LETAUTO2 | Le parametrage des comptes ou du journal OD lettrage est manquant | 400 |
| LETAUTO3 | le compte %1 doit commencer par %2 | 400 |
| LETTER1 | Impossible de modifier les types de paragraphe par défaut | 403 |
| LETTRAGE1 | Le total du débit est différent du total du crédit. | 400 |
| LETTRAGE2 | L'exercice est clôturé | 400 |
| LETTRAGE3 | Impossible de générer les A nouveaux car le lettrage des comptes suivants est déséquilibré: %1 | 400 |
| LETTRAGE4 | Impossible de lettrer un compte de classe 8 | 400 |
| LETTRAGE5 | Impossible de lettrer une ligne d'AN en mode lettrage multi-exercice. | 400 |
| LETTRAGE6 | Impossible de générer l'OD de lettrage sur des exercices différents en mode lettrage mono-exercice. | 400 |
| LETTRAGE7 | Impossible de revenir en mode lettrage mono-exercice une fois passé en multi-exercice. | 400 |
| LIASSE1 | Merci de saisir un régime fiscal pour cette société. | 400 |
| LIASSE2 | Votre régime fiscal n'est pas concerné par les OG. | 400 |
| LIASSE3 | Les informations nécessaires à l'affichage des formulaires OGA ne sont pas saisies pour cette société dans le CRM. | 400 |
| LIASSE4 | Impossible de renseigner un moyen de paiement sans montant. | 400 |
| MEMBRE1 | Veuillez selectionner un membre. | 400 |
| MEMBRE2 | Les cabinets suivants sont liés à des sociétés et ne peuvent donc être supprimés (%1) | 400 |
| MOBILE1 | Veuillez mettre à jour votre application. | 400 |
| MODELEDR1 | Code modèle existant | 400 |
| MODELEDR2 | Impossible de créer le modèle | 400 |
| MODELEDR3 | Impossible de modifier le modèle | 400 |
| MODELEDR4 | Impossible de vérifier l'existence des modeles sur les sociétés | 400 |
| MODELEDR5 | Code cycle existant | 400 |
| MODELEDR6 | Code diligence existant | 400 |
| NOTIF1 | Impossible d'insérer, la notification existe déjà | 400 |
| OCR1 | Extension non acceptée | 400 |
| PAIE1 | Authentification échouée | 403 |
| PAIE10 | Impossible de lire les infos du salarié | 400 |
| PAIE100 | Impossible de récupérer les sociétés pour le traitement auto SILAE | 400 |
| PAIE101 | Impossible de récupérer la configuration de la société pour le traitement auto SILAE | 400 |
| PAIE102 | Jour d'exécution du traitement auto SILAE invalide | 400 |
| PAIE103 | Pas d'exécution du traitement auto SILAE pour cette société aujourd'hui | 400 |
| PAIE104 | Aucune option de génération est configurée pour cette société | 400 |
| PAIE105 | Sortie du traitement auto SILAE sans exécution | 400 |
| PAIE106 | Impossible de valider les bulletins et / ou de les envoyer au coffre fort | 400 |
| PAIE107 | Impossible de récupérer le paramètre de l'application salarié | 400 |
| PAIE108 | Vérifiez la configuration de l'application salariée dans le dshboard Admin E/C. | 400 |
| PAIE109 | L'id edoc du groupe membre n'appartient pas à notre arborescence | 400 |
| PAIE11 | Impossible de télécharger le bulletin | 400 |
| PAIE110 | L'id edoc du membre n'appartient pas à notre arborescence | 400 |
| PAIE111 | L'id edoc de la société n'appartient pas à notre arborescence | 400 |
| PAIE12 | Impossible de sauvegarder le bulletin sur le serveur | 400 |
| PAIE13 | Impossible de créer le répertoire  | 400 |
| PAIE14 | Impossible de déplacer le fichier dans le répertoire | 400 |
| PAIE15 | Aucun bulletin valide à envoyer | 400 |
| PAIE16 | Impossible de créer le fichier header.xml | 400 |
| PAIE17 | Impossible de créer le fichier metaDatas.xml | 400 |
| PAIE18 | Impossible de créer le fichier init.txt | 400 |
| PAIE19 | Impossible de fermer le fichier init.txt | 400 |
| PAIE2 | Impossible de récupérer l'organisation principale | 400 |
| PAIE20 | Impossible de créer le zip | 400 |
| PAIE21 | Impossible d'ajouter le répertoire au zip | 400 |
| PAIE22 | Impossible de supprimer le fichier init.txt | 400 |
| PAIE23 | Impossible de supprimer le répertoire | 400 |
| PAIE24 | Impossible de joindre le zip au formulaire | 400 |
| PAIE25 | Impossible d'envoyer le formulaire | 400 |
| PAIE26 | Impossible de supprimer le zip | 400 |
| PAIE27 | Impossible de mettre à jour le statut du bulletin | 400 |
| PAIE28 | Connexion impossible à SILAE | 400 |
| PAIE29 | Récupération impossible des bulletins SILAE | 400 |
| PAIE3 | Impossible de récupérer le nom de la société | 400 |
| PAIE30 | Impossible de lire les informations des organisations | 400 |
| PAIE31 | SIRET groupe_membre manquant | 400 |
| PAIE32 | Impossible de lire l'id_organisation | 400 |
| PAIE33 | Aucun id_organisation parent pour le cabinet | 400 |
| PAIE34 | Aucun id_organisation parent pour la société | 400 |
| PAIE35 | Recherche SIRET impossible | 400 |
| PAIE36 | La création de l'organisation a échoué | 400 |
| PAIE37 | SIRET membre manquant | 400 |
| PAIE38 | SIRET société manquant | 400 |
| PAIE39 | Impossible de vérifier et créér les organisations | 400 |
| PAIE4 | Nom de la société vide | 400 |
| PAIE40 | Impossible de lire les informations de la personne physique | 400 |
| PAIE41 | Impossible de lire les accès de la personne physique | 400 |
| PAIE42 | Impossible de lire le matricule du salarié | 400 |
| PAIE43 | Matricule du salarié non configuré dans SILAE | 400 |
| PAIE44 | Impossible de mettre à jour les informations du salarié | 400 |
| PAIE45 | Impossible d'enregistrer le matricule du salarié | 400 |
| PAIE46 | Aucun mail valide configuré dans SILAE pour le salarié | 400 |
| PAIE47 | Impossible de lire le profil du salarié | 400 |
| PAIE48 | Impossible de créer l'utilisateur | 400 |
| PAIE49 | Impossible de récupérer l'id user | 400 |
| PAIE5 | Numéro de SIRET vide | 400 |
| PAIE50 | Id user invalide | 400 |
| PAIE51 | Impossible de récupérer le mail du salarié | 400 |
| PAIE52 | Impossible de lire le statut du coffre salarié | 400 |
| PAIE53 | Impossible de mettre à jour le statut du coffre | 400 |
| PAIE54 | Impossible de lire l'id salarié | 400 |
| PAIE55 | Impossible de récupérer l'id salarié | 400 |
| PAIE56 | Impossible d'envoyer la notification de création de coffre | 400 |
| PAIE57 | Impossible de créer le coffre fort | 400 |
| PAIE58 | Impossible d'enregistrer l'id salarié | 400 |
| PAIE59 | Création salarié impossible | 400 |
| PAIE6 | Création dispatch de bulletins impossible | 400 |
| PAIE60 | Impossible de lire les informations du salarié | 400 |
| PAIE61 | Erreur vérification activation coffre | 400 |
| PAIE62 | Impossible de vérifier le bulletin | 400 |
| PAIE63 | Impossible de créer le bulletin | 400 |
| PAIE64 | Impossible de créer l'historique du bulletin | 400 |
| PAIE65 | Impossible de créer le bulletin sur le cloud | 400 |
| PAIE66 | Impossible de créer le document | 400 |
| PAIE67 | Impossible de créer la liaison bulletin document | 400 |
| PAIE68 | Impossible de mettre à jour l'id organisation | 400 |
| PAIE69 | Aucune civilité saisie dans SILAE | 400 |
| PAIE7 | Impossible de lire le statut du bulletin | 400 |
| PAIE70 | Aucun nom saisi dans SILAE | 400 |
| PAIE71 | Aucun prénom saisi dans SILAE | 400 |
| PAIE72 | Aucun matricule saisi dans SILAE | 400 |
| PAIE73 | N° de sécurité sociale invalide | 400 |
| PAIE74 | Date de naissance invalide | 400 |
| PAIE75 | Mail invalide | 400 |
| PAIE76 | Adresse invalide | 400 |
| PAIE77 | Ville invalide | 400 |
| PAIE78 | Pays invalide | 400 |
| PAIE79 | Aucun bulletin valide pour le salarié | 400 |
| PAIE8 | Impossible de valider le bulletin | 400 |
| PAIE80 | Erreur création des accès pour le salarié | 400 |
| PAIE81 | Récupération des bulletins échouée pour le salarié | 400 |
| PAIE82 | Impossible de récupérer les ids des bulletins | 400 |
| PAIE83 | Des erreurs ont été détectées lors de la mise au coffre des bulletins de salaire | 400 |
| PAIE84 | Impossible de lire le souhait du cabinet | 400 |
| PAIE85 | Impossible de lire le souhait de la société | 400 |
| PAIE86 | Impossible de lire le souhait du salarié | 400 |
| PAIE87 | Impossible de mettre à jour le souhait du cabinet | 400 |
| PAIE88 | Impossible de mettre à jour le souhait de la société | 400 |
| PAIE89 | Impossible de vérifier les souhaits cabinet et société | 400 |
| PAIE9 | Impossible de récupérer les infos des bulletins | 400 |
| PAIE90 | Impossible de mettre à jour le souhait du salarié | 400 |
| PAIE91 | Coffre non disponible pour le cabinet | 400 |
| PAIE92 | Coffre désactivé pour la société | 400 |
| PAIE93 | Coffre désactivé pour le salarié | 400 |
| PAIE94 | Impossible de lire le statut du souhait du coffre | 400 |
| PAIE95 | Impossible de mettre à jour le statut du souhait du coffre | 400 |
| PAIE96 | Token bulletin non valide | 400 |
| PAIE97 | Téléchargement du bulletin échoué | 400 |
| PAIE98 | Envoi du bulletin impossible | 400 |
| PAIE99 | Attachement du bulletin au mail échoué | 400 |
| PERS_PHYSIQUE1 | Veuillez saisir un nom | 400 |
| PERS_PHYSIQUE2 | Veuillez saisir un prénom | 400 |
| PERS_PHYSIQUE3 | La date de naissance est invalide. | 400 |
| PERS_PHYSIQUE4 | La coordonnée que vous voulez suppimer est utilisé pour son compte utilisateur. | 400 |
| PERS_PHYSIQUE5 | Aucune personne selectionnée | 400 |
| PERS_PHYSIQUE6 | La longueur du code NIF est invalide pour ce pays (%1) | 400 |
| PERS_PHYSIQUE7 | Le premier caractère ne correspond pas à la norme du pays (%1) | 400 |
| PERS_PHYSIQUE8 | Cette personne a déjà un lien avec cette société qui n'est pas terminé | 400 |
| PERS_PHYSIQUE9 | Cette personne est liée à un dossier | 400 |
| PLAQUETTE1 | modèle non trouvé | 400 |
| PLAQUETTE2 | HTML model type inconnu | 400 |
| PLAQUETTE3 | Impossible de modifier un modèle | 400 |
| PLAQUETTE4 | %1 n'est pas disponible. Veuillez la générer ou l'exclure de la selection. | 400 |
| PLAQUETTE5 | Pied de page non trouvé | 400 |
| PWDSOC1 | Aucun mot de passe définit | 400 |
| PWDSOC2 | Le mot de passe ne correspond pas | 400 |
| PWUSR1 | Le mot de passe ne respecte pas la securite minimale (doit contenir une minuscule, une majuscule, un chiffre, un caractere special et doit être de 8 caractere minimum) | 400 |
| QTY1 | Une des racines de compte est invalide ou déjà couverte dans le paramétrage existant (%1) | 400 |
| QTY2 | Occurrence invalide, il n'y a que 2 quantités différentes possible (1 ou 2) | 400 |
| QTY3 | Unité de la quantité est invalide | 400 |
| QTY4 | Un paramètre obligatoire n'est pas renseigné | 400 |
| QTY5 | Impossible de modifier une unité par défaut | 400 |
| QTY6 | Code de l'unité manquant | 400 |
| QTY7 | Label de l'unité manquant | 400 |
| QTY8 | Les comptes n'ont pas le meme parametrage des quantites | 400 |
| QTY9 | La quantité est utilisée dans les écritures et ne peut etre supprimée | 400 |
| RAPPRO1 | Aucun compte n'a été paramétré pour ce journal | 400 |
| RAPPRO2 | Vous ne pouvez pas faire un rapprochement bancaire à une date ulterieure à la date du jour | 400 |
| RAPPRO3 | Erreur, au moins une des lignes que vous souhaitez pointés, a déjà été pointés | 400 |
| RB1 | La règle que vous souhaitez créer entre en conflit avec une ancienne règle | 403 |
| RB2 | Erreur dans le format du CFONB | 400 |
| RB3 | Erreur récupération tabStructureCFONB120 | 400 |
| RB4 | Mot clé ne peut pas être vide | 400 |
| RGLMT1 | Le montant total ne correspond pas au montant à payer | 400 |
| RGLMT2 | Le montant total est supérieur au montant à payer | 400 |
| RGLMT3 | Le montant à payer est nul | 400 |
| RGLMT4 | Type de formulaire inconnu | 400 |
| RIB1 | Veuillez saisir un IBAN. | 400 |
| RIB10 | IBAN invalide | 400 |
| RIB11 | Cet IBAN existe déja.  | 400 |
| RIB12 | Merci de bien vouloir renseigner le titulaire du compte par défaut. | 400 |
| RIB2 | Veuillez saisir un BIC. | 400 |
| RIB3 | La clé RIB n'est pas valide. | 400 |
| RIB4 | Veuillez saisir une clé. | 400 |
| RIB5 | Veuillez saisir un code banque. | 400 |
| RIB6 | Veuillez saisir un code guichet. | 400 |
| RIB7 | Veuillez saisir un numéro de compte bancaire. | 400 |
| RIB8 | Impossible de paramétrer ce journal car il est déjà lié à un autre RIB | 400 |
| RIB9 | Taille IBAN invalid | 400 |
| ROADTYP1 | Ce type de voie n'existe pas | 400 |
| SECTION001 | Cette section est un section par defaut sur un axe. Impossible de la supprimer | 400 |
| SECTION002 | la section %1 n'a pas été trouvé | 400 |
| SECTION003 | Impossible de supprimer l'axe ou la section car il existe déjà une écriture analytique dessus | 400 |
| SEPA01 | L'IBAN/RIB n'a pas été trouvé pour le compte | 400 |
| SEPA02 | Le fichier XML du prélèvement SEPA est invalide | 400 |
| SEPA03 | Le RUM du compte client doit être renseigné | 400 |
| SERVICE1 | Service invalide | 400 |
| SERVICE2 | Le service n'est pas lié à cette société  | 400 |
| SILAE1 | Veuillez saisir une periode | 400 |
| SILAE10 | Vous n'avez pas de droits en paie sur ce dossier | 400 |
| SILAE11 | Erreur SILAE | 400 |
| SILAE2 | La periode saisie est invalide | 400 |
| SILAE3 | La periode saisie doit être superieure à 12 mois | 400 |
| SILAE4 | Aucun code dossier n'est paramétré pour SILAE dans les connecteurs. | 400 |
| SILAE5 | Le login SILAE n'est pas correctement paramétré sur votre cabinet membre. | 400 |
| SILAE6 | Aucun journal d'OD PAIE n'est paramétré. | 400 |
| SILAE7 | Aucun salarié trouvé | 400 |
| SILAE8 | Le mot de passe du dossier SILAE est invalide. | 400 |
| SILAE9 | Problème de récupération de données de SILAE (%1) | 400 |
| SOCIETE1 | La taille du siren est invalide. | 400 |
| SOCIETE10 | Aucune société selectionnée | 400 |
| SOCIETE11 | Format SIREN/SIRET invalide | 400 |
| SOCIETE12 | Ce dossier est inaccessible car sa formule de facturation est "Inactif" . Pour l'activer, veuillez contacter votre administrateur afin qu’il renseigne la formule que vous souhaitez appliquer à ce dossier. | 400 |
| SOCIETE13 | Impossible de répondre à votre requête, merci de bien vouloir sélectionner une formule de facturation pour ce dossier. Home -> Admin/EC | 400 |
| SOCIETE14 | L'adresse mail liasse est invalide | 400 |
| SOCIETE15 | Code ICS invalide | 400 |
| SOCIETE16 | Société introuvable | 400 |
| SOCIETE17 | Plusieurs sociétés ont été trouvées | 400 |
| SOCIETE2 | La date du capital est invalide. | 400 |
| SOCIETE3 | Veuillez renseigner des parts sur la société | 400 |
| SOCIETE4 | Veuillez saisir un nom pour la société. | 400 |
| SOCIETE5 | Ce siret est déja enregistré dans la base de données. | 400 |
| SOCIETE6 | Le numéro de l'adresse postale est invalide. | 400 |
| SOCIETE7 | Veuillez sélectionner un membre dans la liste. | 400 |
| SOCIETE8 | Veuillez paramètrer le régime TVA de la société. | 400 |
| SOCIETE9 | La déclaration de TVA n'est pas disponible, car votre régime TVA est "Non Assujetti". | 400 |
| STDMEMBRE1 | Le libelle du standard ne peut pas être vide | 400 |
| STDMEMBRE2 | Le cabinet est obligatoire | 400 |
| STDMEMBRE3 | Le plan comptable est obligatoire | 400 |
| STDMEMBRE4 | Le compte "intérêts courus non échus" doit commencer par 168 ou 661 | 400 |
| STDMEMBRE5 | Le journal de comptabilisation des ICNE ne peut être que du type "OD" ou "A EXTOURNER" | 400 |
| SUB1 | Aucune fréquence renseignée | 400 |
| SUB2 | La durée de l'abonnement ne peut pas etre inférieure à 1 mois | 400 |
| SUPER1 | Vous n'avez pas les droits pour ce Dashboard Superviseur | 400 |
| TOKEN1 | Token invalide | 400 |
| TOKEN2 | Token expiré | 400 |
| TOKENERROR | %1 | 400 |
| TYPEPAY1 | Le type de paiement n'appartient pas à la société | 400 |
| UNIK1 | Ce code section existe déjà pour cette société | 400 |
| USER1 | Impossible de trier sur cette colonne | 400 |
| USER10 | L'utilisateur n'est pas rattaché à la société sélectionnée | 400 |
| USER11 | L'utilisateur est déjà dans un groupe pour cette société | 400 |
| USER12 | Utilisateur non autorise | 400 |
| USER2 | Sens de tri invalide | 400 |
| USER3 | Seul un administrateur peut créer un utilisateur | 400 |
| USER4 | L'utilisateur que vous souhaitez modifier n'existe pas | 400 |
| USER5 | Une erreur est survenue lors de la création du jeton de reinitialisation du mot de passe | 500 |
| USER6 | L'adresse email et l'adresse du serveur web sont obligatoire par la réinitialisation du mot de passe | 400 |
| USER7 | le token est expiré | 400 |
| USER8 | Ce mail n'appartient à aucun utilisateur. | 400 |
| USER9 | Veuillez saisir une adresse mail. | 400 |
| VATPARAM1 | Le code TVA que vous tentez de créer existe déjà | 400 |
| VATPARAM2 | Le code TVA renseigné n'appartient pas à la societe | 400 |
| VEHICULE1 | La date de début d'utilisation est absente ou invalide | 400 |
| VEHICULE10 | Le document n'appartient pas au véhicule | 400 |
| VEHICULE11 | Le vehicule n'appartient pas à la societe | 400 |
| VEHICULE2 | La date de fin d'utilisation est invalide | 400 |
| VEHICULE3 | type d'affectation inconnu | 400 |
| VEHICULE4 | L'objet %1 est attendu pour ce type d'affectation | 400 |
| VEHICULE5 | type de vehicule inconnu | 400 |
| VEHICULE6 | type de carburant inconnu | 400 |
| VEHICULE7 | %1.start_date n'est pas valide | 400 |
| VEHICULE8 | La personne renseignée n'est pas un associé de l'entreprise | 400 |
| VEHICULE9 | La personne renseignée n'est pas employée par l'entreprise | 400 |
| WALLET1 | Impossible de supprimer un portefeuille affecté à des utilisateurs. | 400 |
| WALLET2 | La suppresion or la modification du portefeuille "TOUTES" est interdit. | 400 |
| WALLETT3 | L'objet "wallet" est manquant | 400 |
| WEEKERA1 | Le groupe n'est pas relié à la société | 400 |
| WEEKERA2 | Le rôle du superviseur n'est pas actif | 400 |
| WEEKERA3 | Un superviseur ne peut pas superviser un groupe dans lequel il est | 400 |
| WEEKERA4 | Le superviseur saisi est déjà sur un autre rôle pour la fonctionnalité et le groupe sélectionné | 400 |
| WEEKERA5 | Un superviseur est déjà renseigné pour la fonctionnalité, le groupe et le rôle indiqué | 400 |
| WEEKERA6 | Veuillez renseigner toutes les informations pour le paramétrage (fonctionnalité, niveau du rôle, équipe et superviseur) | 400 |
| WEEKERA7 | L'identifiant du paramètre est invalide | 400 |
| WEEKERA8 | Le superviseur n'a pas accès à la société | 400 |
| WEEKERA9 | Vous n'êtes pas superviseur de cet utilisateur | 400 |
| WORKSHEET1 | Vous ne pouvez pas supprimer ou modifier une feuille de travail contenant des écritures | 400 |
| WORKSHEET10 | Les comptes de l'écriture ne correspondent pas à ceux attendus dans la feuille de travail | 400 |
| WORKSHEET11 | Aucune configuration par défaut n'est disponnible pour ce type de feuille de travail | 500 |
| WORKSHEET12 | Aucune feuille de travail selectionnée | 400 |
| WORKSHEET13 | Impossible de supprimer le dernier paramètrage de compte de feuille de travail du type %1. | 400 |
| WORKSHEET14 | Impossible de modifier une feuille de travail Validé (Validation Collab). | 400 |
| WORKSHEET15 | Aucun %1 à constater. Les dates sont comprises dans l’exercice ! | 400 |
| WORKSHEET16 | Imposible de supprimer tous les paramètrage d'un même type | 400 |
| WORKSHEET2 | La feuille de travail existe déjà | 400 |
| WORKSHEET3 | Le numéro de compte %1 est invalide | 400 |
| WORKSHEET4 | id_account_tva ne doit pas être renseigné pour ce type de feuille de travail | 400 |
| WORKSHEET5 | Impossible d'ajouter une feuille de travail avec une date en dehors de l'exercice N | 400 |
| WORKSHEET6 | La valeur du TTC n'est pas égale au HT+TVA | 400 |
| WORKSHEET7 | La periode renseignée n'est pas valide | 400 |
| WORKSHEET8 | Le compte de TVA ne doit pas être renseigné pour ce type de feuille de travail | 400 |
| WORKSHEET9 | Impossible de trouver la feuille de travail sélectionnée | 400 |

---

⬅️ [README](../README.md)
