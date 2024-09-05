---
title: Recommendations und Einschränkungen
description: Recommendations und Einschränkungen bei der Migration zu Campaign v8 REST-APIs.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
mini-toc-levels: 1
badge: label="BEGRENZTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzer beschränkt"
exl-id: 45acebb1-9325-4e26-8fe9-cc73f745d801
source-git-commit: 6e4e214731b9772014d01dde89b3f80e4c4e93a6
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 1%

---

# Recommendations und Einschränkungen {#limitations}

## Berechtigungen und Sicherheit {#permissions}

### Produktprofilzuordnung

Im Campaign Standard wurde Ihnen ungeachtet Ihres zugewiesenen Produktprofils ein erhöhter Administratorrollenzugriff auf APIs gewährt. Campaign v8 führt einen anderen Satz von Produktprofilen ein, was eine Zuordnung von Campaign Standard zu Campaign v8-Produktprofilen erfordert.

Mit der Migration werden Ihren vorhandenen oder vorab erstellten technischen Konten zwei Produktprofile hinzugefügt: Administrator und Message Center (für den Zugriff auf Transaktions-APIs). Überprüfen Sie das Produktprofil-Mapping und weisen Sie das benötigte Produktprofil zu, wenn das Admin-Produktprofil nicht Ihrem technischen Konto zugeordnet werden soll.

### Mandanten-ID

Nach der Migration wird für alle zukünftigen Integrationen empfohlen, Ihre **Campaign v8-Mandanten-ID** in REST-URLs zu verwenden und Ihre vorherige Mandanten-ID des Campaign Standards zu ersetzen.

### Schlüsselverwendung

Die Verwaltung von PKey-Werten unterscheidet sich zwischen Campaign Standard und Campaign v8. Wenn Sie PKeys mit Campaign Standard gespeichert haben, stellen Sie sicher, dass Ihre Implementierung nachfolgende API-Aufrufe mit PKeys dynamisch formt oder href aus vorherigen API-Aufrufen erhält.

## Verfügbare APIs {#deprecated}

Derzeit sind die unten aufgeführten REST-APIs zur Verwendung verfügbar:

* **Profile**
* **Dienste und Abonnements**
* **Benutzerdefinierte Ressourcen**
* **Workflows**

>[!AVAILABILITY]
>
>Derzeit ist die REST-API für **Transaktionsnachrichten** nicht verfügbar.
>
>Die unten aufgeführten REST-APIs sind veraltet und stehen nicht zur Verwendung zur Verfügung:
>* Marketing-Verlauf
>* Organisationseinheiten
>* Datenschutzverwaltung

## Filter

* Um Ihre Filter in REST-API-Payloads zu verwenden, müssen Sie sie in Campaign v8 bearbeiten und einen Namen angeben, der in Ihren Payloads verwendet werden soll. Greifen Sie dazu über die Registerkarte **[!UICONTROL Parameter]** auf die zusätzlichen Parameter des Filters zu und geben Sie den gewünschten Namen im Feld **[!UICONTROL Filtername in REST API]** ein.

  ![](assets/api-filtering.png)


* Das für die Verwendung benutzerdefinierter Filter erforderliche Präfix &quot;by&quot;ist nicht mehr erforderlich. Der Filtername sollte unverändert in Ihren Anforderungen verwendet werden.

  Beispiel:

  `GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/<resourceName>/<customFilterName>?<customFilterparam>=<customFilterValue>`

## Dropped Datenbankfelder

Einige Felder aus der Datenbank werden während der Migration gelöscht. Bei Verwendung eines abgelegten Felds geben REST-APIs leere Werte zurück. In Zukunft werden alle abgelegten Felder nicht mehr unterstützt und entfernt.

## POST mit verknüpften Ressourcen

Bei Verwendung des folgenden Anfrageinhaltsformats, bei dem die Relation zu &quot;nms:recipient&quot;durch &quot;FahrzeugOwner&quot;repräsentiert wird:

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

