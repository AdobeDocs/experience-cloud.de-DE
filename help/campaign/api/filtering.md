---
title: Filterung
description: Erfahren Sie, wie Sie Filtervorgänge durchführen können.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
badge: label="EINGESCHRÄNKTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzende beschränkt"
exl-id: cdb050b7-d327-42f7-b534-d32d988c8ffb
TQID: https://experienceleague.adobe.com/jaVg32T-Frb7jHAZNMNa-iZt2QNF7oIOPbZ4DLzPFJY
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 452
ht-degree: 98%

---

# Filterung {#filtering}

## Abrufen von Filtermetadaten

Für jede Ressource stehen Filter zur Verfügung. Um die mit einer Ressource verknüpften Filter zu ermitteln, müssen Sie eine GET-Anfrage für die Metadaten der Ressource durchführen. Die Anfrage gibt die URL zurück, unter der alle Filter für eine bestimmte Ressource definiert sind. Weiterführende Informationen zu Metadaten finden Sie in [diesem Abschnitt](metadata-mechanism.md).

Um die Metadaten eines Filters und die jeweilige Verwendungsweise zu ermitteln, müssen Sie eine GET-Anfrage für die zuvor zurückgegebene URL durchführen.

<br/>

***Beispielanfrage***

Die folgenden beispielhaften Payloads zeigen, wie die &quot;byText&quot;-Filtermetadaten für die &quot;Profil&quot;-Ressource abgerufen werden. Führen Sie zuerst eine GET-Anfrage für die Metadaten der Ressource &quot;Profil&quot; durch.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/resourceType/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Diese gibt die URL zurück, unter der die Filter beschrieben werden.

```
{
"filters": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/resourceType/<PKEY>/filters/"
    }
  }
```

Führen Sie eine GET-Anfrage für die URL aus. Sie erhalten eine Liste der Filter für die Ressource &quot;Profil&quot; mit den jedem Filter zugeordneten Metadaten.

```
{
"birthday": {
        "PKey": "@FL-CbDFXbnHbXcVpeCGWL46VXJLn1LqxLMPagt2vz8sCxQ52lvB15KiUaxXkxJYQw-tZXYrgUWG6K8QcB4gxVY9RKoba5bRFY3294YFshDmorRr8",
        "category": "0150_profile",
        "condition": ...,
        "data": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/birthday?type=$value&precision=$value&operator=$value&day=$value&month=$value&includeStart=$value&endDay=$value&endMonth=$value&includeEnd=$value&relativeValue=$value&nextUnitsValue=$value&previousUnitsValue=$value",
        "formType": "webPage",
        "fragmentName": "",
        "label": "Birthday",
}
```

## Struktur von Filtermetadaten

Jeder Filter weist dieselbe Metadatenstruktur auf:

* Die Felder **@formType** und **@webPage** sind technische Felder.
* Das Feld **Daten** enthält ein Beispiel zur Verwendung des Filters.
* Der Knoten **Metadaten** beschreibt die Filterparameter.
* Der Knoten **Bedingungen** beschreibt, was der Filter tun soll. Die im Metadaten-Knoten beschriebenen Filterparameter dienen zum Erstellen von Filterbedingungen. Wenn **enabledIf** wahr ist, wird für jede Filterbedingung **expr** angewendet.

<br/>

Beispiel für die Metadatenstruktur:

```
"byText": {
        "PKey": "...",
        "category": "99_none",
        "condition": ...,
        "data": "/profileAndServices/profile/byText?text=$value",
        "formType": "none",
        "fragmentName": "",
        "label": "By name or email",
    }
```

## Verwenden von Filtern

Die Filterung wird mit der folgenden Anfrage durchgeführt:

`GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/<resourceName>/by<filterName>?<filterParam>=<filterValue>`

Es ist möglich, mehrere Filter in einer einzigen Anfrage zu kombinieren:

`GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/<resourceName>/<filter1name>/<filter2name>?<filter1param>=<filter1value>&<filter2param>=<filter2value>`

<br/>

***Beispielanfragen***

