---
title: Branding
description: Erfahren Sie, wie Sie Ihre Marke konfigurieren
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="BEGRENZTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzer beschränkt"
exl-id: 7afc802d-e90c-48c8-aa04-3ea543dfdfbc
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 63%

---

# Konfigurieren von Marken {#branding-configure}

>[!IMPORTANT]
>
>Marken können nicht vom Endnutzer erstellt oder geändert werden. Diese Aktionen müssen von einem technischen Adobe-Campaign-Administrator vorgenommen werden. Bei Fragen wenden Sie sich an die Adobe-Kundenunterstützung.

In Adobe Campaign V8 finden Sie Marken im Menü **[!UICONTROL Administration > Plattform > Branding]** .

Eine **[!UICONTROL Marke]** wird durch die folgenden Eigenschaften definiert:

* eine **[!UICONTROL Identität]**, durch die Ihre Marke definiert und personalisiert wird. Dieser Bereich weist folgende Felder auf:

   * **[!UICONTROL Titel]** (in der Benutzeroberfläche sichtbar)
   * **[!UICONTROL Kennung]**
   * **[!UICONTROL Markenname]**
   * **[!UICONTROL URL]** und **[!UICONTROL Titel]** der Marken-Website
   * **[!UICONTROL Markenlogo]**

  ![](assets/branding_1.png)

* **[!UICONTROL In Header-Parameter für ausgehende E-Mails]** kann der Inhalt für die Empfänger Ihrer Kampagnen personalisiert werden. Dieser Bereich weist folgende Felder auf:

   * **[!UICONTROL Absender (E-Mail)]** mit der E-Mail-Adresse der Marke.
   * **[!UICONTROL Absender (Name)]** mit dem Namen der Marke.
   * **[!UICONTROL Antwortadresse (E-Mail)]** mit der E-Mail-Adresse, an die der Kunde eine Antwort senden kann.
   * **[!UICONTROL Antwortadresse (Name)]** mit dem Namen der Marke.
   * **[!UICONTROL Fehler (E-Mail)]** mit der E-Mail-Adresse, die im Falle eines Fehlers verwendet werden soll.

  >[!IMPORTANT]
  >
  >Sollten nach der Aktualisierung der E-Mail-Header-Parameter Name und E-Mail-Adresse des Absenders in einer neuen, auf dieser Vorlage basierenden E-Mail nicht geändert sein, überprüfen Sie die erweiterten Parameter der Vorlage.

  ![](assets/branding_2.png)

* **[!UICONTROL Markenkonfigurationen]** definiert die Server, die zum Tracking auch für den Zugriff auf Landingpages verwendet werden. Dieser Bereich weist folgende Felder auf:

   * **[!UICONTROL Marken-Subdomain]** bezieht sich auf die spezifische Subdomain-URL für diese Marke, die von Adobe zur Delegierung angefordert wird.

  Beachten Sie, dass die Konfiguration für Tracking-, Mirror- und Anwendungsserver in separaten externen Konten gespeichert ist, die mit dem Routing verknüpft sind. Diese Einstellungen werden während der Bereitstellung angewendet und sollten nicht geändert werden. Um URLs anzuzeigen, greifen Sie von Ihrem externen Konto aus auf die Registerkarte **[!UICONTROL Branding-Präfixe]** zu.

  ![](assets/branding_3.png)

<!--![](assets/branding_05.png)-->

<!--
* **[!UICONTROL Tracking URL configs]**, which defines the configuration of the URLs tracking for your brand.

  The additional parameters that allow the links to be tracked on external systems such as Web Analytics tools like Adobe Analytics or Google Analytics are defined here.
-->
