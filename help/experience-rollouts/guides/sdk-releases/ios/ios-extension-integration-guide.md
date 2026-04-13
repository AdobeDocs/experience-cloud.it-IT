---
title: Guida all’integrazione dell’estensione Experience Rollout per iOS
description: Scopri come integrare l’estensione Experience Rollout con Adobe Experience Platform Mobile SDK su iOS.
source-git-commit: a9f6746c2b470377d2fd58de18e984d1ec404a77
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 7%

---

# Estensione Experience Rollout per iOS {#ios-extension-integration-guide}

Questa guida descrive come integrare l’estensione Experience Rollout con Adobe Experience Platform Mobile SDK su iOS.

## Prerequisiti {#prerequisites}

Prima di implementare l’estensione Experience Rollout, assicurati di disporre di:

* Una proprietà mobile configurata in [Raccolta dati di Adobe Experience Platform](https://experience.adobe.com/#/data-collection)
* L&#39;estensione Experience Rollout installata e configurata nella proprietà mobile
* Un ID organizzazione Adobe Experience Cloud
* Destinazione minima di distribuzione: iOS 12.0
* Xcode 14.1 o versione successiva

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

#### Utilizzo di Gestione pacchetti Swift (consigliato) {#swift-package-manager}

1. In Xcode, passa a **File** > **Aggiungi dipendenze pacchetto**.
1. Immetti l’URL dell’archivio di Adobe Experience Platform Mobile SDK:

   ```
   https://github.com/adobe/aepsdk-core-ios
   ```

1. Aggiungi i seguenti pacchetti:

   | Pacchetto | Archivio |
   |---|---|
   | AEPCore, AEPLifecycle | `https://github.com/adobe/aepsdk-core-ios` |
   | AEPdge | `https://github.com/adobe/aepsdk-edge-ios` |
   | AEPEdgeIdentity | `https://github.com/adobe/aepsdk-edgeidentity-ios` |
   | AEPRollout | `https://github.com/adobe/aepsdk-rollout-ios` |

#### Utilizzo di CocoaPods {#cocoapods}

Aggiungi i seguenti pod a `Podfile`:

```ruby
pod 'AEPCore'
pod 'AEPLifecycle'
pod 'AEPEdge'
pod 'AEPEdgeIdentity'
pod 'AEPRollout'
```

Quindi esegui:

```bash
pod install
```

>[!IMPORTANT]
>
>Per le applicazioni di produzione, Adobe consiglia di aggiungere puntini ai numeri di versione espliciti anziché utilizzare `~>` o intervalli aperti. Per ulteriori informazioni, vedere la [Guida al controllo delle versioni di CocoaPods](https://guides.cocoapods.org/using/the-podfile.html).

### Inizializzare SDK {#initialize-sdk}

Inizializza Mobile SDK in `AppDelegate` (o `SceneDelegate`) prima di richiamare qualsiasi API di estensione Experience Rollout. Utilizza l’ID file dell’ambiente dalla tua proprietà mobile in modo che l’app selezioni le impostazioni di rollout pubblicate in Raccolta dati.

**Swift**

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
>Per le app di produzione, utilizza solo `LogLevel.error`. Non utilizzare `.debug` o `.verbose` nelle build delle versioni.

## Contesto di valutazione {#evaluation-context}

`FeatureEvaluationContext` include attributi di targeting (utilizzati per la corrispondenza delle regole di rollout) e identità facoltativa (utilizzati per Analytics).

| Metodo | Obbligatorio | Descrizione |
|---|---|---|
| `withIdentity(namespace:id:)` | No | Primo argomento: spazio dei nomi delle identità (vedi [Spazi dei nomi delle identità di Adobe](https://experienceleague.adobe.com/it/docs/experience-platform/identity/features/namespaces)). Secondo argomento: valore identità. Includi questo quando desideri che lo spazio dei nomi e l’ID siano rappresentati nell’analisi per questa valutazione. Se non specificato, per impostazione predefinita Analytics utilizza l’ECID. Non viene utilizzato per determinare le decisioni di abilitazione delle funzioni. |
| `withAttributes(_:)` | No | `[String: [String]]`. Chiave è il nome dell&#39;attributo di contesto utilizzato dalle regole di rollout (ad esempio `locale`, `platform`, `appVersion`, `deviceType`). Valore è l&#39;elenco dei valori degli attributi candidati per la chiave per l&#39;utente/sessione corrente (ad esempio `["en_US"]` o `["phone"]`). |

**Swift**

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

### Attributi di targeting di esempio {#sample-attributes}

| Attributo | Descrizione | Valori di esempio |
|---|---|---|
| `locale` | Lingua/lingua dell&#39;utente | `["en_US"]`, `["fr_FR"]` |
| `platform` | Identificatore della piattaforma | `["IOS"]` |
| `appVersion` | Versione applicazione | `["3.0.0"]` |
| `deviceType` | Tipo di dispositivo | `["phone"]`, `["tablet"]` |

## Documentazione delle API {#api-reference}

### isFeatureEnabled {#is-feature-enabled}

`isFeatureEnabled` restituisce se una funzione di rollout esperienza è attiva o disattivata per il contesto specificato. Passa `featureKey`, un `FeatureEvaluationContext` (attributi di targeting facoltativi e identità facoltativa per Analytics) e un gestore di completamento. Vedi [Contesto di valutazione](#evaluation-context).

**Firma**

*Swift*

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

**Parametri**

| Parametro | Tipo | Descrizione |
|---|---|---|
| `featureKey` | Stringa | Chiave della funzione da valutare nel rollout dell’esperienza |
| `evaluationContext` | FeatureEvaluationContext | Includere attributi di targeting e identità facoltativa per l&#39;analisi in base alle esigenze. Utilizzare `FeatureEvaluationContext.builder().build()` per un contesto vuoto. Vedi [Contesto di valutazione](#evaluation-context). |
| `completion` | `(Bool) -> Void` | Chiamata eseguita con `true` se la funzionalità è abilitata, `false` in caso contrario. |

**Esempi**

*Swift*

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

`getFeature` restituisce il payload della funzionalità valutata per il contesto specificato. Utilizza questa API quando hai bisogno di più di abilitato/disabilitato e desideri metadati o valori di funzionalità.

**Firma**

*Swift*

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

**Parametri**

| Parametro | Tipo | Descrizione |
|---|---|---|
| `featureKey` | Stringa | Chiave della funzione da valutare nel rollout dell’esperienza |
| `evaluationContext` | FeatureEvaluationContext | Includere attributi di targeting e identità facoltativa per l&#39;analisi in base alle esigenze. Utilizzare `FeatureEvaluationContext.builder().build()` per un contesto vuoto. Vedi [Contesto di valutazione](#evaluation-context). |
| `completion` | `(FeatureEvaluationResult?) -> Void` | Chiamata eseguita con il payload della funzionalità valutata. Se la funzionalità non è stata trovata, il valore potrebbe essere `nil`. |

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

*Swift*

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

Per impostazione predefinita, l’estensione Rollout esperienza sincronizza regolarmente le regole e le funzionalità di rollout più recenti dal server in base a una pianificazione che puoi configurare. Se è necessario un aggiornamento prima della successiva sincronizzazione pianificata, chiamare `refreshCache` per forzare un aggiornamento. I casi tipici includono dopo l’accesso o quando lo stato dell’app cambia in un modo che dovrebbe influenzare il targeting.

**Sintassi**

*Swift*

```swift
Rollout.refreshCache()
```

*Objective-C*

```objc
[AEPMobileRollout refreshCache];
```

### extensionVersion {#extension-version}

Restituisce la stringa della versione dell&#39;estensione Experience Rollout.

**Sintassi**

```swift
Rollout.extensionVersion(): String
```

**Esempio**

*Swift*

```swift
let version = Rollout.extensionVersion()
```

*Objective-C*

```objc
NSString *version = [AEPMobileRollout extensionVersion];
```

## Riepilogo API {#api-summary}

| API | Restituisce |
|---|---|
| `isFeatureEnabled(featureKey:evaluationContext:completion:)`. `FeatureEvaluationContext` contiene attributi di targeting per le regole e identità facoltativa per analytics. Vedi [isFeatureEnabled](#is-feature-enabled). | Booleano tramite gestore di completamento |
| `getFeature(featureKey:evaluationContext:completion:)`. Restituisce il payload della funzione valutato per il contesto specificato. Vedi [getFeature](#get-feature). | FeatureEvaluationResult? tramite gestore di completamento |
| `refreshCache()` | Vuoto |
| `extensionVersion()` | Stringa |

## Vedi anche {#see-also}

* [Applicazioni mobili](../../integrate/mobile-applications.md)
* [Passaggi dell’integrazione](../../integrate/integration-steps.md)
* [SDK](../../integrate/sdks.md)
* [guida all’integrazione delle estensioni Android](../android/android-extension-integration-guide.md)