* Beispielhafte GET-Anfrage zum Abrufen der &quot;Dienst&quot;-Ressourcen mit dem Typ &quot;email&quot;.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel?channel=email \
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
              "created": "2019-09-25 23:20:35.000Z",
              "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/@I_FIiDush4OQPc0mbOVR9USoh36Tt5CsD35lATvQjdWlXrYc0lFkvle2XIwZUbD8GqTVvSp8AfWFUvjkGMe1fPe5nok",
              "label": "Marketing Newsletter",
              "lastModified": "2019-09-25 23:20:35.000Z",
              "limitedDuration": false,
              "messageType": "email",
              "mode": "newsletter",
              ...
          },
          ...
      ],
      ...
  }
  ```

* Beispiel einer GET-Anfrage zum Abrufen der „Profil“-Ressourcen, die „Mustermann“
in den Feldern „E-Mail“ oder „Nachname“ enthalten (der Filter „byText“ sucht sowohl im Feld „E-Mail“ als auch im Feld „Nachname“).

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=Doe \
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
          }
          ...
      ],
      ...
  }
  ```

* Beispielhafte GET-Anfrage zum Abrufen der &quot;Dienst&quot;-Ressourcen mit dem Typ &quot;email&quot; und dem Titel &quot;sport&quot;.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel/byText?channel=email&text=sport \
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
              "created": "2019-09-26 09:36:01.014Z",
              "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
              "label": "sport",
              "lastModified": "2019-09-26 09:36:01.014Z",
              "limitedDuration": false,
              "messageType": "email",
              "mode": "newsletter",
              "name": "SVC13",
              ...
          }
      ],
      ...
  }
  ```

## Benutzerdefinierte Filter

Wenn Sie einen benutzerdefinierten Filter verwenden möchten, müssen Sie ihn in der Benutzeroberfläche von Adobe Campaign Standard erstellen und anpassen. Der benutzerdefinierte Filter verhält sich dann genauso wie native Filter:

`GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/<resourceName>/by<customFilterName>?<customFilterparam>=<customFilterValue>`

Weiterführende Informationen finden Sie in der Campaign Standard-Dokumentation.

* [Filterdefinition konfigurieren](https://helpx.adobe.com/de/campaign/standard/developing/using/configuring-filter-definition.html).
* [Anwendungsbeispiel: Aufrufen einer Ressource mit einem zusammengesetzten Identifizierungsschlüssel](https://experienceleague.adobe.com/docs/campaign-standard/using/developing/adding-or-extending-a-resource/uc-calling-resource-id-key.html?lang=de).

<br/>

***Beispielanfrage***

Beispielhafte GET-Anfrage zum Abrufen der &quot;Profil&quot;-Ressourcen mit Transaktionsbeträgen von 100 $ oder mehr. Beachten Sie, dass der Filter &quot;byAmount&quot; zunächst in der Benutzeroberfläche von Adobe Campaign Standard definiert und mit der benutzerdefinierten Tabelle &quot;Transaction&quot; verknüpft wurde.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/profile/byAmount?amount_parameter=100 \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

<!--
Response to the request.

```

{
    "content": [
        {
            "PKey": "<PKEY>",
            "builtIn": false,
            "created": "2019-09-26 09:36:01.014Z",
            "desc": "",
            "end": "",
            "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>",
            ...
        }
    ],
}

```

-->

<!-- exemple à vérifier de bout en bout-->

<!--
+category = query editor
privacy ?
displayFOrmat ?
pour faire un POST sur une enum, il faut lui passer le @name décrit dans le noeud values, chaque @name a une correspondance en format = au format définit par le resType
-->





<!--
 if link ou collection.* resName +
* resTarget tout ca, ca va ensemble : le système de lien, resTarget va donner la ressource targetée par le lien. type
resType = type technique (long..) resType = link alors unbound='false' ou 'true'
If type = enumeration alors champ "values" rajouté et les valeurs sont dans values
pour faire un POST sur une enum, il faut lui passer le @name décrit dans le noeud values, chaque @name a une correspondance en format = au format définit par le resType
ail faut que la valeur poster soit conforme ,elle doit valider la dataPolicy . La dataPolicy peut soit controler la valeur (email invalide), soit transformé (cas du smartCase par exemple)
type dans les metadata = type de haut-niveau (nombre, text)
-->
