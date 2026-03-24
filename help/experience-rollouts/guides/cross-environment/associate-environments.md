---
title: Zuordnen von Umgebungen zu einer Anwendung
description: Erfahren Sie, wie Sie Ihre Anwendungsinstanzen in Adobe Experience Rollouts umgebungsübergreifend verknüpfen, damit Sie Feature Flags von der Entwicklung bis zur Produktion konsistent verwalten können.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 1%

---


# Zuordnen von Umgebungen zu einer Anwendung {#associate-environments}

Die Verknüpfung Ihrer Anwendungsinstanzen über Umgebungen hinweg ermöglicht eine umgebungsübergreifende Sichtbarkeit und Import-Workflows. Sie müssen über die Rolle **Admin** verfügen, um dies zu konfigurieren. Siehe [Benutzerrollen](../teams/user-roles.md), wenn Sie Ihre Rolle überprüfen müssen.

Hintergrundinformationen, warum dies nützlich ist, finden Sie [Cross-Environment Concept](cross-environment-concept.md).

## Schritt 1: Anwendungseinstellungen öffnen {#step-1}

1. Melden Sie sich bei der Konsole „Experience Rollouts“ an.
2. Navigieren Sie zu **Admin > Anwendungen**.
3. Wählen Sie **Neue Anwendung** aus, um eine neue Anwendung zu integrieren, oder wählen Sie eine vorhandene Anwendung aus, um sie zu bearbeiten.

## Schritt 2: Konfigurieren des Abschnitts „Zugeordnete Umgebungen“ {#step-2}

Scrollen Sie im Anwendungsformular zum Abschnitt **Zugeordnete Umgebungen** . Jede Zeile in diesem Abschnitt definiert eine der Bereitstellungsumgebungen Ihrer Anwendung. Konfigurieren Sie für jede Umgebung die folgenden Felder:

| Feld | Beschreibung |
|---|---|
| **Umgebung** | Wählen Sie eine Standardumgebungskennung aus der Liste aus: QA1, QA2, STG1, STG2, PROD1 oder PROD2. Dadurch wird bei Erlebnis-Rollouts festgelegt, ob es sich um eine Produktionsumgebung oder eine produktionsfremde Umgebung handelt. Außerdem wird die in der Konsole verwendete Farbcodierung bestimmt. |
| **Umgebungsbezeichnung** | Ein benutzerdefinierter Name für diese Umgebung, wie Ihr Team darauf verweist - z. B. `Dev`, `Staging` oder `Production`. Dies ist eine Freiform und muss nicht mit der Standardkennung übereinstimmen. |
| **Experience Rollouts-Umgebung** | Die Plattform-Umgebung (Staging- oder Produktionsumgebung), in der diese Anwendungsinstanz gehostet wird. Je nachdem, in welcher Konsole Sie sich derzeit befinden, vorausgefüllt. |
| **Anwendungs-ID** | Die Client-ID der Anwendungsinstanz in dieser Umgebung. Wird automatisch ausgefüllt, wenn Sie ein Programm aus der Dropdown-Liste auswählen. |

## Schritt 3: Verknüpfen von Anwendungsinstanzen über Umgebungen hinweg {#step-3}

Um Instanzen umgebungsübergreifend zu verknüpfen, führen Sie für jede zusätzliche Umgebung die folgenden Schritte aus:

1. Erstellen Sie die Anwendungsinstanz in ihrer Zielumgebung (erstellen Sie z. B. die QA-App in der Staging-Konsole).
2. Kehren Sie zur Anwendung zurück, die Sie konfigurieren, und fügen Sie eine neue Zeile in **Zugeordnete Umgebungen** hinzu.
3. Wählen Sie aus **Dropdown-Liste** Anwendungs-ID“ die soeben erstellte Anwendungsinstanz aus. Die Umgebungs-Tags und -Kennzeichnungen werden automatisch ausgefüllt.
4. Wählen Sie **Aktualisieren** aus, um zu speichern.

Wiederholen Sie diesen Vorgang für jede Umgebung, die Sie verknüpfen möchten - z. B. verknüpfen Sie QA-, Staging- und Produktionsinstanzen derselben Anwendung.

## Wichtige Hinweise {#important-notes}

* QA- und Staging-Umgebungen können entweder in der Staging- oder der Produktionsplattform von Experience Rollouts gehostet werden.
* Produktionsumgebungen (PROD1, PROD2) können nur in der Produktionsumgebung von Experience Rollouts gehostet werden.
* Sie können nur von einer höheren Umgebung aus eine Verknüpfung zu einer niedrigeren Umgebung herstellen. Beispielsweise können Sie in der Produktionsumgebung eine Verknüpfung zu einer Staging- oder QA-Instanz herstellen, aber das Gegenteil ist schreibgeschützt.

## Siehe auch {#see-also}

* [Umweltübergreifendes Konzept](cross-environment-concept.md)
* [Anzeigen von Funktions-Flags in Umgebungen](view-feature-flags-across-environments.md)
* [Feature Flags importieren](import-feature-flags.md)
