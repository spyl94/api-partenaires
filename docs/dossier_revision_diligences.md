# Récupérer les diligences d'un cycle/dossier de révision
Ce guide a pour objectif de vous aider dans la récupération des diligences d'un cycle/dossier de révision.

![](./images/dossier_revision_diligences.png)

Dans l'application MyUnisoft les dossiers de révision peuvent gérés depuis le menu : `Révision` > `Révision` > `Dossier de révison`.

![](./images/dossier_revision_menu.png)

## API

La route https://api.myunisoft.fr/api/v1/dadp/work_program permet de récupérer ces informations.

> 👀 Penser à préciser l'en-tête **society-id** si vous utilisez un 🔹 Accès cabinet.

Les paramètres de l'URL sont:

| clé | exemple | description |
| --- | --- | --- |
| category | DA | DA par défaut ??? |
| review_id | 18725 | REQUIRED - [ID du dossier de révision](./dossier_revision.md) |
| start_date | 2020-01-01 | REQUIRED - [Début de la révision/exercice?](./dossier_revision.md) Format: YYYY-MM-DD |
| end_date | 2020-12-31 | REQUIRED - [Fin de la révision/exercice?](./dossier_revision.md) Format: YYYY-MM-DD |
| section_id | 1 | REQUIRED - ??? |
| workSheetOnly | 0 | OPTIONAL - **0** = All, **1** = WorkSheets uniquement |
| cycle_id | 2 | REQUIRED - [ID du cycle](./dossier_revision_cycle.md) |

```bash
$ curl --location --request GET 'https://api.myunisoft.fr/api/v1/dadp/work_program?category=DA&start_date=2020-01-01&end_date=2020-12-31&section_id=1&cycle_id=2&workSheetOnly=0&review_id=18725' \
--header 'X-Third-Party-Secret: nompartenaire-L8vlKfjJ5y7zwFj2J49xo53V' \
--header 'Authorization: Bearer {{API_TOKEN}}'
```

Si tout se passe bien vous devriez recevoir un JSON avec **une structure similaire à l'exemple ci-dessous**

