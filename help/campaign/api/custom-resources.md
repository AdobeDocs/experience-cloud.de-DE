---
title: Benutzerdefinierte Ressourcen
description: Erfahren Sie mehr über die Verwaltung benutzerdefinierter Ressourcen mit APIs.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRENZTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzer beschränkt"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 95%

---

# Benutzerdefinierte Ressourcen {#custom-resources}

Adobe Campaign verfügt über ein vordefiniertes Datenmodell, bei dem Daten über verschiedene Ressourcen definiert werden. Sie können das bereitgestellte Datenmodell anreichern, indem Sie die Ressourcen erweitern, um eigene benutzerdefinierte Felder oder benutzerdefinierte Tabellen hinzuzufügen (z. B. Einkaufs- oder Produkttabellen).

Benutzerdefinierte Ressourcen können über APIs mit dem Endpunkt **/profileAndServicesExt** und dem Namen der benutzerdefinierten Ressource aufgerufen werden.

`https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/<resourceName>/`

>[!NOTE]
>
>Verwenden Sie bei Ressourcen, die nicht vordefiniert sind, immer das Präfix <b>&quot;cus&quot;</b> vor dem Namen der Ressource.

Sie können beliebige Aktionen mit benutzerdefinierten Ressourcen ausführen, solange diese mit der Profiltabelle verknüpft sind. Betrachten wir zum Beispiel die folgende Tabellenstruktur:

![Alternativtext](assets/cusresources.png)

In diesem Fall sind alle Ressourcen aus den Tabellen **Transaktion**, **Transaktionsdetails** und **Produkt** verfügbar, solange sie mit der Tabelle **Profil** verknüpft sind.

<br/>

***Beispielanfrage***

Beispielhafte GET-Anfrage zum Aufrufen der erweiterten Ressource profileAndServicesExt.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/\
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
```

Es wird eine Liste aller verknüpften benutzerdefinierten Ressourcen zurückgegeben. Anschließend können Sie die Ressourcen-URLs verwenden, um beliebige in dieser Dokumentation beschriebenen API-Aufgaben zu erledigen.

```
{
"apiName": "resourceType",
"cusProduct": {
        "content": ...,
        "data": "/profileAndServicesExt/cusProduct/",
        "help": "Product",
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/cusProduct/metadata",
        "name": "cusProduct",
        "type": "collection"
    },
"cusTransaction": {
        "content": ...,
        "data": "/profileAndServicesExt/cusTransaction/",
        "help": "Product",
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/cusTransaction/metadata",
        "name": "cusProduct",
        "type": "collection"
    },
    ...
}
```
