---
title: Fehlerbehebung bei dynamischen Berichten
description: Hier finden Sie häufig gestellte Fragen zu dynamischen Berichten.
audience: end-user
level: Intermediate
badge: label="EINGESCHRÄNKTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierter Benutzer beschränkt"
exl-id: a58fc8fd-e510-45ef-8fe9-c75ff4498113
source-git-commit: 34c6f8a137a9085b26c0ea8f78930cff6192cfc9
workflow-type: tm+mt
source-wordcount: '1239'
ht-degree: 97%

---

# Fehlerbehebung{#troubleshooting}

In diesem Abschnitt finden Sie häufig gestellte Fragen zu dynamischen Berichten.

## Bei Einzelöffnungen und Einzelklicks entspricht die Zahl in der Aggregat-Zeile nicht der Zahl in den einzelnen Zeilen {#unique-open-clicks-no-match}

Dies ist zu erwarten.
Im folgenden Beispiel möchten wir dieses Verhalten erläutern.

Eine E-Mail wird an Profil P1 und P2 gesendet.

P1 öffnet die E-Mail am ersten Tag zweimal und dann am zweiten Tag dreimal.

P2 öffnet die E-Mail am ersten Tag einmal und an den folgenden Tagen nicht mehr.
Im Folgenden finden Sie eine Darstellung der Interaktion der Profile mit der gesendeten E-Mail:

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong>Tag</strong> <br/> </th> 
   <th align="center"> <strong>Öffnungen</strong> <br/> </th> 
   <th align="center"> <strong>Einzelöffnungen</strong> <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> Tag 1<br/> </td> 
   <td align="center"> 2 + 1 = 3<br/> </td> 
   <td align="center"> 1 + 1 = 2<br/> </td> 
  </tr> 
  <tr> 
   <td align="center"> Tag 2<br/> </td> 
   <td align="center"> 3 + 0 = 3<br/> </td> 
   <td align="center"> 1 + 0 = 1<br/> </td> 
  </tr>
 </tbody> 
</table>

Um die Gesamtzahl der Einzelöffnungen zu erhalten, müssen wir die Zeilenanzahl der **[!UICONTROL Einzelöffnungen]** addieren, was 3 ergibt. Da für die E-Mail aber nur 2 Profile ausgewählt wurden, sollte die Öffnungsrate 150 % betragen.

Um keinen Prozentsatz von mehr als 100 zu erhalten, wird zur Definition von **[!UICONTROL Einzelöffnungen]** die Anzahl der eindeutigen Broadlogs herangezogen, die geöffnet wurden. In diesem Fall haben die Einzelöffnungen von P1 den Wert 1, auch wenn P1 die E-Mail an Tag 1 und Tag 2 geöffnet hat.

Daraus ergibt sich die folgende Tabelle:

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong></strong> <br/> </th> 
   <th align="center"> <strong>Öffnungen</strong> <br/> </th> 
   <th align="center"> <strong>Einzelöffnungen</strong> <br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> <strong> Tag </strong><br/> </td> 
   <td align="center"> <strong> 6 </strong><br/> </td> 
   <td align="center"> <strong> 2</strong><br/> </td>
  </tr> 
  <tr> 
   <td align="center"> Tag 1<br/> </td> 
   <td align="center"> 3<br/> </td> 
   <td align="center"> 2<br/> </td>
  </tr> 
  <tr> 
   <td align="center"> Tag 2<br/> </td> 
   <td align="center"> 3<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Die eindeutige Anzahl basiert auf einem HLL-basierten Sketch. Dies kann bei großen Zahlen zu leichten Ungenauigkeiten führen.

## Die Anzahl der Öffnungen stimmt nicht mit der Anzahl in der Datenbank überein {#open-counts-no-match-database}

Der Grund dafür kann darin liegen, dass bei dynamischen Berichten heuristische Modelle verwendet werden, um Öffnungen zu tracken, selbst wenn die Aktion **[!UICONTROL Öffnungen]** nicht getrackt werden kann.

Wenn beispielsweise ein Benutzer die Bilder in seinem Client deaktiviert hat und auf einen Link in der E-Mail klickt, kann es vorkommen, dass die **[!UICONTROL Öffnung]** nicht von der Datenbank getrackt wird, der **[!UICONTROL Klick]** aber schon.

Deshalb kann es sein, dass die Anzahl in den Trackinglogs für **[!UICONTROL Öffnungen]** nicht mit der in der Datenbank übereinstimmt.

Solche Ereignisse werden hinzugefügt, da **ein E-Mail-Klick auf eine E-Mail-Öffnung hinweist**.

