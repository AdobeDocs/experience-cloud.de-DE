---
title: Metadatenmechanismus
description: Erfahren Sie mehr über den Metadatenmechanismus.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRENZTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzer beschränkt"
exl-id: 58ec0999-b28a-4198-8d57-729b074c6a6d
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 96%

---

# Metadatenmechanismus {#metadata-mechanism}

Sie können die Metadaten von Ressourcen mit **resourceType** in einer GET-Anfrage abrufen:

`GET /profileAndServices/resourceType/<resourceName>`

In der Antwort werden die Hauptmetadaten der Ressource zurückgegeben (alle anderen Felder sind beschreibend oder intern):

* Der Knoten **Inhalt** gibt die Felder der Ressource zurück. Für jedes Feld im Knoten **Inhalt** können wir folgende Felder finden:

   * &quot;apiName&quot;: Name des Attributs, das in den APIs verwendet wird.
   * &quot;type&quot;: Dies ist die übergeordnete Typdefinition (Zeichenfolge, Zahl, Link, Sammlung, Auflistung...).
   * &quot;dataPolicy&quot;: Der Wert des Felds muss den angegebenen Regeln entsprechen. Wenn die Regel &quot;dataPolicy&quot; beispielsweise auf &quot;email&quot; gesetzt ist, muss der Wert eine gültige E-Mail-Adresse sein. Während eines PATCH- oder POST-Vorgangs kann &quot;dataPolicy&quot; den Wert überprüfen oder den umzuwandelnden Wert ändern (z. B. smartCase).
   * &quot;category&quot;: Gibt die Kategorie des Felds im Abfrageeditor an.
   * &quot;resType&quot;: Dies ist der technische Typ.

     Wenn &quot;type&quot; mit dem Wert &quot;link&quot; oder &quot;collection&quot; ausgefüllt wird, ist der resTarget-Wert der Name der Ressource, auf die der Link abzielt.
Wenn &quot;type&quot; mit dem Wert &quot;enumeration&quot; ausgefüllt wird, wird ein Feld &quot;values&quot; hinzugefügt und jeder Auflistungswert im Knoten **Werte** detailliert beschrieben.

* Der Knoten **Filter** gibt die URL zum Abrufen der zugehörigen Filter zurück. Weiterführende Informationen zu Filtern finden Sie in [diesem Abschnitt](filtering.md).

<!-- créer une section au même niveau sur les liens -->
<!-- dans l'exemple: birthdate, email +  mettre 2 liens : un de type 1-1 , 1-N
si on prend l'exemple de l'org unit, on aura un bon exemple lien -->
<!-- plus reparler du node Data -->

<br/>

***Beispielanfrage***

Führen Sie eine GET-Anfrage für die Ressource aus.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/resourceType/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Es wird die vollständige Beschreibung der Profil-Ressource zurückgegeben.

```
{
...
"content": {
  "email": {...},
    ...
    },
"data": "/profileAndServices/profile/",
"filters": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/resourceType/<PKEY>"
    },
"help": "Identified profiles",
"href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/metadata",
"label": "Profiles",
"mandatory": false,
"name": "profile",
"pkgStatus": "never",
"readOnly": false,
"schema": "nms:recipient",
"type": "item"
}
```
