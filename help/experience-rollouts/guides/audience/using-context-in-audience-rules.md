---
title: Verwenden des Kontexts in Zielgruppenregeln
description: Erfahren Sie, wie Sie Kontextvariablen in Zielgruppenregeln für Feature Flags und Feature Groups in Adobe Experience Rollouts verwenden.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Verwenden des Kontexts in Zielgruppenregeln {#context-in-audience-rules}

Kontextvariablen sind Werte, die von der Client-Anwendung zur Laufzeit bereitgestellt werden. Sie ermöglichen es Ihnen, Benutzende auf der Grundlage dynamischer Informationen auf Sitzungsebene anzusprechen, wie z. B. die aktive Sprache des Benutzers, der Gerätetyp oder der Anwendungsstatus - Kriterien, die nicht Teil des persistenten Profils des Benutzers sind.

Kontextvariablen sind für Web-, Desktop- und Mobile-Clients relevant.

## Funktionsweise von Kontextvariablen {#how-context-works}

Ihre Anwendung übergibt Kontextvariablen an Erlebnis-Rollouts bei der Auswertung eines Feature Flags. Sie definieren in der Konsole Regeln, die diese Werte überprüfen, und die Plattform verwendet sie zum Zeitpunkt der Auswertung, um festzustellen, ob der Benutzer qualifiziert ist.

Wenn Sie Bedingungen sowohl in den Abschnitten **Profil** als auch **Kontext** der Zielgruppenregeln definieren, werden alle Profilbedingungen mithilfe der Logik UND mit allen Kontextbedingungen kombiniert.

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

>[!NOTE]
>
>Wenn Kontextvariablen in Zielgruppenkriterien enthalten sind, gibt der **Zielgruppenrechner** keine geschätzte Anzahl zurück, da Kontextwerte zur Laufzeit bestimmt werden und nicht im Voraus vorhergesagt werden können.

## Siehe auch {#see-also}

* [Zielgruppe in Feature Flags und Feature Groups](audience-in-feature-flags-and-feature-groups.md)
* [Hinzufügen von Prozentregeln in Zielgruppenkriterien](adding-percentage-rules.md)
* [Zielgruppenregel mit Client-IP-Kontextvariable](clientip-rule.md)
