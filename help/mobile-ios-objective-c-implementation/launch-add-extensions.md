---
title: Erweiterungen zu einer Mobile Launch-Eigenschaft hinzufügen
description: Erfahren Sie, wie Sie einer mobilen Launch-Eigenschaft Erweiterungen hinzufügen. Diese Lektion ist Teil des Lernprogramms "Implementing the Experience Cloud in Mobile iOS Objective-C Applications"(Implementieren der Experience Cloud in Mobile-iOS-Anwendungen).
seo-description: null
seo-title: Erweiterungen zu einer Mobile Launch-Eigenschaft hinzufügen
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 7166d2933cc99bcbbd4713fba8f87fb0826b711e

---


# Erweiterungen hinzufügen

In dieser Lektion fügen Sie Ihrer Launch-Eigenschaft Erweiterungen hinzu.

Launch ist eine Plattform, mit der Adobe und Drittanbieter Erweiterungen erstellen können, um die Bereitstellung ihrer Lösungen über Launch zu erleichtern. Eine Erweiterung ist ein Paket von Code, das die Startschnittstelle und die Clientfunktionalität erweitert. Mit Erweiterungen können Sie nur die Teile des Adobe Experience Platform Mobile SDK auswählen, die Sie für Ihre spezifische App benötigen.  Sie können sich Launch wie ein Betriebssystem vorstellen, und Erweiterungen sind die Apps, mit denen Sie Ihre Aufgaben erledigen.

Da Sie die Adobe-Lösungen (z. B. Target, Analytics und Audience Manager) implementieren, fügen Sie die erforderlichen Erweiterungen hinzu, um sie zu unterstützen.

>[!WARNING] Zum Hinzufügen und Entfernen von Erweiterungen in den Eigenschaften des mobilen Starts müssen Sie Ihre App aktualisieren. Dies unterscheidet sich von den Webstarteigenschaften, in denen Sie jederzeit Erweiterungen hinzufügen oder entfernen können, ohne Ihre Website aktualisieren zu müssen.

## Voraussetzungen 

