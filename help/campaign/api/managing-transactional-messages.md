---
title: Verwalten von Transaktionsnachrichten
description: Erfahren Sie, wie Sie Transaktionsnachrichten mit APIs verwalten.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
badge: label="EINGESCHRÄNKTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzende beschränkt"
exl-id: 00d39438-a232-49f1-ae5e-1e98c73397e3
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 76%

---

# Verwalten von Transaktionsnachrichten {#managing-transactional-messages}

>[!AVAILABILITY]
>
>Derzeit ist Transaktionsnachrichten mithilfe von REST-APIs für die E-Mail- und SMS-Kanäle verfügbar. Sie ist nur für Transaktionsereignisse verfügbar (Anreicherungsdaten sind nur über Payload verfügbar, ähnlich wie in Adobe Campaign V8).

Nachdem Sie ein Transaktionsereignis erstellt und veröffentlicht haben, müssen Sie die Aktivierung dieses Ereignisses in Ihre Website integrieren.

Sie möchten zum Beispiel, dass ein &quot;Warenkorbabbruch&quot; ausgelöst wird, wenn ein Kunde Ihre Website verlässt, bevor er die Produkte in seinem Warenkorb gekauft hat. Dazu muss Ihr Web-Entwickler die REST Transactional Messages-API verwenden.

