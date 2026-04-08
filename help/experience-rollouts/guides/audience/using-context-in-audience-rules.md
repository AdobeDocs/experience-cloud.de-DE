---
title: Verwenden des Kontexts in Zielgruppenregeln
description: Erfahren Sie, wie Sie Kontextvariablen in Zielgruppenregeln für Feature Flags und Feature Groups in Adobe Experience Rollouts verwenden.
exl-id: 0367f475-9209-4d53-86b4-a739a73a23a7
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Verwenden des Kontexts in Zielgruppenregeln {#context-in-audience-rules}

Kontextvariablen sind Werte, die von der Client-Anwendung zur Laufzeit bereitgestellt werden. Sie ermöglichen es Ihnen, Benutzende auf der Grundlage dynamischer Informationen auf Sitzungsebene anzusprechen, wie z. B. die aktive Sprache des Benutzers, der Gerätetyp oder der Anwendungsstatus.

Kontextvariablen sind für Web- und Mobile-Clients relevant.

## Funktionsweise von Kontextvariablen {#how-context-works}

Ihre Anwendung übergibt Kontextvariablen an Erlebnis-Rollouts bei der Auswertung eines Feature Flags. Sie definieren in der Konsole Regeln, die diese Werte überprüfen, und die Plattform verwendet sie zum Zeitpunkt der Auswertung, um festzustellen, ob der Benutzer qualifiziert ist.

## Kontextvariablentypen {#variable-types}

### Vordefinierter (Listen-)Typ {#predefined-type}

Eine Kontextvariable mit einem festen Satz zulässiger Werte, z. B. eine Liste von Sprachen oder Ländern.

Verfügbare Operatoren: **Ist**, **Ist nicht gleich**, **Vorhanden**, **In**

### Ganzzahliger Typ {#integer-type}

Eine Kontextvariable, die einen numerischen Wert enthält.

Verfügbare Operatoren: **größer als**, **größer oder gleich**, **Ist**, **kleiner als**, **kleiner oder gleich**

### Typ der Zeichenfolge {#string-type}

Eine Kontextvariable, die einen Freiformtextwert enthält.

Verfügbare Operatoren: **Ist**, **Ist nicht gleich**

## Kontextvariable hinzufügen {#adding-context-variable}

So fügen Sie einer Zielgruppenregel eine Kontextvariable hinzu:

1. Öffnen Sie das Feature Flag oder die Feature Group in der Konsole.
2. Navigieren Sie zur Registerkarte **Zielgruppe** .
3. Fügen **unter &quot;**&quot; eine neue Bedingung hinzu.
4. Wählen Sie die Kontextvariable, den Operator und den Wert.

Wenn die benötigte Kontextvariable nicht in der Liste angezeigt wird, können Sie im Abschnitt zur Verwaltung von Kontextvariablen der Konsole auf Self-Service-Weise eine neue Variable erstellen.

## Siehe auch {#see-also}

* [Zielgruppe in Feature Flags und Feature Groups](audience-in-feature-flags-and-feature-groups.md)
* [Hinzufügen von Prozentregeln in Zielgruppenkriterien](adding-percentage-rules.md)
