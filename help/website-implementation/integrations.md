---
title: Implementieren von Experience Cloud-Integrationen mit dem Start
description: Erfahren Sie, wie Sie die Integrationen von Zielgruppen, A4T und Kundenattributen in Ihrer Adobe Experience Cloud-Implementierung validieren. Diese Lektion ist Teil des Tutorials zum Implementieren der Experience Cloud in Websites mit Start.
seo-description: null
seo-title: Implementieren von Experience Cloud-Integrationen mit dem Start
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: e9dee6d0aa3b775d0ce617e2b2c57b56de491b8d

---


# Experience Cloud-Integrationen

In dieser Lektion werden Sie die wichtigsten Integrationen zwischen den soeben implementierten Lösungen überprüfen. Die gute Nachricht ist, dass Sie mit dem Abschluss der früheren Lektionen bereits die Code-Aspekte der Integrationen implementiert haben! In dieser Lektion müssen Sie nicht nur lesen und validieren, sondern auch keine weiteren Arbeiten durchführen.

## Lernziele

Dies können Sie am Ende dieser Lektion:

1. Erläuterung der grundlegenden Anwendungsfälle für Audience Sharing, Analytics for Target (A4T) und Kundenattributintegrationen
1. Die grundlegenden clientseitigen Implementierungsaspekte dieser Integrationen validieren

## Voraussetzungen

Bevor Sie die Anweisungen in dieser Lektion befolgen, sollten Sie alle vorherigen Lektionen in diesem Tutorial abschließen.

