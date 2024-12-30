---
title: Recommendations und Einschränkungen
description: Recommendations und Einschränkungen bei der Migration auf Campaign v8 REST-APIs.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
mini-toc-levels: 1
badge: label="EINGESCHRÄNKTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierter Benutzer beschränkt"
exl-id: 45acebb1-9325-4e26-8fe9-cc73f745d801
source-git-commit: 6e4e214731b9772014d01dde89b3f80e4c4e93a6
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 1%

---

# Recommendations und Einschränkungen {#limitations}

## Berechtigungen und Sicherheit {#permissions}

### Zuordnung von Produktprofilen

Im Campaign Standard wurde Ihnen erhöhte Administratorrolle Zugriff auf APIs gewährt, unabhängig von Ihrem zugewiesenen Produktprofil. Campaign v8 führt einen anderen Satz von Produktprofilen ein, für die eine Zuordnung vom Campaign Standard zu Campaign v8-Produktprofilen erforderlich ist.

Bei der Migration werden zwei Produktprofile zu Ihren vorhandenen oder vorab erstellten technischen Konten hinzugefügt: Administrator und Message Center (für den Zugriff auf Transaktions-APIs). Überprüfen Sie die Produktprofilzuordnung und weisen Sie das erforderliche Produktprofil zu, wenn Sie nicht möchten, dass das Admin-Produktprofil Ihrem technischen Konto zugeordnet wird.

### Mandanten-ID

Nach der Migration sollten Sie bei zukünftigen Integrationen Ihre **Campaign v8-Mandanten-ID** in REST-URLs verwenden und Ihre vorherige Campaign Standard-Mandanten-ID ersetzen.

### Verwendung von Schlüsseln

Die Verwaltung der PKey-Werte unterscheidet sich zwischen Campaign Standard und Campaign v8. Wenn Sie PKeys mit Campaign Standard gespeichert haben, stellen Sie sicher, dass Ihre Implementierung nachfolgende API-Aufrufe dynamisch durch PKeys oder aus vorherigen API-Aufrufen erstellt.

## Verfügbare APIs {#deprecated}

Vorerst sind die unten aufgeführten REST-APIs zur Verwendung verfügbar:

* **Profile**
* **Services und Abonnements**
* **Benutzerdefinierte Ressourcen**
* **Workflows**

>[!AVAILABILITY]
>
>Derzeit ist die REST-API **Transaktionsnachrichten** nicht verfügbar.
>
>Die unten aufgeführten REST-APIs sind veraltet und nicht mehr verfügbar:
>* Marketing-Verlauf
>* Organisationseinheiten
>* Datenschutzverwaltung

## Filter

* Um Ihre Filter in den REST-API-Payloads zu verwenden, müssen Sie sie in Campaign v8 bearbeiten und einen Namen angeben, der in Ihren Payloads verwendet werden soll. Greifen Sie dazu über die Registerkarte **[!UICONTROL Parameter]** auf die zusätzlichen Parameter des Filters zu und geben Sie den gewünschten Namen im Feld **[!UICONTROL Filtername in REST-API]** an.

  ![](assets/api-filtering.png)


* Das Präfix „by“, das für die Verwendung benutzerdefinierter Filter erforderlich ist, wird nicht mehr benötigt. Der Filtername sollte in Ihren Anfragen unverändert verwendet werden.

  Beispiel:

  `GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/<resourceName>/<customFilterName>?<customFilterparam>=<customFilterValue>`

## Abgelegte Datenbankfelder

Einige Felder aus der Datenbank werden während der Migration gelöscht. Bei Verwendung eines abgelegten Felds geben REST-APIs leere Werte zurück. In Zukunft werden alle abgelegten Felder veraltet sein und entfernt.

## POST mit verknüpften Ressourcen

Bei Verwendung des folgenden Anfragetext-Formats, wobei „VehicleOwner“ den Link zu „nms:recipient“ darstellt:

