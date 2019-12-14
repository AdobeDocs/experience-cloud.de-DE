---
title: Adobe Analytics mit dem Start implementieren
description: Erfahren Sie, wie Sie Adobe Analytics mit der Adobe Analytics-Starterweiterung implementieren, ein Bildschirmanzeige-Beacon senden, Variablen hinzufügen, Ereignisse verfolgen und Plugins hinzufügen. Diese Lektion ist Teil des Lernprogramms "Implementing the Experience Cloud in Mobile Android Applications"(Implementieren der Experience Cloud in mobilen Android-Anwendungen).
seo-description: null
seo-title: Adobe Analytics mit dem Start implementieren
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: e9dee6d0aa3b775d0ce617e2b2c57b56de491b8d

---


# Hinzufügen von Adobe Analytics

In dieser Lektion aktivieren Sie die Adobe Analytics-Verfolgung in Ihrer App.

[Adobe Analytics](https://docs.adobe.com/content/help/en/analytics/landing/home.html) ist eine branchenführende Lösung, mit der Sie Ihre Kunden besser verstehen und Ihr Geschäft mit Customer Intelligence steuern können.

In den Lektionen [Erweiterungen](launch-add-extensions.md) hinzufügen und das Mobile SDK[ ](launch-install-the-mobile-sdk.md)installieren haben Sie die Adobe Analytics-Erweiterung zu Ihrer Launch-Eigenschaft hinzugefügt und in die Beispielanwendung importiert.  Jetzt müssen Sie nur noch Code hinzufügen, um die Zustände und Aktionen in Ihrer App zu verfolgen!

## Lernziele

Dies können Sie am Ende dieser Lektion:

* Überprüfen, ob Lebenszyklusmetriken an Adobe Analytics gesendet werden
* Fügen Sie Code hinzu, um Zustände in Ihrer App mit zusätzlichen Daten zu verfolgen
* Fügen Sie Code hinzu, um Aktionen in Ihrer App mit zusätzlichen Daten zu verfolgen

Es gibt viele Dinge, die in Analytics in Launch implementiert werden könnten. Diese Lektion ist nicht erschöpfend, sollte Ihnen aber einen soliden Überblick über die wichtigsten Techniken geben, die Sie für die Implementierung in Ihrer eigenen App benötigen.

## Voraussetzungen 

You should have already completed the lessons in the [Configure Launch](launch-create-a-property.md) section. In diesem Abschnitt haben Sie die Analytics-Erweiterung hinzugefügt und Ihre Tracking-Server- und Report Suite-ID(s) konfiguriert.

## Lebenszyklusmetriken und Adobe Analytics

Lebenszyklusmetriken sind umweltrelevante Metriken und Dimensionen, die mit dem Experience Platform Mobile SDK problemlos in einer App aktiviert werden können.

Sie haben die Lebenszyklusmetriken bereits aktiviert, wenn Sie die Core-Erweiterung zu Ihrer Eigenschaft hinzugefügt haben und die Anweisungen zur Installation für Mobilgeräte befolgt haben, die auf der Oberfläche bereitgestellt wurden. Diese Metriken und Dimensionen, einschließlich umwelt- und anwendungsspezifischer Metriken wie App-Version, Anzahl der beteiligten Benutzer, Betriebssystemversion, Zeitaufteilung, Tage seit der letzten Verwendung usw. kann bei der Analyse Ihrer App sehr hilfreich sein, insbesondere wenn Sie daraus Analytics-Segmente erstellen, die auf alle Ihre Berichte angewendet werden. Die vollständige Liste der Metriken finden Sie in der [Dokumentation](https://docs.adobe.com/content/help/en/mobile-services/android/metrics.htmlh).

## ACPCore-Bibliothek importieren

In der vorherigen Lektion ["Install the Mobile SDK"](launch-install-the-mobile-sdk.md)haben Sie eine Importanweisung hinzugefügt, um die AdobeCore-Bibliothek in der Datei BusBookingActivity verfügbar zu machen. Dieselbe Bibliothek wird für zusätzliche API-Aufrufe in den Aktivitäten in dieser Lektion verwendet. In den nächsten Übungen verwenden Sie APIs, um Status ("trackState") und Aktionen ("trackAction") in Ihrer App zu verfolgen, die in der AdobeCore-Bibliothek definiert sind.  Im neuen Experience Cloud Platform Mobile SDK wurden die trackState- und trackAction-APIs von der Analytics-Bibliothek in die Core-Bibliothek verschoben, sodass diese APIs für andere Zwecke als die Adobe Analytics-Verfolgung genutzt werden können.

## Statusverfolgung

In Ihrer App stehen Ihnen möglicherweise viele verschiedene Inhaltsbildschirme zur Verfügung, die Sie Ihren Benutzern bereitstellen. Dies entspricht den Seiten einer Website. Adobe Analytics bietet eine Methode, mit der Sie diese "Seitenansichtstreffer"senden und in denselben Berichten anzeigen können, die Sie für Ihre Webeigenschaften verwendet haben. Diese Methode heißt "trackState".

In dieser Übung platzieren Sie den Code für einen trackState-Aufruf in nur einem Bildschirm (Seite) in Ihrer App. Im echten Leben wird dies auf allen anderen Bildschirmen/Status in Ihrer App repliziert.

Nachstehend finden Sie eine Syntax und ein Codebeispiel aus der Dokumentation, die Sie in diesem Lernprogramm oder in Ihrer eigenen App kopieren und einfügen können.

**Syntax:**

```java
public static void trackState(final String state, final Map<String, String> contextData)
```

**Beispiel:**

```java
HashMap cData = new HashMap<String, String>();
contextData.put("key", "value");
MobileCore.trackState("state name",contextData);
```

### Status ohne Daten verfolgen

1. Öffnen Sie die Beispielanwendung in Android Studio, gehen Sie zu BusBookingActivity und scrollen Sie unten zur Funktion onResume
1. Hinzufügen eines trackState-Methodenaufrufs
1. Auf `state name` "Buchungsbildschirm"einstellen
1. Fügen Sie anstelle zusätzlicher Daten `null` als Platzhalter im API-Aufruf hinzu
1. Kopieren Sie oder fügen Sie Folgendes ein:

   ```java
   MobileCore.trackState("Booking Screen", null);
   ```

![Grundlegender trackState-Aufruf](images/android/mobile-analytics-basicTrackStateCall2.png)

**So validieren Sie den trackState**

1. Speichern, Erstellen und Ausführen des Projekts
1. Wenn der Simulator ausgeführt wird und den Startbildschirm der App öffnet, zeigen Sie die Debug-Konsole von Android Studio Logcat an
1. Suchen Sie in der Konsole nach `pageName=Booking%20Screen`
1. Beachten Sie, dass die Variable "pageName"auf `Booking Screen` (mit %20 als kodiertem Leerzeichen) eingestellt ist und es keine weiteren benutzerdefinierten Datenpaare gibt. Obwohl Sie technisch gesehen einen "Statusnamen"und nicht einen "Seitennamen"festlegen, wird der Parametername verwendet, `pageName` um die Konsistenz mit Website-Implementierungen zu gewährleisten.

   ![Grundlegendes trackState-Ergebnis](images/android/mobile-analytics-basicTrackStateResult.png)

### Status mit Daten verfolgen

1. Gehen Sie zurück zu BusBookingActivity und fügen Sie oben in der Datei `import java.util.HashMap;` unterhalb der vorhandenen Importe einen Import hinzu.
1. In der `onResume()` Funktion kommentieren (oder löschen) Sie den grundlegenden trackState-Aufruf aus der letzten Übung
1. Fügen Sie einen neuen trackState-Methodenaufruf hinzu, diesmal mit Daten, indem Sie eine HashMap erstellen und benennen, mit dem "put"-Befehl einige Schlüssel/Wert-Paare einschließen und dann HashMap im Aufruf an trackState aufrufen
1. Lassen Sie die `state name` Option "Buchungsbildschirm"
1. Oder kopieren und einfügen in:

   ```java
   HashMap cData = new HashMap<String, String>();
   cData.put("cd.section", "Bus Booking");
   cData.put("cd.subSection", "Booking");
   cData.put("cd.conversionType", "Landing");
   MobileCore.trackState("Booking Screen", cData);
   ```

   ![trackState-Aufruf mit Daten](images/android/mobile-analytics-trackStateWithData.png)

**So validieren Sie den trackState mit Daten**

1. Speichern, erstellen und führen Sie das Projekt erneut aus
1. Wenn der Simulator ausgeführt wird und den Startbildschirm der App öffnet, zeigen Sie die Debug-Konsole von Android Studio Logcat an
1. Suchen `subSection` (oder nach einem der Schlüssel oder Werte, die Sie in den Code eingegeben haben)
1. Sehen Sie jetzt, dass Sie neben dem Wert pageName auch die Schlüssel/Wert-Paare haben, die beim Treffer gesendet wurden

   ![trackState mit Datenergebnis](images/android/mobile-analytics-trackStateWithDataResult.png)

>[!NOTE] Wenn Sie in Analytics mit "props and eVars"vertraut sind, werden Sie feststellen, dass diese Variablennamen nicht im SDK enthalten sind. Alle Schlüssel/Wert-Daten aus dem SDK werden als [contextData-Variablen](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/variables-analytics-reporting/context-data-variables.html)gesendet und müssen daher mithilfe von [Verarbeitungsregeln](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html) in der Analytics-Benutzeroberfläche Props oder eVars (oder anderen Variablen) zugeordnet werden.

## Aktionen verfolgen

Ähnlich wie bei Aktionen ohne Seitenladevorgang auf einer Website möchten Sie häufig eine Aktion verfolgen, die ein Benutzer in Ihrer App ausführt, z. B. Klicks auf Dinge, die keinen anderen Bildschirm laden. Dies wird ähnlich wie der zuvor verwendete trackState behandelt, allerdings wird diese Methode aufgerufen `trackAction`.

Nachstehend finden Sie eine Syntax und ein Codebeispiel aus der Dokumentation.

**Syntax:**

```java
public static void trackAction(final String action, final Map<String, String> contextData) data;
```

**Beispiel:**

```java
HashMap<String, String> contextData = new HashMap<String, String>();
contextData.put("key", "value");
MobileCore.trackAction("action taken", contextData);
```

### Interaktion mit dem Destination Switcher verfolgen

In dieser Beispiel-Bus-Buchungs-App können Sie den Ausgangspunkt mit dem Zielort wechseln, indem Sie auf den Pfeil zwischen diesen beiden Werten klicken. Sie haben beschlossen, die Interaktion mit dieser Funktion in Adobe Analytics zu verfolgen.

![Zielleiter](images/android/mobile-analytics-destinationSwitcher.png)

Dieser Umschalter wird in der Datei BusBookingActivity im Beispielprojekt gesteuert. In dieser Übung senden Sie einen trackAction-Treffer, sobald Benutzer darauf klicken.

#### So fügen Sie den trackAction-Code hinzu

1. Öffnen Sie das Beispielprojekt in Android Studio und gehen Sie zu BusBookingActivity
1. Suchen Sie die Funktion "mBtnFlip.setOnClickListener"in oder um Zeile 57
1. Erweitern Sie bei Bedarf die Funktion, sodass Sie den gesamten Code anzeigen können
1. Fügen Sie in der Funktion onClick unter dem Aufruf an `flipSourceDesti()`einen `trackAction()` Aufruf
1. Legen Sie den Aktionsnamen auf "Flip-Ziel"fest und fügen Sie "null"für den Parameter contextData hinzu (da diesmal keine weiteren Informationen gesendet werden müssen)
1. Sie können den folgenden Code kopieren und einfügen

   ```java
   MobileCore.trackAction("Flip Destination", null);
   ```

Die Funktion sieht nun wie folgt aus:

![Destination Switcher Code](images/android/mobile-analytics-destinationSwitcherCode.png)

#### So validieren Sie den trackAction-Code

1. Speichern Sie nach dem Hinzufügen des Codes das Projekt, führen Sie aus und erstellen Sie
1. Klicken Sie auf das Müllsymbol, um die Logcat-Konsole zu leeren.
1. Klicken Sie im Simulator auf den Pfeil Destination Switcher, um festzustellen, dass eine neue Anforderung (oder mehr) in der Konsole angezeigt wird.
1. Suchen nach `Flip%20Destination` in Logcat
1. Beachten Sie, dass sowohl die Parameter action als auch pev2 das Ziel spiegeln%20Ziel (mit kodiertem Leerzeichen)
1. Beachten Sie den `pe=lnk_o` Schlüssel/Wert in derselben Zeile, der anzeigt, dass es sich um einen Treffer für einen "benutzerspezifischen Link"handelt, der von trackAction ausgelöst wird.

   <!--![trackAction Result in Debugger](images/android/mobile-analytics-trackActionResult1.png)-->

Gute Arbeit! Sie haben die Analytics-Lektion abgeschlossen. Natürlich können Sie noch viele andere Dinge tun, um unsere Analytics-Implementierung zu verbessern, aber hoffentlich haben Sie dadurch einige der Kernkompetenzen erhalten, die Sie benötigen, um die restlichen Anforderungen zu erfüllen.

## Zusätzliche Vorteile von trackState und trackAction

In diesen letzten Übungen konnten Sie Daten aus der App mithilfe der trackState- und trackAction-APIs an Adobe Analytics senden. Da das Experience Platform Mobile SDK in Launch wurzelt, gibt es viele weitere Dinge, die Sie in der Benutzeroberfläche "Start"tun können, wobei Sie den soeben hinzugefügten Code nutzen.

Beim Start können Sie Regeln erstellen, die von den trackState- und trackAction-APIs ausgelöst werden, und zusätzliche Aktionen ausführen lassen, z. B. Anforderungen an andere Adobe-Lösungen oder externe Partner.

[Weiter "Adobe Audience Manager hinzufügen"&gt;](audience-manager.md)
