---
title: Veröffentlichen der Starteigenschaft
description: Erfahren Sie, wie Sie Ihre Launch-Eigenschaft aus der Entwicklungsumgebung in den Staging- und Produktionsumgebungen veröffentlichen. Diese Lektion ist Teil des Tutorials "Implementieren der Experience Cloud in mobilen iOS-Swift-Anwendungen mit Start".
seo-description: null
seo-title: Veröffentlichen der Starteigenschaft
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 7166d2933cc99bcbbd4713fba8f87fb0826b711e

---


# Veröffentlichen der Starteigenschaft

Nachdem Sie einige wichtige Lösungen der Adobe Experience Cloud in Ihrer Entwicklungsumgebung implementiert haben, sollten Sie sich mit dem Veröffentlichungs-Workflow vertraut machen.

## Voraussetzungen 

Ihr Benutzerkonto "Starten"benötigt die Berechtigung "Genehmigen"und "Veröffentlichen", um diese Lektion abzuschließen. Wenn Sie diese Schritte nicht ausführen können, da die Benutzeroberflächenoptionen nicht verfügbar sind, wenden Sie sich an Ihren Experience Cloud-Administrator, um Zugriff zu erhalten. For more information on Launch permissions, see [the documentation](https://docs.adobe.com/content/help/en/launch/using/reference/admin/user-permissions.html).

## Lernziele

Dies können Sie am Ende dieser Lektion:

1. eine Entwicklungsbibliothek in der Staging-Umgebung veröffentlichen
1. Aktualisieren Sie Ihre App, um verschiedene Startumgebungen zu laden
1. eine Staging-Bibliothek in der Produktionsumgebung veröffentlichen

## Veröffentlichung im Staging

Nachdem Sie Ihre Bibliothek in der Entwicklungsumgebung erstellt und validiert haben, ist es an der Zeit, sie in Staging zu veröffentlichen.

1. Go to the **[!UICONTROL Publishing]** page

1. Öffnen Sie das Dropdown-Menü neben Ihrer Bibliothek und wählen Sie " **[!UICONTROL Zur Genehmigung übermitteln"]**

   ![Einreichen zur Genehmigung](images/mobile-publishing-submitForApproval.png)

1. Klicken Sie im Dialogfeld auf die Schaltfläche **[!UICONTROL Senden]** :

   ![Klicken Sie im Modul auf Senden](images/mobile-publishing-submit.png)

1. Ihre Bibliothek wird jetzt in der Spalte " [!UICONTROL Gesendet] "in einem nicht erstellten Status angezeigt:

1. Öffnen Sie das Dropdown-Menü und wählen Sie **[!UICONTROL Erstellen für Staging]**:

   ![Build für das Staging](images/mobile-publishing-buildForStaging.png)
1. Sobald das grüne Symbol angezeigt wird, kann die Bibliothek in der Staging-Umgebung als Vorschau angezeigt werden.

In einem realen Szenario würde nun Ihr QA-Team die Änderungen in der Staging-Bibliothek validieren.

**So validieren Sie die Änderungen in der Staging-Bibliothek**

1. Öffnen Sie in der Eigenschaft "Start"die Seite [!UICONTROL Umgebungen]

1. Klicken Sie in der Zeile [!UICONTROL Staging] auf das Symbol Installieren

   ![Symbol](images/mobile-launch-installIcon.png) installieren, um das Modal zu öffnen
   ![Wechseln Sie zur Seite "Umgebungen"und klicken Sie auf , um das Modal zu öffnen](images/ios/swift/mobile-publishing-getStagingCode.png)

Wenn Sie eine andere Arbeitsfläche für Ihre Staging-App verwenden, müssen Sie sicherstellen, dass dieser Arbeitsbereich über alle Pods und App-Aktualisierungen verfügt, die Sie während des gesamten Lernprogramms vorgenommen haben. Der einzige Unterschied in den Installationsanweisungen aus Ihrer Entwicklungsumgebung besteht derzeit in der Startreferenz in der Core-Konfiguration, wie im Screenshot oben dargestellt. Sie müssen die entsprechende Zeile in der Datei AppDelegate.swift aktualisieren und die App neu erstellen.

Wenn sich Ihr Qualitätssicherungsteam in der Staging-Umgebung abgemeldet hat und die Änderungen überprüft, ist es in der Praxis an der Zeit, Inhalte in der Produktion zu veröffentlichen.

## Veröffentlichung in der Produktion

1. Go to the [!UICONTROL Publishing] page

1. Klicken Sie im Dropdownmenü auf **[!UICONTROL Genehmigung für Veröffentlichung]**:

   ![Zur Veröffentlichung genehmigen](images/mobile-publishing-approveForPublishing.png)

1. Klicken Sie im Dialogfeld auf die Schaltfläche **[!UICONTROL Genehmigen]** :

   ![Klicken Sie auf Genehmigen](images/mobile-publishing-approve.png)

1. Die Bibliothek wird nun in der Spalte " [!UICONTROL Genehmigt] "im nicht erstellten Status (gelber Punkt) angezeigt:

1. Öffnen Sie das Dropdown-Menü und wählen Sie **[!UICONTROL Erstellen und Veröffentlichen in Produktion]**:

   ![Klicken Sie auf Erstellen und in Produktion veröffentlichen](images/mobile-publishing-buildAndPublishToProduction.png)

1. Klicken Sie im Dialogfeld auf **[!UICONTROL Veröffentlichen]** :

   ![Klicken Sie auf Veröffentlichen](images/mobile-publishing-publish.png)

1. Die Bibliothek wird nun in der Spalte [!UICONTROL Veröffentlicht] angezeigt:

   ![Veröffentlicht](images/mobile-publishing-published.png)

Beachten Sie erneut, dass die Umgebung "Produktion"einen Startverweis in der Core-Konfiguration verwendet, wie im folgenden Screenshot hervorgehoben.  Wenn Sie eine andere Arbeitsfläche für Ihre Staging-App verwenden, müssen Sie sicherstellen, dass dieser Arbeitsbereich über alle Pods und App-Aktualisierungen verfügt, die Sie während des gesamten Lernprogramms vorgenommen haben.
![Wechseln Sie zur Seite "Umgebungen"und klicken Sie auf , um das Modal zu öffnen](images/ios/swift/mobile-publishing-getProductionCode.png)

>[!WARNING] Wenn Sie das nächste Mal Änderungen an Ihrer Startkonfiguration vornehmen, müssen Sie eine neue Bibliothek in der Entwicklungsumgebung erstellen. Denken Sie daran, dass das Hinzufügen und Entfernen von Erweiterungen Aktualisierungen der App selbst erfordern. Achten Sie darauf, Ihre Startumgebungen und Ihren App-Code synchron zu halten, um Probleme zu vermeiden.

Das ist's! Sie haben das Tutorial abgeschlossen und Ihre erste mobile Eigenschaft in Launch veröffentlicht!