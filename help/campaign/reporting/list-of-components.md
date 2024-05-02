---
title: Komponentenliste
description: Hier finden Sie die Liste der in dynamischen Berichten enthaltenen Komponenten sowie ihre Definitionen.
level: Beginner
audience: end-user
badge: label="BEGRENZTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzer beschränkt"
source-git-commit: b11d696767209145511b38735f22275a38676ade
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 94%

---

# Komponentenliste {#list-of-components}

Beachten Sie, dass die Zelle den Wert anzeigt, wenn zwei Komponenten nicht kompatibel sind **Keines**.

## Dimensionen {#dimensions}

In der Tabelle unten finden Sie die Liste der Dimensionen, die in Berichten verwendet werden, sowie ihre Definitionen.

<table> 
 <thead> 
  <tr> 
   <th> Dimension<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Browser<br/> </td> 
   <td> Browser, in dem die Nachricht geöffnet oder angeklickt wurde<br/> </td> 
  </tr> 
  <tr> 
   <td> Campaign<br/> </td> 
   <td> Titel und Kennung Ihrer Kampagne<br/> </td> 
  </tr> 
  <tr> 
   <td> Versand<br/> </td> 
   <td> Titel und Kennung des Versands<br/> </td> 
  </tr> 
  <tr> 
   <td> Gerät<br/> </td> 
   <td> Gerät, auf dem die E-Mail/SMS/Push-Benachrichtigung geöffnet/angesehen/angeklickt wurde.<br/> </td> 
  </tr> 
  <tr> 
   <td> Grund des Fehlschlagens<br/> </td> 
   <td> Fehlertypen, die bei jedem Versand zu Bounces führten, z. B. unbekannte Nutzer, ungültige Domain oder Postfach voll.<br/> </td> 
  </tr> 
  <tr> 
   <td> Name der Mobile App<br/> </td> 
   <td> Name der Mobile App<br/> </td> 
  </tr>
  <tr> 
   <td> Plattform<br/> </td> 
   <td> Plattform des Geräts, auf dem die Nachricht geöffnet/angesehen/angeklickt wurde<br/> </td> 
  </tr> 
  <tr> 
   <td> Profil<br/> </td> 
   <td> Fasst native und benutzerdefinierte Profilfelder zusammen, die während der Erweiterung der Profilressource erstellt wurden.<br/> </td> 
  </tr> 
  <tr> 
   <td> Empfänger-Domain<br/> </td> 
   <td> Die zum Öffnen der E-Mail verwendete Domain<br/> </td> 
  </tr> 
  <tr> 
   <td> Wiederkehrender Versand<br/> </td> 
   <td> Titel und Kennung des wiederkehrenden Versands<br/> </td> 
  </tr> 
  <tr> 
   <td> Absender-Domain<br/> </td> 
   <td> Die zum Senden der E-Mail verwendete Domain<br/> </td> 
  </tr> 
  <tr> 
   <td> Absender-IP<br/> </td> 
   <td> Die zum Senden der E-Mail verwendete IP<br/> </td> 
  </tr> 
  <tr> 
   <td> Tracking-URL<br/> </td> 
   <td> URL, die der Benutzer in der Nachricht angeklickt hat<br/> </td> 
  </tr> 
  <tr> 
   <td> Kategorie des URL-Trackings<br/> </td> 
   <td> Die der Tracking-URL zugewiesene Kategorie<br/> </td> 
  </tr> 
  <tr> 
   <td> Titel des URL-Trackings<br/> </td> 
   <td> Der an die URL vergebene Titel, wie "Mirrorseite", "Kontakt" oder "Öffnung".<br/> </td> 
  </tr> 
  <tr> 
   <td> Versand von Transaktionsnachrichten<br/> </td> 
   <td> Titel und Kennung des Transaktionsnachrichtenversands<br/> </td> 
  </tr> 
  <tr> 
   <td> Variante<br/> </td> 
   <td> Variante der E-Mail im Fall von A/B-Tests<br/> </td> 
  </tr> 
 </tbody> 
