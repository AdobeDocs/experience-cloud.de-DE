---
title: Erstellen und Verwalten von Experience Cloud Triggers
description: Entdecken Sie die Benutzeroberfläche von Adobe Experience Cloud Triggers
hide: true
hidefromtoc: true
source-git-commit: ce0faf9fab45c931feb666ac0c77f5ab5c231746
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 27%

---

# Experience Cloud Trigger erstellen {#create-triggers}

>[!NOTE]
>
> Die neue Benutzeroberfläche für Experience Cloud-Trigger bietet ein intuitives Erlebnis für die Verwaltung von Verbraucherverhaltensweisen und die Personalisierung von Benutzererlebnissen. Um zur vorherigen Benutzeroberfläche zurückzukehren, klicken Sie auf das **[!UICONTROL Zum klassischen Modus wechseln]** Schaltfläche.

Erstellen Sie einen Trigger und konfigurieren Sie die Bedingungen für den Trigger. Sie können beispielsweise die Kriterien für die Regeln eines Triggers während eines Besuchs angeben, z. B. Metriken wie Warenkorbabbruch oder Dimensionen wie den Produktnamen. Wenn die Regeln erfüllt sind, wird der Trigger ausgeführt.

1. Wählen Sie im Experience Cloud das erweiterte Menü und dann Trigger aus.

   ![](assets/triggers_7.png)

1. Klicken Sie auf Ihrer Trigger-Homepage auf **[!UICONTROL Trigger erstellen]** und geben Sie dann den Typ des Triggers an.

   Es stehen drei Typen von Triggern zur Verfügung:

   * **[!UICONTROL Abbruch]**: Sie können einen Trigger erstellen, der ausgelöst wird, wenn ein Besucher ein Produkt anzeigt, es jedoch nicht zum Warenkorb hinzufügt.

   * **[!UICONTROL Aktion]**: Sie können beispielsweise Trigger erstellen, die nach der Newsletter-Anmeldung, E-Mail-Abonnements oder Kreditkartenanträgen (Bestätigungen) ausgelöst werden. Wenn Sie ein Händler sind, können Sie einen Trigger für einen Besucher erstellen, der sich für ein Treueprogramm anmeldet. Erstellen Sie in Medien und Unterhaltung Trigger für Besucher, die eine bestimmte Sendung ansehen. Sie können auch mit einer Umfrage reagieren.

   * **[!UICONTROL Sitzungsbeginn und Sitzungsende]**: Erstellen Sie einen Trigger für die Sitzungsbeginn- und Sitzungsende-Ereignisse.

   ![](assets/triggers_1.png)

1. Hinzufügen einer **[!UICONTROL Name]** und **[!UICONTROL Beschreibung]** auf Ihren Trigger.

1. Analytics auswählen **[!UICONTROL Report Suite]** verwendet für diesen Trigger. Diese Einstellung identifiziert die zu verwendenden Berichtsdaten.

   [Weitere Informationen zu Report Suites](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/c-new-report-suite/t-create-a-report-suite.html?lang=de).

1. Wählen Sie die **[!UICONTROL Trigger nach ausbleibender Aktion für]** Gültigkeitsdauer.

1. Aus dem **[!UICONTROL Besuch muss beinhalten]** und **[!UICONTROL Besuch darf nicht beinhalten]** -Kategorien können Sie Kriterien oder das Besucherverhalten definieren, die auftreten sollen oder die nicht auftreten sollen. Sie können **und** oder **Oder** -Logik innerhalb oder zwischen Bedingungen, je nach den von Ihnen festgelegten Kriterien.

   Regeln für einen einfachen Warenkorbabbruchs-Trigger können beispielsweise die folgenden sein:

   * **[!UICONTROL Besuch muss beinhalten]**: `Carts (metric) Is greater or equal to 1` , um Besucher mit mindestens einem Artikel in ihrem Warenkorb anzusprechen.
   * **[!UICONTROL Besuch darf nicht beinhalten]**: `Checkout (metric) Exists.` um Besucher zu entfernen, die die Artikel in ihrem Warenkorb gekauft haben.

   ![](assets/triggers_2.png)

1. Klicken **[!UICONTROL Container]** , um Regeln, Bedingungen oder Filter zu erstellen und zu speichern, die einen Trigger definieren. Damit Ereignisse gleichzeitig auftreten, sollten Sie sie im selben Container platzieren.

   Jeder Container wird unabhängig auf der Trefferebene verarbeitet, d. h. wenn zwei Behälter mit der **[!UICONTROL und]** -Operator verwenden, werden die Regeln nur qualifiziert, wenn zwei Treffer die Anforderungen erfüllen.

1. Aus dem **[!UICONTROL Metadaten]** Feld, klicken Sie auf **[!UICONTROL + Dimension]** zur Auswahl einer bestimmten Kampagnendimension oder von Variablen, die für das Verhalten eines Besuchers relevant sind.

   ![](assets/triggers_3.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Wählen Sie die neu erstellte **[!UICONTROL Trigger]** aus der Liste, um auf den Detailbericht Ihres Triggers zuzugreifen.

   ![](assets/triggers_4.png)

1. Über die Detailansicht Ihres Triggers können Sie auf Berichte zugreifen, in denen beschrieben wird, wie viele Trigger ausgelöst wurden. Bei Bedarf können Sie Ihren Trigger mit dem Stiftsymbol bearbeiten.

   ![](assets/triggers_5.png)
