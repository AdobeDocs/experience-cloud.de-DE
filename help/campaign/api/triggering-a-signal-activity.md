---
title: Auslösen einer Signalaktivität
description: Erfahren Sie, wie Sie mit APIs eine Signalaktivität auslösen können.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
badge: label="EINGESCHRÄNKTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzende beschränkt"
exl-id: 9f94e98f-fe04-4369-8946-1380e02cdece
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 97%

---

# Auslösen einer Signalaktivität {#triggering-a-signal-activity}

In einem Adobe Campaign Standard-Workflow kann es eine oder mehrere **externe Signalaktivitäten** geben. Bei diesen Aktivitäten handelt es sich um &quot;Listener&quot;, die auf ihre Auslösung warten.

Mit Campaign Standard-APIs können Sie eine **externe Signalaktivität** auslösen, um einen Workflow aufzurufen. Der API-Aufruf kann Parameter enthalten, die in die Ereignisvariablen des Workflows aufgenommen werden (Name der auszuwählenden Zielgruppe, zu importierender Dateiname, Teil des Nachrichteninhalts usw.). Auf diese Weise lassen sich Ihre automatisch durchgeführten Campaign-Prozesse einfach mit einem externen Datensystem integrieren.

>[!NOTE]
>
>Externe Signalaktivitäten können nicht öfter als alle zehn Minuten ausgelöst werden und der Ziel-Workflow muss bereits ausgeführt werden.

Gehen Sie zur Auslösung eines Workflows wie folgt vor:

1. Führen Sie für den Workflow eine **GET**-Anfrage aus, um die URL des Auslösers für eine externe Signalaktivität abzurufen.

   `GET https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID>`

1. Führen Sie eine **POST**-Anfrage für die zurückgegebene URL aus, um die Signalaktivität auszulösen, wobei der Parameter **&quot;Quelle&quot;** in der Payload enthalten ist. Dieses Attribut ist obligatorisch. Sie können damit die auslösende Anfragequelle angeben.

Wenn Sie den Workflow mit Parametern aufrufen möchten, fügen Sie sie mit dem Attribut **&quot;Parameter&quot;** in die Payload ein. Die Syntax besteht aus dem Namen des Parameters gefolgt von seinem Wert (folgende Typen werden unterstützt: **Zeichenfolge**, **Zahl**, **Boolescher Wert** und **Datum/Uhrzeit**).

```
  -X POST <TRIGGER_URL>
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>' \
  -H 'Content-Type: application/json;charset=utf-8' \
  -H 'Content-Length:79' \
  -i
  -d {
  -d    "source":"<SOURCE>",
  -d    "parameters":{
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>",
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>",
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>",  
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>"
  -d    }
  -d }
```

>[!NOTE]
>
>Stellen Sie beim Hinzufügen eines Parameters zur Payload sicher, dass die Werte **Name** und **Typ** mit den in der externen Signalaktivität deklarierten Daten übereinstimmen. Darüber hinaus darf die Payload-Größe 64 KB nicht überschreiten.

<br/>

***Beispielanfrage***

Führen Sie eine GET-Anfrage für den Workflow durch.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Es werden die Signalaktivität des Workflows und die zugehörige Auslöser-URL zurückgegeben.

```
{
"PKey": "<PKEY>",
"activities": {
  "activity": {
    "signal1": {
      ...
      "trigger": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<PKEY>/activities/activity/<PKEY>/trigger/"
        },
        ...
      }
    }
  }
}
```

Um eine Signalaktivität auszulösen, führen Sie eine POST-Anfrage für die Auslöser-URL mit der &quot;Quelle&quot; aus. Fügen Sie die Attribute für &quot;Parameter&quot; hinzu, wenn Sie den Workflow mit Parametern aufrufen möchten.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<PKEY>/activities/activity/<PKEY>/trigger \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-i
-d '{
-d "source":"API",
-d "parameters":{
-d    "audience":"audience",
-d    "email":"anna.varney@mail.com",
-d    "template":"05",
-d    "contentURL":"http://www.adobe.com",
-d    "test":"true",
-d    "segmentCode":"my segment",
-d    "attribute":"2019-04-03 08:17:19.100Z"}
-d  }'
```

<!-- + réponse -->

Wenn einer der Parameter nicht in der externen Signalaktivität deklariert ist, gibt die POST-Anfrage den folgenden Fehler zurück; dabei wird angegeben, welcher Parameter fehlt.

```
RST-360011 An error has occurred - please contact your administrator.
'contentURL' parameter isn't defined in signal activity.
XTK-170006 Unable to parse expression 'HandleTrigger(@name, $(source), $({parameters}))'.
RST-360000 Error while assessing 'HandleTrigger(@name, $(source), $({parameters}))' expression ('xtk:workflow:execution/activities/signal/trigger' resource)
```
