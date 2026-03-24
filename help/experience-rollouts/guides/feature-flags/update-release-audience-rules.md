---
title: Aktualisieren der Regeln für Veröffentlichungszielgruppen
description: Erfahren Sie, wie Sie Zielgruppenkriterien für eine Version in Adobe Experience Rollouts konfigurieren und aktualisieren, einschließlich unterstützter Regeltypen und wie Sie sie kombinieren.
source-git-commit: bb4541dd7a77edadded2edbc9c71905cf70f2e24
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 3%

---


# Aktualisieren der Regeln für Veröffentlichungszielgruppen {#update-release-audience-rules}

## Zugreifen auf die Zielgruppeneinstellungen {#access}

Um zu konfigurieren, wer Ihre Version erhält, navigieren Sie zu den Zielgruppeneinstellungen in der Konsole:

1. Öffnen Sie Ihre Version in der Konsole „Experience Rollouts“.
2. Navigieren Sie zur Registerkarte **Zielgruppe** .
3. Aktivieren Sie den Umschalter neben **Zielgruppenregeln**.
4. Wählen Sie aus, ob **Einschlussregeln** (wer die Version erhalten soll) oder **Ausschlussregeln** (wer nicht) hinzugefügt werden sollen.

## Unterstützte Zielgruppenkriterien {#criteria}

### ID-Typ {#id-type}

Targeting von Benutzern basierend auf ihrem Kontotyp (z. B. persönliche oder Unternehmenskonten).

### Land {#country}

Targeting von Benutzern basierend auf ihrem registrierten Land.

### Benutzer-ID {#user-id}

Targeting bestimmter Benutzer anhand ihrer eindeutigen Benutzerkennung (GUID).

### E-Mail-Adresse {#email}

Targeting von Benutzern anhand ihrer genauen E-Mail-Adresse. Um mehrere E-Mail-Adressen gleichzeitig hinzuzufügen, wählen Sie **in** aus der Dropdown-Liste Operator (anstelle von **is**) aus und klicken Sie dann auf:

* Geben Sie eine kommagetrennte Liste von Adressen in das Textfeld ein oder
* eine `.txt` Datei mit einer Adresse pro Zeile hochladen oder
* Hochladen einer `.csv`-Datei mit der Liste der Adressen

Wenn Ihre Liste sehr groß ist, teilen Sie sie in kleinere Batches auf.

### Email domain {#email-domain}

Targeting aller Benutzer, deren E-Mail-Adresse zu einer bestimmten Domain gehört (z. B. `yourcompany.com`)

### Client-IP {#client-ip}

Targeting von Benutzern basierend auf ihrer Client-IP-Adresse.

### Prozentsatz {#percentage}

Targeting eines zufälligen Prozentsatzes aller Benutzer, einschließlich nicht authentifizierter Benutzer.

### Prozentsatz (nur authentifiziert) {#percentage-auth}

Targeting eines zufälligen Prozentsatzes nur authentifizierter Benutzer. Nicht authentifizierte Benutzer werden ausgeschlossen.

## Kombinieren mehrerer Regeln {#combining-rules}

Sie können mehrere Zielgruppenkriterien mithilfe der UND/ODER-Logik kombinieren.

**Beispiele:**

* Um nur Unternehmenskonten aus einer bestimmten Domain als Ziel festzulegen, kombinieren Sie die Regel **ID-Typ** mit der Regel **E-Mail-Domain** mithilfe von UND.
* Um 10 % der Benutzer aus einem bestimmten Land anzusprechen, kombinieren Sie die Regel **Land** mit der Regel **Prozentsatz**.

Verwenden Sie die Symbole **+/-**, um Bedingungen hinzuzufügen oder zu entfernen. Um eine Bedingung zu duplizieren, klicken Sie auf das Symbol Duplizieren neben einer vorhandenen Regel. Aktivieren Sie für komplexe verschachtelte Logik **verschachtelte Logik** und geben Sie einen gültigen Ausdruck in das Textfeld ein.

## Siehe auch {#see-also}

* [Release anfordern](request-a-release.md)
* [End-to-End-Workflow für die Veröffentlichung](release-workflow-end-to-end.md)
* [Versionsstatus](release-states.md)