Ihr Benutzerkonto "Start"benötigt die Berechtigung "Erweiterungen verwalten", um diese Lektion abzuschließen. Wenn Sie diese Schritte nicht ausführen können, da die Benutzeroberflächenoptionen nicht verfügbar sind, wenden Sie sich an Ihren Experience Cloud-Administrator, um Zugriff zu erhalten. For more information on Launch permissions, see [the documentation](https://docs.adobe.com/content/help/en/launch/using/reference/admin/user-permissions.html).

Sie benötigen die folgenden Lösungsdetails:

* Mindestens eine Analytics-Report Suite-ID. Für die Report Suite sollten [App-Berichte aktiviert](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/mobile-management.html)sein. If you don't have a test/dev report suite that you can use for this tutorial, please [create one](https://docs.adobe.com/content/help/en/analytics/admin/manage-report-suites/new-report-suite/new-report-suite.html). Eine Report Suite ist ausreichend für dieses Lernprogramm, aber in der realen Welt sollten Sie unterschiedliche Report Suites für Ihre Entwicklungs-, Staging- und Produktionsumgebungen verwenden.

* Ihr Analytics-Tracking-Server. Sie können Ihren Tracking-Server von Ihrer aktuellen Implementierung, Ihrem Adobe-Berater oder Ihrem Kundendienstmitarbeiter abrufen.

## Lernziele

Dies können Sie am Ende dieser Lektion:

* Erweiterungen zu einer mobilen Starteigenschaft hinzufügen
* Konfigurieren der Analytics-Erweiterung
* Target- und Target-VEC-Erweiterungen konfigurieren

>[!NOTE] Adobe Audience Manager kann über eine Konfiguration in der Analytics-Erweiterung implementiert werden. Daher müssen Sie die Audience Manager-Erweiterung in diesem Lernprogramm nicht hinzufügen

## Überprüfen der vorinstallierten Erweiterungen

1. Klicken Sie auf die Registerkarte **[!UICONTROL Erweiterungen]** , um zur Seite Erweiterungen zu gelangen.
1. Beachten Sie, dass der Mobile Core und `Profile` die Erweiterungen in Ihrer neuen Eigenschaft für Mobilgeräte vorinstalliert sind
1. Klicken Sie auf die Schaltfläche " **[!UICONTROL Konfigurieren]** "in der Core-Erweiterung, um deren Einstellungen zu überprüfen

   ![Wechseln Sie zur Registerkarte Erweiterungen](images/mobile-extensions-installed-default.png)

1. Die Mobile Core Extension stellt das Adobe Experience Platform Mobile-SDK dar, das für jede App-Implementierung erforderlich ist. Der Core enthält allgemeine Funktionen und Frameworks wie Experience Cloud-Identitätsdienste, Datenereignis-Hub, Regeln-Engine, wiederverwendbare Netzwerke, Festplattenzugriffsroutinen usw., die für alle Erweiterungen von Adobe und Drittanbietern erforderlich sind.  Weitere Informationen zur Mobile Core Extension finden Sie in [der Dokumentation](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core).

   1. Beachten Sie, dass Ihre Experience Cloud-Organisations-ID automatisch erkannt und vorausgefüllt wird.
   1. Im Feld Experience Cloud-Server können Sie einen benutzerdefinierten Endpunkt für Besucher-ID-Dienst-Anforderungen angeben. Verwenden Sie die Standardeinstellung (leer lassen) für dieses Lernprogramm.
   1. Im Feld Sitzungs-Timeout können Sie angeben, wann eine App-Lebenszyklussitzung mit einem Timeout beginnen soll. Standardmäßig wird ein Timeout ausgeführt, wenn sich die App 300 Sekunden lang im Hintergrund befindet. Verwenden Sie die Standardeinstellung für dieses Lernprogramm.

1. Da Sie keine der Einstellungen geändert haben, klicken Sie auf **[!UICONTROL Abbrechen]** , um die Erweiterungskonfiguration zu belassen

   ![Klicken Sie auf Abbrechen, um die Konfiguration zu verlassen](images/mobile-extensions-core-cancel.png)

1. Mit der Profilerweiterung kann das SDK Daten in einem clientseitigen Profil speichern. Es hat keine Konfigurationen, daher gibt es nichts zu betrachten. Weitere Informationen zur Profilerweiterung finden Sie in [der Dokumentation](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/profile).

## Lösungserweiterungen hinzufügen

Jetzt ist es an der Zeit, zu dem lustigen Teil zu kommen und die Erweiterungen für die Lösungen hinzuzufügen, die Sie in diesem Tutorial implementieren werden. Bei Verwendung von Launch mit mobilen Anwendungen muss die App jedes Mal aktualisiert werden, wenn eine Erweiterung hinzugefügt oder entfernt wird. Um später Zeit zu sparen, werden wir alle Erweiterungen in dieser Lektion hinzufügen. Überspringen Sie einfach alle Lösungen, die Ihr Unternehmen nicht lizenziert hat.

### Adobe Analytics-Erweiterung hinzufügen

>[!NOTE] Wenn Sie keine Lizenz für Adobe Analytics haben, können Sie diesen Abschnitt überspringen. Derzeit wird die Analytics-Erweiterung für mobile Eigenschaften ausschließlich zur Verwaltung von SDK-Einstellungen verwendet und fügt keine Oberflächenoptionen zum Starten hinzu, wie z. B. Regelaktionen.

**So fügen Sie die Erweiterung hinzu**

1. Klicken Sie auf die Registerkarte "Katalog", um die _deinstallierten_ Erweiterungen anzuzeigen

1. Suchen Sie die **[!UICONTROL Adobe Analytics]** -Erweiterung und klicken Sie auf **[!UICONTROL Installieren]**

   ![Wechseln Sie zum Erweiterungskatalog und klicken Sie auf Installieren, um die Analytics-Erweiterung hinzuzufügen](images/mobile-extensions-catalog-installAnalytics.png)

1. Wählen Sie Ihre **[!UICONTROL Report Suites]** aus den vorausgefüllten Listen aus. Dies sind die Report Suites, an die die App Daten sendet. Sie können verschiedene Report Suites für Ihre Entwicklungs-, Staging- und Produktionsumgebungen auswählen.
1. Ihr **[!UICONTROL Analytics-Tracking-Server]** kann vorausgefüllt sein oder Sie müssen ihn aus einer vorab ausgefüllten Liste auswählen oder manuell eingeben. Dies ist die Domäne, an die die Beacons gesendet werden, normalerweise im Format `yoursite.sc.omtrdc.net`.
1. Markieren Sie das Kontrollkästchen für " **[!UICONTROL Offline aktiviert]**". Wenn das Kontrollkästchen "Offline aktiviert"aktiviert ist, werden Analytics-Treffer in die Warteschlange gestellt, wenn Ihr Gerät offline ist, und später gesendet, wenn Ihr Gerät wieder online ist. Um die Offline-Verfolgung zu verwenden, **stellen** Sie sicher, dass Ihre Report Suite zeitstempelfähig ist. Weitere Informationen finden Sie in der [Dokumentation zu ](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/offline-tracking.html).
1. Markieren Sie das Kästchen für **[!UICONTROL Audience Manager-Weiterleitung]**. Dadurch werden Analytics-Daten an Audience Manager weitergeleitet, sodass Sie keinen zusätzlichen Aufruf der App an Audience Manager vornehmen müssen. In dieser Übung gehen wir davon aus, dass Sie über Audience Manager verfügen und daher die Daten von Analytics weiterleiten. Wenn Sie nicht über Audience Manager verfügen, aktivieren Sie dieses Kontrollkästchen nicht, da Sie Analytics für Ihre eigene Implementierung einrichten.
1. Markieren Sie das Kontrollkästchen zum **[!UICONTROL Zurückdatieren der Informationen zur vorherigen Sitzung.]**
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Speichern]**

   ![Wechseln Sie zum Erweiterungskatalog und klicken Sie auf Installieren, um die Analytics-Erweiterung hinzuzufügen](images/mobile-extensions-analytics-settings.png)

