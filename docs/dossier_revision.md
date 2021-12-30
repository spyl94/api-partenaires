# Récupérer les dossiers de révision d'une société (dossier de production)
Ce guide a pour objectif de vous aider dans la récupération des dossiers de révision d'une société (dossier de production).

![](./images/dossier_revision.png)

Dans l'application MyUnisoft les dossiers de révision peuvent gérés depuis le menu: `Révision` > `Révision` > `Dossier de révison`.

![](./images/dossier_revision_menu.png)

## API

La route https://api.myunisoft.fr/api/v1/dadp/dossier_revision_list permet de récupérer ces informations.

> 👀 Penser à préciser l'en-tête **society-id** si vous utilisez un 🔹 Accès cabinet.

> 👀 Vous pouvez récupérer un seul dossier de révision en renseigant le paramètre **review_id**.

```bash
# GET ALL
$ curl --location --request GET 'https://api.myunisoft.fr/api/v1/dadp/dossier_revision_list' \
--header 'X-Third-Party-Secret: nompartenaire-L8vlKfjJ5y7zwFj2J49xo53V' \
--header 'Authorization: Bearer {{API_TOKEN}}'

# GET ONE
$ curl --location --request GET 'https://api.myunisoft.fr/api/v1/dadp/dossier_revision_list?review_id=ID_DE_LA_REVIEW' \
--header 'X-Third-Party-Secret: nompartenaire-L8vlKfjJ5y7zwFj2J49xo53V' \
--header 'Authorization: Bearer {{API_TOKEN}}'
```

Si tout se passe bien vous devriez recevoir un JSON avec **une structure similaire à l'exemple ci-dessous**

```json
{
    "dossier_revision_list": [
        {
            "type": {
                "id": 2,
                "code": "BIL",
                "label": "Bilan"
            },
            "end_date": "2021-12-31",
            "exercise": "N+1",
            "start_date": "2021-01-01",
            "review_model": {
                "label": "Modèle Standard Myunisoft",
                "modified_by": "MyUniSoft",
                "id_review_model": 1,
                "last_modify_date": "2021-11-26T22:57:40"
            },
            "id_dossier_revision": 1
        },
        {
            "type": {
                "id": 2,
                "code": "BIL",
                "label": "Bilan"
            },
            "end_date": "2020-12-31",
            "exercise": "N",
            "start_date": "2020-01-01",
            "review_model": {
                "label": "Modèle Standard Myunisoft",
                "modified_by": "MyUniSoft",
                "id_review_model": 1,
                "last_modify_date": "2021-11-26T22:57:40"
            },
            "id_dossier_revision": 2
        },
        {
            "type": {
                "id": 2,
                "code": "BIL",
                "label": "Bilan"
            },
            "end_date": "2019-12-31",
            "exercise": "N-1",
            "start_date": "2019-01-01",
            "review_model": {
                "label": "Modèle Standard Myunisoft",
                "modified_by": "MyUniSoft",
                "id_review_model": 1,
                "last_modify_date": "2021-11-26T22:57:40"
            },
            "id_dossier_revision": 3
        },
        {
            "type": {
                "id": 2,
                "code": "BIL",
                "label": "Bilan"
            },
            "end_date": "2018-12-31",
            "exercise": "N-2",
            "start_date": "2018-01-01",
            "review_model": {
                "label": "Modèle Standard Myunisoft",
                "modified_by": "MyUniSoft",
                "id_review_model": 1,
                "last_modify_date": "2021-11-26T22:57:40"
            },
            "id_dossier_revision": 4
        },
        {
            "type": {
                "id": 2,
                "code": "BIL",
                "label": "Bilan"
            },
            "end_date": "2017-12-31",
            "exercise": "N-3",
            "start_date": "2017-01-01",
            "review_model": {
                "label": "Modèle Standard Myunisoft",
                "modified_by": "MyUniSoft",
                "id_review_model": 1,
                "last_modify_date": "2021-11-26T22:57:40"
            },
            "id_dossier_revision": 5
        },
        {
            "type": {
                "id": 2,
                "code": "BIL",
                "label": "Bilan"
            },
            "end_date": "2016-12-31",
            "exercise": "N-4",
            "start_date": "2016-01-01",
            "review_model": {
                "label": "Modèle Standard Myunisoft",
                "modified_by": "MyUniSoft",
                "id_review_model": 1,
                "last_modify_date": "2021-11-26T22:57:40"
            },
            "id_dossier_revision": 6
        },
        {
            "type": {
                "id": 2,
                "code": "BIL",
                "label": "Bilan"
            },
            "end_date": "2015-12-31",
            "exercise": "N-5",
            "start_date": "2015-01-01",
            "review_model": {
                "label": "Modèle Standard Myunisoft",
                "modified_by": "MyUniSoft",
                "id_review_model": 1,
                "last_modify_date": "2021-11-26T22:57:40"
            },
            "id_dossier_revision": 7
        },
        {
            "type": {
                "id": 2,
                "code": "BIL",
                "label": "Bilan"
            },
            "end_date": "2014-12-31",
            "exercise": "N-6",
            "start_date": "2014-01-01",
            "review_model": {
                "label": "Modèle Standard Myunisoft",
                "modified_by": "MyUniSoft",
                "id_review_model": 1,
                "last_modify_date": "2021-11-26T22:57:40"
            },
            "id_dossier_revision": 8
        },
        {
            "type": {
                "id": 2,
                "code": "BIL",
                "label": "Bilan"
            },
            "end_date": "2013-12-31",
            "exercise": "N-7",
            "start_date": "2013-01-01",
            "review_model": {
                "label": "Modèle Standard Myunisoft",
                "modified_by": "MyUniSoft",
                "id_review_model": 1,
                "last_modify_date": "2021-11-26T22:57:40"
            },
            "id_dossier_revision": 9
        },
        {
            "type": {
                "id": 1,
                "code": "SITU",
                "label": "Situation"
            },
            "end_date": "2020-02-15",
            "exercise": "N",
            "start_date": "2020-01-01",
            "review_model": {
                "label": "Modèle Standard Myunisoft",
                "modified_by": "MyUniSoft",
                "id_review_model": 1,
                "last_modify_date": "2021-11-26T22:57:40"
            },
            "id_dossier_revision": 10
        },
        {
            "type": {
                "id": 1,
                "code": "SITU",
                "label": "Situation"
            },
            "end_date": "2019-04-30",
            "exercise": "N-1",
            "start_date": "2019-01-01",
            "review_model": {
                "label": "Modèle Standard Myunisoft",
                "modified_by": "MyUniSoft",
                "id_review_model": 1,
                "last_modify_date": "2021-11-26T22:57:40"
            },
            "id_dossier_revision": 11
        }
    ]
}
```

Le endpoint **/dadp/dossier_revision_list** retourne un tableau de structure DossierRevision.

```ts
interface DossierRevision {
  id_dossier_revision: number;
  type: {
    id: number;
    label: string;

    /** Max-length: 4. Uppercase. */
    code: string;
  };

  /** Format: YYYY-MM-DD */
  end_date: string;

  /** Format: YYYY-MM-DD */
  start_date: string;

  /** 
  * @example
  * "N-1" | "N0" | "N-1"
  */
  exercise: string;

  review_model: {
    label: string;
    modified_by: string;
    id_review_model: number;

    /** Format: YYYY-MM-DDTHH:MM:SS */
    last_modify_date: string;
  };
}
```