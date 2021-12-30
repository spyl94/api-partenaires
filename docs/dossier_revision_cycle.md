# Récupérer les cycles d'un dossier de révision/modèle de révision.
Ce guide a pour objectif de vous aider dans la récupération des cycles d'un dossier de révision/modèle de révision.

![](./images/dossier_revision_cycle.png)

Dans l'application MyUnisoft les dossiers de révision peuvent gérés depuis le menu : `Révision` > `Révision` > `Dossier de révison`.

![](./images/dossier_revision_menu.png)

## API

La route https://api.myunisoft.fr/api/v1/dadp/dossier_revision_list permet de récupérer ces informations.

> 👀 Penser à préciser l'en-tête **society-id** si vous utilisez un 🔹 Accès cabinet.

Les parmètres de l'URL sont:

| clé | exemple | description |
| --- | --- | --- |
| category | DA | DA par défaut ??? |
| dossier_revision_id | 11733 | REQUIRED - [ID du dossier de révision](./dossier_revision.md)|
| start_date | 2018-01-01 | REQUIRED - [Début de la révision/exercice?](./dossier_revision.md) Format: YYYY-MM-DD |
| end_date | 2018-12-31 | REQUIRED - [Fin de la révision/exercice?](./dossier_revision.md) Format: YYYY-MM-DD |
| section_id | 1 | REQUIRED - ??? |
| cycle_da_dp_id | -1 | REQUIRED - Pour récupérer un ou tous les cycles. (**-1** pour tous les cycles)|

```bash
$ curl --location --request GET 'https://api.myunisoft.fr/api/v1/dadp/cycle?category=DA&dossier_revision_id=11733&start_date=2018-01-01&end_date=2018-12-31&section_id=1&cycle_da_dp_id=-1' \
--header 'X-Third-Party-Secret: nompartenaire-L8vlKfjJ5y7zwFj2J49xo53V' \
--header 'Authorization: Bearer {{API_TOKEN}}'
```

Si tout se passe bien vous devriez recevoir un JSON avec **une structure similaire à l'exemple ci-dessous**

```json
[
    {
        "code": "AC-A",
        "label": "Régularité",
        "valid_rm": "to_validate",
        "section_id": 1,
        "valid_collab": "to_do",
        "cycle_da_dp_id": 1
    },
    {
        "code": "AC-B",
        "label": "Trésorerie",
        "valid_rm": "to_validate",
        "section_id": 1,
        "valid_collab": "to_do",
        "cycle_da_dp_id": 2
    },
    {
        "code": "AC-C",
        "label": "Achats + Fournisseurs",
        "valid_rm": "to_validate",
        "section_id": 1,
        "valid_collab": "to_do",
        "cycle_da_dp_id": 3
    },
    {
        "code": "AC-D",
        "label": "Charges Externes",
        "valid_rm": "to_validate",
        "section_id": 1,
        "valid_collab": "to_do",
        "cycle_da_dp_id": 4
    },
    {
        "code": "AC-E",
        "label": "Ventes + Clients",
        "valid_rm": "to_validate",
        "section_id": 1,
        "valid_collab": "to_do",
        "cycle_da_dp_id": 5
    },
    {
        "code": "AC-F",
        "label": "Stocks",
        "valid_rm": "to_validate",
        "section_id": 1,
        "valid_collab": "to_do",
        "cycle_da_dp_id": 6
    },
    {
        "code": "AC-G",
        "label": "Immobilisations",
        "valid_rm": "to_validate",
        "section_id": 1,
        "valid_collab": "to_do",
        "cycle_da_dp_id": 7
    },
    {
        "code": "AC-H",
        "label": "Personnel",
        "valid_rm": "to_validate",
        "section_id": 1,
        "valid_collab": "to_do",
        "cycle_da_dp_id": 8
    },
    {
        "code": "AC-I",
        "label": "Etat",
        "valid_rm": "to_validate",
        "section_id": 1,
        "valid_collab": "to_do",
        "cycle_da_dp_id": 9
    },
    {
        "code": "AC-J",
        "label": "Capitaux + Provisions",
        "valid_rm": "to_validate",
        "section_id": 1,
        "valid_collab": "to_do",
        "cycle_da_dp_id": 10
    },
    {
        "code": "AC-K",
        "label": "Groupe et Associés",
        "valid_rm": "to_validate",
        "section_id": 1,
        "valid_collab": "to_do",
        "cycle_da_dp_id": 11
    },
    {
        "code": "AC-L",
        "label": "Autres comptes",
        "valid_rm": "to_validate",
        "section_id": 1,
        "valid_collab": "to_do",
        "cycle_da_dp_id": 12
    },
    {
        "code": "AC-M",
        "label": "Annexe",
        "valid_rm": "to_validate",
        "section_id": 1,
        "valid_collab": "to_do",
        "cycle_da_dp_id": 13
    }
]
```

Le endpoint **/dadp/cycle** retourne un tableau de structure Cycle.

```ts
interface Cycle {
  code: string;
  label: string;
  valid_rm: string;
  section_id: number;
  valid_collab: string;
  cycle_da_dp_id: number;
}
```
