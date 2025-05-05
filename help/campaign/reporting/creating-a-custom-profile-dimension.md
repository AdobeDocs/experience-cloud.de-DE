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

Berichte können auch basierend auf Profildaten, die während der Erweiterung des Empfängerschemas erstellt wurden, erstellt und verwaltet werden.

* [Schritt 1: Empfängerschema erweitern](##extend-schema)
* [Schritt 2: Verknüpfen des neuen benutzerdefinierten Felds](#link-custom)
* [Schritt 3: Dynamischen Bericht erstellen, um Empfänger mit der Profildimension zu filtern](#create-report)

## Schritt 1: Empfängerschema erweitern {#extend-schema}

Um ein neues Profilfeld hinzuzufügen, müssen Sie Ihr Schema erweitern, gehen Sie wie folgt vor:

1. Navigieren Sie im **[!UICONTROL zum Ordner]** Administration **[!UICONTROL > Konfiguration]** > **[!UICONTROL Datenschemata]** .

   ![](assets/custom_field_1.png)

1. Identifizieren Sie das benutzerdefinierte Empfängerschema und wählen Sie es aus. Wenn Sie das integrierte Schema nms:recipient noch nicht erweitert haben, lesen Sie [dieses Verfahren](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Fügen Sie das benutzerdefinierte Feld zum Schema-Editor hinzu.

   So fügen Sie beispielsweise ein benutzerdefiniertes Feld Treue in Ihrem Empfängerschema hinzu:

   ```
   <attribute label="Loyalty" name="loyalty" type="string"/>
   ```

   ![](assets/custom_field_2.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Identifizieren Sie dann Ihr benutzerdefiniertes broadLogRcp-Schema und wählen Sie es aus. Wenn Sie das integrierte Versandlog-Schema noch nicht erweitert haben, lesen Sie [dieses Verfahren](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/developer/shemas-forms/extend-schema).

1. Fügen Sie dem Schema-Editor dasselbe benutzerdefinierte Feld wie Ihr Empfängerschema hinzu.

   ![](assets/custom_field_3.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Um die an den Schemata vorgenommenen Änderungen anzuwenden, starten Sie den Datenbankaktualisierungs-Assistenten über **[!UICONTROL Tools]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Datenbankstruktur aktualisieren]** und führen Sie das Update der Datenbankstruktur aus. [Weitere Informationen](https://experienceleague.adobe.com/de/docs/campaign/campaign-v8/developer/shemas-forms/update-database-structure)

   ![](assets/custom_field_4.png)

Ihr neues Profilfeld kann jetzt verwendet und von Empfängern ausgewählt werden.

## Schritt 2: Verknüpfen des neuen benutzerdefinierten Felds {#link-custom}

>[!NOTE]
>
> Sie können nur bis zu 20 benutzerdefinierte Felder zu dynamischen Berichten hinzufügen.

Nachdem Ihr Profilfeld erstellt wurde, müssen wir es mit der entsprechenden Dimension für dynamische Berichte verknüpfen.

Bevor Sie das Protokoll mit unserem Profilfeld erweitern, stellen Sie sicher, dass das PII-Fenster akzeptiert wurde, um PII-Daten an einen dynamischen Bericht senden zu können. Weiterführende Informationen hierzu finden Sie auf [dieser Seite](pii-agreement.md).

1. Navigieren Sie im Explorer zum Ordner **[!UICONTROL Administration]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Datenschemata]** > **[!UICONTROL Zusätzliches]**).

   ![](assets/custom_field_5.png)

1. Klicken Sie **[!UICONTROL Neu]**, um die entsprechende Dimension für dynamische Berichte zu erstellen.

1. Wählen Sie **[!UICONTROL Ausdruck bearbeiten]** aus und durchsuchen Sie das Empfängerschema, um Ihr zuvor erstelltes Profilfeld zu finden.

   ![](assets/custom_field_6.png)

1. Klicken Sie auf **[!UICONTROL Fertigstellen]**.

1. Geben Sie Ihre Dimension (**[!UICONTROL ) ein]** die in dynamischen Berichten sichtbar ist, und klicken Sie auf **[!UICONTROL Speichern]**.

   ![](assets/custom_field_7.png)

Ihr Profilfeld ist jetzt als Profildimension in Ihren Berichten verfügbar. Um Ihre Profildimension zu löschen, können Sie sie auswählen und auf das Symbol **[!UICONTROL Löschen]** klicken.

Nachdem das Empfängerschema nun um dieses Profilfeld erweitert und Ihre benutzerdefinierte Dimension erstellt wurde, können Sie in Sendungen beginnen, Empfänger anzusprechen.

## Schritt 3: Dynamischen Bericht erstellen, um Empfänger mit der Profildimension zu filtern {#create-report}

Nach dem Versand können Sie Berichte mithilfe Ihrer Profildimension aufschlüsseln.

1. Wählen Sie im Tab **[!UICONTROL Berichte]** einen vordefinierten Bericht oder die Schaltfläche **[!UICONTROL Erstellen]**, um einen neuen Bericht zu erstellen.

   ![](assets/custom_field_8.png)

1. Klicken Sie in der **&#x200B;**&#x200B;Dimensionen auf **[!UICONTROL Profil]** und ziehen Sie Ihre Profildimension per Drag-and-Drop in Ihre Freiformtabelle.

   ![](assets/custom_field_9.png)

1. Ziehen Sie beliebige Metriken per Drag-and-Drop, um Ihre Daten zu filtern.

1. Ziehen Sie bei Bedarf ein Visualisierungselement in den Arbeitsbereich.