Die Linkinformationen werden ignoriert. Folglich wird ein neuer Datensatz unter &quot;cusVehicle&quot; erstellt, der nur die Werte &quot;FahrzeugNumber&quot; und &quot;FahrzeugName&quot; enthält. Der Link bleibt jedoch null, was dazu führt, dass &quot;carOwner&quot;auf null gesetzt wird.

Wenn in Campaign v8 dieselbe Struktur des Anfragetexts verwendet wird und das &quot;Fahrzeug&quot; mit einem Profil verknüpft ist, tritt ein Fehler auf. Dieser Fehler tritt auf, weil die Eigenschaft &quot;firstName&quot;für &quot;cusVehicle&quot;nicht als gültig erkannt wird. Ein Anfragetext, der nur die Attribute ohne Link enthält, funktioniert jedoch ohne Probleme.

## PATCH-Vorgänge

* Campaign v8 unterstützt kein PATCH mit einem leeren Anfrageinhalt: Es wird der Status &quot;204 Kein Inhalt&quot;zurückgegeben.
* Campaign Standard unterstützt zwar das PATCH von Elementen/Attributen innerhalb eines Schemas, beachten Sie jedoch, dass PATCH-Vorgänge am Standort in Campaign v8 nicht unterstützt werden. Beim Versuch, eine PATCH an einem Ort durchzuführen, wird ein 500-Fehler mit einer Fehlermeldung angezeigt, die angibt, dass die Eigenschaft &quot;zipCode&quot;für die Ressource &quot;profile&quot;nicht gültig ist.

## REST-Antworten

Im folgenden Abschnitt werden geringfügige Unterschiede zwischen Campaign Standard- und v8-REST-Antworten aufgeführt.

* Bei einzelnen GET enthält die Antwort das href in der Antwort.
* Wenn mit dem -Attribut abgefragt wird, bietet Campaign v8 in der Antwort &quot;Count&quot;(Zählung) und &quot;Paginierung&quot;(Paginierung).
* Nach der POST werden in der Antwort Werte aus verknüpften Ressourcen zurückgegeben.

## Fehlercodes und -nachrichten

Im folgenden Abschnitt finden Sie die Unterschiede zwischen den Fehlercodes und -nachrichten von Campaign Standard und Campaign v8.

