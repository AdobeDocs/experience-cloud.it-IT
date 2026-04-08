---
title: Guida all’integrazione dell’estensione Experience Rollout per Android
description: Scopri come integrare l’estensione Experience Rollout con Adobe Experience Platform Mobile SDK su Android.
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 7%

---


# Estensione Experience Rollout per Android {#android-extension-integration-guide}

Questa guida descrive come integrare l’estensione Experience Rollout con Adobe Experience Platform Mobile SDK su Android.

## Prerequisiti {#prerequisites}

Prima di implementare l’estensione Experience Rollout, assicurati di disporre di:

* Una proprietà mobile configurata in [Raccolta dati di Adobe Experience Platform](https://experience.adobe.com/#/data-collection)
* L&#39;estensione Experience Rollout installata e configurata nella proprietà mobile
* Un ID organizzazione Adobe Experience Cloud
* SDK minimo: API 21 (Android 5.0 Lollipop)

## Dipendenze delle estensioni {#extension-dependencies}

L’estensione Experience Rollout richiede le seguenti estensioni Adobe Experience Platform:

| Estensione | Descrizione | Obbligatorio |
|---|---|---|
| Mobile Core | Offre funzionalità di base, tra cui configurazione ed elaborazione degli eventi | Sì |
| Ciclo di vita | Raccoglie i dati del ciclo di vita dell&#39;applicazione e della sessione per Mobile SDK | Sì |
| Edge Network | Abilita la comunicazione con Adobe Experience Platform Edge Network | Sì |
| Edge Identity | Gestisce l’identità utente per Edge Network | Sì |

Assicurati che queste estensioni siano installate nella proprietà mobile di Data Collection e incluse nelle dipendenze dell’app.

## Configurare l’estensione Experience Rollout in Raccolta dati {#configure}

### Installare l’estensione {#install-extension}

1. Accedi a [Raccolta dati Adobe Experience Platform](https://experience.adobe.com/#/data-collection).
1. Seleziona la scheda **Tag** e scegli la tua proprietà mobile.
1. Passa a **Estensioni** > **Catalogo**.
1. Cerca **l&#39;estensione di rollout esperienza** e seleziona **Installa**.
1. Configura le impostazioni dell&#39;estensione:

   | Impostazione | Descrizione |
   |---|---|
   | Sandbox | La sandbox di Adobe Experience Platform contenente la configurazione di Rollout esperienza |
   | ID applicazione | Un identificatore univoco per l’applicazione in Experience Rollout |
   | ID set di dati | ID del set di dati di Adobe Experience Platform per i dati dell’evento di analisi |

1. Seleziona **Salva**.
1. Segui il [processo di pubblicazione](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/overview) per aggiornare la configurazione.

### Ottieni l’ID del file di ambiente {#environment-file-id}

1. Nella tua proprietà mobile, passa a **Ambienti**.
1. Seleziona l&#39;icona della casella nella colonna **Installa** dell&#39;ambiente.
1. Nella finestra di dialogo **Istruzioni di installazione per dispositivi mobili**, copia **ID file ambiente**.

## Aggiungere l’estensione Experience Rollout all’app {#add-to-app}

### Aggiungi dipendenze {#add-dependencies}

Aggiungi le dipendenze di Mobile SDK al progetto. L&#39;estensione Experience Rollout richiede Mobile Core e le estensioni relative ad Edge elencate di seguito.

#### Utilizzo di Gradle con DBA (scelta consigliata) {#gradle-bom}

Aggiungi le dipendenze seguenti al file `build.gradle.kts` dell&#39;app:

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

#### Utilizzo di Gradle (Groovy) {#gradle-groovy}

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
>Per le applicazioni di produzione, Adobe consiglia di utilizzare numeri di versione espliciti anziché versioni dinamiche. Per ulteriori informazioni, vedere [Gestione delle dipendenze Gradle](https://docs.gradle.org/current/userguide/dependency_management.html).

### Aggiungere autorizzazioni {#add-permissions}

Aggiungi le seguenti autorizzazioni al file `AndroidManifest.xml`:

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

### Inizializzare SDK {#initialize-sdk}

Inizializza Mobile SDK nella classe `Application` prima di chiamare qualsiasi API di estensione Experience Rollout. Utilizza l&#39;ID file dell&#39;ambiente dalla tua proprietà mobile con `MobileCore.initialize` in modo che l&#39;app selezioni le impostazioni di rollout pubblicate in Raccolta dati.

#### Utilizzo di MobileCore.initialize {#mobile-core-initialize}

Disponibile a partire dalla versione DBA di Android 3.8.0, questa API registra automaticamente le estensioni e abilita il tracciamento del ciclo di vita.

>[!IMPORTANT]
>
>Per le app di produzione, utilizza solo `LoggingMode.ERROR`. Non utilizzare `DEBUG` o `VERBOSE` nelle build delle versioni.

**Cotlino**

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

### Registrare la classe Application {#register-application}

Registra la classe `Application` in `AndroidManifest.xml`:

```xml
<application
    android:name=".MainApplication"
    ... >
</application>
```

## Contesto di valutazione {#evaluation-context}

`FeatureEvaluationContext` include attributi di targeting (utilizzati per la corrispondenza delle regole di rollout) e identità facoltativa (utilizzati per Analytics).

| Metodo | Obbligatorio | Descrizione |
|---|---|---|
| `withIdentity(namespace, id)` | No | Primo argomento: spazio dei nomi delle identità (vedi [Spazi dei nomi delle identità di Adobe](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)). Secondo argomento: valore identità. Includi questo quando desideri che lo spazio dei nomi e l’ID siano rappresentati nell’analisi per questa valutazione. Se non specificato, per impostazione predefinita Analytics utilizza l’ECID. Non viene utilizzato per determinare le decisioni di abilitazione delle funzioni. |
| `withAttributes(map)` | No | `Map<String, List<String>>`. Chiave è il nome dell&#39;attributo di contesto utilizzato dalle regole di rollout (ad esempio `locale`, `platform`, `appVersion`, `deviceType`). Valore è l&#39;elenco dei valori degli attributi candidati per la chiave per l&#39;utente/sessione corrente (ad esempio `["en_US"]` o `["phone"]`). |

**Cotlino**

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

### Attributi di targeting di esempio {#sample-attributes}

| Attributo | Descrizione | Valori di esempio |
|---|---|---|
| `locale` | Lingua/lingua dell&#39;utente | `["en_US"]`, `["fr_FR"]` |
| `platform` | Identificatore della piattaforma | `["ANDROID"]` |
| `appVersion` | Versione applicazione | `["3.0.0"]` |
| `deviceType` | Tipo di dispositivo | `["phone"]`, `["tablet"]` |

## Documentazione delle API {#api-reference}

### isFeatureEnabled {#is-feature-enabled}

`isFeatureEnabled` restituisce se una funzione di rollout esperienza è attiva o disattivata per il contesto specificato. Passa `featureKey`, un `FeatureEvaluationContext` (attributi di targeting facoltativi e identità facoltativa per Analytics) e un callback. Vedi [Contesto di valutazione](#evaluation-context).

**Firma**

*Cotlino*

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

**Parametri**

| Parametro | Tipo | Descrizione |
|---|---|---|
| `featureKey` | Stringa | Chiave della funzione da valutare nel rollout dell’esperienza |
| `evaluationContext` | FeatureEvaluationContext | Includere attributi di targeting e identità facoltativa per l&#39;analisi in base alle esigenze. Utilizzare `FeatureEvaluationContext.builder().build()` per un contesto vuoto. Vedi [Contesto di valutazione](#evaluation-context). |
| `callback` | AdobeCallback&lt;Booleano> | Richiamato con `true` se la funzionalità è abilitata, `false` in caso contrario. È inoltre possibile passare `AdobeCallbackWithError<Boolean>` per gestire `fail(...)`. |

**Esempi**

*Cotlino*

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

`getFeature` restituisce il payload della funzionalità valutata per il contesto specificato. Utilizza questa API quando hai bisogno di più di abilitato/disabilitato e desideri metadati o valori di funzionalità.

**Firma**

*Cotlino*

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

**Parametri**

| Parametro | Tipo | Descrizione |
|---|---|---|
| `featureKey` | Stringa | Chiave della funzione da valutare nel rollout dell’esperienza |
| `evaluationContext` | FeatureEvaluationContext | Includere attributi di targeting e identità facoltativa per l&#39;analisi in base alle esigenze. Utilizzare `FeatureEvaluationContext.builder().build()` per un contesto vuoto. Vedi [Contesto di valutazione](#evaluation-context). |
| `callback` | AdobeCallback&lt;RisultatoValutazioneFunzionalità> | Richiamato con il payload della funzionalità valutata; potrebbe essere `null` quando la funzionalità non viene trovata. È inoltre possibile passare `AdobeCallbackWithError<FeatureEvaluationResult>` per gestire `fail(...)`. |

**Risposta**

*RisultatoValutazioneFunzionalità*

| Campo | Tipo | Descrizione |
|---|---|---|
| `id` | Intero | Identificatore numerico di funzione |
| `key` | Stringa | Chiave funzione |
| `releaseKey` | Stringa? | Chiave di rilascio per questa funzione, se disponibile |
| `meta` | Stringa? | Metadati delle funzioni come stringa JSON, se disponibili |
| `analyticsParam` | AnalyticsParam? | Dettagli di Analytics per la funzione valutata |

*AnalyticsParam*

| Campo | Tipo | Descrizione |
|---|---|---|
| `releaseId` | Intero | Identificatore di versione numerico |
| `featureId` | Intero | Identificatore numerico di funzione |
| `variantId` | Stringa? | Identificatore variante |

**Esempi**

*Cotlino*

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

Per impostazione predefinita, l’estensione Rollout esperienza sincronizza regolarmente le regole e le funzionalità di rollout più recenti dal server in base a una pianificazione che puoi configurare. Se è necessario un aggiornamento prima della successiva sincronizzazione pianificata, chiamare `refreshCache` per forzare un aggiornamento. I casi tipici includono dopo l’accesso o quando lo stato dell’app cambia in un modo che dovrebbe influenzare il targeting.

**Sintassi**

*Cotlino*

```kotlin
Rollout.refreshCache()
```

*Java*

```java
Rollout.refreshCache();
```

### extensionVersion {#extension-version}

Restituisce la stringa della versione dell&#39;estensione Experience Rollout.

**Sintassi**

```kotlin
Rollout.extensionVersion(): String
```

**Esempio**

*Cotlino*

```kotlin
val version = Rollout.extensionVersion()
```

*Java*

```java
String version = Rollout.extensionVersion();
```

## Riepilogo API {#api-summary}

| API | Restituisce |
|---|---|
| `isFeatureEnabled(featureKey, evaluationContext, callback)`. `FeatureEvaluationContext` contiene attributi di targeting per le regole e identità facoltativa per analytics. Consulta [Valutazione delle funzionalità](#is-feature-enabled). | Booleano tramite callback |
| `getFeature(featureKey, evaluationContext, callback)`. Restituisce il payload della funzione valutato per il contesto specificato. Vedi [getFeature](#get-feature). | FeatureEvaluationResult tramite callback |
| `refreshCache()` | void |
| `extensionVersion()` | Stringa |

## Vedi anche {#see-also}

* [Applicazioni mobili](../../integrate/mobile-applications.md)
* [Passaggi dell’integrazione](../../integrate/integration-steps.md)
* [SDK](../../integrate/sdks.md)
