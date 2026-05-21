---
title: Erste Schritte mit dynamischen Berichten
description: Weitere Informationen zur Nutzungsvereinbarung zu dynamischen Berichten
level: Beginner
badge: label="EINGESCHRÄNKTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzende beschränkt"
audience: end-user
exl-id: 9fcef466-f306-480e-b42e-d18daa8bcf06
TQID: https://experienceleague.adobe.com/AGXqq-XOQU8SmHobDIA-nZqw3eNSa2THnw2jQQP54YA
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
feature_v2: id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 549
ht-degree: 86%

---

# Nutzungsvereinbarung zur dynamischen Berichterstattung {#pii-agreement}

Die Nutzungsvereinbarung zur dynamischen Berichterstattung wird als Popup angezeigt und ermöglicht die Zustimmung zur Datenverarbeitung. Standardmäßig ist diese Vereinbarung nur für Benutzer mit Administratorrechten sichtbar und kann auch nur durch diese akzeptiert oder abgelehnt werden.

Um auf die Nutzungsvereinbarung zu dynamischen Berichten zuzugreifen, wählen Sie **[!UICONTROL Werkzeuge]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Bereitstellungsassistent]** aus.

![](assets/pii-agreement.png)

Drei Optionen stehen zur Wahl:

* **[!UICONTROL Später fragen]**: Bis Sie der Vereinbarung zustimmen oder diese ablehnen, werden die Profildimensionen nicht in Ihren Berichten angezeigt und die personenbezogenen Daten Ihrer Kundinnen und Kunden werden weder erfasst noch gesendet.
* **[!UICONTROL Annehmen]**: Wenn Sie die Nutzungsvereinbarung akzeptieren, gestatten Sie Adobe Campaign, personenbezogene Daten Ihrer Kunden zu erfassen und zum Reporting- oder Rechenzentrum zu übertragen.
* **[!UICONTROL Ablehnen]**: Wenn Sie die Nutzungsvereinbarung ablehnen, erscheinen die Profildimensionen nicht in Ihren Berichten und personenbezogene Daten Ihrer Kunden werden weder erfasst noch übertragen. Beachten Sie, dass in diesem Fall die externe Kennung dennoch erfasst und zur Identifizierung der Endbenutzer verwendet wird.

Die nachstehende Tabelle zeigt, was nach der Annahme dieser Vereinbarung je nach Region geschieht.

|  | Dynamisches Reporting | Microsoft Dynamics 365 Connector |
|---|---|---|
| Amerika und APAC (Asien/Pazifik) | **Funktion verfügbar** <br>Alle nativen Profildaten (d. h. Stadt, Land/Region, Bundesland, Geschlecht und Segmente auf der Grundlage des Alters) sowie benutzerdefinierten Profildaten werden an das US-Berichtszentrum gesendet. | **Funktion verfügbar** <br>Alle nativen und benutzerdefinierten Profilfelder sowie Ereignisfelder von Adobe Campaign werden im US-Rechenzentrum verarbeitet. |
| EMEA (Europa, Naher Osten und Afrika) | **Funktion verfügbar** <br>Alle nativen Profildaten (d. h. Stadt, Land/Region, Bundesland, Geschlecht und Segmente auf der Grundlage des Alters) sowie benutzerdefinierten Profildaten werden an das EMEA-Berichtszentrum gesendet. | **Funktion verfügbar.** <br>Alle vordefinierten und benutzerdefinierten Profilfelder und Adobe Campaign-Ereignisfelder, die im EMEA-Rechenzentrum verarbeitet werden. <br>**[!UICONTROL Kontrolldaten ]**, in denen Adobe I/O-Registrierungsdaten und Kennungen von Endbenutzerereignissen enthalten sind, werden zum US-Rechenzentrum gesendet und dort gespeichert. |

Die nachstehende Tabelle zeigt, was nach der Ablehnung dieser Vereinbarung je nach Region geschieht. Beachten Sie, dass auch dann Berichte zu Sendungen und der Microsoft Dynamics 365-Integration verfügbar sind, wenn Sie diese Vereinbarung ablehnen.

| Region | Dynamisches Reporting | Microsoft Dynamics 365 Connector |
|---|---|---|
| Amerika und APAC (Asien/Pazifik) | **Funktion verfügbar**. <br> Keine vordefinierten und benutzerdefinierten Profilinformationen, die in das US-Reporting-Center verschoben werden, mit Ausnahme von ExternalID. | **Funktion verfügbar** <br>Es werden keine nativen und benutzerdefinierten Profilfelder an das US-Rechenzentrum gesendet, mit Ausnahme der externen Kennung und der Empfänger-ID. <br>Alle Ereignisfelder von Adobe Campaign werden im US-Rechenzentrum verarbeitet, mit Ausnahme der Mirrorseiten-ID. |
| EMEA (Europa, Naher Osten und Afrika) | **Funktion verfügbar** <br>Es werden keine nativen und benutzerdefinierten Profildaten an das Reporting-Zentrum in EMEA gesendet, mit Ausnahme der externen Kennung. | **Funktion verfügbar.** <br>Keine vordefinierten oder benutzerdefinierten Profilfelder, die an das EMEA-Rechenzentrum gesendet werden, mit Ausnahme der externen ID und der Empfänger-ID. <br>Alle Ereignisfelder von Adobe Campaign werden im EMEA-Rechenzentrum verarbeitet, mit Ausnahme der Mirrorseiten-ID. |

Diese Auswahl ist nicht endgültig. Sie können sie jederzeit ändern, indem Sie die Option **[!UICONTROL realtimeReporting_collectPII]** unter **[!UICONTROL Administration]** > **[!UICONTROL Plattform]** > **[!UICONTROL Optionen]** auswählen.

Der Wert kann jederzeit geändert werden. Der Wert 1 bedeutet **[!UICONTROL Später fragen]**, 2 bedeutet **[!UICONTROL Ablehnen]** und 3 bedeutet **[!UICONTROL Annehmen]**.
