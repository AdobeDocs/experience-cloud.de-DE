---
title: Zielgruppe in Feature Flags und Feature Groups
description: Erfahren Sie, wie Sie Zielgruppenkriterien für Feature Flags und Funktionsgruppen in Adobe Experience Rollouts mithilfe von Profilattributen, Segmenten und dem Zielgruppenrechner definieren.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Zielgruppe in Feature Flags und Feature Groups {#audience-overview}

Erlebnis-Rollouts bieten eine umfassende Zielgruppen-Zielgruppenbestimmung für Feature Flags und Feature Groups. Sie können Profilattribute, Kontextvariablen und Zielgruppensegmente kombinieren, um genau zu steuern, welche Benutzer eine Funktion erhalten.

## Profilregeln {#profile-rules}

Mit Profilregeln können Sie Benutzende anhand von Attributen wie Land, E-Mail-Domain, Kontotyp, Benutzer-ID und mehr ansprechen. Sie können mehrere Attribute mithilfe von AND/OR-Operatoren kombinieren und eine verschachtelte Logik für komplexe Zielgruppenbestimmungsszenarien erstellen.

Zum Hinzufügen von Profilregeln wechseln Sie zur Registerkarte **Zielgruppe** eines Feature Flags oder einer Feature Group und fügen Sie Bedingungen unter **Profil** hinzu.

Sie können einen Satz von Zielgruppenregeln als wiederverwendbare **Zielgruppe** speichern, die über mehrere Flags und Gruppen hinweg verwendet werden können.

Informationen zu kontextbasiertem Targeting (z. B. Targeting nach der aktiven Sprache oder dem Client-Typ des Benutzers) finden Sie unter [Verwenden des Kontexts in Zielgruppenregeln](using-context-in-audience-rules.md).

## Segmente {#segments}

Funktions-Flags und -Funktionsgruppen unterstützen Zielgruppensegmente. Mit Segmenten können Sie:

* Verwenden einer einzelnen vordefinierten Zielgruppendefinition für mehrere Feature Flags und Gruppen
* **ereignisbasierte Kriterien“ in** Zielgruppen-Targeting einschließen - etwas, das mit Profilregeln allein nicht möglich ist

Um ein Segment zu verwenden, wechseln Sie zur Registerkarte **Zielgruppe** und wählen Sie ein oder mehrere Segmente aus der Liste aus. Sie können mehrere Segmente mithilfe von AND/OR-Operatoren kombinieren und parallel dazu zusätzliche Profil- oder Kontextfilter hinzufügen.

>[!NOTE]
>
>Zum Erstellen von Zielgruppensegmenten benötigen Sie **Rolle** Test-Manager“ oder höher.

## Audience-Rechner {#audience-calculator}

Nachdem Sie die Kriterien für Ihre Zielgruppe definiert haben, wählen **in der** Leiste die Option „Berechnen“ aus, um eine geschätzte Anzahl an qualifizierten Benutzern zu erhalten. Auf diese Weise können Sie die Reichweite Ihrer Zielgruppenbestimmung vor der Aktivierung der Funktion überprüfen.

>[!NOTE]
>
>Der Zielgruppenrechner gibt keinen Wert zurück, wenn Kontextvariablen in die Kriterien einbezogen werden, da Kontextwerte zur Laufzeit bestimmt werden und nicht im Voraus vorhergesagt werden können.

## Siehe auch {#see-also}

* [Verwenden des Kontexts in Zielgruppenregeln](using-context-in-audience-rules.md)
* [Hinzufügen von Prozentregeln in Zielgruppenkriterien](adding-percentage-rules.md)
* [Komplexe Zielgruppenregeln](complex-rules.md)
* [Erstellen des ersten Feature Flags](../feature-flags/create-your-first-feature-flag.md)