</table>

## Metriken {#metrics}

In den Tabellen unten finden Sie nach Versandtyp geordnet die Liste der Metriken, die in Berichten verwendet werden, sowie ihre Definitionen.

### Email-Metriken {#email-and-sms-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Metrik<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Auf Blockierungsliste<br/> </td> 
   <td> Anzahl der Empfänger, die eine E-Mail als Spam oder Junk gekennzeichnet haben<br/> </td> 
  </tr> 
  <tr> 
   <td> Blockierungslistenrate<br/> </td> 
   <td> Prozentsatz der Sendungen, die auf einer Blockierungsliste markiert sind.<br/> </td> 
  </tr> 
  <tr> 
   <td> Bounces + Fehler<br/> </td> 
   <td> Gesamtzahl der kumulierten Fehler bei Versand und automatischer Bounce-Verarbeitung im Verhältnis zur Gesamtzahl der gesendeten Nachrichten.<br/> </td> 
  </tr> 
  <tr> 
   <td> Bounce + Fehlerrate<br/> </td> 
   <td> Prozentsatz der Bounce-E-Mails in Bezug auf die gesendeten E-Mails<br/> </td> 
  </tr> 
  <tr> 
   <td> Klicks<br/> </td> 
   <td> Die Anzahl der Klicks auf einen Inhalt in einem Versand.<br/> </td> 
  </tr> 
  <tr> 
   <td> Klickrate<br/> </td> 
   <td> Prozentsatz der Klicks in einem Versand<br/> </td> 
  </tr> 
  <tr> 
   <td> Zugestellt<br/> </td> 
   <td> Zahl der erfolgreich gesendeten Nachrichten im Verhältnis zur Gesamtzahl der gesendeten Nachrichten.<br/> </td> 
  </tr> 
  <tr> 
   <td> Zustellrate<br/> </td> 
   <td> Prozentsatz der erfolgreich gesendeten Nachrichten<br/> </td> 
  </tr> 
  <tr> 
   <td> Hardbounce<br/> </td> 
   <td> Gesamtzahl der permanenten Fehler, beispielsweise einer falschen E-Mail-Adresse<br/> </td> 
  </tr> 
  <tr> 
   <td> Hardbounce-Rate<br/> </td> 
   <td> Prozentsatz der Sendungen, die permanent fehlgeschlagen sind<br/> </td> 
  </tr> 
  <tr> 
   <td> Mirrorseite<br/> </td> 
   <td> Die Anzahl der Empfänger, die den Mirrorseiten-Link angeklickt haben<br/> </td> 
  </tr> 
  <tr> 
   <td> Mirrorseitenrate<br/> </td> 
   <td> Prozentsatz der Klicks auf den Mirrorseiten-Link in Bezug auf die Gesamtzahl der Sendungen<br/> </td> 
  </tr> 
  <tr> 
   <td> Klicks auf Angebot<br/> </td> 
   <td> Die Anzahl der Klicks auf ein Angebot in einem Versand.<br/> </td> 
  </tr> 
  <tr> 
   <td> Klickrate des Angebots<br/> </td> 
   <td> Prozentsatz der Klicks auf ein Angebot.<br/> </td> 
  </tr> 
  <tr> 
   <td> Öffnungen<br/> </td> 
   <td> Anzahl der Öffnungen einer Nachricht in einem Versand.<br/> </td> 
  </tr> 
  <tr> 
   <td> Öffnungsrate<br/> </td> 
   <td> Prozentsatz der geöffneten Nachrichten<br/> </td> 
  </tr> 
  <tr> 
   <td> Verarbeitet/gesendet<br/> </td> 
   <td> Gesamtzahl der gesendeten Nachrichten<br/> </td> 
  </tr> 
  <tr> 
   <td> Quarantäne<br/> </td> 
   <td> Anzahl der Bounce-Nachrichten, aufgrund derer eine Adresse unter Quarantäne gestellt wurde<br/> </td> 
  </tr> 
  <tr> 
   <td> Quarantänerate<br/> </td> 
   <td> Prozentsatz der Quarantänen in Bezug auf die gesendeten Nachrichten<br/> </td> 
  </tr> 
  <tr> 
   <td> Abgelehnt<br/> </td> 
   <td> Anzahl der Sendungen, die von SMTP-Servern als Spam gekennzeichnet wurden<br/> </td> 
  </tr> 
  <tr> 
   <td> Zurückweisungsrate<br/> </td> 
   <td> Prozentsatz der Nachrichten, die als abgelehnt gekennzeichnet wurden<br/> </td> 
  </tr> 
  <tr> 
   <td> Softbounce<br/> </td> 
   <td> Gesamtzahl der temporären Fehler, beispielsweise einer vollen Inbox<br/> </td> 
  </tr> 
  <tr> 
   <td> Softbounce-Rate<br/> </td> 
   <td> Prozentsatz der Sendungen, die vorläufig fehlgeschlagen sind<br/> </td> 
  </tr> 
  <tr> 
   <td> Einmalige Klicks<br/> </td> 
   <td> Anzahl der Empfänger, die einen Inhalt in einem Versand angeklickt haben<br/> </td> 
  </tr> 
  <tr> 
   <td> Einzelöffnungen<br/> </td> 
   <td> Anzahl der Empfänger, die den Versand geöffnet haben<br/> </td> 
  </tr> 
  <tr> 
   <td> Eindeutige Abmeldung<br/> </td> 
   <td> Die Anzahl der Empfänger, die den Abmelde-Link angeklickt haben.<br/> </td> 
  </tr> 
  <tr> 
   <td> Abmelderate<br/> </td> 
   <td> Anzahl der Einzelabmeldungen im Vergleich zu den zugestellten Nachrichten.<br/> </td> 
  </tr> 
  <tr> 
   <td> Abgemeldet<br/> </td> 
   <td> Gesamtanzahl der Klicks auf den Abmelde-Link.<br/> </td> 
  </tr> 
 </tbody> 
