---
title: Implementieren des Identitätsdienstes für Adobe Experience Platform mit dem Start
description: Erfahren Sie, wie Sie die Erweiterung des Identitätsdienstes für Adobe Experience Platform hinzufügen und mit der Aktion Kunden-IDs festlegen Kunden-IDs erfassen. Diese Lektion ist Teil des Tutorials "Implementieren der Experience Cloud in Mobile iOS Swift Applications".
seo-description: null
seo-title: Implementieren des Identitätsdienstes für Adobe Experience Platform mit dem Start
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: e9dee6d0aa3b775d0ce617e2b2c57b56de491b8d

---


# Adobe Experience Platform Identity Service hinzufügen

Der [Adobe Experience Platform-Identitätsdienst](https://docs.adobe.com/content/help/en/id-service/using/home.html) legt eine allgemeine Besucher-ID für alle Adobe-Lösungen fest, um Experience Cloud-Funktionen wie die Freigabe von Zielgruppen zwischen verschiedenen Lösungen zu nutzen.  Sie können auch Ihre eigenen Kunden-IDs an den Service senden, um geräteübergreifendes Targeting und Integrationen in Ihr CRM-System (Customer Relationship Management) zu aktivieren.

Der Identitätsdienst ist Teil der Mobile Core Extension, ***sodass Sie ihn bereits implementiert haben, wenn Sie das Mobile SDK*** installiert haben! Derzeit enthält dieses Lernprogramm keine Anweisungen zum Festlegen von Kunden-IDs. Einzelheiten zum [Festlegen von Kunden-IDs](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/identity/identity-api-reference)finden Sie in der Dokumentation.

## Überprüfungsschritte

Um die Aufrufe des Identitätsdienstes zu überprüfen, führen Sie die Beispielanwendung in Xcode oder Developer Studio aus, öffnen Sie die Debug-Konsole und suchen Sie nach der Anforderung und der Antwort:

1. **Anforderung an den Identitätsdienst** (Filtern Sie Ihre Konsole nach `demdex.net`) In diesem Beispiel wurde die ID (`d_mid`) bereits festgelegt und wird gerade erneut gemeldet)

   ```swift
   2019-01-15 12:11:45.164590-0500 BusDemoSwift[52399:5056322] [AMSDK DEBUG <com.adobe.module.identity>]: Sending request (https://dpm.demdex.net/id?d_rtbd=json&d_ver=2&d_orgid=7ABB3E6A5A7491460A495D61@AdobeOrg&d_mid=17179986463578698626041670574784107777&d_blob=j8Odv6LonN4r3an7LhD3WZrU1bUpAkFkkiY1ncBR96t2PTI&dcs_region=9)
   ```

1. **Antwort vom Identitätsdienst** (Filtern Sie Ihre Konsole auf `ID Service`). Beachten Sie, wie der `mid` Wert mit dem `d_mid` Wert in der oben stehenden Anforderung übereinstimmt:

   ```swift
   2019-01-15 12:11:45.681821-0500 BusDemoSwift[52399:5056322] [AMSDK DEBUG <com.adobe.module.identity>]: ID Service - Got ID Response (mid: 17179986463578698626041670574784107777, blob: j8Odv6LonN4r3an7LhD3WZrU1bUpAkFkkiY1ncBR96t2PTI, hint: 9, ttl: "604800000 ms")
   
[Weiter "Adobe Target VEC-Support hinzufügen"&gt;](target-vec.md)
