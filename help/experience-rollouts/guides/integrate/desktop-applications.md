---
title: Desktop-Programme
description: Erfahren Sie, wie Sie Adobe Experience Rollouts mithilfe der Feature API V2 in ein Desktop-Programm integrieren.
source-git-commit: b82520eebe0070b5f76e0f7daeb2bb79a4bccca0
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 2%

---


# Desktop-Programme {#desktop-applications}

Desktop-Programme lassen sich durch direkte REST-API-Aufrufe in Experience Rollouts integrieren. Verwenden Sie die **Feature API V2** für Desktop-Clients.

Siehe **GET Feature API V2** im Abschnitt Funktions-API dieses Handbuchs für die vollständige API-Referenz.

## Integrationsanforderungen {#requirements}

Desktop-Clients müssen:

* **Berücksichtigen Sie den TTL** Wert, der in der API-Antwort zurückgegeben wird. Die TTL definiert, wie lange der Client Feature Flag-Daten zwischenspeichern soll, bevor er die API erneut aufruft. Implementieren Sie einen Testfall, der dieses Verhalten überprüft, um sicherzustellen, dass ältere Anwendungsversionen korrekt in den Ruhezustand übergehen, wenn keine Feature Flags bereitgestellt werden.
* **Handhabung von HTTP-Fehlerszenarien**. Erstellen Sie einen Fallback-Funktionssatz, damit die Anwendung funktionsfähig bleibt, wenn die API vorübergehend nicht verfügbar ist.
* **Führen Sie einen detaillierten Integrationstestplan durch** der sowohl die oben genannten TTL- als auch die Fehlerbehandlungsanforderungen abdeckt.

## Anwendungs-ID {#app-id}

Desktop-Clients können beim Aufrufen der API anstelle **standardmäßigen Client-ID einen** Produkt-Code und eine Produktversion) als Anwendungs-ID verwenden.

## Siehe auch {#see-also}

* [Integrationsschritte](integration-steps.md)
* [Starthandbuch](startup-guide.md)
