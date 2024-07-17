---
title: Abrufen von Profilen mit APIs
description: Erfahren Sie mehr über das Erstellen von Profilen mit APIs.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRENZTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzer beschränkt"
exl-id: 69e8d034-6bdd-4b82-bcd7-1ef4be0a59b3
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 91%

---

# Erstellen von Profilen mit APIs {#creating-profiles-api}

Profile lassen sich durch Ausführen einer **POST**-Anfrage für die Profilressource erstellen.

>[!CAUTION]
>
>Wenn Sie mit dem erstellten Profil eine <b>orgUnit</b> verknüpfen möchten, müssen Sie die Profilressource mit diesem Feld erweitern und nach der Veröffentlichung der Erweiterung eine POST-Anfrage für den Endpunkt <b>ProfilAndServicesExt</b> ausführen.
>
>Weiterführende Informationen zur Ressourcenerweiterung des Profils finden Sie in der <a href="https://helpx.adobe.com/de/campaign/standard/administration/using/organizational-units.html#partitioning-profiles">Campaign-Dokumentation</a>.

<br/>

***Beispielanfrage***

Beispielhafte POST-Anfrage zum Erstellen eines Profils mit der E-Mail-Adresse &quot;max.mustermann@mail.com&quot;.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-i
-d '{"email":"john.doe@mail.com"}'
```

Es wird das neu erstellte Profil mit der E-Mail-Adresse &quot;max.mustermann@mail.com&quot; zurückgegeben.

```
{
    "PKey": "<PKEY>",
    "firstName": "John",
    "lastName":"Doe",
    "birthDate": "1980-10-24",
    "email": "john.doe@mail.com",
    ...
}
```