>[!NOTE]
>
>Da die eindeutige Anzahl auf einem HLL-basierten Sketch basiert, können zwischen den Zahlen kleine Unterschiede auftreten.

## Wie werden die Zahlen für wiederkehrende Sendungen/den Versand von Transaktionsnachrichten berechnet?  {#counts-recurring-deliveries}

Bei wiederkehrenden Sendungen und dem Versand von Transaktionsnachrichten werden die Zahlen sowohl den über- als auch den untergeordneten Sendungen zugeordnet.
Nehmen Sie zum Beispiel einen wiederkehrenden Versand mit der Bezeichnung **R1**, der täglich an Tag 1 (RC1), Tag 2 (RC2) und Tag 3 (RC3) ausgeführt wird.
Nehmen wir an, dass nur eine einzige Person alle untergeordneten Sendungen mehrmals geöffnet hat. In diesem Fall wird für die einzelnen wiederkehrenden untergeordneten Sendungen als Anzahl der **[!UICONTROL Öffnungen]** 1 angezeigt.
Da jedoch dieselbe Person auf alle Sendungen geklickt hat, wird für den übergeordneten wiederkehrenden Versand unter **[!UICONTROL Einzelöffnungen]** ebenfalls 1 angezeigt.

Berichte sollten wie folgt aussehen:

<table> 
 <thead> 
  <tr> 
   <th align="center"> <strong>Versand</strong> <br/> </th> 
   <th align="center"> <strong>Gesendet</strong> <br/> </th> 
   <th align="center"> <strong>Zugestellt</strong> <br/> </th>
   <th align="center"> <strong>Öffnungen</strong> <br/> </th> 
   <th align="center"> <strong>Einzelöffnungen</strong> <br/> </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td align="center"> <strong>R1</strong><br/> </td> 
   <td align="center"> <strong>100</strong><br/> </td> 
   <td align="center"> <strong>90</strong><br/> </td> 
   <td align="center"> <strong>10</strong><br/> </td> 
   <td align="center"> <strong>3</strong><br/> </td> 
  </tr> 
  <tr> 
   <td align="center"> RC1<br/> </td> 
   <td align="center"> 20<br/> </td> 
   <td align="center"> 20<br/> </td> 
   <td align="center"> 6<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr>
    <tr> 
   <td align="center"> RC2<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 30<br/> </td> 
   <td align="center"> 2<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
    <tr> 
   <td align="center"> RC3<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 40<br/> </td> 
   <td align="center"> 2<br/> </td> 
   <td align="center"> 1<br/> </td> 
  </tr> 
 </tbody> 
</table>

## Was bedeuten die Farben in der Tabelle meiner Berichte? {#reports-color-signification}

Die Farben in Ihren Berichten sind zufällig gewählt und können nicht personalisiert werden. Sie stellen einen Fortschrittsbalken dar und sollen Ihnen helfen, den in den Berichten erzielten Höchstwert besser zu erkennen.

Im folgenden Beispiel hat die Zelle die gleiche Farbe, da ihr Wert 100 % beträgt.

![](assets/troubleshooting_1.png)

Wenn Sie die **[!UICONTROL bedingte Formatierung]** in benutzerdefinierte Formatierung ändern, wird die Zelle grüner, wenn der Wert den oberen Grenzwert erreicht. Wenn er umgekehrt jedoch den unteren Grenzwert erreicht, wird er röter.

Hier legen wir beispielsweise die **[!UICONTROL Obergrenze]** mit 500 und die **[!UICONTROL Untergrenze]** mit 0 fest.

![](assets/troubleshooting_2.png)

## Warum wird der Wert &quot;K. A.&quot; in meinen Berichten angezeigt?

![](assets/troubleshooting_3.png)

Der Wert **K. A.** wird manchmal in Ihren dynamischen Berichten angegeben. Dies kann aus drei Gründen angezeigt werden:

* Der Versand wurde gelöscht und wird hier als **K. A.** angegeben, sodass keine Diskrepanz in den Ergebnissen verursacht wird.
* Wenn Sie die Dimension **[!UICONTROL Versand von Transaktionsnachrichten]** per Drag-and-Drop in Ihre Berichte ziehen, wird als Ergebnis möglicherweise der Wert **K. A.** angezeigt. Dies geschieht, weil der dynamische Bericht alle Sendungen abruft, auch wenn sie keine Transaktionsnachrichten sind. Dies kann auch passieren, wenn Sie die Dimension **[!UICONTROL Versand]** in Ihren Bericht ziehen. In diesem Fall stellt der Wert **K. A.** jedoch den Versand von Transaktionsnachrichten dar.
* Wenn eine Dimension mit einer Metrik verwendet wird, die sich nicht auf die Dimension bezieht. Im folgenden Beispiel wird eine Aufschlüsselung mit der Dimension **[!UICONTROL Tracking-URL]** hinzugefügt, obwohl die **[!UICONTROL Klick]**-Anzahl in diesem Versand auf 0 gesetzt ist.

  ![](assets/troubleshooting_4.png)

