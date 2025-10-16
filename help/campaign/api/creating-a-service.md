---
title: Erstellen eines Service mit APIs
description: Erfahren Sie, wie Sie mit APIs einen Service erstellen können
role: Developer
level: Experienced
badge: label="EINGESCHRÄNKTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzende beschränkt"
exl-id: 91bbce9e-a618-4be2-840b-c7d021271f4e
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 89%

---

# Erstellen eines Service mit APIs{#creating-a-service-api}

Dienste lassen sich mit einer **POST**-Anfrage für die Dienstressource erstellen.

Wenn Sie den Dienst mit bestimmten Attributen erstellen möchten, fügen Sie sie der Payload hinzu. Andernfalls wird der neue Dienst mit Standardattributen eingerichtet.

<br/>

***Beispielanfrage***

Beispielhafte POST-Anfrage zum Erstellen eines Diensts mit bestimmten Attributen.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/ \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
-i
-d {
-d "label": "My newsletter",
-d "messageType": "email",
-d "name": "email_newsletter",
-d "start": "2019-10-06"
-d }
```

Es wird der neu erstellte Dienst mit den aktualisierten Attributen zurückgegeben.

```
{
    "PKey": "<PKEY>",
    "builtIn": false,
    "created": "2019-09-26 12:00:37.005Z",
    "href": "https://mc.adobe.io/<ORGANIZATION>/profileAndServices/service/@NLscZuVHxdVu9rPftvrMWFfR1zRIxQGswSOmGLrK09JTF_iWhB0JCUHEndA_vvy__k9mzOYa5NVkcWDcrK8qGh0wygahX9kRcD44kiWWSEceShn3",
    "label": "My newsletter",
    ...
}
```
