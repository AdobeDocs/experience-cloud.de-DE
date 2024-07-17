---
title: Branding
description: Entdecken Sie alle verfügbaren Tools zum Verwalten Ihrer Markenidentitäten
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="BEGRENZTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzer beschränkt"
exl-id: f6438303-5ae8-47c6-8c34-8e586f4b6fe7
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 54%

---

# Erste Schritte mit Branding {#branding-gs}

>[!IMPORTANT]
>
>Marken können nicht vom Endnutzer erstellt oder geändert werden. Diese Aktionen müssen von einem technischen Adobe-Campaign-Administrator vorgenommen werden. Bei Fragen wenden Sie sich an die Adobe-Kundenunterstützung.

Jedes Unternehmen verfügt über Markenrichtlinien, die sowohl visuelle Elemente als auch technische Details definieren. Adobe Campaign unterstützt Sie bei der zentralen Verwaltung dieser Richtlinien, sodass Sie Ihren Kunden ein einheitliches Markenbild präsentieren können - von Logos in E-Mails bis hin zu den URLs und Domänen, die in Ihren Kampagnen verwendet werden.

Technische Administratoren können innerhalb von Adobe Campaign mehrere Marken erstellen und verwalten. Auf diese Weise können Sie alle Elemente Ihrer Markenidentität definieren, einschließlich Logos und sogar E-Mail-Tracking-Einstellungen. Nach der Erstellung können diese Marken einfach mit Ihren Sendungen verknüpft werden.

Sie können in Campaign neue Entitäten Ihrer Organisation hinzufügen oder einen neuen E-Mail-Typ erstellen, den Sie unter einer anderen Subdomain senden müssen. Gehen Sie dazu wie folgt vor:

1. **Neue Subdomain konfigurieren**: Damit eine neue Subdomain von Adobe verwendet werden kann, müssen Sie sie zunächst konfigurieren. Sie können dies über das [Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/subdomains-branding.html?lang=de) in Campaign durchführen oder sich an Ihren technischen Ansprechpartner bei Adobe wenden. Weitere Informationen zur Subdomain-Konfiguration [finden Sie auf dieser Seite](https://experienceleague.adobe.com/en/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/ac-domain-name-setup).

   >[!NOTE]
   >
   >Das Control Panel steht allen Administratoren zur Verfügung. Die Schritte, um einem Benutzer Administratorzugriff zu gewähren, finden Sie auf [dieser Seite](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=de#discover-control-panel).

1. **Versandvorlage erstellen**: Sobald die neue Marke verfügbar ist, sollten Sie mindestens eine neue leere Versandvorlage erstellen, die auf diese neue Marke verweist. [Weitere Informationen](branding-assign.md).

1. **Zustellbarkeitsrichtlinien prüfen**: Bevor Sie mit der Verwendung der neuen Domain beginnen, sollte die Strategie mit dem Adobe Zustellbarkeits-Team besprochen werden. Sie helfen bei der Definition der Best Practices, wenn eine neue Affinität erstellt werden soll, um beispielsweise die IPs zwischen Domänen zu unterteilen, und/oder wenn ein Hochlaufplan definiert werden soll.
