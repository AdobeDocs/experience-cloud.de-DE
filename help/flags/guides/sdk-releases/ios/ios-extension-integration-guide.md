---
title: Handbuch zur Integration der Experience Rollout-Erweiterung für iOS
description: Erfahren Sie, wie Sie die Experience Rollout-Erweiterung mit Adobe Experience Platform Mobile SDK auf iOS integrieren.
hide: true
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 8%

---

# Experience Rollout-Erweiterung für iOS {#ios-extension-integration-guide}

In diesem Handbuch wird beschrieben, wie Sie die Experience Rollout-Erweiterung in Adobe Experience Platform Mobile SDK in iOS integrieren.

## Voraussetzungen {#prerequisites}

Stellen Sie vor der Implementierung der Experience Rollout-Erweiterung Folgendes sicher:

* Eine Mobile-Eigenschaft, die in der Datenerfassung von [Adobe Experience Platform konfiguriert ist](https://experience.adobe.com/#/data-collection)
* Die in Ihrer Mobile-Eigenschaft installierte und konfigurierte Experience Rollout-Erweiterung
* Eine Adobe Experience Cloud-Organisations-ID
* Mindestziel für die Bereitstellung: iOS 12.0
* Xcode 14.1 oder höher

## Abhängigkeiten der Erweiterung {#extension-dependencies}

Für die Erweiterung „Experience Rollout“ sind die folgenden Adobe Experience Platform-Erweiterungen erforderlich:

| Erweiterung | Beschreibung | Erforderlich |
|---|---|---|
| Core für Mobilgeräte | Bietet Kernfunktionen, einschließlich Konfiguration und Ereignisverarbeitung | Ja |
| Lebenszyklus | Erfasst Anwendungslebenszyklus- und Sitzungsdaten für die Mobile SDK | Ja |
| Edge Network | Ermöglicht die Kommunikation mit Adobe Experience Platform Edge Network | Ja |
| Edge-Identität | Verwaltet die Benutzeridentität für Edge Network | Ja |

Stellen Sie sicher, dass diese Erweiterungen in Ihrer Datenerfassungs-Eigenschaft für Mobilgeräte installiert und in Ihren App-Abhängigkeiten enthalten sind.

## Konfigurieren der Experience Rollout-Erweiterung in der Datenerfassung {#configure}

### Installieren der Erweiterung {#install-extension}

1. Melden Sie sich bei der [Adobe Experience Platform-Datenerfassung](https://experience.adobe.com/#/data-collection) an.
1. Wählen Sie die Registerkarte **Tags** und dann Ihre Mobile-Eigenschaft aus.
1. Navigieren Sie **Erweiterungen** > **Katalog**.
1. Suchen Sie nach **Experience Rollout-Erweiterung** und wählen Sie **Installieren** aus.
1. Konfigurieren Sie die Erweiterungseinstellungen:

   | Einstellung | Beschreibung |
   |---|---|
   | Sandbox | Die Adobe Experience Platform-Sandbox mit Ihrer Experience Rollout-Konfiguration |
   | Anwendungs-ID | Eine eindeutige Kennung für Ihr Programm im Experience Rollout |
   | Datensatz-ID | Die Adobe Experience Platform-Datensatz-ID für die Analytics-Ereignisdaten |

1. Wählen Sie **Speichern** aus.
1. Befolgen Sie den [Veröffentlichungsprozess](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/overview), um Ihre Konfiguration zu aktualisieren.

### Abrufen der Umgebungsdatei-ID {#environment-file-id}

1. Navigieren Sie in Ihrer Mobile-Eigenschaft zu **Umgebungen**.
1. Wählen Sie das Kästchen-Symbol unter der Spalte **Installieren** für Ihre Umgebung aus.
1. Kopieren Sie **Dialogfeld „Mobile-**&quot; die **Umgebungsdatei-ID**.

## Hinzufügen der Experience Rollout-Erweiterung zu Ihrer App {#add-to-app}

### Hinzufügen von Abhängigkeiten {#add-dependencies}

Fügen Sie die Mobile SDK-Abhängigkeiten zu Ihrem Projekt hinzu. Für die Erweiterung „Experience Rollout“ sind Mobile Core und die unten aufgeführten Edge-Erweiterungen erforderlich.

#### Verwenden von Swift Package Manager (empfohlen) {#swift-package-manager}

1. Navigieren Sie in Xcode zu **Datei** > **Paketabhängigkeiten hinzufügen**.
1. Geben Sie die Adobe Experience Platform Mobile SDK Repository-URL ein:

   ```
   https://github.com/adobe/aepsdk-core-ios
   ```

1. Fügen Sie die folgenden Pakete hinzu:

   | Paket | Repository |
   |---|---|
   | AEPCore, AEPLifecycle | `https://github.com/adobe/aepsdk-core-ios` |
   | AEPEdge | `https://github.com/adobe/aepsdk-edge-ios` |
   | AEPEdgeIdentity | `https://github.com/adobe/aepsdk-edgeidentity-ios` |
   | AEPRollout | `https://github.com/adobe/aepsdk-rollout-ios` |

#### Verwenden von Kakaofrüchten {#cocoapods}

Fügen Sie die folgenden Pods zu Ihrem `Podfile` hinzu:

```ruby
pod 'AEPCore'
pod 'AEPLifecycle'
pod 'AEPEdge'
pod 'AEPEdgeIdentity'
pod 'AEPRollout'
```

Führen Sie dann aus:

```bash
pod install
```

>[!IMPORTANT]
>
>Für Produktionsanwendungen empfiehlt Adobe, an explizite Versionsnummern anzuheften, anstatt `~>` oder offene Bereiche zu verwenden. Weitere Informationen finden Sie [&#x200B; „CocoaPods](https://guides.cocoapods.org/using/the-podfile.html)Versionshandbuch“.

### SDK initialisieren {#initialize-sdk}

Initialisieren Sie die Mobile SDK in Ihrem `AppDelegate` (oder `SceneDelegate`), bevor Sie APIs für Experience Rollout-Erweiterungen aufrufen. Verwenden Sie die Umgebungsdatei-ID aus Ihrer Mobile-Eigenschaft, damit die App die Rollout-Einstellungen übernimmt, die Sie in der Datenerfassung veröffentlicht haben.

**SWIFT**

```swift
import AEPCore
import AEPLifecycle
import AEPEdge
import AEPEdgeIdentity
import AEPRollout

@main
class AppDelegate: UIResponder, UIApplicationDelegate {

    func application(
        _ application: UIApplication,
        didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?
    ) -> Bool {

        MobileCore.setLogLevel(.error)

        MobileCore.registerExtensions(
            [Lifecycle.self, Edge.self, Identity.self, Rollout.self]
        ) {
            // Initialize with your Environment File ID from Data Collection
            MobileCore.configureWith(appId: "YOUR_ENVIRONMENT_FILE_ID")
        }

        return true
    }
}
```

**Objective-C**

```objc
@import AEPCore;
@import AEPLifecycle;
@import AEPEdge;
@import AEPEdgeIdentity;
@import AEPRollout;

@implementation AppDelegate

- (BOOL)application:(UIApplication *)application
    didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    [AEPMobileCore setLogLevel:AEPLogLevelError];

    NSArray *extensions = @[
        AEPMobileLifecycle.class,
        AEPMobileEdge.class,
        AEPMobileEdgeIdentity.class,
        AEPMobileRollout.class
    ];

    [AEPMobileCore registerExtensions:extensions completion:^{
        // Initialize with your Environment File ID from Data Collection
        [AEPMobileCore configureWithAppId:@"YOUR_ENVIRONMENT_FILE_ID"];
    }];

    return YES;
}

@end
```

>[!IMPORTANT]
>
>Verwenden Sie für Produktions-Apps nur `LogLevel.error`. Verwenden Sie `.debug` oder `.verbose` nicht in Release-Builds.

## Auswertungskontext {#evaluation-context}

`FeatureEvaluationContext` umfasst Zielgruppenattribute (für die Zuordnung von Rollout-Regeln verwendet) und optionale Identität (für Analysen verwendet).

| Methode | Erforderlich | Beschreibung |
|---|---|---|
| `withIdentity(namespace:id:)` | Nein | Erstes Argument: Identity-Namespace (siehe [Adobe Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)). Zweites Argument: Identitätswert. Schließen Sie dies ein, wenn dieser Namespace und diese ID in Analytics für diese Auswertung dargestellt werden sollen. Falls nicht angegeben, verwendet Analytics standardmäßig die ECID. Dies wird nicht verwendet, um Entscheidungen zur Aktivierung von Funktionen zu fördern. |
| `withAttributes(_:)` | Nein | `[String: [String]]`. Der Schlüssel ist der Kontextattributname, der von Ihren Rollout-Regeln verwendet wird (z. B. `locale`, `platform`, `appVersion`, `deviceType`). Wert ist die Liste der möglichen Attributwerte für diesen Schlüssel für den aktuellen Benutzer/die aktuelle Sitzung (z. B. `["en_US"]` oder `["phone"]`). |

**SWIFT**

```swift
import AEPRollout

let attrs: [String: [String]] = [
    "locale": ["en_US"],
    "platform": ["IOS"],
    "appVersion": ["3.0.0"]
]

let ctx = FeatureEvaluationContext.builder()
    .withIdentity(namespace: "Email", id: "customer@example.com")
    .withAttributes(attrs)
    .build()
```

**Objective-C**

```objc
@import AEPRollout;

NSDictionary<NSString *, NSArray<NSString *> *> *attrs = @{
    @"locale": @[@"en_US"],
    @"platform": @[@"IOS"],
    @"appVersion": @[@"3.0.0"]
};

AEPFeatureEvaluationContext *ctx = [[[AEPFeatureEvaluationContextBuilder builder]
    withIdentityNamespace:@"Email" id:@"customer@example.com"]
    withAttributes:attrs]
    .build;
```

### Beispiele für Zielgruppenattribute {#sample-attributes}

| Attribut | Beschreibung | Beispielwerte |
|---|---|---|
| `locale` | Gebietsschema/Sprache des Benutzers | `["en_US"]`, `["fr_FR"]` |
| `platform` | Plattformkennung | `["IOS"]` |
| `appVersion` | Anwendungsversion | `["3.0.0"]` |
| `deviceType` | Gerätetyp | `["phone"]`, `["tablet"]` |

## API-Referenz {#api-reference}

### isFeatureEnabled {#is-feature-enabled}

`isFeatureEnabled` gibt zurück, ob eine Experience Rollout-Funktion für den jeweiligen Kontext aktiviert oder deaktiviert ist. Übergeben Sie `featureKey`, einen `FeatureEvaluationContext` (optionale Zielgruppenattribute und optionale Identität für Analytics) und einen Fertigstellungs-Handler. Siehe [Evaluierungskontext](#evaluation-context).

**Signatur**

*SWIFT*

```swift
Rollout.isFeatureEnabled(
    featureKey: String,
    evaluationContext: FeatureEvaluationContext,
    completion: @escaping (Bool) -> Void
)
```

*Objective-C*

```objc
[AEPMobileRollout isFeatureEnabled:(NSString *)featureKey
               evaluationContext:(AEPFeatureEvaluationContext *)evaluationContext
                      completion:(void (^)(BOOL))completion];
```

**Parameter**

| Parameter | Typ | Beschreibung |
|---|---|---|
| `featureKey` | Zeichenfolge | Funktionsschlüssel zur Auswertung im Erlebnis-Rollout |
| `evaluationContext` | FeatureEvaluationContext | Zielgruppenattribute und optionale Identität für die Analyse nach Bedarf einschließen; `FeatureEvaluationContext.builder().build()` für einen leeren Kontext verwenden. Siehe [Evaluierungskontext](#evaluation-context). |
| `completion` | `(Bool) -> Void` | Wird mit `true` aufgerufen, wenn die Funktion aktiviert ist, andernfalls `false`. |

**Beispiele**

*SWIFT*

```swift
import AEPRollout

Rollout.isFeatureEnabled(
    featureKey: "new-checkout-experience",
    evaluationContext: ctx
) { isEnabled in
    if isEnabled {
        showNewCheckout()
    } else {
        showDefaultCheckout()
    }
}
```

*Objective-C*

```objc
@import AEPRollout;

[AEPMobileRollout isFeatureEnabled:@"new-checkout-experience"
               evaluationContext:ctx
                      completion:^(BOOL isEnabled) {
    if (isEnabled) {
        [self showNewCheckout];
    } else {
        [self showDefaultCheckout];
    }
}];
```

### getFeature {#get-feature}

`getFeature` gibt die ausgewertete Funktions-Payload für den angegebenen Kontext zurück. Verwenden Sie diese API, wenn Sie mehr als aktivierte/deaktivierte Funktionen benötigen und Funktionsmetadaten oder -werte benötigen.

**Signatur**

*SWIFT*

```swift
Rollout.getFeature(
    featureKey: String,
    evaluationContext: FeatureEvaluationContext,
    completion: @escaping (FeatureEvaluationResult?) -> Void
)
```

*Objective-C*

```objc
[AEPMobileRollout getFeature:(NSString *)featureKey
         evaluationContext:(AEPFeatureEvaluationContext *)evaluationContext
                completion:(void (^)(AEPFeatureEvaluationResult * _Nullable))completion];
```

**Parameter**

| Parameter | Typ | Beschreibung |
|---|---|---|
| `featureKey` | Zeichenfolge | Funktionsschlüssel zur Auswertung im Erlebnis-Rollout |
| `evaluationContext` | FeatureEvaluationContext | Zielgruppenattribute und optionale Identität für die Analyse nach Bedarf einschließen; `FeatureEvaluationContext.builder().build()` für einen leeren Kontext verwenden. Siehe [Evaluierungskontext](#evaluation-context). |
| `completion` | `(FeatureEvaluationResult?) -> Void` | Wird mit der ausgewerteten Feature-Payload aufgerufen und kann `nil` werden, wenn die Funktion nicht gefunden wird. |

**Antwort**

*FeatureEvaluationResult*

| Feld | Typ | Beschreibung |
|---|---|---|
| `id` | Int | Numerische Funktionskennung |
| `key` | Zeichenfolge | Funktionsschlüssel |
| `releaseKey` | Zeichenfolge? | Freigabeschlüssel für diese Funktion, falls verfügbar |
| `meta` | Zeichenfolge? | Metadaten als JSON-Zeichenfolge kennzeichnen, sofern verfügbar |
| `analyticsParam` | AnalyticsParam? | Analytics-Details für die ausgewertete Funktion |

*AnalyticsParam*

| Feld | Typ | Beschreibung |
|---|---|---|
| `releaseId` | Int | Numerische Versionskennung |
| `featureId` | Int | Numerische Funktionskennung |
| `variantId` | Zeichenfolge? | Variantenkennung |

**Beispiele**

*SWIFT*

```swift
import AEPRollout

Rollout.getFeature(
    featureKey: "new-checkout-experience",
    evaluationContext: ctx
) { feature in
    if let meta = feature?.meta, !meta.isEmpty {
        applyMetaDrivenExperience(meta)
    } else {
        showFallbackExperience()
    }
}
```

*Objective-C*

```objc
@import AEPRollout;

[AEPMobileRollout getFeature:@"new-checkout-experience"
         evaluationContext:ctx
                completion:^(AEPFeatureEvaluationResult * _Nullable feature) {
    NSString *meta = feature.meta;
    if (meta != nil && meta.length > 0) {
        [self applyMetaDrivenExperience:meta];
    } else {
        [self showFallbackExperience];
    }
}];
```

### refreshCache {#refresh-cache}

Standardmäßig synchronisiert die Experience Rollout-Erweiterung regelmäßig die neuesten Rollout-Regeln und -Funktionen vom Server nach einem Zeitplan, den Sie konfigurieren können. Wenn Sie ein Update früher als bei der nächsten geplanten Synchronisierung benötigen, rufen Sie `refreshCache` auf, um eine Aktualisierung zu erzwingen. Typische Fälle sind nach der Anmeldung oder Änderungen des App-Status, die sich auf das Targeting auswirken sollten.

**Syntax**

*SWIFT*

```swift
Rollout.refreshCache()
```

*Objective-C*

```objc
[AEPMobileRollout refreshCache];
```

### extensionVersion {#extension-version}

Gibt die Versionszeichenfolge der Experience Rollout-Erweiterung zurück.

**Syntax**

```swift
Rollout.extensionVersion(): String
```

**Beispiel**

*SWIFT*

```swift
let version = Rollout.extensionVersion()
```

*Objective-C*

```objc
NSString *version = [AEPMobileRollout extensionVersion];
```

## API-Zusammenfassung {#api-summary}

| API | Rückgaben |
|---|---|
| `isFeatureEnabled(featureKey:evaluationContext:completion:)`. `FeatureEvaluationContext` enthält Zielgruppenattribute für Regeln und optionale Identität für Analytics. Siehe [isFeatureEnabled](#is-feature-enabled). | Boolescher Wert über Completion Handler |
| `getFeature(featureKey:evaluationContext:completion:)`. Gibt die ausgewertete Funktions-Payload für den angegebenen Kontext zurück. Siehe [getFeature](#get-feature). | FeatureEvaluationResult? Über Completion Handler |
| `refreshCache()` | ungültig machen |
| `extensionVersion()` | Zeichenfolge |

## Siehe auch {#see-also}

* [Apps](../../integrate/mobile-applications.md)
* [Integrationsschritte](../../integrate/integration-steps.md)
* [SDKs](../../integrate/sdks.md)
* [Handbuch zur Integration von Android-Erweiterungen](../android/android-extension-integration-guide.md)

<!-- -->
