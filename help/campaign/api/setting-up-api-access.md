---
title: Einrichten von API-Zugriff
description: Erfahren Sie, wie Sie Zugriff auf Campaign Standard-APIs einrichten können.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="BEGRENZTE VERFÜGBARKEIT" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Auf Campaign Standard migrierte Benutzer beschränkt"
exl-id: efbbd0cd-9c56-4ad0-8bcb-efba4b63c28b
source-git-commit: 18979fea28f4f3adce1139293203a59876831313
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 95%

---

# Einrichten von API-Zugriff {#setting-up-api-access}

Der Zugriff auf Adobe Campaign Standard-APIs lässt sich mit den folgenden Schritten einrichten: Jeder dieser Schritte wird in der [Adobe Developer-Dokumentation](https://developer.adobe.com/developer-console/docs/guides/#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md) beschrieben.

>[!IMPORTANT]
>
>Um Zertifikate in [Adobe Developer](https://developer.adobe.com/) zu verwalten, stellen Sie sicher, dass Sie Rechte als **System-Administrator** für die Organisation oder ein [Entwicklerkonto](https://helpx.adobe.com/de/enterprise/using/manage-developers.html) in der Admin Console haben.

1. **Überprüfen Sie, ob Sie ein digitales Zertifikat haben**, oder erstellen Sie bei Bedarf eines. Die mit dem Zertifikat bereitgestellten öffentlichen und privaten Schlüssel werden in den folgenden Schritten benötigt.
1. **Erstellen Sie eine neue Integration mit Adobe Campaign Service** in [Adobe Developer](https://developer.adobe.com/) und konfigurieren Sie diese. Dann werden Ihre Zugangsdaten generiert (API-Schlüssel, Client-Geheimnis …).
1. **Erstellen Sie eine OAuth Server-to-Server**-Berechtigung, indem Sie die folgenden [Implementierungsschritte](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/) befolgen.

   >[!IMPORTANT]
   >
   >JWT (JSON Web Tokens) wird gerade eingestellt und durch OAuth ersetzt. Die Umstellung erfolgt schrittweise in den kommenden Campaign-Versionen. Die Anmeldedaten für das Service-Konto (JWT) wurden als veraltet gekennzeichnet, funktionieren jedoch weiterhin bis zum 27. Januar 2025. Daher müssen Sie Ihre Anwendung oder Integration migrieren, um die neuen OAuth-Server-zu-Server-Anmeldedaten vor dem 27. Januar 2025 zu verwenden. Die OAuth-Authentifizierung wird bevorzugt. Auf diesen Seiten finden Sie alle Elemente, um von der JWT-Authentifizierung zur OAuth-Authentifizierung zu migrieren:
   >* [Migration](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/)
   >* [Implementierung](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/)
   >* [Häufig gestellte Fragen zur Einstellung von JWT](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/faqs/)

Um eine sichere Service-to-Service-Adobe I/O-API-Sitzung herzustellen, muss jede Anfrage an einen Adobe-Dienst folgende Informationen in der Autorisierungskopfzeile umfassen.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

* **&lt;ORGANIZATION>**: Dies ist Ihre persönliche Organisationskennung; von Adobe erhalten Sie für jede Ihrer Instanzen eine Organisationskennung:

   * &lt;ORGANIZATION>: Ihre Produktionsinstanz,
   * &lt;ORGANIZATION-mkt-stage>: Ihre Staging-Instanz.

  Um den Wert der ORGANISATIONS-ID zu erhalten, wenden Sie sich wahlweise an Ihre Administrierenden oder Ihre technische Kontaktperson bei Adobe. Sie können sie auch beim Erstellen einer neuen Integration in Adobe I/O abrufen, und zwar in der Lizenzliste (siehe <a href="https://developer.adobe.com/developer-console/docs/guides/authentication/">Adobe Developer-Dokumentation</a>).

* **&lt;ACCESS_TOKEN>**: Ihr persönlicher Zugriffstoken, der beim Austausch Ihres JSON-Web-Token über eine POST-Anfrage abgerufen wurde.

* **&lt;API_KEY>**: Ihr persönlicher API-Schlüssel. Er wird in Adobe I/O bereitgestellt, nachdem eine neue Integration mit Adobe Campaign Service erstellt wurde.

  ![Alternativtext](assets/tenant.png)

## Fehlerbehebung

Wenn bei der Adobe I/O-Integration der folgende Fehler angezeigt wird:

```
{ 
"code": 502, 
"message": "Oops. Something went wrong. Check your URI and try again." 
}
```


Wenden Sie sich an Ihren Administrator oder Ihren technischen Ansprechpartner bei Adobe, um zu prüfen, ob der Parameter CNAME korrekt erstellt wurde.