</table>

<!--
### Push notification metrics {#push-notification-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Metric<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Bounces + Errors<br/> </td> 
   <td> Total of errors cumulated during delivery in relation to the total number of sent messages, e.g. errors from MCPNS or provider.<br/> </td> 
  </tr> 
  <tr> 
   <td> Bounce + Error rate<br/> </td> 
   <td> Percentage of push notifications that bounced compared to push notifications sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click<br/> </td> 
   <td> Number of times a push notification has been delivered to the device and clicked on by the user. The user either wanted to view the notification, which will then be moved to Push Open tracking, or dismiss it.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click through rate<br/> </td> 
   <td> Percentage of users who interacted with the push notification.<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> Number of push notifications successfully sent, in relation to the total number of sent push notifications.<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered rate<br/> </td> 
   <td> Percentage of push notifications successfully sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> Number of times a push notification has been delivered to the device and left untouched in the notification center. In most cases, impressions number should be similar to the delivered number. This ensures that the device got the message and relayed that information back to the server.<br/> </td> 
  </tr> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> Total number of push notifications sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Open<br/> </td> 
   <td> Total number of push notifications delivered to the device and clicked on by users thus opening the app. This is similar to the Push Click except a Push Open will not be triggered if the notification was dismissed.<br/> </td> 
  </tr> 
  <tr> 
   <td> Open rate<br/> </td> 
   <td> Percentage of opened push notifications.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique clicks<br/> </td> 
   <td> Number of times a unique user interacts with the push notification, e.g. clicks on the notification or button.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> Number of impressions by recipient.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique Opens<br/> </td> 
   <td> Number of recipients who opened the delivery.<br/> </td> 
  </tr> 
 </tbody> 
</table>

