---
title: Branding
description: Informationen zum Konfigurieren Ihrer Marke
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="EINGESCHRÄNKTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzende beschränkt"
exl-id: 7afc802d-e90c-48c8-aa04-3ea543dfdfbc
TQID: https://experienceleague.adobe.com/hnN2EgVkkBA0Zp6NYqk2ID2XgHjv1EBDrWRW7k7qJ7Q
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
feature_v2: id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 380
ht-degree: 97%

---

# Konfigurieren von Marken {#branding-configure}

>[!IMPORTANT]
>
>Marken können von Endnutzenden nicht erstellt oder geändert werden. Diese Tätigkeiten müssen von technischen Adobe Campaign-Admins vorgenommen werden. Bei Fragen wenden Sie sich an die Adobe-Kundenunterstützung.

In Adobe Campaign V8 finden Sie Marken im Menü **[!UICONTROL Administration > Plattform > Branding]**.

Eine **[!UICONTROL Marke]** wird durch die folgenden Eigenschaften definiert:

* eine **[!UICONTROL Identität]**, durch die Ihre Marke definiert und personalisiert wird. Dieser Abschnitt weist folgende Felder auf:

   * **[!UICONTROL Titel]** (in der Benutzeroberfläche sichtbar)
   * **[!UICONTROL Kennung]**
   * **[!UICONTROL Markenname]**
   * **[!UICONTROL URL]** und **[!UICONTROL Titel]** der Marken-Website
   * **[!UICONTROL Markenlogo]**

  ![](assets/branding_1.png)

* **[!UICONTROL In Header-Parameter für ausgehende E-Mails]** kann der Inhalt für die Empfänger Ihrer Kampagnen personalisiert werden. Dieser Abschnitt weist folgende Felder auf:

   * **[!UICONTROL Absender (E-Mail)]** mit der E-Mail-Adresse der Marke.
   * **[!UICONTROL Absender (Name)]** mit dem Namen der Marke.
   * **[!UICONTROL Antwortadresse (E-Mail)]** mit der E-Mail-Adresse, an die der Kunde eine Antwort senden kann.
   * **[!UICONTROL Antwortadresse (Name)]** mit dem Namen der Marke.
   * **[!UICONTROL Fehler (E-Mail)]** mit der E-Mail-Adresse, die im Falle eines Fehlers verwendet werden soll.

  >[!IMPORTANT]
  >
  >Sollten nach der Aktualisierung der E-Mail-Header-Parameter Name und E-Mail-Adresse des Absenders in einer neuen, auf dieser Vorlage basierenden E-Mail nicht geändert sein, überprüfen Sie die erweiterten Parameter der Vorlage.

  ![](assets/branding_2.png)

* Über **[!UICONTROL Markenkonfigurationen]** werden die Server definiert, die für das Tracking sowie den Zugriff auf Landingpages verwendet werden. Dieser Abschnitt weist folgende Felder auf:

   * **[!UICONTROL Marken-Subdomain]** bezieht sich auf die für diese Marke spezifische designierte Subdomain-URL, die von Adobe delegiert werden soll.

  Beachten Sie, dass die Konfiguration für Tracking-, Mirror- und Anwendungs-Server in separaten externen Konten gespeichert ist, die mit dem Routing verbunden sind. Diese Einstellungen werden während der Bereitstellung angewendet und sollten nicht geändert werden. Um URLs anzuzeigen, greifen Sie über Ihr externes Konto auf die Registerkarte **[!UICONTROL Branding-Präfixe]** zu.

  ![](assets/branding_3.png)

* Über das Menü **[!UICONTROL Konfiguration der Tracking-URL]** können Sie das URL-Tracking verbessern, indem Sie zusätzliche Parameter für die Integration mit Web-Analyse-Tools wie Adobe Analytics und Google Analytics definieren.

  Verwenden Sie das Menü **[!UICONTROL Zusätzliche URL-Parameter]**, um zusätzliche Parameter als Schlüssel-Wert-Paare zusammen mit ihren Anwendungsbedingungen zu erstellen. Alle Parameternamen müssen eindeutig und dürfen nicht leer sein. Alle Parameterwerte dürfen nicht leer sein. Die Anwendungsbedingung kann leer sein, aber keiner dieser Werte darf JST-Tags enthalten.

  Diese Parameter werden auf getrackte URLs angewendet, die mit einem in der **[!UICONTROL Liste der Domain-Namen]** angegebenen Domain-Namen übereinstimmen, der reguläre Ausdrücke enthalten kann.