>[!NOTE] Es gibt viele Benutzerberechtigungen, Kontokonfigurationen und Bereitstellungsschritte, die zum vollständigen Einsatz dieser Integrationen erforderlich sind und die über den Rahmen dieses Tutorials hinausgehen. Wenn Sie diese Integrationen noch nicht in Ihrer aktuellen Implementierung der Experience Cloud verwenden, sollten Sie Folgendes beachten:
>
> * Überprüfen Sie die vollständigen Anforderungen der [Core Services-Integrationen.](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html)
> * Überprüfen Sie die vollständigen Anforderungen für die [Integration von Analytics for Target](https://docs.adobe.com/content/help/en/target/using/integrate/a4t/before-implement.html)
> * Have an Administrator of your Experience Cloud Organization [request provisioning of these integrations](https://www.adobe.com/go/audiences)


## Zielgruppen

[Zielgruppen](https://docs.adobe.com/content/help/en/core-services/interface/audiences/audience-library.htm) sind Teil des Hauptdiensts "Personen"und ermöglichen es Ihnen, Zielgruppen zwischen verschiedenen Lösungen zu teilen. Sie können beispielsweise eine Zielgruppe in Audience Manager erstellen und damit personalisierte Inhalte mit Target bereitstellen.

Die wichtigsten Voraussetzungen für die Implementierung von A4T - die Sie bereits getan haben - sind:

1. Implementieren des Identitätsdienstes für Adobe Experience Platform
1. Implementieren von Audience Manager
1. Implementieren anderer Lösungen, die Sie Zielgruppen empfangen oder erstellen möchten, z. B. Target und Analytics

### Überprüfen der Integration von Zielgruppen

Die beste Methode zur Validierung der Zielgruppen-Integration besteht darin, eine Zielgruppe zu erstellen, sie an eine andere Lösung weiterzugeben und sie dann in vollem Umfang in der anderen Lösung zu verwenden (z. B. zu bestätigen, dass ein Besucher, der sich für ein AAM-Segment qualifiziert, sich für eine Target-Aktivität für dieses Segment qualifizieren kann). Das überschreitet jedoch den Rahmen dieses Tutorials.

Diese Validierungsschritte konzentrieren sich auf den kritischen Teil, der in der clientseitigen Implementierung sichtbar ist - die Besucher-ID.

1. Open the [Luma site](https://luma.enablementadobe.com/content/luma/us/en.html)

1. Make sure the Debugger is mapping the Launch property to *your* Development environment, as described in the [earlier lesson](launch-switch-environments.md)

   ![Ihre Entwicklungsumgebung "Start"im Debugger](images/switchEnvironments-debuggerOnWeRetail.png)

1. Wechseln Sie zur Registerkarte Netzwerk des Debuggers

1. Klicken Sie auf **[!UICONTROL Alle Anforderungen]** löschen, um nur die Elemente zu bereinigen

1. Laden Sie die Luma-Seite neu, um sicherzustellen, dass sowohl die Target- als auch die Analytics-Anforderungen im Debugger angezeigt werden

1. Laden Sie die Luma-Seite erneut

1. Sie sollten jetzt auf der Registerkarte "Netzwerk"des Debuggers vier Anforderungen sehen: zwei für Target und zwei für Analytics

1. Sehen Sie sich die Zeile "Experience Cloud-Besucher-ID"an. Die IDs in jeder einzelnen Anfrage sollten immer gleich sein.

   ![Übereinstimmende SDIDs bestätigen](images/integrations-matchingECIDs.png)

1. Die IDs sind pro Besucher eindeutig, was Sie bestätigen können, indem Sie einen Kollegen bitten, diese Schritte zu wiederholen.

## Analytics for Target (A4T)

The [Analytics for Target (A4T)](https://docs.adobe.com/content/help/en/target/using/integrate/a4t/a4t.html) integration allows you to leverage your Analytics data as the source for reporting metrics in Target.

Die wichtigsten Voraussetzungen für die Implementierung von A4T - die Sie bereits getan haben - sind:

1. Implementieren des Identitätsdienstes für Adobe Experience Platform
1. Laden der Target-Seite vor dem Analytics-Seitenansichts-Beacon starten

A4T funktioniert, indem eine serverseitige Anforderung von Target an Analytics mit dem Analytics-Seitenansichts-Beacon zusammengeführt wird, das wir "Trefferzuordnung"nennen.  Für die Trefferzuordnung muss die Target-Anforderung, die die Aktivität bereitstellt (oder eine Target-basierte Zielmetrik inkrementiert), über einen Parameter verfügen, der mit einem Parameter im Analytics-Seitenansichts-Beacon übereinstimmt. Dieser Parameter wird als ergänzende Daten-ID (SDIDs) bezeichnet.

### Validieren der A4T-Implementierung

Die beste Methode zur Validierung der A4T-Integration besteht darin, eine Target-Aktivität mit A4T zu erstellen und die Berichtsdaten zu validieren. Dies liegt jedoch außerhalb des Geltungsbereichs dieses Lernprogramms. Dieses Lernprogramm zeigt Ihnen, wie Sie sicherstellen können, dass die zusätzlichen Daten-IDs zwischen den Lösungsaufrufen übereinstimmen.

**So validieren Sie die SDIDs**

1. Open the [Luma site](https://luma.enablementadobe.com/content/luma/us/en.html)

1. Make sure the Debugger is mapping the Launch property to *your* Development environment, as described in the [earlier lesson](launch-switch-environments.md)

   ![Ihre Entwicklungsumgebung "Start"im Debugger](images/switchEnvironments-debuggerOnWeRetail.png)

1. Wechseln Sie zur Registerkarte Netzwerk des Debuggers

1. Klicken Sie auf **[!UICONTROL Alle Anforderungen]** löschen, um nur die Elemente zu bereinigen

1. Laden Sie die Luma-Seite neu, um sicherzustellen, dass sowohl die Target- als auch die Analytics-Anforderungen im Debugger angezeigt werden

1. Laden Sie die Luma-Seite erneut

1. Sie sollten jetzt auf der Registerkarte "Netzwerk"des Debuggers vier Anforderungen sehen: zwei für Target und zwei für Analytics

1. Überprüfen Sie die Spalte mit den IDs für zusätzliche Daten. Die IDs des ersten Seitenladevorgangs sollten zwischen Target und Analytics übereinstimmen. Die IDs des zweiten Seitenladevorgangs sollten ebenfalls übereinstimmen, unterscheiden sich jedoch von denen des ersten Seitenladevorgangs.

   ![Übereinstimmende SDIDs bestätigen](images/integrations-matchingSDIDs.png)

Wenn Sie zusätzliche Target-Anforderungen im Rahmen eines Seitenladevorgangs (ohne einseitige Apps) stellen, die Teil von A4T-Aktivitäten sind, sollten Sie ihnen eindeutige Namen zuweisen (nicht target-global-mbox), damit sie weiterhin über dieselben SDIDs der ursprünglichen Target- und Analytics-Anforderungen verfügen.

## Kundenattribute

[Kundenattribute](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html) sind Teil des People Core Service, mit dem Sie Daten aus Ihrer CRM-Datenbank (Customer Relationship Management) hochladen und in Adobe Analytics und Adobe Target nutzen können.

Die wichtigsten Voraussetzungen für die Implementierung von Kundenattributen - die Sie bereits getan haben - sind:

1. Implementieren des Identitätsdienstes für Adobe Experience Platform
1. Set Customer Ids via the Id Service *before* Target and Analytics fire their requests (which you accomplished using the rule ordering feature in Launch)

### Implementierung der Kundenattribute überprüfen

Sie haben bereits überprüft, dass die Kunden-IDs in früheren Lektionen sowohl an den Identitätsdienst als auch an Target weitergeleitet werden. Sie können auch die Kunden-ID im Analytics-Treffer validieren.
Derzeit ist die Kunden-ID einer der wenigen Parameter, der nicht im Experience Cloud-Debugger angezeigt wird. Daher verwenden Sie die JavaScript-Konsole des Browsers, um sie anzuzeigen.

1. Öffnen der Luma-Site
1. Öffnen Sie die Entwicklertools Ihres Browsers
1. Wechseln Sie zur Registerkarte Netzwerk
1. Geben Sie in das Filterfeld ein, `b/ss` welche die Anzeige auf die Adobe Analytics-Anforderungen beschränkt

   ![Öffnen Sie die Developer Tools und filtern Sie die Registerkarte "Netzwerk", um nur die Analytics-Anforderungen anzuzeigen](images/aam-openTheJSConsole.png)

1. Klicken Sie oben rechts auf der Site auf den Link **[!UICONTROL LOGIN]** .

   ![Klicken Sie in der oberen Navigation auf Anmelden](images/idservice-loginNav.png)

1. Als `test@adobe.com` Benutzernamen eingeben
1. Als `test` Kennwort eingeben
1. Klicken Sie auf die Schaltfläche **[!UICONTROL ANMELDEN]**

   ![Anmeldeinformationen eingeben und auf Anmelden klicken](images/idservice-login.png)

1. Es sollte Sie auf die Homepage zurückführen, die auch einen Beacon auslöst, den Sie in den Entwicklerwerkzeugen sehen können. Wenn Sie auf die Seite mit den Kontoinformationen gehen, klicken Sie auf das Logo WE.RETAIL, um zur Homepage zurückzukehren.
1. Klicken Sie auf die Anforderung und wählen Sie die Registerkarte "Kopfzeilen"
1. Scrollen Sie nach unten, bis einige verschachtelte Parameter angezeigt werden
   1. cid - dies ist das Standardtrennzeichen für den Kunden-ID-Teil der Anforderung
   1. crm_id - Dies ist der benutzerdefinierte Integrationscode, den Sie in der Lektion zum Identitätsdienst angegeben haben
   1. id - Der Kunden-ID-Wert, der von Ihrem `Email (Hashed)` Datenelement stammt
   1. as - Der Authentifizierungsstatus mit "1" bedeutet angemeldet
   ![Validierung der Analytics-Kunden-ID](images/integrations-analyticsCustomerIDValidation.png)

[Weiter "Eigenschaft veröffentlichen"&gt;](publish.md)