```json
[
    {
        "na": {
            "id": 3499294,
            "value": false
        },
        "ref": "AC-B-01",
        "help": "Vérifier que les rapprochements bancaires permettent de justifier le solde comptable des comptes 512.",
        "name": "Rapprochements bancaires",
        "ref_id": 6,
        "children": {
            "id_ref_da_dp": 6,
            "diligence_list": [
                {
                    "to": "2020-01-31",
                    "from": "2020-01-01",
                    "name": "Janvier 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489536,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                },
                {
                    "to": "2020-02-29",
                    "from": "2020-02-01",
                    "name": "Février 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489537,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                },
                {
                    "to": "2020-03-31",
                    "from": "2020-03-01",
                    "name": "Mars 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489538,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                },
                {
                    "to": "2020-04-30",
                    "from": "2020-04-01",
                    "name": "Avril 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489539,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                },
                {
                    "to": "2020-05-31",
                    "from": "2020-05-01",
                    "name": "Mai 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489540,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                },
                {
                    "to": "2020-06-30",
                    "from": "2020-06-01",
                    "name": "Juin 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489541,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                }
            ]
        },
        "periodicity": "M"
    },
    {
        "na": {
            "id": 3499306,
            "value": false
        },
        "ref": "AC-B-02",
        "help": "Rapprocher le relevé bancaire à la comptabilité\nObtenir les justificatifs des comptes bancaires clôturés sur l’exercice",
        "name": "Relevés bancaires",
        "ref_id": 7,
        "children": {
            "id_ref_da_dp": 7,
            "diligence_list": [
                {
                    "to": "2020-01-31",
                    "from": "2020-01-01",
                    "name": "Janvier 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489548,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                },
                {
                    "to": "2020-02-29",
                    "from": "2020-02-01",
                    "name": "Février 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489549,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                },
                {
                    "to": "2020-03-31",
                    "from": "2020-03-01",
                    "name": "Mars 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489550,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                },
                {
                    "to": "2020-04-30",
                    "from": "2020-04-01",
                    "name": "Avril 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489551,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                },
                {
                    "to": "2020-05-31",
                    "from": "2020-05-01",
                    "name": "Mai 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489552,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                },
                {
                    "to": "2020-06-30",
                    "from": "2020-06-01",
                    "name": "Juin 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489553,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                }
            ]
        },
        "periodicity": "M"
    },
    {
        "na": {
            "id": 3499318,
            "value": false
        },
        "ref": "AC-B-03",
        "help": "Vérifier que l'ensemble des comptes de virement de fonds (58) sont soldés",
        "name": "Vérification que les comptes de virement de fonds sont soldés",
        "ref_id": 8,
        "children": {
            "id_ref_da_dp": 8,
            "diligence_list": [
                {
                    "to": "2020-01-31",
                    "from": "2020-01-01",
                    "name": "Janvier 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489560,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                },
                {
                    "to": "2020-02-29",
                    "from": "2020-02-01",
                    "name": "Février 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489561,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                },
                {
                    "to": "2020-03-31",
                    "from": "2020-03-01",
                    "name": "Mars 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489562,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                },
                {
                    "to": "2020-04-30",
                    "from": "2020-04-01",
                    "name": "Avril 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489563,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                },
                {
                    "to": "2020-05-31",
                    "from": "2020-05-01",
                    "name": "Mai 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489564,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                },
                {
                    "to": "2020-06-30",
                    "from": "2020-06-01",
                    "name": "Juin 2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489565,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                }
            ]
        },
        "periodicity": "M"
    },
    {
        "na": {
            "id": 3499330,
            "value": false
        },
        "ref": "AC-B-04",
        "help": "Contrôler l’antériorité et le dénouement des opérations en rapprochement, justifier les opérations anciennes",
        "name": "Vérification du dénouement des opérations",
        "ref_id": 9,
        "children": {
            "id_ref_da_dp": 9,
            "diligence_list": [
                {
                    "to": "2020-06-30",
                    "from": "2019-07-01",
                    "name": "Du 01/07/2019 Au 30/06/2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489566,
                    "valid_collab": "to_do",
                    "link_work_sheet": "",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": ""
                }
            ]
        },
        "periodicity": "E"
    },
    {
        "na": {
            "id": 3499345,
            "value": false
        },
        "ref": "AC-B-08",
        "help": "Vérifier si des agios ou des frais bancaires sont à provisionner à la date de clôture",
        "name": "CAP - Intérèts courus non échus",
        "ref_id": 13,
        "children": {
            "id_ref_da_dp": 13,
            "diligence_list": [
                {
                    "to": "2020-06-30",
                    "from": "2019-07-01",
                    "name": "Du 01/07/2019 Au 30/06/2020",
                    "pj_list": [],
                    "comments": 0,
                    "valid_rm": "to_validate",
                    "diligence_id": 3489581,
                    "valid_collab": "to_do",
                    "link_work_sheet": "CAPInt",
                    "custom_worksheet": {
                        "original_custom_worksheet": {},
                        "diligence_custom_worksheet": {}
                    },
                    "hasJustification": false,
                    "label_work_sheet": "CAP_INT"
                }
            ]
        },
        "periodicity": "E"
    },
    {
        "na": null,
        "ref": "AC-B-99",
        "help": "Contrôles divers trésorerie",
        "name": "Divers - Trésorerie",
        "ref_id": 14,
        "children": null,
        "periodicity": "PONC"
    }
]
```

Le endpoint **/dadp/work_program** retourne un tableau de structure DiligenceGroup.

```ts
interface DiligenceGroup {
	na: {
		id: number;
		value: boolean;
	};
	ref: string;
	help: string;
	name: string;
	ref_id: number;
	children: {
		id_ref_da_dp: number;
		diligence_list: Diligence;
	};
	periodicity: string;
}

interface Diligence {
  to: string;
  from: string;
  name: string;
  pj_list: [];
  comments: number;
  valid_rm: string;
  diligence_id: number;
  valid_collab: string;
  link_work_sheet: string;
  custom_worksheet: {
    original_custom_worksheet: {};
    diligence_custom_worksheet: {}
  };
  hasJustification: boolean;
  label_work_sheet: string
}
```