## Versandberichte zeigen bei Verwendung von benutzerdefinierten Zielgruppen-Mappings unvollständige Daten an

Wenn Sie in Sendungen importierte benutzerdefinierte Zielgruppen-Mappings verwenden und in den verschiedenen Berichten keine Daten angezeigt werden, kann das bedeuten, dass die Berichtsanreicherungen für diese Zielgruppen-Mappings nicht erstellt wurden.

So beheben Sie das Problem:

* Nach dem Importieren Ihres Zielgruppen-Mappings aus einer XML-Datei müssen Sie auch die Berichtsanreicherung importieren.

* Anstatt Ihr Zielgruppen-Mapping zu importieren, können Sie es auch direkt in der Web-Benutzeroberfläche von Adobe Campaign erstellen. Dadurch wird die Berichtsanreicherung automatisch erstellt.

## Diskrepanz zwischen der Spaltentitelnummer und der Summe der Zeilen

In den folgenden Fällen wird eine Diskrepanz zwischen der Spaltentitelnummer und der Summe aller Zeilen erwartet:

* **Eindeutige Metriken**: Durch die Verwendung eindeutiger Metriken kann sich die in der Kopfzeile angezeigte Gesamtanzahl ändern, da sie auf Empfängerkennungen und nicht auf einer einfachen Summe der Zeilenanzahl basiert. Daher kann ein einzelnes Profil mehrere Ereignisse über verschiedene Dimensionen hinweg auslösen, was zu mehreren Zeilen im Datensatz führt. In der Kopfzeile wird jedes Profil jedoch nur einmal gezählt.

  z. B.:

   * Wenn Profil A eine E-Mail an drei verschiedenen Tagen öffnet, wird A in der Aufschlüsselung nach Tag in drei Zeilen angezeigt. In der Kopfzeile wird A jedoch als 1 gezählt.

   * Wenn Profil A am selben Tag auf drei verschiedene Links in einer E-Mail klickt, wird A für die Aufschlüsselung nach Tracking-URL in drei Zeilen angezeigt. In der Kopfzeile wird A jedoch als 1 gezählt. Dasselbe gilt für Aufschlüsselungen nach Gerät und Browser.

* **Öffnungsmetriken**: Die Anzahl der Öffnungen wird durch die Aggregation der Summe der tatsächlichen Öffnungsereignisse und der Einzelklickereignisse (pro Empfängerkennung) ermittelt. Dabei werden Fälle ausgeschlossen, in denen kein Öffnungsereignis aufgetreten ist, da es ohne ein Öffnungsereignis nicht möglich ist, auf einen E-Mail-Link zu klicken.

  z. B.:

   * Wenn Profil A eine nachverfolgte E-Mail öffnet (mit URL U1), wird dies als Öffnungsereignis registriert, wobei die URL als Null aufgezeichnet wird. Beim späteren Klicken auf U1 wird ein Klickereignis generiert. Obwohl der Klick von A auf U1 auch als Öffnungsereignis gezählt wird, gibt es kein spezifisches Öffnungsereignis für U1. Daher wird A nur einmal in der Anzahl der Einzelöffnungen gezählt.

   * Profil R öffnet eine E-Mail am ersten Tag, was als Öffnungsereignis registriert wird, und klickt auf einen Link. In den nächsten zwei Tagen öffnet R die E-Mail erneut und klickt wieder auf den Link, wodurch jeden Tag ein Klickereignis generiert wird. Während die Interaktion von R täglich in der Zahl der Öffnungen verfolgt wird, wird R im Spaltentitel nur einmal gezählt, da der Schwerpunkt auf eindeutigen Interaktionen liegt.

* **Negiertes Ereignis**: In Berichten beschreibt ein negiertes Ereignis Versandversuche, die ursprünglich als erfolgreich gekennzeichnet wurden, nach weiteren Zustellversuchen jedoch letztendlich fehlgeschlagen sind. Diese werden durch die Anzahl „-1“ angegeben. Um Verwirrung zu vermeiden, wird diese negative Anzahl aus den angezeigten Versandmetriken ausgeschlossen. Daher stimmt die Summe aller Zeilen für die Versandmetrik möglicherweise nicht mit der Spaltentitelnummer überein.
