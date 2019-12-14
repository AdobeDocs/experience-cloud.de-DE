---
title: Startumgebungen mit dem Adobe Experience Cloud-Debugger wechseln
description: Erfahren Sie, wie Sie mit dem Experience Cloud-Debugger verschiedene Start-Einbettungscodes laden können. Diese Lektion ist Teil des Tutorials zum Implementieren der Experience Cloud in Websites mit Start.
seo-description: null
seo-title: Startumgebungen mit dem Adobe Experience Cloud-Debugger wechseln
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 79d5274d09d66b80a49aba5db3e0a997d0f0ff61

---


# Startumgebungen mit dem Experience Cloud-Debugger wechseln

In this lesson you will use the [Adobe Experience Cloud Debugger extension](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) to replace the Launch property hardcoded on the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html) with your own property.

Diese Technik wird als "Umschalten zwischen Umgebungen"bezeichnet und wird später hilfreich sein, wenn Sie mit Launch auf Ihrer eigenen Website arbeiten. Sie können Ihre Produktions-Website in Ihren Browser laden, aber mit Ihrer *Entwicklungsumgebung* starten. Auf diese Weise können Sie Launch-Änderungen unabhängig von Ihren regulären Code-Versionen selbstbewusst vornehmen und validieren.  Schließlich ist diese Trennung von Marketing-Tag-Releases aus Ihren regulären Code-Releases einer der Hauptgründe, warum Kunden Launch überhaupt verwenden!

## Lernziele

Dies können Sie am Ende dieser Lektion:

* Verwenden Sie den Debugger, um eine alternative Startumgebung zu laden
* Verwenden Sie den Debugger, um zu überprüfen, ob Sie eine alternative Startumgebung geladen haben

## URL der Entwicklungsumgebung abrufen

1. In your Launch property, open the `Environments` page

1. In the **[!UICONTROL Development]** row, click the Install icon ![Install icon](images/launch-installIcon.png) to open the modal

1. Klicken Sie auf das Symbol " ![Kopieren", um den Einbettungscode in die Zwischenablage zu kopieren](images/launch-copyIcon.png) .

1. Click **[!UICONTROL Close]** to close the modal

   ![Installationssymbol](images/launch-copyInstallCode.png)

## Ersetzen Sie die Start-URL auf der Luma Demo-Site.

1. Open the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html) in your Chrome browser

1. Öffnen Sie die [Experience Cloud Debugger-Erweiterung](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) , indem Sie auf das Symbol ![Debugger](images/icon-debugger.png) klicken

   ![Klicken Sie auf das Symbol Debugger](images/switchEnvironments-openDebugger.png)

1. Beachten Sie, dass die derzeit implementierte Eigenschaft Start auf der Registerkarte Zusammenfassung angezeigt wird.

   ![Startumgebung im Debugger](images/switchEnvironments-debuggerOnWeRetail-prod.png)

1. Wechseln Sie zur Registerkarte "Werkzeuge"

1. Bildlauf zum Abschnitt Einbettungscode **[!UICONTROL ersetzen]**

1. Stellen Sie sicher, dass sich die Registerkarte "Chrome"mit der Luma-Site hinter dem Debugger befindet (nicht die Registerkarte mit diesem Tutorial oder die Registerkarte mit der Startschnittstelle).  Fügen Sie den Einbettungscode aus der Zwischenablage in das Eingabefeld ein

1. Schalten Sie die Funktion "Übernehmen über luma.enablementadobe.com"um, damit alle Seiten auf der Luma-Site Ihrer Launch-Eigenschaft zugeordnet werden

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Speichern]**

   ![Startumgebung im Debugger](images/switchEnvironments-debugger-save.png)

1. Laden Sie die Luma-Site neu und überprüfen Sie die Registerkarte Zusammenfassung des Debuggers. Im Abschnitt "Start"sollten Sie nun sehen, dass Ihre Development-Eigenschaft verwendet wird. Vergewissern Sie sich, dass sowohl der Name der Eigenschaft mit Ihrer übereinstimmt, als auch die Umgebung "development".

   ![Startumgebung im Debugger](images/switchEnvironments-debuggerOnWeRetail.png)

>[!NOTE] Der Debugger speichert diese Konfiguration und ersetzt die Einbettungscodes "Start", sobald Sie zur Luma-Site zurückkehren. Sie hat keine Auswirkungen auf andere Sites, die Sie in anderen offenen Registerkarten besuchen. To stop the Debugger from replacing the embed code, click the **[!UICONTROL Remove]** button next to the embed code in the Tools tab of the Debugger.

Während Sie das Tutorial fortsetzen, verwenden Sie diese Methode, um die Luma-Site Ihrer eigenen Launch-Eigenschaft zuzuordnen, um Ihre Launch-Implementierung zu validieren. Wenn Sie mit der Verwendung von Launch auf Ihrer Produktions-Website beginnen, können Sie die Änderungen auf dieselbe Weise überprüfen.

[Weiter "Adobe Experience Platform Identity Service hinzufügen"&gt;](id-service.md)