```
{
    "vehicleNumber": "20009",
    "vehicleName": "Model E",
    "vehicleOwner":{
        "firstName":"tester 11",
        "lastName":"Smith 11"
    }
}
```

Die Link-Informationen werden ignoriert. Daher wird unter „cusVehicle“ ein neuer Datensatz generiert, der nur die Werte „vehicleNumber“ und „vehicleName“ enthält. Der Link bleibt jedoch null, was dazu führt, dass für „VehicleOwner“ „null“ festgelegt wird.

Wenn in Campaign v8 dieselbe Anfragekörperstruktur verwendet wird und das „Fahrzeug“ mit einem Profil verknüpft ist, tritt ein Fehler auf. Dieser Fehler tritt auf, weil die Eigenschaft „firstName“ für „cusVehicle“ nicht als gültig erkannt wird. Ein Anfragetext, der nur die Attribute ohne die Relation enthält, funktioniert jedoch problemlos.

## PATCH-Vorgänge

* Campaign v8 unterstützt das PATCH mit einem leeren Anfrageinhalt nicht: Der Status „Kein Inhalt“ wird 204 zurückgegeben.
* Campaign Standard unterstützt zwar das PATCH von Elementen/Attributen innerhalb eines Schemas, aber beachten Sie, dass PATCH-Vorgänge am Speicherort in Campaign v8 nicht unterstützt werden. Der Versuch, eine PATCH am Speicherort abzulegen, führt zu einem internen 500-Server-Fehler mit einer Fehlermeldung, die angibt, dass die Eigenschaft „zipCode“ für die Ressource „profile“ nicht gültig ist.

## REST-Antworten

Im folgenden Abschnitt sind geringfügige Unterschiede zwischen REST-Antworten von Campaign Standard und v8 aufgeführt.

* Bei einzelnen GET-Einträgen enthält die Antwort die href in der Antwort.
* Bei der Abfrage mit dem -Attribut liefert Campaign v8 Anzahl und Paginierung in der Antwort.
* Nach POST werden Werte von verknüpften Ressourcen in der Antwort zurückgegeben.

## Fehlercodes und Meldungen

Im folgenden Abschnitt werden die Unterschiede zwischen Fehler-Codes und Fehlermeldungen von Campaign Standard und Campaign v8 aufgeführt.

