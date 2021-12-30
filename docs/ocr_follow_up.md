# Récupérer le suivi OCR
Ce guide a pour objectif de vous aider dans la récupération du suivi OCR.

![](./images/ocr_follow_up.png)

Dans l'application MyUnisoft le suivi OCR peut être géré:
- Depuis le menu: `Tenue` > `Flux` > `Suivi OCR`

![](./images/ocr_follow_up_menu.png)

- Depuis la navigation rapide: `Envoi de nouveau document` > `Consulter le suivi OCR`

![](./images/ocr_follow_up_menu2.png)

## API

La route https://api.myunisoft.fr/api/v1/ocr_follow_up permet de récupérer ces informations.

Les paramètres de l'URL sont:

| clé | exemple | description |
| --- | --- | --- |
| start_date | 20210101 | REQUIRED - Format: YYYYMMDD |
| end_date | 20210510 | REQUIRED - Format: YYYYMMDD |
| request_mode | 1 | REQUIRED - Request Mode :, All my folders = 1, All sent by me = 2, OCR only = 3 |
| offset | 10 | OPTIONAL - Default value = 0 |
| limit | 100000 | REQUIRED |
| filter |  | OPTIONAL |
| sort | { "direction": "asc", "column": "society" } | OPTIONAL - direction: "asc" "desc" et column: "society" "fileName" "type" "sendBy" "status" |

L'interface du body:

```ts
interface RequestBody {
    societies_array: number[];
}
```

## EXEMPLE

Ici on récupère le suivi OCR des sociétés: 3, 10 et 5.

Request:

```bash
curl --location --request POST 'https://api.myunisoft.fr/api/v1/ocr_follow_up?start_date=20210101&end_date=20210510&request_mode=1&offset=0&limit=100000&filter&sort' \
--header 'X-Third-Party-Secret: {{X-Third-Party-Secret}}' \
--data-raw '{
  "societies_array": [3, 10, 5]
}'
```

Request body:

```json
{
  "societies_array": [3, 10, 5]
}
```

Response:

```json
{
}
```