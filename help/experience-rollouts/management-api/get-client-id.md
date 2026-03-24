---
title: Client-ID für ein Programm abrufen
description: Erfahren Sie, wie Sie die numerische Client-ID für eine Anwendung in der Konsole „Experience Rollouts“ finden, die beim Aufrufen der Verwaltungs-APIs erforderlich ist.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---


# Client-ID für ein Programm abrufen {#get-client-id}

Für Feature Flags und Feature Group Management-APIs ist eine numerische `clientId` erforderlich, um zu identifizieren, zu welcher Anwendung die Funktion gehört. Dies unterscheidet sich von der zeichenfolgenbasierten IMS-Client-ID, die für die API-Authentifizierung verwendet wird.

Führen Sie diese Schritte aus, um die numerische Client-ID für eine Anwendung zu finden.

## Schritte {#steps}

Gehen Sie wie folgt vor, um die numerische Client-ID für eine Anwendung zu finden:

1. Melden Sie sich bei der Konsole „Experience Rollouts“ an.
2. Navigieren Sie zu **Funktionen und Versionen**.
3. Wählen Sie die Registerkarte **Feature Flags** aus.
4. Öffnen Sie das **Programm** und wählen Sie die Anwendung aus, deren Client-ID Sie benötigen.
5. Sehen Sie sich die URL in der Adressleiste Ihres Browsers an. Nach dem `feature-flags/` ist die angezeigte Zahl die numerische Client-ID für diese Anwendung.

Wenn die URL beispielsweise mit `.../feature-flags/1191/...` endet, wird die Client-ID `1191`.

## Verwenden der Client-ID in API-Aufrufen {#use-in-api}

Übergeben Sie diesen Wert als `clientId` in Verwaltungs-API-Anfragen. Wenn Sie beispielsweise ein Feature Flag erstellen:

```json
{
  "name": "my-feature-flag",
  "clientId": 1191,
  "state": "disabled"
}
```

## Siehe auch {#see-also}

* [Feature Flags Management-API](feature-flags-management-api.md)
* [Feature Group Management-API](feature-group-management-api.md)
* [Abrufen der gewünschten Zielgruppenkriterien](get-audience-criteria.md)
