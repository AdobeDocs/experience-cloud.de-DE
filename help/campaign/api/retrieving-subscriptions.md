---
title: Abrufen von Abonnements
description: Erfahren Sie, wie Sie mit APIs Abonnements abrufen können
role: Data Engineer
level: Experienced
badge: label="BEGRENZTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzer beschränkt"
exl-id: 6d935074-3196-45c5-97cd-ccb7c80bbba8
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 95%

---

# Abrufen von Abonnements mit APIs {#retrieving-subscriptions-api}

## Abrufen der Profile, die einen Dienst abonniert haben

Dies ist ein zweistufiges Verfahren.

1. Rufen Sie die Anmeldungs-URL für den gewünschten Dienst ab.
1. Führen Sie eine GET-Anfrage für die Anmeldungs-URL aus. Es wird eine Liste der Anmeldungen für den Dienst mit jedem zugehörigen Profil zurückgegeben.

>[!CAUTION]
>
>Die REST-API gibt die Eigenschaft &quot;href&quot; zurück; diese enthält die zu verwendende URL. <b>Nutzen Sie stets die in der Antwort enthaltene URL, um die nachfolgende API-Anfrage zu erstellen</b>.

<br/>

***Beispielanfrage***

Führen Sie eine GET-Anfrage aus, um den Dienst abzurufen.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Es wird die Anmeldungs-URL für den Dienst zurückgegeben.

```
  {
    ...
    "messageType": "email",
    "name": "SVC1",
    "subscriptions": {
                "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/"
    },
    ...
  },
```

Führen Sie eine GET-Anfrage für die Anmeldungs-URL aus.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Eine Liste der Anmeldungen für den Dienst mit jedem zugehörigen Profil wird angezeigt.

```
  {
    ...
    "service": ...,
    "serviceName": "SVC3",
    "subscriber": {
        "PKey": "<PKEY>",
        "email": "",
        "firstName": "John",
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>",
        "lastName": "Doe",
    },
  }
```

## Abrufen der Dienste, die ein Profil abonniert hat

Dies ist ein zweistufiges Verfahren.

1. Rufen Sie die Anmeldungs-URL für ein bestimmtes Profil ab.
1. Führen Sie eine GET-Anfrage für die URL aus. Es wird eine Liste der Anmeldungen für das Profil mit jedem zugehörigen Dienst zurückgegeben.

<br/>

***Beispielanfrage***

Führen Sie eine GET-Anfrage aus, um das Profil abzurufen.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Gibt die Anmeldungs-URL für das Profil zurück.

```
  {
    ...
    "postalAddress":...,
    "preferredLanguage": "none",
    "subscriptions": {
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>/subscriptions/"
    },
    ...
  }
```

Führen Sie eine GET-Anfrage für die Anmeldungs-URL aus.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Es wird eine Liste der Dienste zurückgegeben, die das Profil abonniert hat.

```
  {
    ...
    "PKey": "<PKEY>",
    "created": "2017-03-03 10:54:00.363Z",
    "service": {
      "PKey": "<PKEY>",
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
      "label": "Sport Newsletter",
      "name": "SVC1",
      "title": "Sport Newsletter (SVC1)"
    },
    ...
  }
```
