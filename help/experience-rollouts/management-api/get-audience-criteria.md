---
title: Abrufen der gewünschten Zielgruppenkriterien
description: Erfahren Sie, wie Sie mithilfe der -Konsole und der GET-Funktions-API die richtige JSON-Struktur für Zielgruppenkriterien für die Verwendung in den Experience Rollouts Management-APIs generieren.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 1%

---


# Abrufen der gewünschten Zielgruppenkriterien {#get-audience-criteria}

Das Feld Zielgruppenkriterien in den Verwaltungs-APIs verwendet ein strukturiertes JSON-Format, das in der manuellen Bearbeitung komplex sein kann. Es wird empfohlen, die gewünschte Zielgruppe mithilfe der -Konsole zu erstellen und dann ihre JSON-Darstellung über die API abzurufen.

## Schritte {#steps}

Gehen Sie wie folgt vor, um die JSON für die gewünschten Zielgruppenkriterien abzurufen:

1. Erstellen Sie in der Konsole „Erlebnis-Rollouts“ ein temporäres Feature Flag mit den Zielgruppenkriterien, die Sie in Ihrem API-Aufruf verwenden möchten.
2. Notieren Sie sich nach dem Speichern die Feature Flag-ID aus der Browser-URL. Die ID wird in der URL nach der Client-ID angezeigt. In `.../feature-flags/1191/22080` ist die Funktions-ID beispielsweise `22080`.
3. Rufen Sie den Endpunkt [Funktion abrufen nach ID](feature-flags-management-api.md#get-feature-by-id) mit dieser Funktions-ID auf.
4. Suchen Sie in der Antwort-JSON das Feld `audience` . Hier finden Sie die genaue Struktur der Zielgruppenkriterien, die Sie benötigen.
5. Kopieren Sie den `audience` Wert und entfernen Sie das `id` Attribut aus jedem Regelobjekt. Verwenden Sie dies in Ihrem Aufruf der Feature API zum Erstellen oder Aktualisieren.

## Beispiel {#example}

Nach dem Aufruf von GET `/m/api/v1/mgmt/feature/22080` enthält die Antwort:

```json
{
  "audience": [
    {
      "id": 10034665,
      "criteria": {
        "and": [
          {
            "operator": "EQ",
            "attr": "LOCALE",
            "val": "EN",
            "ruleId": 1,
            "category": "default"
          }
        ]
      }
    }
  ]
}
```

Um dies in einem Funktionsaufruf „Erstellen“ zu verwenden, entfernen Sie das `id` Feld aus dem Zielgruppenobjekt:

```json
{
  "audience": [
    {
      "criteria": {
        "and": [
          {
            "operator": "EQ",
            "attr": "LOCALE",
            "val": "EN",
            "ruleId": 1,
            "category": "default"
          }
        ]
      }
    }
  ]
}
```

## Siehe auch {#see-also}

* [Feature Flags Management-API](feature-flags-management-api.md)
* [Client-ID für ein Programm abrufen](get-client-id.md)
* [Verwaltungs-Patch-API](management-patch-api.md)