| Szenario | Campaign Standard | Campaign v8 |
|  ---  |  ---  |  ---  |
| Verwenden eines ungültigen PKey im Anfrageinhalt | 500 - Attribut &#39;O5iRp40EGA&#39; unbekannt (siehe Definition des Schemas &#39;Profile (nms:recipient)&#39;). XTK-170036 Ausdruck &#39;@id = @O5iRp40EGA&#39; kann nicht analysiert werden. | 404 - PKey kann nicht entschlüsselt werden. (PKey=@jksad) |
| Verwenden eines ungültigen PKey in URI | 500 - Attribut &#39;O5iRp40EGA&#39; unbekannt (siehe Definition des Schemas &#39;Profile (nms:recipient)&#39;). XTK-170036 Ausdruck &#39;@id = @O5iRp40EGA&#39; kann nicht analysiert werden. | 404 - PKey kann nicht entschlüsselt werden. (PKey=@jksad) Nicht unterstützter Endpunkt. (endpoint=rest/profileAndServices/profile/@jksad) |
| Verwenden von zwei verschiedenen Pkeys im URI- und Anfrageinhalt | 500 - RST-360011 Es ist ein Fehler aufgetreten - wenden Sie sich an Ihren Administrator. RST-360012 Inkonsistenter Betrieb der Ressource &#39;service&#39; - Schlüssel &#39;SVC3&#39; kann nicht auf &#39;SVC4&#39; aktualisiert werden. | 500 - Ein Fehler ist aufgetreten. Wenden Sie sich an Ihren Administrator. |
| Verwenden von PKey im URI und einem anderen PKey im Anfragetext | 500 - Ein &#39;Dienst&#39; mit dem gleichen Schlüssel &#39;SVC4&#39; ist bereits vorhanden. PGS-220000 PostgreSQL-Fehler: ERROR: Duplizierter Schlüsselwert verletzt eindeutige Einschränkung &quot;nmsservice_name&quot; DETAIL: Schlüssel (sname)=(SVC4) ist bereits vorhanden. | 500 - Ein Fehler ist aufgetreten. Wenden Sie sich an Ihren Administrator. |
| Verwenden nicht vorhandener Rohdaten in URI | 404 - RST-360011 Es ist ein Fehler aufgetreten - wenden Sie sich an Ihren Administrator. Dokument mit dem Pfad &quot;Service&quot;kann nicht über den Schlüssel &quot;adobe_nl:0&quot;gefunden werden (Dokument mit Schema &quot;service&quot;und Name &quot;adobe_nl&quot;) | 404 - Dokument mit dem Pfad &quot;Dienst&quot;aus dem Schlüssel &quot;adobe_nl&quot;nicht finden (Dokument mit Schema &quot;service&quot;und Name &quot;adobe_nl&quot;) |
| Verwenden nicht vorhandener Rohdaten im Anfrageinhalt | 404 - RST-360011 Es ist ein Fehler aufgetreten - wenden Sie sich an Ihren Administrator. Dokument mit dem Pfad &quot;Dienst&quot;kann nicht über den Schlüssel &quot;adobe_nl&quot;gefunden werden (Dokument mit Schema &quot;service&quot;und Name &quot;adobe_nl&quot;) | 404 - Dokument mit dem Pfad &quot;Dienst&quot;aus dem Schlüssel &quot;adobe_nl&quot;nicht finden (Dokument mit Schema &quot;service&quot;und Name &quot;adobe_nl&quot;) |
| – | 500 - RST-360011 Es ist ein Fehler aufgetreten - wenden Sie sich an Ihren Administrator. | 500 - Ein Fehler ist aufgetreten. Wenden Sie sich an Ihren Administrator. |
| Profil/Dienst mit ungültigem Enum-Wert (oder beliebigem Enum-Wert) einfügen | 500 - RST-360011 Es ist ein Fehler aufgetreten - wenden Sie sich an Ihren Administrator. Der Wert &#39;invalid&#39; ist nicht gültig für die Auflistung &#39;nms:recipient:gender&#39; des Felds &#39;@gender&#39;. | 500 - Ein Fehler ist aufgetreten. Wenden Sie sich an Ihren Administrator. |

## Profil - Zeitzone

Mit Campaign Standard wird die Zeitzone als Teil der JSON-Antwort von **profileAndServices/profile** REST-API-Aufrufen angezeigt.

Bei Campaign v8 wird die Zeitzone dem Benutzer nur im Rahmen von **profileAndServicesExt/profile** REST-API-Aufrufen angezeigt. Sie ist nicht Teil der REST-API-Aufrufe **profileAndServices/profile** , da sie in einem erweiterten Schema hinzugefügt werden.

## Workflows - Auslösung von Externem Signal

Die Campaign Standard Workflow-GET-API gibt Parameternamen wie die Workflow-Instanzvariablen und ihre Datentypen (boolesch, Zeichenfolge usw.) zurück. Damit wird beim Auslösen des Signals über einen POST-API-Aufruf ein entsprechend formatierter JSON-Anfrageinhalt erstellt.

Campaign v8 unterstützt keine Instanzvariablen im Werbe-Workflow, erwartet jedoch, dass Entwickler wissen, was diese sind. Daher müssen nach der Migration Parameterinformationen im Anfragetext der POST erstellt werden, ohne dass in der Antwort der GET API Parameterinformationen verfügbar sind.

<!--## Transactional messages

* With Campaign Standard, a POST request returns empty fields for elements and attributes in the request body. With Campaign v8, the response returns values that match the ones in the request body instead.

* When publishing an event configuration, the API preview panel displays the REST URL alongside the request body syntax.

    Since Campaign v8 does not support event configuration fields definition (event creation is just adding a value to eventType enumeration), there is no API preview panel when adding an event type. The REST URL is displayed  in the transactional message user interface once an event transactional message is published.-->
