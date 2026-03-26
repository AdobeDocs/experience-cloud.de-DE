---
title: Verwenden von Unternehmensgruppendaten in Zielgruppenregeln
description: Erfahren Sie, wie Sie in Adobe Experience Rollouts Enterprise-Organisations-IDs als Zielgruppenkriterien verwenden, um bestimmte Kundenorganisationen anzusprechen.
exl-id: 74f97ec7-a809-41bf-a41d-bb57f033040f
source-git-commit: 4a3133f014a9bb9d6ed26eb9d9f763db79ce63b3
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 1%

---

# Verwenden von Unternehmensgruppendaten in Zielgruppenregeln {#enterprise-org-data}

Erlebnis-Rollouts unterstützen Benutzerinnen und Benutzer basierend auf ihrer Organisations-ID (Organisations-ID). Auf diese Weise können Sie Funktionen für bestimmte Kundenorganisationen bereitstellen, bevor Sie sie allgemein verfügbar machen.

## Hinzufügen einer Organisation in einer Zielgruppenregel {#adding-org-rule}

Zielgruppenbestimmung für Unternehmen ist auf der Registerkarte **Zielgruppe** unter **Zielgruppenregeln > Profil > Unternehmen** verfügbar.

Es werden zwei Organisationsarten unterstützt:

### DME-Organisationen {#dme-orgs}

DME-Organisationen werden anhand ihrer Organisations-ID identifiziert. Geben Sie beim Erstellen der Regel nur die Organisations-ID ein - geben Sie keine Authentifizierungsquelle an.

### DMA-Organisationen {#dma-orgs}

DMA-Organisationen verwenden Organisations-IDs im Format `XXXXXXXXXXXXXXXXXXXXXXXX@ADOBEORG`. Bei der Eingabe einer DMA-Organisations-ID:

* Verwenden Sie die vollständige Organisations-ID einschließlich des `@ADOBEORG` Suffix.
* `ADOBEORG` in Großbuchstaben eingeben.

**Beispiel:** `57F22B5D5A5F83AE0A495E6E@ADOBEORG`

## Wichtige Hinweise {#important-notes}

* Das org-basierte Targeting wird anhand der Organisation ausgewertet, die mit der authentifizierten Sitzung des Benutzers verknüpft ist. Stellen Sie sicher, dass der Benutzer beim Testen bei der richtigen Organisation angemeldet ist.
* Wenn eine Organisation, die Sie finden möchten, nicht in den Zielgruppenkriterien angezeigt wird oder wenn Funktionen für eine bestimmte Organisation nicht wie erwartet zurückgegeben werden, wenden Sie sich an den Experience Rollouts-Support.
* Staging- und Produktionsumgebungen können je nach Organisation unterschiedlich sein. Testen Sie Ihre Zielgruppenregeln in der Staging-Phase, bevor Sie sie in die Produktion weiterleiten.

## Siehe auch {#see-also}

* [Zielgruppe in Feature Flags und Feature Groups](audience-in-feature-flags-and-feature-groups.md)
* [Komplexe Zielgruppenregeln](complex-rules.md)
