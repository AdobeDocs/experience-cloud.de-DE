---
title: Implementieren des Einbettungscodes starten
description: Erfahren Sie, wie Sie die Einbettungscodes Ihrer Launch-Eigenschaft abrufen und auf Ihrer Website implementieren können. Diese Lektion ist Teil des Tutorials zum Implementieren der Experience Cloud in Websites mit Start.
seo-description: null
seo-title: Implementieren des Einbettungscodes starten
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 14e46fa7d806f2713a69fe5d3a0a8c326de26d23

---


# Hinzufügen des eingebetteten Launch-Codes

In dieser Lektion implementieren Sie den asynchronen Einbettungscode der Entwicklungsumgebung Ihrer Launch-Eigenschaft. Außerdem lernen Sie zwei Hauptkonzepte von Launch kennen: Umgebungen und Einbettungscodes.

## Lernziele

Dies können Sie am Ende dieser Lektion:

* Einbettungscode für Ihre Launch-Eigenschaft abrufen
* Den Unterschied zwischen einer Entwicklungs-, Staging- und Produktionsumgebung erläutern
* Einbettungscode für "Start"zu einem HTML-Dokument hinzufügen
* Explain the optimal location of the Launch embed code in relation to other code in the `<head>` of an html document

## Einbettungscode kopieren

The embed code is a `<script>` tag that you put on your webpages to load and execute the logic you build in Launch. Wenn Sie die Bibliothek asynchron laden, lädt der Browser die Seite weiter, ruft die Startbibliothek ab und führt sie parallel aus. In diesem Fall ist nur ein Einbettungscode vorhanden, den Sie in den `<head>` einfügen. (When Launch is deployed synchronously, there are two embed codes, one which you put in the `<head>` and another which you put before the `</body>`).

Klicken Sie in der Property-Übersicht auf die Registerkarte `Environments`, um zur Umgebungsseite zu gelangen. Beachten Sie, dass Entwicklungs-, Staging- und Produktionsumgebungen für Sie vordefiniert wurden.

![Klicken Sie auf Umgebungen in der oberen Navigationsleiste](images/launch-environments.png)

Diese Umgebungen entsprechen den typischen Phasen im Prozess der Code-Entwicklung und -Veröffentlichung. Code wird zuerst von einem Entwickler in einer Entwicklungsumgebung geschrieben. Wenn sie ihre Arbeit abgeschlossen haben, senden sie den Code an eine Staging-Umgebung, in der QA- und andere Teams ihn überprüfen können. Sobald die Qualitätssicherungs- und anderen Teams zufrieden sind, wird der Code dann in der Produktionsumgebung veröffentlicht, der Umgebung für die Öffentlichkeit, in der Ihre Besucher Ihre Website besuchen.

Launch ermöglicht zusätzliche Entwicklungsumgebungen, was in großen Organisationen nützlich ist, in denen mehrere Entwickler gleichzeitig an verschiedenen Projekten arbeiten.

Dies sind die einzigen Umgebungen, in denen wir das Tutorial abschließen müssen. Umgebungen ermöglichen es Ihnen, verschiedene Arbeitsversionen Ihrer Launch-Bibliotheken unter verschiedenen URLs zu hosten, sodass Sie problemlos neue Funktionen hinzufügen und sie den richtigen Benutzern zur Verfügung stellen können (z. B. Entwickler, QA-Techniker, die Öffentlichkeit usw.) zum richtigen Zeitpunkt.

Kopieren wir nun den Einbettungscode:

1. In the **[!UICONTROL Development]** row, click the Install icon ![Install icon](images/launch-installIcon.png) to open the modal.

1. Beachten Sie, dass Launch standardmäßig die asynchronen Einbettungscodes verwendet

1. Klicken Sie auf das Symbol " ![Kopieren", um den Einbettungscode in die Zwischenablage zu kopieren](images/launch-copyIcon.png) .

1. Click **[!UICONTROL Close]** to close the modal.

   ![Installationssymbol](images/launch-copyInstallCode.png)

## Implement the Embed Code in the `<head>` of the Sample HTML Page

The embed code should be implemented in the `<head>` element of all HTML pages that will share the property. You might have one or several template files which control the `<head>` globally across the site, making it a straightforward process to add Launch.

Laden Sie [die HTML-Beispielseite](https://www.enablementadobe.com/multi/web/basic-sample.html) herunter (klicken Sie mit der rechten Maustaste auf diesen Link und klicken Sie auf "Link speichern unter") und öffnen Sie sie in einem Code-Editor. [Brackets](http://brackets.io/) ist ein kostenloser Open Source Editor, wenn Sie einen benötigen.

Ersetzen Sie den vorhandenen Einbettungscode in oder um Zeile 34 durch den in der Zwischenablage vorhandenen und speichern Sie die Seite. Öffnen Sie jetzt die Seite in einem Webbrowser. If you are loading the page using the `file://` protocol, you will need to add "https:" at the beginning of the embed code URL in your code editor). Die Zeilen 33 bis 36 Ihrer Beispielseite sollten etwa wie folgt aussehen:

```html
    <!--Launch Header Embed Code: REPLACE LINE 39 WITH THE EMBED CODE FROM YOUR OWN DEVELOPMENT ENVIRONMENT-->
    <script src="https://assets.adobedtm.com/launch-ENa21cfed3f06f4ddf9690de8077b39e81-development.min.js" async></script>
    <!--/Launch Header Embed Code-->
```

Öffnen Sie die Entwicklerwerkzeuge Ihres Webbrowsers und gehen Sie zur Registerkarte Netzwerk. At this point you should see a 404 error for the Launch environment URL:
![404 error](images/samplepage-404.png)

