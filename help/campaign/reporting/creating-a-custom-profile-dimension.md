---
title: Benutzerdefinierte Profildimension erstellen
description: Hier erfahren Sie, wie Sie eine benutzerdefinierte Profildimension auf der Basis von benutzerdefinierten Profildaten erstellen können.
audience: reporting
content-type: reference
level: Intermediate
source-git-commit: 5a7337c44d6ca5ee4403d9fe0b65246b629afacd
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 22%

---

# Benutzerdefinierte Profildimension erstellen{#creating-a-custom-profile-dimension}

Berichte können auch basierend auf benutzerdefinierten Profildaten erstellt und verwaltet werden, die während der Erweiterung des Empfängerschemas erstellt wurden.

* [Schritt 1: Erweiterung des Empfängerschemas](##extend-schema)
* [Schritt 2: Verknüpfen Sie Ihr neues benutzerdefiniertes Feld](#link-custom)
* [Schritt 3: Erstellen Sie einen dynamischen Bericht, um Empfänger mithilfe der benutzerdefinierten Profildimension zu filtern.](#create-report)

## Schritt 1: Erweiterung des Empfängerschemas {#extend-schema}

Gehen Sie wie folgt vor, um ein neues Profilfeld hinzuzufügen:

1. Navigieren Sie zum **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Datenschemata]** im Explorer angezeigt.

   ![](assets/custom_field_1.png)

1. Identifizieren Sie das benutzerdefinierte Empfängerschema und wählen Sie es aus. Wenn Sie das integrierte Schema nms:recipient noch nicht erweitert haben, lesen Sie den Abschnitt [dieses Verfahrens](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Fügen Sie das benutzerdefinierte Feld zum Schema-Editor hinzu.

   So fügen Sie beispielsweise ein benutzerdefiniertes Treuefeld in Ihr Empfängerschema ein:

   ```
   <attribute label="Loyalty" name="loyalty" type="string"/>
   ```

   ![](assets/custom_field_2.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Identifizieren Sie dann Ihr benutzerdefiniertes broadLogRcp-Schema und wählen Sie es aus. Wenn Sie das integrierte Versandlog-Schema noch nicht erweitert haben, lesen Sie den Abschnitt [dieses Verfahrens](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Fügen Sie dasselbe benutzerdefinierte Feld wie das Empfängerschema zum Schema-Editor hinzu.

   ![](assets/custom_field_3.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Starten Sie den Datenbankaktualisierungs-Assistenten über **[!UICONTROL Instrumente]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Datenbankstruktur aktualisieren]** und führen Sie die Option Datenbankstruktur aktualisieren aus. [Weitere Informationen](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/update-database-structure)

   ![](assets/custom_field_4.png)

Ihr neues Profilfeld kann jetzt verwendet und von Empfängern ausgewählt werden.

## Schritt 2: Verknüpfen Sie Ihr neues benutzerdefiniertes Feld {#link-custom}

>[!NOTE]
>
> Sie können dem dynamischen Bericht nur bis zu 20 benutzerdefinierte Felder hinzufügen.

Nachdem Sie Ihr Profilfeld erstellt haben, müssen wir es mit der entsprechenden Dimension für dynamische Berichte verknüpfen.

1. Navigieren Sie zum **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Datenschemata]** > **[!UICONTROL Zusätzliches Berichtsfeld]** im Explorer angezeigt.

   ![](assets/custom_field_5.png)

1. Klicks **[!UICONTROL Neu]** , um Ihre entsprechende dynamische Berichtsdimension zu erstellen.

1. Auswählen **[!UICONTROL Ausdruck bearbeiten]** und durchsuchen Sie das Schema Empfänger , um das zuvor erstellte benutzerdefinierte Profilfeld zu finden.

   ![](assets/custom_field_6.png)

1. Klicken Sie auf **[!UICONTROL Fertigstellen]**.

1. Eingeben Ihrer Dimension **[!UICONTROL Titel]**, in dynamischen Berichten angezeigt werden, und klicken Sie auf **[!UICONTROL Speichern]**.

   ![](assets/custom_field_7.png)

Ihr benutzerdefiniertes Profilfeld ist jetzt als benutzerdefinierte Profildimension in Ihren Berichten verfügbar. Um Ihre benutzerdefinierte Profildimension zu löschen, können Sie sie auswählen und auf das **[!UICONTROL Löschen]** Symbol.

Nachdem das Empfängerschema mit diesem Profilfeld erweitert und Ihre benutzerdefinierte Dimension erstellt wurde, können Sie mit der Zielgruppenbestimmung von Empfängern in Sendungen beginnen.

## Schritt 3: Erstellen Sie einen dynamischen Bericht, um Empfänger mithilfe der benutzerdefinierten Profildimension zu filtern. {#create-report}

Nach dem Versand Ihrer Nachricht können Sie die Berichte mithilfe Ihrer benutzerdefinierten Profildimension aufschlüsseln.

1. Wählen Sie im Tab **[!UICONTROL Berichte]** einen vordefinierten Bericht oder die Schaltfläche **[!UICONTROL Erstellen]**, um einen neuen Bericht zu erstellen.

   ![](assets/custom_field_8.png)

1. Im **[!UICONTROL Dimensionen]** category, click **[!UICONTROL Profil]** Ziehen Sie dann Ihre benutzerdefinierte Profildimension in Ihre Freiformtabelle.

   ![](assets/custom_field_9.png)

1. Ziehen Sie Metriken per Drag-and-Drop in den Arbeitsbereich, um Ihre Daten zu filtern.

1. Ziehen Sie bei Bedarf ein Visualisierungselement in den Arbeitsbereich.
