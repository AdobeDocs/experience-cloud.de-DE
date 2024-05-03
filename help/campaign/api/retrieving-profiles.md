---
title: Abrufen von Profilen
description: Erfahren Sie, wie Sie mit APIs Profile abrufen können
role: Data Engineer
level: Experienced
badge: label="BEGRENZTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzer beschränkt"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 96%

---

# Abrufen von Profilen mit APIs {#retrieving-profiles}

Profile lassen sich mit einer **GET**-Anfrage abrufen.

Anschließend können Sie die Suche mithilfe von Filtern, Reihenfolge und Paginierung verfeinern. Weiterführende Informationen dazu finden Sie im Abschnitt [Zusätzliche Vorgänge](sorting.md).

Darüber hinaus können Sie mit Campaign Standard-APIs nach Profilen suchen, die auf einem der folgenden Felder basieren: E-Mail, Vorname, Nachname oder ein benutzerdefiniertes Feld. Weiterführende Informationen hierzu finden Sie in [diesem Abschnitt](#searching-field).

<br/>

***Beispielanfragen***

* Beispielhafte GET-Anfrage zum Abrufen aller Profile.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
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
              "firstName": "John",
              "lastName":"Doe",
              "birthDate": "1980-10-24",
              ...
          },
          ...
  }
  ```

* Beispielhafte GET-Anfrage zum Abrufen der ersten 10 E-Mail-Werte.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10 \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Antwort auf die Anfrage. Der Knoten &quot;Nächste&quot; gibt die URL zurück, mit der Sie auf die nächsten 10 E-Mail-Werte zugreifen können.

  ```
  {
  "content": [
      "amy.dakota@mail.com",
      "kristen.smith@mail.com",
      "omalley@mail.com",
      "xander.harrys@mail.com",
      "jane.summer@mail.com",
      "gloria.boston@mail.com",
      "edward.snow@mail.com",
      "dorian.simons@mail.com",
      "peter.paolini@mail.com",
      "mingam+test08@adobe.com"
  ],
  "next": {
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10&_
      lineStart=@Qy2MRJCS67PFf8soTf4BzF7BXsq1Gbkp_e5lLj1TbE7HJKqc"
  }
  }
  ```

## Anhand eines Felds nach Profilen suchen {#searching-field}

Mit dem Parameter **[!UICONTROL filterType]** können Sie Profile anhand eines dieser Felder abrufen: E-Mail, Vorname, Nachname oder ein beliebiges benutzerdefiniertes Feld, das den erweiterten Filtern beim Erweitern der Profilressource hinzugefügt wurde.

>[!NOTE]
>
>Bei der Suche wird zwischen Groß- und Kleinschreibung unterschieden, und es wird nur nach Präfixen gesucht. Sie können beispielsweise nicht anhand der letzten Buchstaben des Nachnamens nach einem Profil suchen.

***Beispielanfragen***

* Beispielanfrage zum Filtern von Profilen anhand des Vornamens.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=John&filterType=firstName \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* Beispielanfrage zum Filtern von Profilen anhand des Nachnamens.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=Miller&filterType=lastName \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* Beispielanfrage zum Filtern von Profilen anhand der E-Mail.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=John%40gmail.com&filterType=email \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* Beispielanfrage zum Filtern von Profilen anhand des benutzerdefinierten Felds &quot;Hobby&quot;.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/profile/byText?cusHobby=Dancing&filterType=Hobby \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```