### Hinzufügen der Target-Erweiterung

Adobe Target verfügt über zwei offizielle Erweiterungen: die Adobe Target-Erweiterung und die Adobe Target VEC-Erweiterung. Adobe Target unterstützt alle APIs, die Benutzern unserer früheren mobilen SDKs bekannt sind. Die Adobe Target VEC-Erweiterung unterstützt den Visual Experience Composer von Target, der es Marketingexperten ermöglicht, einfache Aktivitäten zu erstellen, die Bild- und Textelemente auf der Seite in einer WYSIWYG-Schnittstelle (What-You-See-Is-What-You-Get) ändern. In diesem Tutorial verwenden Sie beide.

>[!NOTE] Wenn Sie keine Lizenz für Adobe Target haben, können Sie diesen Abschnitt überspringen. Derzeit wird die Target-Erweiterung für mobile Eigenschaften ausschließlich zur Verwaltung von SDK-Einstellungen verwendet. Es werden keine Optionen für die Benutzeroberfläche zum Starten hinzugefügt, z. B. Regelaktionen.

**So fügen Sie die Erweiterung hinzu**

1. Klicken Sie auf die Registerkarte "Katalog", um die _deinstallierten_ Erweiterungen anzuzeigen

1. Suchen Sie die **[!UICONTROL Adobe Target]** -Erweiterung und klicken Sie auf **[!UICONTROL Installieren]**

   ![Gehen Sie zum Erweiterungskatalog und klicken Sie auf Installieren, um die Target-Erweiterung hinzuzufügen](images/mobile-extensions-catalog-installTarget.png)

