# Recherche simplifiée dans les écritures d'un dossier

Ce guide a pour objectif de vous aider à effectuer une recherche dans les écritures d'un dossier.

> **Note**
>
> Cet endpoint est uniquement disponible avec un accès cabinet.

Dans MyUnisoft, vous pouvez accéder à la recherche rapide en cliquant sur la loupe du menu rapide comme indiqué dans l'image ci-dessous.

![](./images/quick_search.jpg)

## Liste des paramètres de recherche

| Nom | Description | Obligatoire |
|---|---|---|
|idEtablissement||✔️|
|startDate||❌|
|endDate||❌|
|journalId||❌|
|accountId||❌|
|axeId||❌|
|intitule||❌|
|sectionId||❌|
|exerciceIds||❌|
|debit||❌|
|credit||❌|
|plusMinusRange||❌|
|page||❌|
|resultPerPage||❌|

## Quick Search

```bash
curl --location --request GET 'https://app.myunisoft.fr/api/v1/accounting/entry/search?idEtablissement=5300&startDate=2020-01-01&endDate=2020-12-31' \
--header 'X-Third-Party-Secret: X-Third-Party-Secret'
```

<details>
  <summary>Retour JSON de l'API</summary>

  ```json
    {
      "data": [
        {
          "ligneEcriture_piece": null,
          "ligneEcriture_piece_2": "0000",
          "ligneEcriture_lettrage": null,
          "ligneEcriture_debit": "0",
          "ligneEcriture_credit": "14.62",
          "journal_code": "20",
          "id_etablissement": "5300",
          "id_ecriture": "46889055",
          "date_comptabilisation": "2020-12-30T23:00:00.000Z",
          "date_piece": "2020-12-30T23:00:00.000Z",
          "id_axe": null,
          "code_axe": null,
          "label_axe": null,
          "id_journal": "128926",
          "intitule_journal": "JOURNAL D' OD",
          "no_compte": "280500",
          "id_compte": "6393513",
          "intitule_ligne": "DOT. AMORT. 12/2020",
          "idligneecriture": "141757599",
          "date_echeance": null,
          "id_exercice": "29623",
          "exercice_date_debut": "2019-12-31T23:00:00.000Z",
          "exercice_date_fin": "2020-12-30T23:00:00.000Z",
          "type_reglement_name": null,
          "type_reglement_abbreviation": null,
          "analytics": null
        },
        // ...
        {
          "ligneEcriture_piece": null,
          "ligneEcriture_piece_2": "0000",
          "ligneEcriture_lettrage": null,
          "ligneEcriture_debit": "2.1",
          "ligneEcriture_credit": "0",
          "journal_code": "20",
          "id_etablissement": "5300",
          "id_ecriture": "46889057",
          "date_comptabilisation": "2020-12-30T23:00:00.000Z",
          "date_piece": "2020-12-30T23:00:00.000Z",
          "id_axe": null,
          "code_axe": null,
          "label_axe": null,
          "id_journal": "128926",
          "intitule_journal": "JOURNAL D' OD",
          "no_compte": "681000",
          "id_compte": "6393510",
          "intitule_ligne": "DOT. AMORT. 12/2020",
          "idligneecriture": "141757603",
          "date_echeance": null,
          "id_exercice": "29623",
          "exercice_date_debut": "2019-12-31T23:00:00.000Z",
          "exercice_date_fin": "2020-12-30T23:00:00.000Z",
          "type_reglement_name": null,
          "type_reglement_abbreviation": null,
          "analytics": null
        }
      ]
    }
  ```
</details>

---

⬅️ [README](../README.md)
