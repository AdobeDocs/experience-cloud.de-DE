---
title: Sortieren
description: Erfahren Sie mehr über die Verwendung von Sortiervorgängen.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRENZTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzer beschränkt"
exl-id: 7db25b8d-a6f1-4151-bf37-c47e9991ae48
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 90%

---

# Sortieren

Die Sortierung ist standardmäßig in aufsteigender Reihenfolge verfügbar. Um in absteigender Reihenfolge zu sortieren, hängen Sie **%20desc** an den Wert des Parameters **_order** an.

Um zu erfahren, ob sich ein Feld sortieren lässt, prüfen Sie den Parameter &quot;sortable&quot; in den Metadaten der Ressource. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](metadata-mechanism.md).

<br/>

***Beispielanfragen***

* Beispielhafte GET-Anfrage zum Abrufen von E-Mails in der Datenbank in alphabetischer Reihenfolge.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_order=email \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Antwort auf die Anfrage

  ```
  {
  "content": [
      "adam@email.com",
      "allison.durance@example.com",
      "amy.dakota@mail.com",
      "andrea.johnson@mail.com",
      ...
  ]
  ...
  }
  ```

* Beispielhafte GET-Anfrage zum Abrufen der E-Mails in der Datenbank in absteigender alphabetischer Reihenfolge.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_order=email%20desc \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Antwort auf die Anfrage

  ```
  {
  "content": [
      "tombinder@example.com",
      "tombinder@example.com",
      "timross@example.com",
      "john.smith@example.com",
      ...
  ]
  }
  ```
