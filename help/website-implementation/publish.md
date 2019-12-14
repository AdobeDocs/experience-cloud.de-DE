---
title: Veröffentlichen der Starteigenschaft
description: Erfahren Sie, wie Sie Ihre Launch-Eigenschaft aus der Entwicklungsumgebung in den Staging- und Produktionsumgebungen veröffentlichen. Diese Lektion ist Teil des Tutorials zum Implementieren der Experience Cloud in Websites mit Start.
seo-description: null
seo-title: Veröffentlichen der Starteigenschaft
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: aacd691c176da6ae5b247a19051de57289c128c5

---


# Veröffentlichen der Starteigenschaft

Nachdem Sie einige wichtige Lösungen der Adobe Experience Cloud in Ihrer Entwicklungsumgebung implementiert haben, sollten Sie sich mit dem Veröffentlichungs-Workflow vertraut machen.

## Lernziele

Dies können Sie am Ende dieser Lektion:

1. eine Entwicklungsbibliothek in der Staging-Umgebung veröffentlichen
1. Ordnen Sie Ihrer Produktions-Website mithilfe des Debuggers eine Staging-Bibliothek zu
1. eine Staging-Bibliothek in der Produktionsumgebung veröffentlichen

## Veröffentlichung im Staging

Nachdem Sie Ihre Bibliothek in der Entwicklungsumgebung erstellt und validiert haben, ist es an der Zeit, sie in Staging zu veröffentlichen.

1. Go to the **[!UICONTROL Publishing]** page

1. Öffnen Sie das Dropdown-Menü neben Ihrer Bibliothek und wählen Sie " **[!UICONTROL Zur Genehmigung übermitteln"]**

   ![Einreichen zur Genehmigung](images/publishing-submitForApproval.png)

1. Klicken Sie im Dialogfeld auf die Schaltfläche **[!UICONTROL Senden]** :

   ![Klicken Sie im Modul auf Senden](images/publishing-submit.png)

1. Ihre Bibliothek wird jetzt in der Spalte " [!UICONTROL Gesendet] "in einem nicht erstellten Status angezeigt:

1. Öffnen Sie das Dropdown-Menü und wählen Sie **[!UICONTROL Erstellen für Staging]**:

   ![Build für das Staging](images/publishing-buildForStaging.png)

1. Sobald das grüne Symbol angezeigt wird, kann die Bibliothek in der Staging-Umgebung als Vorschau angezeigt werden.

In einem realen Szenario würde nun Ihr QA-Team die Änderungen in der Staging-Bibliothek validieren. Sie können dies mit dem Debugger tun.

**So validieren Sie die Änderungen in der Staging-Bibliothek**

1. Öffnen Sie in der Eigenschaft "Start"die Seite [!UICONTROL Umgebungen]

1. Klicken Sie in der Zeile [!UICONTROL Staging] auf das Symbol ![](images/launch-installIcon.png) Installation, um das Modal zu öffnen.

   ![Wechseln Sie zur Seite "Umgebungen"und klicken Sie auf , um das Modal zu öffnen](images/publishing-getStagingCode.png)

1. Klicken Sie auf das Symbol " ![Kopieren", um den Einbettungscode in die Zwischenablage zu kopieren](images/launch-copyIcon.png) .

1. Click **[!UICONTROL Close]** to close the modal

   ![Installationssymbol](images/publishing-copyStagingCode.png)

1. Open the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html) in your Chrome browser

1. Öffnen Sie die [Experience Cloud Debugger-Erweiterung](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) , indem Sie auf das Symbol ![Debugger](images/icon-debugger.png) klicken

   ![Klicken Sie auf das Symbol Debugger](images/switchEnvironments-openDebugger.png)

1. Wechseln Sie zur Registerkarte "Werkzeuge"

1. Klicken Sie auf " **[!UICONTROL Adobe Launch"&gt; "Dynamischer Start"&gt; "Code]** einbetten", um das Texteingabefeld zu öffnen (derzeit kann es die URL Ihres Entwicklungs-Einbettungscodes haben):

   ![Klicken Sie auf die Schaltfläche Adobe Launch &gt; Dynamischer Start einfügen &gt; Code einbetten.](images/switchEnvironments-debugger-editEmbedCode.png)

1. Einbettungscode für Staging in die Zwischenablage einfügen

1. Klicken Sie auf das Diskettensymbol, um zu speichern

   ![Startumgebung im Debugger](images/switchEnvironments-debugger-save.png)

1. Laden Sie die Registerkarte Zusammenfassung des Debuggers neu und aktivieren Sie sie. Im Abschnitt "Start"sollten Sie nun sehen, dass Ihre Staging-Eigenschaft implementiert ist und Ihren Eigenschaftsnamen (d. h. "Launch Tutorial" oder was auch immer Sie Ihre Eigenschaft genannt haben)!

   ![Startumgebung im Debugger](images/publishing-debugger-staging.png)

Wenn sich Ihr Qualitätssicherungsteam in der Staging-Umgebung abgemeldet hat und die Änderungen überprüft, ist es in der Praxis an der Zeit, Inhalte in der Produktion zu veröffentlichen.

## Veröffentlichung in der Produktion

1. Go to the [!UICONTROL Publishing] page

1. Klicken Sie im Dropdownmenü auf **[!UICONTROL Genehmigung für Veröffentlichung]**:

   ![Zur Veröffentlichung genehmigen](images/publishing-approveForPublishing.png)

1. Klicken Sie im Dialogfeld auf die Schaltfläche **[!UICONTROL Genehmigen]** :

   ![Klicken Sie auf Genehmigen](images/publishing-approve.png)

1. Die Bibliothek wird nun in der Spalte " [!UICONTROL Genehmigt] "im nicht erstellten Status (gelber Punkt) angezeigt:

1. Öffnen Sie das Dropdown-Menü und wählen Sie **[!UICONTROL **Erstellen und in Produktion]** veröffentlichen:

   ![Klicken Sie auf Erstellen und in Produktion veröffentlichen](images/publishing-buildAndPublishToProduction.png)

1. Klicken Sie im Dialogfeld auf **[!UICONTROL Veröffentlichen]** :

   ![Klicken Sie auf Veröffentlichen](images/publishing-publish.png)

1. Die Bibliothek wird nun in der Spalte [!UICONTROL Veröffentlicht] angezeigt:

   ![Veröffentlicht](images/publishing-published.png)

Das ist's! Sie haben das Tutorial abgeschlossen und Ihre erste Eigenschaft in Launch veröffentlicht!