Der Fehler 404 wird erwartet, da Sie in dieser Startumgebung noch keine Bibliothek erstellt haben. Hierzu kommen wir in der nächsten Lektion. Wenn anstelle eines 404-Fehlers die Meldung „Fehlgeschlagen“ angezeigt wird, haben Sie wahrscheinlich vergessen, das `https://`-Protokoll im Einbettungscode hinzuzufügen. Sie müssen das `https://`-Protokoll nur angeben, wenn Sie die Beispielseite mit dem `file://`-Protokoll laden. Nehmen Sie die Änderung vor und laden Sie die Seite neu, bis der 404-Fehler angezeigt wird.

## Best Practices zur Implementierung starten

Nehmen wir einen Moment Zeit, um einige der Best Practices zur Implementierung von Launch zu überprüfen, die auf der Beispielseite gezeigt werden:

* **Datenschicht**:

   * We *strongly* recommend creating a digital data layer on your site containing all of the attributes needed to populate variables in Analytics, Target, and other marketing solutions. Diese Beispielseite enthält nur eine sehr einfache Datenschicht. Eine echte Datenschicht kann viele weitere Details über Seite, Besucher, Warenkorbdetails usw. enthalten. For more info on data layers, please see [Customer Experience Digital Data Layer 1.0](https://www.w3.org/2013/12/ceddl-201312.pdf)

   * Definieren Sie Ihre Datenschicht vor dem Einbettungscode starten, um das zu maximieren, was Sie in Target, Kundenattributen und Analytics tun können.

* **JavaScript-Hilfsbibliotheken**: Wenn Sie bereits eine Bibliothek wie JQuery in `<head>` Ihren Seiten implementiert haben, laden Sie sie vor dem Start, um ihre Syntax in Launch und Target zu nutzen

* **HTML5-Dokumenttyp**: Der HTML5-Dokumenttyp wird von Target benötigt

* **Vorabladen und DNS-Vorabruf**: Verwenden Sie diese Funktionen, um die Seitenladezeit zu optimieren. Siehe auch: [/https://w3c.github.io/resource-hints/](https://w3c.github.io/resource-hints/)

* **Ausblenden von Snippets für asynchrone Target-Implementierungen**: Weitere Informationen hierzu finden Sie in der Target-Lektion. Wenn Target jedoch über asynchrone Startbettcodes bereitgestellt wird, sollten Sie vor den Einbettungscodes "Starten"ein vorzeitiges Ausblenden-Snippet auf Ihren Seiten komprimieren, um das Flackern von Inhalten zu verwalten

Im Folgenden finden Sie eine Zusammenfassung dieser Best Practices in der empfohlenen Reihenfolge. Beachten Sie, dass es einige Platzhalter für kontospezifische Details gibt:

```html
<!doctype html>
<html lang="en">
<head>
    <title>Basic Demo</title>
    <!--Preconnect and DNS-Prefetch to improve page load time. REPLACE "techmarketingdemos" WITH YOUR OWN AAM PARTNER ID, TARGET CLIENT CODE, AND ANALYTICS TRACKING SERVER-->
    <link rel="preconnect" href="//dpm.demdex.net">
    <link rel="preconnect" href="//fast.techmarketingdemos.demdex.net">
    <link rel="preconnect" href="//techmarketingdemos.demdex.net">
    <link rel="preconnect" href="//cm.everesttech.net">
    <link rel="preconnect" href="//techmarketingdemos.tt.omtrdc.net">
    <link rel="preconnect" href="//techmarketingdemos.sc.omtrdc.net">
    <link rel="dns-prefetch" href="//dpm.demdex.net">
    <link rel="dns-prefetch" href="//fast.techmarketingdemos.demdex.net">
    <link rel="dns-prefetch" href="//techmarketingdemos.demdex.net">
    <link rel="dns-prefetch" href="//cm.everesttech.net">
    <link rel="dns-prefetch" href="//techmarketingdemos.tt.omtrdc.net">
    <link rel="dns-prefetch" href="//techmarketingdemos.sc.omtrdc.net">
    <!--/Preconnect and DNS-Prefetch-->
    <!--Data Layer to enable rich data collection and targeting-->
    <script>
    var digitalData = {
        "page": {
            "pageInfo" : {
                "pageName": "Home"
                }
            }
    };
    </script>
    <!--/Data Layer-->
    <!--jQuery or other helper libraries-->
    <script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
    <!--/jQuery-->
    <!--prehiding snippet for Adobe Target with asynchronous Launch deployment-->
    <script>
        (function(g,b,d,f){(function(a,c,d){if(a){var e=b.createElement("style");e.id=c;e.innerHTML=d;a.appendChild(e)}})(b.getElementsByTagName("head")[0],"at-body-style",d);setTimeout(function(){var a=b.getElementsByTagName("head")[0];if(a){var c=b.getElementById("at-body-style");c&&a.removeChild(c)}},f)})(window,document,"body {opacity: 0 !important}",3E3);
    </script>
    <!--/prehiding snippet for Adobe Target with asynchronous Launch deployment-->
    <!--Launch Header Embed Code: REPLACE LINE 39 WITH THE INSTALL CODE FROM YOUR OWN DEVELOPMENT ENVIRONMENT-->
    <script src="//assets.adobedtm.com/launch-EN93497c30fdf0424eb678d5f4ffac66dc.min.js" async></script>
    <!--/Launch Header Embed Code-->
</head>
<body>
    <h1>Launch by Adobe: Basic Demo</h1>
    <p>This is a very simple page to demonstrate basic concepts of Launch by Adobe</p>
</body>
</html>
```

Jetzt wissen Sie, wie Sie den Einbettungscode starten zu Ihrer Site hinzufügen!

[Weiter "Datenelement, Regel und Bibliothek hinzufügen"&gt;](launch-data-elements-rules.md)