---
title: Handbuch zur Integration der Experience Rollout-Erweiterung für Android
description: Erfahren Sie, wie Sie die Experience Rollout-Erweiterung mit Adobe Experience Platform Mobile SDK auf Android integrieren.
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 8%

---


# Experience Rollout-Erweiterung für Android {#android-extension-integration-guide}

In diesem Handbuch wird beschrieben, wie Sie die Experience Rollout-Erweiterung in Adobe Experience Platform Mobile SDK in Android integrieren.

## Voraussetzungen {#prerequisites}

Stellen Sie vor der Implementierung der Experience Rollout-Erweiterung Folgendes sicher:

* Eine Mobile-Eigenschaft, die in der Datenerfassung von [Adobe Experience Platform konfiguriert ist](https://experience.adobe.com/#/data-collection)
* Die in Ihrer Mobile-Eigenschaft installierte und konfigurierte Experience Rollout-Erweiterung
* Eine Adobe Experience Cloud-Organisations-ID
* Minimum SDK: API 21 (Android 5.0 Lollipop)

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

#### Gradle mit Stückliste verwenden (empfohlen) {#gradle-bom}

Fügen Sie der `build.gradle.kts`-Datei Ihrer App die folgenden Abhängigkeiten hinzu:

```kotlin
dependencies {
    // Adobe Experience Platform Mobile SDK BOM
    implementation(platform("com.adobe.marketing.mobile:sdk-bom:3.+"))

    // Required extensions
    implementation("com.adobe.marketing.mobile:core")
    implementation("com.adobe.marketing.mobile:lifecycle")
    implementation("com.adobe.marketing.mobile:edge")
    implementation("com.adobe.marketing.mobile:edgeidentity")

    // Experience Rollout extension
    implementation("com.adobe.marketing.mobile:rollout")
}
```

#### Gradle (Groovy) benutzen {#gradle-groovy}

```groovy
dependencies {
    // Adobe Experience Platform Mobile SDK BOM
    implementation platform('com.adobe.marketing.mobile:sdk-bom:3.+')

    // Required extensions
    implementation 'com.adobe.marketing.mobile:core'
    implementation 'com.adobe.marketing.mobile:lifecycle'
    implementation 'com.adobe.marketing.mobile:edge'
    implementation 'com.adobe.marketing.mobile:edgeidentity'

    // Experience Rollout extension
    implementation 'com.adobe.marketing.mobile:rollout'
}
```

>[!IMPORTANT]
>
>Für Produktionsanwendungen empfiehlt Adobe die Verwendung expliziter Versionsnummern anstelle von dynamischen Versionen. Weitere Informationen finden [&#x200B; unter „Verwalten &#x200B;](https://docs.gradle.org/current/userguide/dependency_management.html) Gradle-Abhängigkeiten“.

### Hinzufügen von Berechtigungen {#add-permissions}

Fügen Sie Ihrer `AndroidManifest.xml`-Datei die folgenden Berechtigungen hinzu:

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

### SDK initialisieren {#initialize-sdk}

Initialisieren Sie die Mobile SDK in Ihrer `Application`, bevor Sie APIs für Experience Rollout-Erweiterungen aufrufen. Verwenden Sie die Umgebungsdatei-ID aus Ihrer Mobile-Eigenschaft mit `MobileCore.initialize`, damit die App die Rollout-Einstellungen übernimmt, die Sie in der Datenerfassung veröffentlicht haben.

#### Verwenden von MobileCore.initialize {#mobile-core-initialize}

Diese API ist ab Android BOM Version 3.8.0 verfügbar und registriert automatisch Erweiterungen und ermöglicht die Lebenszyklusverfolgung.

>[!IMPORTANT]
>
>Verwenden Sie für Produktions-Apps nur `LoggingMode.ERROR`. Verwenden Sie `DEBUG` oder `VERBOSE` nicht in Release-Builds.

**Kotlin**

```kotlin
import android.app.Application
import com.adobe.marketing.mobile.LoggingMode
import com.adobe.marketing.mobile.MobileCore

class MainApplication : Application() {

    override fun onCreate() {
        super.onCreate()

        MobileCore.setLogLevel(LoggingMode.ERROR)

        // Initialize with your Environment File ID from Data Collection
        MobileCore.initialize(this, "YOUR_ENVIRONMENT_FILE_ID")
    }
}
```

**Java**

```java
import android.app.Application;
import com.adobe.marketing.mobile.LoggingMode;
import com.adobe.marketing.mobile.MobileCore;

public class MainApplication extends Application {

    @Override
    public void onCreate() {
        super.onCreate();

        MobileCore.setLogLevel(LoggingMode.ERROR);

        // Initialize with your Environment File ID from Data Collection
        MobileCore.initialize(this, "YOUR_ENVIRONMENT_FILE_ID", null);
    }
}
```

### Registrieren der Application-Klasse {#register-application}

Registrieren Sie Ihre `Application` in `AndroidManifest.xml`:

```xml
<application
    android:name=".MainApplication"
    ... >
</application>
```

## Auswertungskontext {#evaluation-context}

`FeatureEvaluationContext` umfasst Zielgruppenattribute (für die Zuordnung von Rollout-Regeln verwendet) und optionale Identität (für Analysen verwendet).

| Methode | Erforderlich | Beschreibung |
|---|---|---|
| `withIdentity(namespace, id)` | Nein | Erstes Argument: Identity-Namespace (siehe [Adobe Identity-Namespaces](https://experienceleague.adobe.com/de/docs/experience-platform/identity/features/namespaces)). Zweites Argument: Identitätswert. Schließen Sie dies ein, wenn dieser Namespace und diese ID in Analytics für diese Auswertung dargestellt werden sollen. Falls nicht angegeben, verwendet Analytics standardmäßig die ECID. Dies wird nicht verwendet, um Entscheidungen zur Aktivierung von Funktionen zu fördern. |
| `withAttributes(map)` | Nein | `Map<String, List<String>>`. Der Schlüssel ist der Kontextattributname, der von Ihren Rollout-Regeln verwendet wird (z. B. `locale`, `platform`, `appVersion`, `deviceType`). Wert ist die Liste der möglichen Attributwerte für diesen Schlüssel für den aktuellen Benutzer/die aktuelle Sitzung (z. B. `["en_US"]` oder `["phone"]`). |

**Kotlin**

```kotlin
import com.adobe.marketing.mobile.rollout.FeatureEvaluationContext

val attrs = mapOf(
    "locale" to listOf("en_US"),
    "platform" to listOf("ANDROID"),
    "appVersion" to listOf("3.0.0")
)

val ctx = FeatureEvaluationContext.builder()
    .withIdentity("Email", "customer@example.com")
    .withAttributes(attrs)
    .build()
```

**Java**

```java
import com.adobe.marketing.mobile.rollout.FeatureEvaluationContext;
import java.util.Arrays;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

Map<String, List<String>> attrs = new HashMap<>();
attrs.put("locale", Arrays.asList("en_US"));
attrs.put("platform", Arrays.asList("ANDROID"));
attrs.put("appVersion", Arrays.asList("3.0.0"));

FeatureEvaluationContext ctx = FeatureEvaluationContext.builder()
        .withIdentity("Email", "customer@example.com")
        .withAttributes(attrs)
        .build();
```

### Beispiele für Zielgruppenattribute {#sample-attributes}

| Attribut | Beschreibung | Beispielwerte |
|---|---|---|
| `locale` | Gebietsschema/Sprache des Benutzers | `["en_US"]`, `["fr_FR"]` |
| `platform` | Plattformkennung | `["ANDROID"]` |
| `appVersion` | Anwendungsversion | `["3.0.0"]` |
| `deviceType` | Gerätetyp | `["phone"]`, `["tablet"]` |

## API-Referenz {#api-reference}

### isFeatureEnabled {#is-feature-enabled}

`isFeatureEnabled` gibt zurück, ob eine Experience Rollout-Funktion für den jeweiligen Kontext aktiviert oder deaktiviert ist. Übergeben Sie `featureKey`, einen `FeatureEvaluationContext` (optionale Zielgruppenattribute und optionale Identität für Analytics) und einen Callback. Siehe [Evaluierungskontext](#evaluation-context).

**Signatur**

*Kotlin*

```kotlin
Rollout.isFeatureEnabled(
    featureKey: String,
    evaluationContext: FeatureEvaluationContext,
    callback: AdobeCallback<Boolean>
)
```

*Java*

```java
Rollout.isFeatureEnabled(
    String featureKey,
    FeatureEvaluationContext evaluationContext,
    AdobeCallback<Boolean> callback);
```

**Parameter**

| Parameter | Typ | Beschreibung |
|---|---|---|
| `featureKey` | Zeichenfolge | Funktionsschlüssel zur Auswertung im Erlebnis-Rollout |
| `evaluationContext` | FeatureEvaluationContext | Zielgruppenattribute und optionale Identität für die Analyse nach Bedarf einschließen; `FeatureEvaluationContext.builder().build()` für einen leeren Kontext verwenden. Siehe [Evaluierungskontext](#evaluation-context). |
| `callback` | AdobeCallback&lt;Boolean> | Wird mit `true` aufgerufen, wenn die Funktion aktiviert ist, andernfalls `false`. Sie können auch `AdobeCallbackWithError<Boolean>` zur Handhabung von `fail(...)` übergeben. |

**Beispiele**

*Kotlin*

```kotlin
import com.adobe.marketing.mobile.AdobeCallback
import com.adobe.marketing.mobile.rollout.Rollout

Rollout.isFeatureEnabled(
    "new-checkout-experience",
    ctx,
    object : AdobeCallback<Boolean> {
        override fun call(isEnabled: Boolean?) {
            if (isEnabled == true) {
                showNewCheckout()
            } else {
                showDefaultCheckout()
            }
        }
    }
)
```

*Java*

```java
import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.rollout.Rollout;

Rollout.isFeatureEnabled(
    "new-checkout-experience",
    ctx,
    new AdobeCallback<Boolean>() {
        @Override
        public void call(Boolean isEnabled) {
            if (Boolean.TRUE.equals(isEnabled)) {
                showNewCheckout();
            } else {
                showDefaultCheckout();
            }
        }
    }
);
```

### getFeature {#get-feature}

`getFeature` gibt die ausgewertete Funktions-Payload für den angegebenen Kontext zurück. Verwenden Sie diese API, wenn Sie mehr als aktivierte/deaktivierte Funktionen benötigen und Funktionsmetadaten oder -werte benötigen.

**Signatur**

*Kotlin*

```kotlin
Rollout.getFeature(
    featureKey: String,
    evaluationContext: FeatureEvaluationContext,
    callback: AdobeCallback<FeatureEvaluationResult>
)
```

*Java*

```java
Rollout.getFeature(
    String featureKey,
    FeatureEvaluationContext evaluationContext,
    AdobeCallback<FeatureEvaluationResult> callback);
```

**Parameter**

| Parameter | Typ | Beschreibung |
|---|---|---|
| `featureKey` | Zeichenfolge | Funktionsschlüssel zur Auswertung im Erlebnis-Rollout |
| `evaluationContext` | FeatureEvaluationContext | Zielgruppenattribute und optionale Identität für die Analyse nach Bedarf einschließen; `FeatureEvaluationContext.builder().build()` für einen leeren Kontext verwenden. Siehe [Evaluierungskontext](#evaluation-context). |
| `callback` | AdobeCallback&lt;FeatureEvaluationResult> | Wird mit der ausgewerteten Funktion Payload aufgerufen. Kann `null` werden, wenn die Funktion nicht gefunden wird. Sie können auch `AdobeCallbackWithError<FeatureEvaluationResult>` zur Handhabung von `fail(...)` übergeben. |

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

*Kotlin*

```kotlin
import com.adobe.marketing.mobile.AdobeCallback
import com.adobe.marketing.mobile.rollout.FeatureEvaluationResult
import com.adobe.marketing.mobile.rollout.Rollout

Rollout.getFeature(
    "new-checkout-experience",
    ctx,
    object : AdobeCallback<FeatureEvaluationResult> {
        override fun call(feature: FeatureEvaluationResult?) {
            val meta = feature?.meta
            if (!meta.isNullOrEmpty()) {
                applyMetaDrivenExperience(meta)
            } else {
                showFallbackExperience()
            }
        }
    }
)
```

*Java*

```java
import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.rollout.FeatureEvaluationResult;
import com.adobe.marketing.mobile.rollout.Rollout;

Rollout.getFeature(
    "new-checkout-experience",
    ctx,
    new AdobeCallback<FeatureEvaluationResult>() {
        @Override
        public void call(FeatureEvaluationResult feature) {
            String meta = feature != null ? feature.getMeta() : null;
            if (meta != null && !meta.isEmpty()) {
                applyMetaDrivenExperience(meta);
            } else {
                showFallbackExperience();
            }
        }
    }
);
```

### refreshCache {#refresh-cache}

Standardmäßig synchronisiert die Experience Rollout-Erweiterung regelmäßig die neuesten Rollout-Regeln und -Funktionen vom Server nach einem Zeitplan, den Sie konfigurieren können. Wenn Sie ein Update früher als bei der nächsten geplanten Synchronisierung benötigen, rufen Sie `refreshCache` auf, um eine Aktualisierung zu erzwingen. Typische Fälle sind nach der Anmeldung oder Änderungen des App-Status, die sich auf das Targeting auswirken sollten.

**Syntax**

*Kotlin*

```kotlin
Rollout.refreshCache()
```

*Java*

```java
Rollout.refreshCache();
```

### extensionVersion {#extension-version}

Gibt die Versionszeichenfolge der Experience Rollout-Erweiterung zurück.

**Syntax**

```kotlin
Rollout.extensionVersion(): String
```

**Beispiel**

*Kotlin*

```kotlin
val version = Rollout.extensionVersion()
```

*Java*

```java
String version = Rollout.extensionVersion();
```

## API-Zusammenfassung {#api-summary}

| API | Rückgaben |
|---|---|
| `isFeatureEnabled(featureKey, evaluationContext, callback)`. `FeatureEvaluationContext` enthält Zielgruppenattribute für Regeln und optionale Identität für Analytics. Siehe [Funktionsauswertung](#is-feature-enabled). | Boolescher Wert über Callback |
| `getFeature(featureKey, evaluationContext, callback)`. Gibt die ausgewertete Funktions-Payload für den angegebenen Kontext zurück. Siehe [getFeature](#get-feature). | FeatureEvaluationResult über Callback |
| `refreshCache()` | ungültig machen |
| `extensionVersion()` | Zeichenfolge |

## Siehe auch {#see-also}

* [Apps](../../integrate/mobile-applications.md)
* [Integrationsschritte](../../integrate/integration-steps.md)
* [SDKs](../../integrate/sdks.md)
