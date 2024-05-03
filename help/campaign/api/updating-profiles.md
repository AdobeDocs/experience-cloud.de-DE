---
title: Aktualisieren von Profilen
description: Erfahren Sie, wie Sie mit APIs Profile aktualisieren können
role: Data Engineer
level: Experienced
badge: label="BEGRENZTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzer beschränkt"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 91%

---

# Aktualisieren von Profilen mit APIs{#updating-profiles-api}

Das Aktualisieren von Profilen erfolgt über eine **PATCH**-Anfrage.

`https://mc.adobe.io/<ORGANIZATION>/campaign/<apiName>/<resourceName>/<PKEY>`

1. Der erste Schritt besteht aus dem **Abrufen des Profils**.

1. Im zweiten Schritt führen wir eine **PATCH-Anfrage** für das Profil mit den ausgefüllten Informationen in der Payload aus.

1. Um zu überprüfen, ob die PATCH-Anfrage das Profil aktualisiert hat, können wir eine letzte GET-Anfrage ausführen.

<br/>

***Beispielanfrage***

Beispielhafte GET-Anfrage zum Abrufen eines Profils.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>\
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Antwort auf die Anfrage.

```
{
    "content": [
        {
            "PKey": "<PKEY>",
            "firstName": "Amy",
            "lastName":"Dakota",
            "birthDate": "1980-10-24",
            ...
        }
    ]
}
```

PATCH-Anfrage zum Aktualisieren des Attributs &quot;phone&quot;.

```
-X PATCH https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-d '{"phone":"3301020304"}'
```

Es werden der PKEY und die URL zum Abrufen des aktualisierten Profils zurückgegeben.

```
{
    "PKey": "<PKEY>",
    "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/@2v1dr3ZKJveMDhAdh0MPnh9hNQQ93qb7AW6BNVVKknjwXvTZRBAgUqz1SNcB4ZndgjqOofx3BwBZYBftlmObISoM3rs"
}
```