1. Ihr **[!UICONTROL Clientcode]** wird vorab aufgefüllt.
1. Lassen Sie die **[!UICONTROL Umgebungs-ID]** leer. Diese Einstellung wird in Verbindung mit der [Hosts](https://docs.adobe.com/help/en/target/using/administer/hosts.html) -Funktion in Adobe Target verwendet, mit der Sie die Daten in verschiedene Berichtsumgebungen (z. B. Entwicklung, Staging, Produktion) senden können. Standardmäßig werden die Daten an die Produktionsumgebung gesendet.
1. Lassen Sie die **[!UICONTROL Target Workspace-Eigenschaft]** leer. Diese Einstellung wird in Verbindung mit der Funktion für [Enterprise-Benutzerberechtigungen](https://docs.adobe.com/content/help/en/target/using/administer/manage-users/enterprise/property-channel.html) von Target Premium verwendet.
1. Lassen Sie das **[!UICONTROL Timeout]** auf 5 Sekunden eingestellt. Diese Einstellung steuert, wie lange die App auf die Target-Antwort warten soll, bevor Standardinhalte angezeigt werden.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Speichern]**

   ![Target-Einstellungen konfigurieren](images/mobile-extensions-target-settings.png)

### Hinzufügen der Target VEC-Erweiterung

Nachdem die Target-Erweiterung hinzugefügt wurde, können Sie die Target VEC-Erweiterung hinzufügen.

>[!NOTE] Wenn Sie keine Lizenz für Adobe Target haben, können Sie diesen Abschnitt überspringen. Derzeit wird die Target VEC-Erweiterung für mobile Eigenschaften ausschließlich zur Verwaltung von SDK-Einstellungen verwendet. Es werden keine Optionen für die Benutzeroberfläche zum Starten hinzugefügt, wie z. B. Regelaktionen.

**So fügen Sie die Erweiterung hinzu**

1. Klicken Sie auf die Registerkarte "Katalog", um die _deinstallierten_ Erweiterungen anzuzeigen

1. Suchen Sie die **[!UICONTROL Adobe Target VEC]** -Erweiterung und klicken Sie auf **[!UICONTROL Installieren]**

   ![Gehen Sie zum Erweiterungskatalog und klicken Sie auf Installieren, um die Target-Erweiterung hinzuzufügen](images/mobile-extensions-catalog-installTargetVEC.png)

1. Aktivieren Sie die **[!UICONTROL automatisierte Abrufen von Target-Kampagnen]**`ON` . Dadurch werden beim ersten Laden der App alle Target-Aktivitäten vorab abgerufen, sodass weniger Anforderungen erforderlich sind.
1. Lassen Sie **[!UICONTROL die Suche im Hintergrund]**`OFF`. Diese Einstellung wird nur angezeigt, wenn sie verwendet `Auto-Fetch Target Campaigns` wird.  Wenn Sie diese Einstellung beibehalten, `OFF` können Sie VEC-Aktivitäten auf dem Startbildschirm der App ausführen. Außerdem wird eine Verzögerung beim Starten der App hinzugefügt, um sicherzustellen, dass die Target-Anforderung abgeschlossen oder abgelaufen ist, bevor der Startbildschirm angezeigt wird. Es wird empfohlen, diese Einstellung zu belassen, `OFF` wenn Sie Aktivitäten auf dem Startbildschirm ausführen, und sie zu aktivieren, `ON` wenn dies nicht der Fall ist.  Diese Einstellung kann jederzeit in der Benutzeroberfläche "Starten"geändert werden, ohne dass die App aktualisiert werden muss.
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Speichern]**

   ![Target VEC-Einstellungen konfigurieren](images/mobile-extensions-targetVEC-settings.png)

Das ist alles! Nachdem Sie die Erweiterungen Ihrer Eigenschaft hinzugefügt haben, können Sie sie einer Bibliothek hinzufügen:

[Weiter "Bibliothek erstellen"&gt;](launch-create-a-library.md)