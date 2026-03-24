---
title: Hinzufügen von Prozentregeln in Zielgruppenkriterien
description: Erfahren Sie, wie Sie in Adobe Experience Rollouts prozentualbasierte Regeln innerhalb von Zielgruppenkriterien hinzufügen, um verschiedene Rollout-Prozentsätze für verschiedene Zielgruppensegmente auszuwählen.
source-git-commit: ae420329b94b24fcd173734b414aecf1c5fc16ca
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# Hinzufügen von Prozentregeln in Zielgruppenkriterien {#adding-percentage-rules}

## Verwendung von Prozentregeln auf der Registerkarte Zielgruppe {#when-to-use}

Das Feld **Rollout in Prozent** auf der Registerkarte Grundlegende Details wendet einen einzelnen Prozentsatz auf Ihre gesamte Zielgruppe an. Ein Rollout von 50 % bedeutet beispielsweise, dass 50 % aller Benutzer, die Ihren Zielgruppenkriterien entsprechen, die Funktion erhalten.

Einige Rollout-Szenarien erfordern jedoch unterschiedliche Prozentsätze für verschiedene Gruppen, zum Beispiel:

* 100 % der Benutzer in Großbritannien und 50 % der Benutzer in den USA
* Alle Benutzer einer importierten E-Mail-Liste plus 50 % der Benutzer aus einem bestimmten Land

Verwenden Sie in diesen Fällen die **Prozentsatz**-Regel im Profilabschnitt der Registerkarte **Zielgruppe** in Kombination mit verschachtelter Logik.

>[!TIP]
>
>Wenn Sie einen einzelnen Prozentsatz auf Ihre gesamte Zielgruppe anwenden möchten - z. B. 10 % der Benutzenden in (USA und Großbritannien) -, verwenden Sie stattdessen den **Rollout** Prozentsatz“ auf der Registerkarte Grundlegende Details .

## Hinzufügen einer Prozentregel {#how-to-add}

Die **Prozentsatz**-Option ist in der Regel im Abschnitt Profil der Registerkarte Zielgruppe verfügbar.

1. Navigieren Sie zur **Zielgruppe** Ihrer Feature Flag oder Feature Group.
2. Fügen **unter &quot;**&quot; eine **Prozentsatz**-Regel hinzu und legen Sie den gewünschten Wert fest.
3. Fügen Sie alle weiteren erforderlichen Zielgruppenbedingungen hinzu (z. B. eine Länderregel).

## Kombinieren von Prozentregeln mit verschachtelter Logik {#nested-logic}

Um unterschiedliche Prozentsätze auf verschiedene Segmente anzuwenden, verwenden Sie **verschachtelte Logik**, um die Bedingungen zu kombinieren:

1. Aktivieren Sie **Verschachtelte Logik** im Abschnitt Zielgruppenregeln .
2. Jeder Bedingung wird automatisch eine Nummer zugewiesen.
3. Geben Sie einen logischen Ausdruck ein, der auf diese Zahlen verweist.

Verwenden Sie einen der folgenden Ausdrücke, um die Beziehung zwischen Ihren Bedingungen zu beschreiben:

* `1 and (2 or 3)` — Bedingung 1 UND (Bedingung 2 ODER Bedingung 3)
* `(1 and 2) or 3` — (Bedingung 1 UND Bedingung 2) ODER Bedingung 3
* `(1 and 2) or (3 and 4)` — zwei unabhängige Gruppen

## Beispiele {#examples}

**Beispiel 1: Alle Benutzer aus einer importierten Liste und 10 % der Benutzer aus einem bestimmten Land**

Fügen Sie zwei Regeln hinzu: eine für die importierte Benutzerliste und eine Prozentregel (10 %) in Kombination mit einer Länderregel. Verwenden Sie eine verschachtelte Logik: `1 or (2 and 3)`.

**Beispiel 2: 10 % der Benutzer in den USA und 20 % der Benutzer in Großbritannien**

Fügen Sie vier Regeln hinzu: Land = USA, Prozentsatz = 10 %, Land = UK, Prozentsatz = 20 %. Verwenden Sie eine verschachtelte Logik: `(1 and 2) or (3 and 4)`.

## Siehe auch {#see-also}

* [Zielgruppe in Feature Flags und Feature Groups](audience-in-feature-flags-and-feature-groups.md)
* [Komplexe Zielgruppenregeln](complex-rules.md)
* [Festlegen einer Funktion für das schrittweise Rollout](../feature-flags/set-feature-gradual-rollout.md)
