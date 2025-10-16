---
title: Löschen von Abonnements
description: Erfahren Sie, wie Sie Abonnements mit APIs löschen können
role: Developer
level: Experienced
badge: label="EINGESCHRÄNKTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzende beschränkt"
exl-id: 76e2d102-c877-41a6-af87-2f407201a572
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 96%

---

# Löschen von Abonnements mit APIs {#mdeleting-subscriptions-api}

<!--NOTE TO WRITER: There are two duplicate headings that seem to have the same content. Delete one? Rename if different?-->

## Löschen einer Dienstanmeldung für ein bestimmtes Profil {#deleting-service-subscription}

Dies ist ein dreistufiges Verfahren.

1. Rufen Sie die Anmeldungs-URL für das gewünschte Profil ab.
1. Führen Sie eine GET-Anfrage für die Anmeldungs-URL aus.
1. Führen Sie eine DELETE-Anfrage für die gewünschte Dienst-URL aus.

Ist die Löschanfrage erfolgreich, lautet der Antwortstatus &quot;204 Kein Inhalt&quot;.

<br/>

***Beispielanfrage***

Die folgenden beispielhaften Payloads zeigen, wie Sie ein Profil von einem Service abmelden können. Führen Sie zuerst eine GET-Anfrage aus, um das Profil abzurufen.

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

Es wird eine Liste der Anmeldungen für das ausgewählte Profil mit einer URL für jeden abonnierten Dienst zurückgegeben.

```
...
"service": {
  "PKey": "<PKEY>",
  "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
  "label": "Sport Newsletter",
  "name": "SVC1",
  "title": "Sport Newsletter (SVC1)"
},
...
```

Führen Sie eine DELETE-Anfrage für die gewünschte Dienst-URL aus.

```
-X DELETE https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

<!-- + réponse -->

## Löschen einer Dienstanmeldung für ein bestimmtes Profil

Dies ist ein dreistufiges Verfahren.

1. Rufen Sie den gewünschten Dienst und dessen Anmeldungs-URL ab.
1. Führen Sie eine GET-Anfrage für die Anmeldungs-URL durch, um alle Profilanmeldungen abzurufen.
1. Führen Sie eine DELETE-Anfrage für die gewünschte Profilanmeldungs-URL aus.

Ist die Löschanfrage erfolgreich, lautet der Antwortstatus &quot;204 Kein Inhalt&quot;.

<br/>

***Beispielanfrage***

Rufen Sie den Dienstdatensatz ab.

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
  "mode": "newsletter",
  "name": "SVC3",
  "subScenarioEventType": "subscriptionEvent",
  "subscriptions": {
    "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/"
  },
  "targetResource": "profile",
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

Für den ausgewählten Dienst wird die Liste aller Anmeldungen zurückgegeben, wobei für jede Profilanmeldung eine URL (href) angegeben ist.

```
{
  "PKey": "<PKEY>",
  "created": "2019-03-26 08:58:04.764Z",
  "email": "",
  "expirationDate": "",
  "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/<PKEY>",
  "metadata": "subscriptionRcp",
  "service": ...,
  "serviceName": "SVC3",
  "subscriber": ...,
  ...
}
```

Führen Sie eine DELETE-Anfrage für die gewünschte Profilanmeldungs-URL aus.

```
-X DELETE https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

<!-- + réponse -->