| Szenario | Campaign Standard | Campaign v8 |
|  ---  |  ---  |  ---  |
| Ungültigen PKey im Anfragetext verwenden | 500 - Attribut &#39;O5iRp40EGA&#39; unbekannt (siehe Definition des Schemas &#39;Profiles (nms:recipient)&#39;). XTK-170036 Ausdruck &#39;@id = @O5iRp40EGA&#39; kann nicht analysiert werden. | 404 - PKey kann nicht entschlüsselt werden. (PKey=@jksad) |
| Ungültigen PKey im URI verwenden | 500 - Attribut &#39;O5iRp40EGA&#39; unbekannt (siehe Definition des Schemas &#39;Profiles (nms:recipient)&#39;). XTK-170036 Ausdruck &#39;@id = @O5iRp40EGA&#39; kann nicht analysiert werden. | 404 - PKey kann nicht entschlüsselt werden. (PKey=@jksad) Nicht unterstützter Endpunkt. (endpoint=rest/profileAndServices/profile/@jksad) |
| Verwenden zweier verschiedener roher PKey im URI und Anfragetext | 500 - RST-360011 Ein Fehler ist aufgetreten - Bitte Admin kontaktieren. Inkonsistenter RST-360012-Vorgang für Ressource „service“ - Schlüssel „SVC3“ kann nicht auf „SVC4“ aktualisiert werden. | 500 - Ein Fehler ist aufgetreten - Bitte Admin kontaktieren. |
| Verwenden von PKey im URI und eines anderen rohen PKey im Anfragetext | 500 - Ein &#39;Dienst&#39; mit demselben Schlüssel &#39;SVC4&#39; ist bereits vorhanden. PGS-220000 PostgreSQL-Fehler: FEHLER: Doppelter Schlüsselwert verletzt eindeutige Einschränkung „nmsservice_name“ DETAIL: Schlüssel (sname)=(SVC4) existiert bereits. | 500 - Ein Fehler ist aufgetreten - Bitte Admin kontaktieren. |
| Verwenden einer nicht vorhandenen Roh-ID im URI | 404 - RST-360011 Ein Fehler ist aufgetreten - Bitte Admin kontaktieren. Dokument mit dem Pfad &#39;Service&#39; kann nicht ausgehend vom Schlüssel &#39;adobe_nl:0&#39; gefunden werden (Dokument mit Schema &#39;service&#39; und Namen &#39;adobe_nl&#39;) | 404 - Dokument mit dem Pfad &#39;Service&#39; kann nicht über den Schlüssel &#39;adobe_nl&#39; gefunden werden (Dokument mit dem Schema &#39;service&#39; und dem Namen &#39;adobe_nl&#39;) |
| Verwenden einer nicht vorhandenen Raw-ID im Anfrageinhalt | 404 - RST-360011 Ein Fehler ist aufgetreten - Bitte Admin kontaktieren. Dokument mit dem Pfad &#39;Service&#39; kann nicht ausgehend vom Schlüssel &#39;adobe_nl&#39; gefunden werden (Dokument mit Schema &#39;service&#39; und Namen &#39;adobe_nl&#39;) | 404 - Dokument mit dem Pfad &#39;Service&#39; kann nicht über den Schlüssel &#39;adobe_nl&#39; gefunden werden (Dokument mit dem Schema &#39;service&#39; und dem Namen &#39;adobe_nl&#39;) |
| – | 500 - RST-360011 Ein Fehler ist aufgetreten - Bitte Admin kontaktieren. | 500 - Ein Fehler ist aufgetreten - Bitte Admin kontaktieren. |
| Fügen Sie ein Profil/einen Service mit einem ungültigen Aufzählungswert für Geschlecht (oder sonstiges) ein. | 500 - RST-360011 Ein Fehler ist aufgetreten - Bitte Admin kontaktieren. Der Wert &#39;ungültig&#39; ist für die Auflistung &#39;nms:recipient:gender&#39; des Feldes &#39;@gender&#39; ungültig | 500 - Ein Fehler ist aufgetreten - Bitte Admin kontaktieren. |

## Profil - Zeitzone

Bei Campaign Standard wird die Zeitzone als Teil der JSON-Antwort der REST-API **Aufrufe von „profileAndServices**/profile“ angezeigt.

In Campaign v8 wird die Zeitzone Benutzenden nur als Teil der REST-API **Aufrufe von „profileAndServicesExt/profile** angezeigt. Sie ist nicht Teil der **profileAndServices/profile** REST-API-Aufrufe, da sie in einem erweiterten Schema hinzugefügt wird.

## Workflows - Auslösen externer Signale

Die Campaign Standard Workflow GET-API gibt Parameternamen wie die Workflow-Instanzvariablen und deren Datentypen (boolesch, Zeichenfolge usw.) zurück. Dies wird verwendet, um beim Auslösen des Signals über einen POST-API-Aufruf einen entsprechend formatierten JSON-Anfragetext zu erstellen.

Campaign v8 unterstützt keine Advertising Workflow-Instanzvariablen, erwartet jedoch, dass die Entwickler wissen, was diese sind. Daher müssen nach der Migration Parameterinformationen im POST-Anfragetext ohne Parameterinformationen in der GET-API-Antwort erstellt werden.

<!--## Transactional messages

* With Campaign Standard, a POST request returns empty fields for elements and attributes in the request body. With Campaign v8, the response returns values that match the ones in the request body instead.

* When publishing an event configuration, the API preview panel displays the REST URL alongside the request body syntax.

    Since Campaign v8 does not support event configuration fields definition (event creation is just adding a value to eventType enumeration), there is no API preview panel when adding an event type. The REST URL is displayed  in the transactional message user interface once an event transactional message is published.-->
