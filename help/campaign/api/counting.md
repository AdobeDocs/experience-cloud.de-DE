---
title: Zählung
description: Erfahren Sie, wie Sie Zählvorgänge durchführen können.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
badge: label="EINGESCHRÄNKTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzende beschränkt"
exl-id: d6354249-3b0d-4532-951f-b0fae953f7e1
TQID: https://experienceleague.adobe.com/HgtrtWqn6tdgTQR9lORGusyQswJX2zOWUvPOWXksS8c
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 95
ht-degree: 91%

---

# Zählung

Die Adobe Campaign REST-API kann die Anzahl der Datensätze in einer Anfrage zählen. Verwenden Sie dazu die URL, die im Knoten **Zählung** zurückgegeben wird.

<br/>

***Beispielanfrage***

Um alle Dienste zu zählen, deren **messageType**-Wert &quot;sms&quot; ist, führen Sie eine GET-Anfrage mit dem Filter **byChannel** aus.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel?channel=sms \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Es werden die Dienste zurückgegeben, die dem Filter entsprechen.

```
{
    "content": [
        {
            ...
            "messageType": "sms",
            "mode": "newsletter",
            "name": "SVC6",
            ...
        },
        ...
    ],
    "count": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel/_count?channel=sms&_lineStart=@iKTZ2q3IiSEDqZ5Nw1vdoGnQCqF-8DAUJRaVwR9obqqTxhMy"
    },
    "serverSidePagination": true
}
```

Führen Sie eine GET-Anfrage für die URL des Knotens **Zählung** aus, um die Anzahl der Ergebnisse abzurufen.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel/_count?channel=sms&_lineStart=@iKTZ2q3IiSEDqZ5Nw1vdoGnQCqF-8DAUJRaVwR9obqqTxhMy \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Es wird die Anzahl der Datensätze zurückgegeben.

```
{
    "count": 26
}
```