### In-App metrics {#in-app-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Metric<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> Total number of In-App messages delivered to the device by the service provider.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> Total of In-App messages seen by recipients depending on whether trigger criterion was met.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App clicks <br/> </td> 
   <td> Total number of recipients who clicked on Button 1 or Button 2.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App click through rate<br/> </td> 
   <td> Percentage of users who clicked on Button 1 or Button 2 compared to users who saw the message.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal<br/> </td> 
   <td> Total number of messages that recipients dismissed either by clicking the close button or auto-dismiss.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal rate<br/> </td> 
   <td> Percentage of In-App messages that recipients dismissed.<br/> </td> 
  </tr> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> Total number of In-App messages sent from Adobe Campaign as part of the delivery sent process.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> Number of impressions by a unique recipient.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App clicks<br/> </td> 
   <td> Number of times recipients clicked on Button 1 or Button 2.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App dismissals<br/> </td> 
   <td> Number of time recipients dismissed an In-App message.<br/> </td> 
  </tr> 
 </tbody> 
</table>
-->

## Segmente {#segments}

In der Tabelle unten finden Sie die Liste der Segmente, die in Berichten verwendet werden, sowie ihre Definitionen.

<table> 
 <thead> 
  <tr> 
   <th> Segment<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Alter: Boomers 1<br/> </td> 
   <td> Empfänger mit Geburtsjahr 1946 bis 1954<br/> </td> 
  </tr> 
  <tr> 
   <td> Alter: Boomers 2<br/> </td> 
   <td> Empfänger mit Geburtsjahr 1955 bis 1965<br/> </td> 
  </tr> 
  <tr> 
   <td> Alter: von 18 bis 25<br/> </td> 
   <td> Empfänger im Alter von 18 bis 25 Jahren<br/> </td> 
  </tr> 
  <tr> 
   <td> Alter: von 26 bis 30<br/> </td> 
   <td> Empfänger im Alter von 26 bis 30 Jahren<br/> </td> 
  </tr> 
  <tr> 
   <td> Alter: von 31 bis 40<br/> </td> 
   <td> Empfänger im Alter von 31 bis 40 Jahren<br/> </td> 
  </tr> 
  <tr> 
   <td> Alter: von 41 bis 50<br/> </td> 
   <td> Empfänger im Alter von 41 bis 50 Jahren<br/> </td> 
  </tr> 
  <tr> 
   <td> Alter: Generation X<br/> </td> 
   <td> Empfänger mit Geburtsjahr 1966 bis 1976<br/> </td> 
  </tr> 
  <tr> 
   <td> Alter: Generation Y (Millennials)<br/> </td> 
   <td> Empfänger mit Geburtsjahr 1977 bis 1994<br/> </td> 
  </tr> 
  <tr> 
   <td> Alter: Generation Z<br/> </td> 
   <td> Empfänger mit Geburtsjahrgang 1995 bis heute<br/> </td> 
  </tr> 
  <tr> 
   <td> Alter: über 50<br/> </td> 
   <td> Empfänger im Alter von über 50 Jahren<br/> </td> 
  </tr> 
  <tr> 
   <td> Alter: unter 25<br/> </td> 
   <td> Empfänger im Alter von unter 25 Jahren<br/> </td> 
  </tr> 
  <tr> 
   <td> Alter: unter 30<br/> </td> 
   <td> Empfänger im Alter von unter 30 Jahren<br/> </td> 
  </tr> 
  <tr> 
   <td> Alter: unter 40<br/> </td> 
   <td> Empfänger im Alter von unter 40 Jahren<br/> </td> 
  </tr> 
  <tr> 
   <td> Alter: unter 50<br/> </td> 
   <td> Empfänger im Alter von unter 50 Jahren<br/> </td> 
  </tr> 
  <tr> 
   <td> Alter: Stille Generation<br/> </td> 
   <td> Empfänger mit Geburtsjahr 1945 oder früher<br/> </td> 
  </tr> 
  <tr> 
   <td> Alle Besuche<br/> </td> 
   <td> Jeder Empfänger<br/> </td> 
  </tr>
 </tbody> 
</table>
