---
title: Steuern eines Workflows
description: Erfahren Sie, wie Sie mit APIs einen Workflow steuern können.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="EINGESCHRÄNKTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierter Benutzer beschränkt"
exl-id: 79eacc31-d5a2-4e13-aa0b-744d7ab7004f
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 90%

---

# Steuern eines Workflows {#controlling-a-workflow}

Sie können einen Workflow direkt über die REST-API steuern, indem Sie eine POST-Anfrage mit der Workflow-Kennung und dem erforderlichen Ausführungsbefehl verwenden:

`POST https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID>/commands`

>[!CAUTION]
>
>Wenn die Workflow-Kennung in Adobe Campaign geändert wird, funktioniert die API-Anfrage nicht mehr.

Zum Steuern eines Workflows stehen vier Ausführungsbefehle zur Verfügung:

* Starten
* Aussetzen
* Fortsetzen
* Anhalten

Weiterführende Informationen zu den Ausführungsbefehlen finden Sie in der [Campaign-Dokumentation](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/executing-a-workflow/about-workflow-execution.html?lang=de).

<br/>

***Beispielanfragen***

* Workflow starten

  ```
  -X POST https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID>/commands \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>' \
  -i
  -d '{"method":"start"}'
  ```

  <!-- + réponse -->

* Workflow anhalten

  ```
  -X POST https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID>/commands \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>' \
  -i
  -d '{"method":"stop"}'
  ```

  <!-- + réponse -->
