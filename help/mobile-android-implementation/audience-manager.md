---
title: Implementieren von Adobe Audience Manager mit dem Start
description: Erfahren Sie, wie Sie Adobe Audience Manager mithilfe von serverseitigem Weiterleiten und Starten auf Ihrer Website implementieren. Diese Lektion ist Teil des Lernprogramms "Implementing the Experience Cloud in Mobile Android Applications"(Implementieren der Experience Cloud in mobilen Android-Anwendungen).
seo-description: null
seo-title: Implementieren von Adobe Audience Manager mit dem Start
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: e9dee6d0aa3b775d0ce617e2b2c57b56de491b8d

---


# Adobe Audience Manager hinzufügen

Diese Lektion führt Sie durch die Schritte zur Implementierung von Adobe Audience Manager in Experience Platform Mobile SDK mithilfe der serverseitigen Weiterleitung.

[Adobe Audience Manager](https://docs.adobe.com/content/help/en/audience-manager/user-guide/aam-home.html) (AAM) bietet branchenführende Dienste für das Online-Management von Zielgruppendaten. So erhalten Digital-Advertiser und -Herausgeber die Werkzeuge, die sie zur Steuerung und Nutzung ihrer Datenelemente benötigen, um den Erfolg ihrer Verkäufe zu fördern.

## Lernziele

Dies können Sie am Ende dieser Lektion:

1. Beschreiben Sie die zwei Hauptmethoden zum Implementieren von Audience Manager in einer mobilen App
1. Hinzufügen von Audience Manager mithilfe der serverseitigen Weiterleitung des Analytics-Beacons
1. Validieren der Implementierung von Audience Manager

## Voraussetzungen 

Um diese Lektion abzuschließen, benötigen Sie:

1. Um die Lektionen im Abschnitt zum Konfigurieren des Starts abgeschlossen zu haben, d. h. eine [Starteigenschaft](launch-create-a-property.md)erstellen, Erweiterungen[](launch-add-extensions.md)hinzufügen, eine Bibliothek[](launch-create-a-library.md)erstellen und das Mobile SDK[](launch-install-the-mobile-sdk.md)installieren.

1. Administratorzugriff auf Adobe Analytics, damit Sie die serverseitige Weiterleitung für die Report Suite aktivieren können, die Sie für dieses Lernprogramm verwenden. Alternativ können Sie auch einen Administrator in Ihrem Unternehmen bitten, dies anhand der unten stehenden Anweisungen für Sie zu übernehmen.

## Implementierungsoptionen

Es gibt zwei Möglichkeiten, Audience Manager in einer App zu implementieren:

* Serverseitige Weiterleitung (SSF) - Für Kunden mit Adobe Analytics ist dies die einfachste und empfohlene Methode zur Implementierung. Adobe Analytics leitet Daten an AAM im Back-End von Adobe weiter, damit Sie keine Anforderungen aus der App direkt an Audience Manager senden müssen. Dies ermöglicht auch wichtige Integrationsfunktionen und entspricht unseren Best Practices für die Implementierung und Bereitstellung von Audience Manager-Code.

* Clientseitiges DIL - Dieser Ansatz richtet sich an Kunden, die nicht über Adobe Analytics verfügen. Audience Manager-Methoden in der App senden Daten direkt an Audience Manager. In diesem Fall würden Sie die Audience Manager-Erweiterung in Launch verwenden, wenn Sie die Eigenschaft "Mobilstart"einrichten.

Wenn Sie die Analytics-Erweiterung zuvor im Abschnitt "Erweiterungen [hinzufügen](launch-add-extensions.md) "dieses Lernprogramms eingerichtet haben, haben Sie das Kontrollkästchen aktiviert, um die serverseitige Weiterleitung von Daten aus Analytics an Audience Manager zu starten. Dadurch wird dynamisch der Code eingefügt, der für die Verarbeitung der Antwort von Audience Manager-Segmenten benötigt wird, und wieder in Ihre App. Die Erweiterung Audience Manager wird in diesem Lernprogramm nicht hinzugefügt, da dies wiederum nur für den Fall gilt, dass Sie NICHT über Adobe Analytics verfügen.

## Aktivieren der serverseitigen Weiterleitung

Zur Umsetzung des SSF gibt es drei Hauptschritte:

1. Hinzufügen der Experience Cloud Mobile SDK- und Analytics-Erweiterung zur App, ***die Sie bereits im Abschnitt Konfigurieren von Startstunden durchgeführt** haben
1. Aktivieren der Audience Manager-Weiterleitung in der Analytics-Erweiterungskonfiguration, ***die Sie bereits während der Lektion**Erweiterungen* hinzufügen durchgeführt[](launch-add-extensions.md) haben, indem Sie einfach ein Kontrollkästchen aktivieren.
1. Aktivieren Sie einen "Switch" in der Analytics Admin-Konsole, um Daten von Analytics an Audience Manager *pro Report Suite* weiterzuleiten, was wir im weiteren Verlauf dieser Lektion überprüfen werden.

### Aktivieren der serverseitigen Weiterleitung in der Admin Console

Eine Konfiguration in der Adobe Analytics Admin-Konsole ist erforderlich, um Daten von Adobe Analytics an Adobe Audience Manager weiterzuleiten. Bitte beachten Sie, dass es bis zu vier Stunden dauern kann, bis das System die Daten weiterleitet. Denken Sie daran, wenn Sie die Weiterleitung bearbeiten.

#### So aktivieren Sie SSF in der Analytics Admin-Konsole

1. Melden Sie sich über die Experience Cloud-Benutzeroberfläche bei Analytics an. Wenn Sie keinen Administratorzugriff auf Analytics haben, müssen Sie mit Ihrem Experience Cloud- oder Analytics-Administrator sprechen, um Ihnen Zugriff auf diese Schritte zu gewähren oder sie abzuschließen.

   ![Anmelden bei der Adobe Analytics-Benutzeroberfläche](images/mobile-aam-logIntoAnalytics.png)

1. Wählen Sie in der oberen Navigation in Analytics " **[!UICONTROL Admin"&gt; "Report Suites]**"und wählen Sie in der Liste die Report Suites aus (oder wählen Sie sie aus), die Sie an Audience Manager weiterleiten möchten.

   ![Klicken Sie auf die Admin-Konsole](images/mobile-aam-analyticsAdminConsoleReportSuites.png)

1. Wählen Sie im Bildschirm "Report Suites"und bei Auswahl der Report Suite(s) "Einstellungen **[!UICONTROL bearbeiten"&gt; "Allgemein"&gt; "Serverseitige Weiterleitung]**".

   ![Wählen Sie das SSF-Menü](images/mobile-aam-selectSSFmenu.png)

   >[!WARNING] Wie oben angegeben, müssen Sie über Administratorberechtigungen verfügen, um dieses Menüelement anzuzeigen.

1. Lesen Sie auf der Seite "Serverseitige Weiterleitung"die Informationen und markieren Sie das Kästchen zum **[!UICONTROL Aktivieren der serverseitigen Weiterleitung]** für die Report Suite(s).

1. Klicken Sie auf **[!UICONTROL Speichern]**

   ![Vollständige SSF-Einrichtung](images/mobile-aam-enableSSFcomplete.png)

>[!NOTE] Da SSF pro Report Suite aktiviert werden muss, sollten Sie diesen Schritt für Ihre echten Report Suites wiederholen, wenn Sie SSF in der Report Suite Ihrer eigentlichen App bereitstellen.
>
>Wenn die SSF-Option ausgegraut ist, müssen Sie die Report Suite(s) auch Ihrer Experience Cloud-Organisation zuordnen, um die Option zu aktivieren. Dies wird in der [Dokumentation](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/report-suite-mapping.html) näher erläutert.

Dieser Switch startet die tatsächliche Weiterleitung der Daten an AAM, solange der Adobe Experience Platform Identity Service implementiert ist. Der Rest der SSF-Implementierung findet im Code statt, der beim Start verarbeitet wurde, als Sie das Kontrollkästchen in der Analytics-Erweiterung aktiviert haben, um an AAM weiterzuleiten.

Serverseitiger Weiterleitungscode ist jetzt für Ihre App implementiert!

[Weiter "Eigenschaft veröffentlichen"&gt;](publish.md)