1. Senden Sie anhand der POST-Methode eine Anfrage, die das [Senden des Transaktionsereignisses](#sending-a-transactional-event) auslöst.
1. Die Antwort auf die POST-Anfrage enthält einen Primärschlüssel, mit dem Sie eine oder mehrere Anfragen über eine GET-Anfrage senden können. Sie können dann den [Ereignisstatus](#transactional-event-status) abrufen.

## Senden eines Transaktionsereignisses {#sending-a-transactional-event}

Das Transaktionsereignis wird über eine POST-Anfrage mit der folgenden URL-Struktur gesendet:

```
POST https://mc.adobe.io/<ORGANIZATION>/campaign/<transactionalAPI>/<eventID>
```

* **&lt;ORGANISATION>**: Ihre persönliche Organisationskennung. Weitere Informationen finden Sie in [diesem Abschnitt](must-read.md).

* **&lt;transactionalAPI>**: die Endpunkte der Transaktionsnachrichten-API.

  Der Name des API-Endpunkts für Transaktionsnachrichten hängt von der Konfiguration Ihrer Instanz ab. Er entspricht dem Wert &quot;mc&quot;, gefolgt von Ihrer persönlichen Organisationskennung. Nehmen wir als Beispiel das Unternehmen Geometrixx mit der Organisationskennung &quot;geometrixx&quot;. In diesem Fall sieht die POST-Anfrage wie folgt aus:

  `POST https://mc.adobe.io/geometrixx/campaign/mcgeometrixx/<eventID>`

* **&lt;eventID>**: der Ereignistyp, den Sie senden möchten. Diese ID wird beim Erstellen der Ereigniskonfiguration generiert

### POST-Anfrage-Kopfzeile

Die Anfrage muss eine &quot;Inhaltstyp: application/json&quot;-Kopfzeile beinhalten.

Sie müssen einen Zeichensatz hinzufügen, z. B. **utf-8**. Beachten Sie, dass dieser Wert von der verwendeten REST-Anwendung abhängt.

```
-X POST \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-H 'Content-Type: application/json;charset=utf-8' \
-H 'Content-Length:79' \
```

### POST-Anfrage-Hauptteil

Die Ereignisdaten sind im JSON-POST-Hauptteil enthalten. Die Ereignisstruktur hängt von ihrer Definition ab.

Die folgenden optionalen Parameter können zum Ereignisinhalt hinzugefügt werden, um das Senden von mit dem Ereignis verknüpften Transaktionsnachrichten zu verwalten:

* **Ablauf** (optional): Nach diesem Datum wird das Senden des Transaktionsereignisses abgebrochen.
* **Geplant** (optional): Ab diesem Datum wird das Transaktionsereignis verarbeitet und die Transaktionsnachricht gesendet.

>[!NOTE]
>
>Die Werte der Parameter &quot;Ablauf&quot; und &quot;Geplant&quot; entsprechen dem ISO 8601-Format. ISO 8601 gibt die Verwendung des Großbuchstabens &quot;T&quot; zur Trennung von Datum und Uhrzeit an. Dies kann jedoch aus der Ein- oder Ausgabe entfernt werden, um die Lesbarkeit zu verbessern.

### Parameter des Kommunikationskanals

Je nach zu verwendendem Kanal sollte die Payload die folgenden Parameter enthalten:

* E-Mail-Kanal: „Mobiltelefon“
* SMS-Kanal: „email“

Wenn die Payload nur „Mobiltelefon“ enthält, wird der SMS-Kommunikationskanal ausgelöst. Wenn die Payload nur „E-Mail“ enthält, wird der E-Mail-Kommunikationskanal ausgelöst.

Das folgende Beispiel zeigt eine Payload, bei der eine SMS-Kommunikation ausgelöst wird:

```
curl --location 'https://mc.adobe.io/<ORGANIZATION>/campaign/mcAdobe/EVTcartAbandonment' \
--header 'Authorization: Bearer <ACCESS_TOKEN>' \
--header 'Cache-Control: no-cache' \
--header 'X-Api-Key: <API_KEY>' \
--header 'Content-Type: application/json;charset=utf-8' \
--header 'Content-Length: 79' \
--data '
{
  "mobilePhone":"+9999999999",
  "scheduled":"2017-12-01 08:00:00.768Z",
  "expiration":"2017-12-31 08:00:00.768Z",
  "ctx":
  {
    "cartAmount": "$ 125",
    "lastProduct": "Leather motorbike jacket",
    "firstName": "Jack"
  }
}'
```

Wenn die Payload sowohl „E-Mail“ als auch „Mobiltelefon“ enthält, ist die standardmäßige Kommunikationsmethode E-Mail. Um eine SMS zu senden, wenn beide Felder vorhanden sind, müssen Sie sie explizit in der Payload mit dem Parameter „wishChannel“ angeben.

### Antwort auf die POST-Anfrage

Die POST-Antwort gibt den Status des Transaktionsereignisses zum Zeitpunkt der Erstellung zurück. Verwenden Sie zum Abrufen des aktuellen Status (Ereignisdaten, Ereignisstatus...) den in einer GET-Anfrage von der POST-Antwort zurückgegebenen Primärschlüssel:

`GET https://mc.adobe.io/<ORGANIZATION>/campaign/<transactionalAPI>/<eventID>/`

<br/>

***Beispielanfrage***

POST-Anfrage zum Senden des Ereignisses.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/mcAdobe/EVTcartAbandonment \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-H 'Content-Type: application/json;charset=utf-8' \
-H 'Content-Length:79'

{
  "
  
  
  ":"test@example.com",
  "scheduled":"2017-12-01 08:00:00.768Z",
  "expiration":"2017-12-31 08:00:00.768Z",
  "ctx":
  {
    "cartAmount": "$ 125",
    "lastProduct": "Leather motorbike jacket",
    "firstName": "Jack"
  }
}
```

Antwort auf die POST-Anfrage.

```
{
  "PKey":"<PKEY>",
  "ctx":
  {
    "cartAmount": "",
    "lastProduct": "",
    "firstName": ""
  }
  "email":"",
  "scheduled":"2017-12-01 08:00:00.768Z",
  "expiration":"2017-12-31 08:00:00.768Z",
  "href": "mcAdobe/EVTcartAbandonment/<PKEY>",
  "serverUrl":" https://myserver.com ",
  "status":"pending",
  "type":""
}
```

### Status des Transaktionsereignisses {#transactional-event-status}

In der Antwort können Sie im Feld &quot;Status&quot; ermitteln, ob das Ereignis verarbeitet wurde oder nicht:

* **Ausstehend**: Das Ereignis steht aus – das Ereignis erhält diesen Status, wenn es gerade ausgelöst wurde.
* **Verarbeitung läuft**: Das Ereignis muss noch versandt werden – es wird in eine Nachricht umgewandelt und die Nachricht wird gesendet.
* **Angehalten**: Der Ereignisvorgang wurde angehalten. Sie wird nicht mehr verarbeitet, sondern in einer Warteschlange in der Adobe Campaign-Datenbank aufbewahrt.
* **Verarbeitet**: Das Ereignis wurde verarbeitet und die Nachricht wurde erfolgreich gesendet.
* **Ignoriert**: Das Ereignis wurde vom Versand ignoriert, normalerweise dann, wenn eine Adresse unter Quarantäne steht.
* **Versand fehlgeschlagen**: Bei der Verarbeitung des Ereignisses ist ein Versandfehler aufgetreten.
* **Routing fehlgeschlagen**: Die Routing-Phase ist fehlgeschlagen. Dies kann beispielsweise geschehen, wenn der angegebene Ereignistyp nicht gefunden werden kann.
* **Zu alt**: Das Ereignis ist abgelaufen, bevor es verarbeitet werden konnte. Das kann verschiedene Gründe haben, z. B. wenn ein Senden mehrmals fehlschlägt (was dazu führt, dass das Ereignis nicht mehr aktuell ist) oder der Server Ereignisse nach einer Überlastung nicht mehr verarbeiten kann.
