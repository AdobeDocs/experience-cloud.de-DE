---
title: Profildimension erstellen
description: Erfahren Sie, wie Sie eine Profildimension basierend auf Profildaten erstellen.
audience: reporting
content-type: reference
level: Intermediate
exl-id: a12dc772-13c7-45ff-9fbf-3dfdd3801eae
source-git-commit: 5da9b29c424f019f3dafc127a41e974017af494c
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 12%

---

# Profildimension erstellen{#creating-a-custom-profile-dimension}

Berichte können auch basierend auf Profildaten erstellt und verwaltet werden, die während der Erweiterung des Empfängerschemas erstellt wurden.

* [Schritt 1: Erweiterung des Empfängerschemas](##extend-schema)
* [Schritt 2: Verknüpfen Sie Ihr neues benutzerdefiniertes Feld](#link-custom)
* [Schritt 3: Erstellen Sie einen dynamischen Bericht, um Empfänger mit der Profildimension zu filtern](#create-report)

## Schritt 1: Erweiterung des Empfängerschemas {#extend-schema}

Gehen Sie wie folgt vor, um ein neues Profilfeld hinzuzufügen:

1. Navigieren Sie im Explorer zum Ordner **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Datenschemata]** .

   ![](assets/custom_field_1.png)

1. Identifizieren Sie das benutzerdefinierte Empfängerschema und wählen Sie es aus. Wenn Sie das integrierte Schema nms:recipient noch nicht erweitert haben, lesen Sie [dieses Verfahren](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Fügen Sie das benutzerdefinierte Feld zum Schema-Editor hinzu.

   So fügen Sie beispielsweise ein benutzerdefiniertes Treuefeld in Ihr Empfängerschema ein:

   ```
   <attribute label="Loyalty" name="loyalty" type="string"/>
   ```

   ![](assets/custom_field_2.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Identifizieren Sie dann Ihr benutzerdefiniertes broadLogRcp-Schema und wählen Sie es aus. Wenn Sie das integrierte Versandlog-Schema noch nicht erweitert haben, lesen Sie [dieses Verfahren](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Fügen Sie dasselbe benutzerdefinierte Feld wie das Empfängerschema zum Schema-Editor hinzu.

   ![](assets/custom_field_3.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Um die Änderungen an den Schemas anzuwenden, starten Sie den Datenbankaktualisierungs-Assistenten über **[!UICONTROL Tools]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Datenbankstruktur aktualisieren]** und führen Sie die Option Datenbankstruktur aktualisieren aus. [Weitere Informationen](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/shemas-forms/update-database-structure)

   ![](assets/custom_field_4.png)

Ihr neues Profilfeld kann jetzt verwendet und von Empfängern ausgewählt werden.

## Schritt 2: Verknüpfen Sie Ihr neues benutzerdefiniertes Feld {#link-custom}

>[!NOTE]
>
> Sie können dem dynamischen Bericht nur bis zu 20 benutzerdefinierte Felder hinzufügen.

Nachdem Sie Ihr Profilfeld erstellt haben, müssen wir es mit der entsprechenden Dimension für dynamische Berichte verknüpfen.

Bevor Sie das Protokoll mit unserem Profilfeld erweitern, müssen Sie sicherstellen, dass das PII-Fenster akzeptiert wurde, um personenbezogene Daten an dynamische Berichte senden zu können. Weiterführende Informationen hierzu finden Sie auf [dieser Seite](pii-agreement.md).

1. Navigieren Sie im Explorer zum Ordner **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Datenschemata]** > **[!UICONTROL Zusätzliches Berichtsfeld]** .

   ![](assets/custom_field_5.png)

1. Klicken Sie auf **[!UICONTROL Neu]** , um die entsprechende dynamische Berichtsdimension zu erstellen.

1. Wählen Sie **[!UICONTROL Ausdruck bearbeiten]** und durchsuchen Sie das Empfängerschema, um das zuvor erstellte Profilfeld zu finden.

   ![](assets/custom_field_6.png)

1. Klicken Sie auf **[!UICONTROL Fertigstellen]**.

1. Geben Sie Ihre Dimension **[!UICONTROL Beschriftung]** ein, die in dynamischen Berichten angezeigt wird, und klicken Sie auf **[!UICONTROL Speichern]**.

   ![](assets/custom_field_7.png)

Ihr Profilfeld ist jetzt als Profildimension in Ihren Berichten verfügbar. Um Ihre Profildimension zu löschen, können Sie sie auswählen und auf das Symbol **[!UICONTROL Löschen]** klicken.

Nachdem das Empfängerschema mit diesem Profilfeld erweitert und Ihre benutzerdefinierte Dimension erstellt wurde, können Sie mit der Zielgruppenbestimmung von Empfängern in Sendungen beginnen.

## Schritt 3: Erstellen Sie einen dynamischen Bericht, um Empfänger mit der Profildimension zu filtern {#create-report}

Nach dem Versand Ihrer Nachricht können Sie die Berichte anhand Ihrer Profildimension aufschlüsseln.

1. Wählen Sie im Tab **[!UICONTROL Berichte]** einen vordefinierten Bericht oder die Schaltfläche **[!UICONTROL Erstellen]**, um einen neuen Bericht zu erstellen.

   ![](assets/custom_field_8.png)

1. Klicken Sie in der Kategorie **[!UICONTROL Dimensionen]** auf **[!UICONTROL Profil]** und ziehen Sie dann Ihre Profildimension in Ihre Freiformtabelle.

   ![](assets/custom_field_9.png)

1. Ziehen Sie Metriken per Drag-and-Drop in den Arbeitsbereich, um Ihre Daten zu filtern.

1. Ziehen Sie bei Bedarf ein Visualisierungselement in den Arbeitsbereich.

