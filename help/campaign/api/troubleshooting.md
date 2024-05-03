---
title: Fehlerbehebung bei APIs
description: Erfahren Sie mehr über häufige Probleme bei Campaign Standard-APIs
role: Data Engineer
level: Experienced
badge: label="BEGRENZTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzer beschränkt"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 97%

---

# Fehlerbehebung bei APIs {#troubleshooting}

* **Wenn Sie zur Adobe.io-Konsole wechseln, erhalten Sie den folgenden Fehler: &quot;Die Adobe I/O-Konsole steht nur ausgewählten Mitgliedern von Unternehmenskonten zur Verfügung. Wenden Sie sich an Ihren Systemadministrator, wenn Sie meinen, Zugriff zu benötigen.&quot;**

API-Schlüssel können Sie nur für die Organisationen erstellen, deren Administrator Sie sind. Wenn diese Nachricht angezeigt wird und Sie API-Schlüssel erstellen möchten, fragen Sie einen Administrator der Organisation.

* **Bei einer Anfrage an Adobe.io erhalten Sie {&quot;error_code&quot;:&quot;403023&quot;,&quot;message&quot;:&quot;Profil ist ungültig&quot;}**

Das heißt, dass es ein Problem mit der IMS-Bereitstellung Ihres Campaign-Produkts gibt; sie muss vom IMS-Team repariert werden.

Um mehr zu erfahren, können Sie mit Ihrem Token die IMS-API aufrufen und sich Ihr IMS-Profil ansehen: Sie müssen über einen prodCtx-Wert verfügen, bei dem die Organisationskennung mit der übereinstimmt, die Sie in die URL eingegeben haben, damit Adobe.io Ihre Anfrage weiterleiten kann.
Wenn die IMS-Bereitstellung fehlt, muss dies behoben werden.

```
-X GET https://mc.adobe.io/{ORGANIZATION}/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Folgender Fehler wird zurückgegeben.

```
{"error_code":"403023","message":"Profile is not valid"}
```

Überprüfen Sie Ihr IMS-Profil mit dieser Anfrage.

```
-X GET https://ims-na1.adobelogin.com/ims/profile/v1 \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

In der Antwort muss der Wert ORGANISATION_ID mit dem in Ihrer ersten GET-Anfrage übereinstimmen.

```
{
  "countryCode": "FR",
  "mrktPermEmail": null,
  "projectedProductContext": [
    {
    "prodCtx": {
      "statusCode": "ACTIVE",
      "ident": "ZQ9FRQK7BF09YXAESFY9DDQP1G",
      "modDts": 1448307260000,
      "organization_id": "actest",
      "owningEntity": "6096892F54B5819E0A4C98A2@AdobeOrg",
      "serviceCode": "dma_tartan",
      "label": "Adobe Marketing Cloud",
      "serviceLevel": "standard",
      "createDts": 1421181343000,
      "deal_id": " "
      }
    }
  ]
}
```

* **Wenn Sie eine Anfrage an Adobe.io richten, erhalten Sie {&quot;code&quot;:500, &quot;message&quot;:&quot;Oh. Da ist etwas schiefgelaufen. Überprüfen Sie Ihren URI und versuchen Sie es erneut.&quot;}**

Adobe.io deklariert Ihren ungültigen URI: Der von Ihnen angefragte URI ist höchstwahrscheinlich ungültig. Wenn Sie in Adobe.io den Campaign-Dienst wählen, erhalten Sie eine Auswahl mit einer Liste möglicher Organisationskennungen. Sie müssen dafür sorgen, dass die von Ihnen gewählte Option mit der Eingabe in Ihrer URL übereinstimmt.

* **Bei einer Anfrage an Adobe.io erhalten Sie {&quot;error_code&quot;:&quot;401013&quot;,&quot;message&quot;:&quot;Oauth-Token ist ungültig&quot;}**

Entweder ist Ihr Token ungültig (unzulässiger IMS-Aufruf zum Generieren eines Tokens) oder abgelaufen.

* **Ich kann mein Profil nach der Erstellung nicht sehen**

Je nach Instanzkonfiguration muss das erstellte Profil einer **orgUnit** zugeordnet werden. Informationen zum Hinzufügen dieses Felds zu Ihrer Erstellung finden Sie in [diesem Abschnitt](creating-profiles-api.md).

<!-- * (error duplicate key : quand tu crées un profile qui existe déjà , il faut faire un patch pour updater le profile plutôt qu'un POST)

With Curl
List all profiles

Create a profile

Update the mobilePhone attribute of a profile

API Calls on Service

GET the list of services

-->

<!--

How to find and use a filter?
Error codes:

* PAtch sur Age = message d'erreur :
500
Cannot update the 'age' property that is read-only
'age' property is not valid for the 'profile' resource.
-->

<!--
How to filter a list of subscribed profiles with available profile filters ? by date (by les filtres dispo sur la ressource) ?

Pattern classique :

recupérer la liste des subscriptions filtrées d'un profile
1) get sur profile
2) recup PKey
3) get sur PKey
4) get sur href des subscriptions

Comment savoir quel filtre appliquer ?

1) get sur metadata de profile
2) retourne description de la collection subscription
3) get sur la valeur du champ resTarget
4) get sur le href dans filters
5) retourne les filtres applicables sur l'url des data.

-->
