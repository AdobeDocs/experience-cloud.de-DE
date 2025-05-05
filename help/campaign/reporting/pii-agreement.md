---
title: Erste Schritte mit dynamischen Berichten
description: Weitere Informationen zur Nutzungsvereinbarung für dynamische Berichte
level: Beginner
badge: label="EINGESCHRÄNKTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierter Benutzer beschränkt"
audience: end-user
exl-id: 9fcef466-f306-480e-b42e-d18daa8bcf06
source-git-commit: dbdf1c4f8b676c73a7cc3a46af2838ebb9326457
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 63%

---

# Nutzungsvereinbarung zur dynamischen Berichterstattung {#pii-agreement}

Die Nutzungsvereinbarung zur dynamischen Berichterstattung wird als Popup angezeigt und ermöglicht die Zustimmung zur Datenverarbeitung. Standardmäßig ist diese Vereinbarung nur für Benutzer mit Administratorrechten sichtbar und kann auch nur durch diese akzeptiert oder abgelehnt werden.

Um auf die Nutzungsvereinbarung zur dynamischen Berichterstellung zuzugreifen, wählen Sie **[!UICONTROL Tools]** > **[!UICONTROL Erweitert]** > **[!UICONTROL Bereitstellungsassistent]**.

![](assets/pii-agreement.png)

Drei Optionen stehen zur Wahl:

* **[!UICONTROL Später nachfragen]**: Bis Sie die Vereinbarung akzeptieren oder ablehnen, werden die Profildimensionen nicht in Ihren Berichten angezeigt und die persönlichen Identifizierungsinformationen Ihrer Kunden werden nicht erfasst oder gesendet.
* **[!UICONTROL Annehmen]**: Wenn Sie die Nutzungsvereinbarung akzeptieren, gestatten Sie Adobe Campaign, personenbezogene Daten Ihrer Kunden zu erfassen und zum Reporting- oder Rechenzentrum zu übertragen.
* **[!UICONTROL Ablehnen]**: Wenn Sie die Nutzungsvereinbarung ablehnen, erscheinen die Profildimensionen nicht in Ihren Berichten und personenbezogene Daten Ihrer Kunden werden weder erfasst noch übertragen. Beachten Sie, dass in diesem Fall die externe Kennung dennoch erfasst und zur Identifizierung der Endbenutzer verwendet wird.

Die nachstehende Tabelle zeigt, was nach der Annahme dieser Vereinbarung je nach Region geschieht.

|  | Dynamische Berichterstellung | Microsoft Dynamics 365 Connector |
|---|---|---|
| Amerika und APAC (Asien/Pazifik) | **Funktion verfügbar** <br>Alle vorkonfigurierten (d. h. Stadt, Land/Region, Bundesland, Geschlecht und Segmente auf Altersbasis) und benutzerdefinierte Profilinformationen, die in das US-Berichtszentrum gesendet werden. | **Funktion verfügbar** <br>Alle vordefinierten und benutzerdefinierten Profilfelder und Adobe Campaign-Ereignisfelder werden im US-Rechenzentrum verarbeitet. |
| EMEA (Europa, Naher Osten und Afrika) | **Funktion verfügbar** <br>Alle vorkonfigurierten (d. h. Stadt, Land/Region, Bundesland, Geschlecht und Segmente auf Altersbasis) und benutzerdefinierten Profilinformationen, die in das EMEA-Berichtszentrum übertragen werden. | **Funktion verfügbar** <br>Alle vordefinierten und benutzerdefinierten Profilfelder und Adobe Campaign-Ereignisfelder, die im EMEA-Rechenzentrum verarbeitet werden. <br>**[!UICONTROL Kontrolldaten &#x200B;]**, in denen Adobe I/O-Registrierungsdaten und Kennungen von Endbenutzerereignissen enthalten sind, werden zum US-Rechenzentrum gesendet und dort gespeichert. |

Die nachstehende Tabelle zeigt, was nach der Ablehnung dieser Vereinbarung je nach Region geschieht. Beachten Sie, dass auch dann Berichte zu Sendungen und der Microsoft Dynamics 365-Integration verfügbar sind, wenn Sie diese Vereinbarung ablehnen.

| Region | Dynamische Berichterstellung | Microsoft Dynamics 365 Connector |
|---|---|---|
| Amerika und APAC (Asien/Pazifik) | **Funktion verfügbar** <br>Es werden keine nativen und benutzerdefinierten Profildaten an das Reporting-Zentrum in den USA gesendet, mit Ausnahme der externen Kennung. | **Funktion verfügbar** <br>Es werden keine nativen und benutzerdefinierten Profilfelder an das US-Rechenzentrum gesendet, mit Ausnahme der externen Kennung und der Empfänger-ID. <br>Alle Adobe Campaign-Ereignisfelder, die im US-Rechenzentrum verarbeitet werden, mit Ausnahme der Mirrorseiten-ID. |
| EMEA (Europa, Naher Osten und Afrika) | **Funktion verfügbar** <br>Es werden keine nativen und benutzerdefinierten Profildaten an das Reporting-Zentrum in EMEA gesendet, mit Ausnahme der externen Kennung. | **Funktion verfügbar** <br>Es werden keine nativen und benutzerdefinierten Profilfelder an das EMEA-Rechenzentrum gesendet, mit Ausnahme der externen Kennung und der Empfänger-ID. <br>Alle Adobe Campaign-Ereignisfelder, die im EMEA-Rechenzentrum verarbeitet werden, mit Ausnahme der Mirrorseiten-ID. |

Diese Auswahl ist nicht endgültig. Sie können sie jederzeit ändern, indem Sie die Option **[!UICONTROL realtimeReporting_collectPII]** unter **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** auswählen.

Der Wert kann jederzeit geändert werden. Der Wert 1 bedeutet **[!UICONTROL Später fragen]**, 2 bedeutet **[!UICONTROL Ablehnen]** und 3 bedeutet **[!UICONTROL Annehmen]**.
