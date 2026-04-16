---
title: Komplexe Zielgruppenregeln
description: Erfahren Sie, wie Sie mit Regelsätzen für große oder komplexe Zielgruppen in Flags arbeiten, einschließlich der Begrenzung von Massenwerten und wie Sie Regeln über mehrere Bedingungen hinweg aufteilen.
hide: true
exl-id: 37e037b6-45eb-4261-b580-30d94d8e55da
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Komplexe Zielgruppenregeln {#complex-rules}

## Grenzwerte für Massenwerte {#bulk-value-limits}

Beim Hinzufügen einer großen Anzahl von Werten zu einer einzelnen Zielgruppenregel - z. B. einer langen Liste von E-Mail-Adressen - kann ein Fehler auftreten, der darauf hinweist, dass die Regel die maximal zulässige Größe überschritten hat.

Jede Zielgruppenregel verfügt über eine Größenbeschränkung pro Attribut. Bei E-Mail-Adressen hängt das Limit von der Gesamtzeichenlänge der Einträge und nicht von einer festen Anzahl ab. Als allgemeine Richtlinie sollten Sie ungefähr **100-115 E-Mail-Adressen pro Regel**.

Wenn Sie mehr Einträge als auf diese Beschränkung beschränkt ansprechen müssen, teilen Sie die Liste in kleinere Abschnitte auf und wenden Sie sie mithilfe verschachtelter Logik als separate ODER-verbundene Bedingungen an.

## Verwenden verschachtelter Logik für komplexe Regeln {#nested-logic}

Verschachtelte Logik ermöglicht die Kombination mehrerer Zielgruppenbedingungen mit präziser UND/ODER-Steuerung. So aktivieren Sie es:

1. Fügen Sie die gewünschten Zielgruppenbedingungen hinzu.
2. Aktivieren Sie **Verschachtelte Logik** im Abschnitt Zielgruppenregeln .
3. Jeder Bedingung wird eine Nummer zugewiesen. Geben Sie einen logischen Ausdruck ein, der auf diese Zahlen verweist. Beispiel:
   * `1 and (2 or 3)`
   * `(1 and 2) or 3`
   * `(1 and 2) or (3 and 4)`

Dies ist derselbe Mechanismus, der für Prozentregeln in Kombination mit anderen Kriterien verwendet wird. Unter [Hinzufügen von Prozentregeln in Zielgruppenkriterien](adding-percentage-rules.md) finden Sie funktionierende Beispiele.

## Siehe auch {#see-also}

* [Zielgruppe in Feature Flags und Feature Groups](audience-in-feature-flags-and-feature-groups.md)
* [Hinzufügen von Prozentregeln in Zielgruppenkriterien](adding-percentage-rules.md)

<!-- -->
