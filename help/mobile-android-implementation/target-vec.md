---
title: Aggiunta di Visual Experience Composer (VEC) di Adobe Target
description: Scoprite come implementare Visual Experience Composer (VEC) di Target con parametri personalizzati, associarli al dispositivo e creare un'attività. Questa lezione fa parte dell'esercitazione Implementazione di Experience Cloud nelle applicazioni Android per dispositivi mobili.
seo-description: null
seo-title: Aggiunta di Visual Experience Composer (VEC) di Adobe Target
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 79d5274d09d66b80a49aba5db3e0a997d0f0ff61

---


# Aggiunta di Visual Experience Composer (VEC) di Adobe Target

In questa lezione, abiliterete Target Visual Experience Composer (VEC) per le app mobili.

[Adobe Target](https://docs.adobe.com/content/help/en/target/using/target-home.html) è la soluzione Adobe Experience Cloud che offre tutto il necessario per adattare e personalizzare l'esperienza dei clienti, in modo da massimizzare le entrate sui siti Web e mobili, le app, i social media e altri canali digitali.

Il compositore esperienza visivo (VEC) per app mobile native ti permette di creare attività e personalizzare contenuti in app mobile native in modalità fai-da-te senza dover dipendere sempre dagli sviluppatori e dai cicli di rilascio delle app.

Nella lezione [Aggiungi estensioni](launch-add-extensions.md), hai aggiunto l’estensione VEC di Target alla proprietà Launch. Nella lezione [Installa l’SDK](launch-install-the-mobile-sdk.md) Mobile che hai importato nell’applicazione di esempio. Per avviare la configurazione delle attività in Target Mobile Experience Composer (Compositore esperienza visiva mobile) sono necessari solo alcuni piccoli aggiornamenti!

>[!IMPORTANT] Sia le estensioni Target che Target VEC Launch sono necessarie per utilizzare Target VEC nella vostra applicazione mobile.

## Obiettivi di apprendimento

Alla fine di questa lezione, potrai:

* Abilitare l'app di esempio per Target VEC
* Aggiunta di parametri alla richiesta VEC di Target
* Collegare il dispositivo al VEC
* Creazione di un'attività tramite VEC

## Prerequisiti 

Per completare le lezioni in questa sezione, dovete:

* Completa le lezioni nella sezione [Configura lancio](launch-create-a-property.md) .
* Accesso a livello di approver all'interfaccia di Adobe Target

## Richiesta di caricamento app

In Target verrà generata una richiesta di "caricamento app" al primo caricamento dell'app a causa delle impostazioni selezionate al momento della configurazione dell'estensione VEC di Target. Questa richiesta prerileva tutte le attività VEC di Target create per la vostra app.

Nello studio Android, filtrate Logcat su "Target r" per mostrare le richieste e le risposte di Target. Osservate i parametri per il nome e la versione dell’applicazione. Tutte le attività VEC Target create verranno automaticamente indirizzate a queste proprietà.

![Visualizza richieste VEC Target](images/android/mobile-targetvec-viewLogs.png)

## Aggiungi parametri

Come hai visto nell'ultimo esercizio, le metriche del ciclo di vita delle app vengono automaticamente incluse come parametri nella richiesta VEC di Target. Puoi anche aggiungere parametri personalizzati alle richieste, a livello globale o per viste specifiche nell'app.

**Aggiunta di parametri personalizzati a livello globale**

1. In Android Studio, aprite `DemoApplication` il file.
1. Importa l’estensione VEC di destinazione aggiungendo `import ACPTargetVEC` sotto l’importazione esistente
1. Aggiungere il seguente codice di esempio nella `onCreate()` funzione, prima che le estensioni siano registrate. Questo codice di esempio mostra come parametri regolari, parametri di profilo, parametri di prodotto (o entità) e parametri di ordine possono essere aggiunti alla richiesta TargetVEC. In questo esempio vengono utilizzati valori statici, mentre nell'app effettiva è probabile che si desideri utilizzare variabili dinamiche per comporre i valori. Naturalmente, è consigliabile compilare solo i parametri rilevanti per tutte le viste:

   ```java
   Map<String, String>targetParams = new HashMap<>(); //params
   targetParams.put( "param1", "value1");
   Map<String, String>taregtProfileParams = new HashMap<>(); //profile params
   taregtProfileParams.put("profilekey1","profilevalue1");
   
   TargetVEC.setGlobalRequestParameters(new TargetParameters.Builder()
            .parameters(targetParams)
            .profileParameters(taregtProfileParams)
            .product(new TargetProduct("1234", "furniture"))
            .order(new TargetOrder("12343", 123.45, Arrays.asList("100", "200")))
            .build());
   ```

1. È possibile che si verifichino degli errori in Android Studio, dal momento che il codice del parametro precedente richiede le seguenti importazioni, che è necessario aggiungere al file:

   ```java
   import com.adobe.marketing.mobile.TargetOrder;
   import com.adobe.marketing.mobile.TargetProduct;
   import com.adobe.marketing.mobile.TargetParameters;
   import java.util.Arrays;
   import java.util.Map;
   import java.util.HashMap;
   ```

   ![Aggiunta di parametri alla richiesta TargetVEC](images/android/mobile-targetvec-addParameters.png)

Ora che hai aggiunto parametri all'app, è ora di confermare che verranno passati nella richiesta.

**Verifica dei parametri**

1. Salvataggio del progetto Android Studio
1. Generate di nuovo l'app e attendete che venga riaperta nell'emulatore
1. Aprire il riquadro Logcat di Android Studio
1. Filtra per mostrare tutte le istruzioni con "Target r"
1. I parametri personalizzati appena aggiunti dovrebbero essere visibili nella richiesta

   ![Verifica parametri alla richiesta TargetVEC](images/android/mobile-targetvec-verifyParams.png)

Per ulteriori informazioni e dettagli su come trasmettere parametri con viste specifiche, consulta [la documentazione](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/composer/mobile-visual-experience-composer-android.html#parameters).

## Associazione dell'app mobile all'interfaccia di destinazione

Per creare attività VEC nell'interfaccia di Target, devi prima associare Target alla tua app. Questo accoppiamento è ottenuto con l'uso di collegamenti profondi.

### Creazione di un collegamento profondo

Android supporta l'utilizzo di collegamenti [profondi e collegamenti](https://developer.android.com/training/app-links/deep-linking) app Android per creare URL che vanno direttamente in posizioni specifiche dell'app. Probabilmente li usi già nell'app. In tal caso, potete utilizzare la struttura URL esistente per effettuare la coppia con Target. In questa esercitazione, controllerete il collegamento profondo predefinito nell'app di prenotazione bus, confermerete che funziona, quindi utilizzatelo per associare l'app a Target VEC for Mobile Apps.

**Per rivedere la configurazione del collegamento profondo**

1. In Android Studio, aprite il file AndroidManifest.xml
1. Si noti che esiste già un filtro Intent configurato per lo schema di collegamento profondo dell'app Bus Booking
1. Si noti che `Host` e `Scheme` sono già impostati rispettivamente su `com.adobe.example.busbooking` e `http`. Ciò significa che un URL come `http://com.adobe.example.busbooking` quando aperto nell'emulatore dovrebbe aprire automaticamente l'app di esempio

   ![Registra schema URL](images/android/mobile-targetvec-registerScheme.png)

Il passo successivo è confermare che lo schema di collegamento profondo funziona

### Verifica del collegamento profondo

Ora accertatevi che il collegamento profondo apra l'app nell'emulatore. È possibile utilizzare il modo preferito per eseguire i comandi adb, che è possibile utilizzare.

**Per verificare il collegamento profondo con adb (Mac®)**

1. Accertatevi che l'emulatore Android sia in esecuzione
1. Chiudi l'app di prenotazione bus se è già aperta
1. Aprire una finestra Terminal
1. Andate alla directory degli strumenti della piattaforma Android: `cd Library/Android/sdk/platform-tools/`
1. Confermate che l'emulatore sia collegato: `./adb devices`
1. Aprite la shell adb: `./adb shell`
1. Nella shell adb testare il collegamento profondo: `am start -W -a android.intent.action.VIEW -d "http://com.adobe.example.busbooking" "com.adobe.busbooking"`
1. Conferma che l'app di prenotazione bus è stata avviata nell'emulatore

   ![Verifica del collegamento profondo](images/android/mobile-targetvec-verifyDeepLink.png)

Ora che la vostra struttura di collegamento profondo è configurata, siete pronti a utilizzare Target VEC per configurare le attività!

## Creare un'attività in Mobile VEC

Ora creiamo un'attività nell'interfaccia di Target.

**Per creare un'attività con Target VEC**

1. Accedi ad [Adobe Experience Cloud](https://experiencecloud.adobe.com)
1. Utilizzare lo switcher della soluzione per passare a Target

   ![Verifica del collegamento profondo](images/mobile-targetvec-goToTarget.png)

1. Destinazione lancio

   ![Verifica del collegamento profondo](images/mobile-targetvec-launchTarget.png)

1. Fate clic sul pulsante **[!UICONTROL Crea attività]** e selezionate Test **[!UICONTROL A/B]**
1. Seleziona app **[!UICONTROL mobile]**
1. Accertatevi che **[!UICONTROL Visual]** sia selezionato in **[!UICONTROL Scegli Experience Composer (Scegli Experience Composer)]**
1. Fate clic sul pulsante **[!UICONTROL Avanti]**

   ![Creare un'attività A/B utilizzando Mobile VEC](images/mobile-targetvec-createActivity.png)

1. Nella schermata **[!UICONTROL Selezionate un'app da usare]** , fate clic su **[!UICONTROL Aggiungi nuova app]**

   ![Aggiungi una nuova app](images/mobile-targetvec-addNewApp.png)

1. Inserire lo schema URL appena definito nel campo **[!UICONTROL Inserisci schema]** URL, ad esempio `http://com.adobe.example.busbooking/`
1. Fai clic su **[!UICONTROL Crea collegamento profondo]**

   ![Inserisci il tuo schema URL e crea il collegamento profondo](images/android/mobile-targetvec-enterURLScheme.png)

   >[!NOTE] Hai alcune opzioni per inviare il collegamento profondo all'app. È possibile:
   >
   >   1. Invia per e-mail il collegamento profondo a un indirizzo e-mail valido, quindi apri il collegamento con un'applicazione e-mail sul dispositivo
   >   1. Scatta una foto del codice QR dal tuo dispositivo Android (nella nostra esercitazione, il dispositivo dovrebbe essere collegato ad Android Studio)
   >   1. Copiare il collegamento profondo dall'interfaccia di Target e inviarlo al dispositivo come desiderato


1. Fate clic sulla scheda **[!UICONTROL Copia e invia collegamento]** .
1. Fate clic sull’URL generato (fate clic sull’URL per copiarlo automaticamente negli Appunti)

   ![Copiare l’URL](images/android/mobile-targetvec-copyURL.png)

1. Aprire una finestra del terminale (o tornare ad essa se è ancora aperta)
1. Andate alla directory degli strumenti della piattaforma Android (potete già essere qui): `cd Library/Android/sdk/platform-tools/`
1. Confermate che l'emulatore sia collegato: `./adb devices`
1. Aprite la shell adb: `./adb shell`
1. Nella shell adb, sostituisci [TUO_TARGET_URL_WITH_TOKEN] nel seguente comando con l’URL appena copiato negli Appunti: `am start -W -a android.intent.action.VIEW -d "[YOUR_TARGET_URL_WITH_TOKEN]" "com.adobe.busbooking"`
1. Dopo il caricamento dell'app, tornate alla scheda del browser in cui avete aperto Target. Dovresti vedere l'app caricata nel VEC.
1. Fai clic sulle risorse di testo e immagini nell'app e dovresti vedere le opzioni per modificarle e sostituirle!

   ![Carichi delle app nel VEC](images/android/mobile-targetvec-devicePaired.png)

   > [!TIP] Se non visualizzi Mobile VEC automaticamente aperto nell'interfaccia di Target dopo l'apertura del collegamento profondo nel dispositivo mobile, puoi provare ad effettuare le seguenti operazioni:
   >
   >   1. Accertatevi di usare lo stesso URL esatto nell'interfaccia di Target e di non rimuovere accidentalmente alcun carattere. Quando eseguite il comando nella shell adb, accertatevi che l’URL sia racchiuso tra virgolette
      >
      >
      >   

   1. Confermate di aver aggiunto al file build.gradle le dipendenze aggiuntive richieste dalla VEC di Target. Queste dipendenze avrebbero dovuto essere aggiunte durante la lezione [Installa l’SDK di Mobile](https://docs.adobe.com/content/help/en/experience-cloud/implementing-in-mobile-android-apps-with-launch/configure-launch/launch-install-the-mobile-sdk.html#update-the-buildgradle-file)
      >
      >
      >   

   1. Prova a cancellare i dati memorizzati nell'app, come illustrato nell'immagine seguente
      >
      >       
      ![Carichi delle app nel VEC](images/android/mobile-targetvec-pairing-clearData.png)


1. Apportate alcune modifiche alla prima schermata dell'app
1. Ora posizionare l'emulatore accanto al browser con il VEC aperto
1. Andate a una schermata diversa nell'app e notate come il VEC si aggiorna con l'emulatore!
1. Puoi effettuare aggiornamenti a più viste nell'app, in una singola attività!

   ![Carichi delle app nel VEC](images/android/mobile-targetvec-navigateTheApp.png)

1. Puoi anche aggiungere visivamente metriche di monitoraggio dei clic!
1. Salvate e accettate l'attività e verificate di poterla vedere nell'app di esempio

La coppia del dispositivo con il VEC è un'azione una tantum. Quando crei più attività in futuro sullo stesso dispositivo, potrai semplicemente selezionare il dispositivo da un elenco, come illustrato di seguito:

![Utilizzo di un dispositivo salvato](images/android/mobile-targetvec-useSavedApp.png)

>[!TIP] Se il dispositivo è aperto, ma è "Non disponibile" nel menu di selezione, provate a chiudere e riaprire l'app sull'emulatore o sul dispositivo.

## Creazione di audience in base alle metriche del ciclo di vita

Metriche del ciclo di vita integrate relative all’utilizzo dell’app da parte del visitatore, incluse automaticamente nelle chiamate effettuate dall’SDK di Adobe Mobile. Puoi creare facilmente audience in Target in base a queste metriche.

**Per creare un'audience**

1. Nell'interfaccia di Target, fai clic su **Audience** nella navigazione superiore
1. Fate clic sul pulsante **Crea pubblico**

   ![Creare una nuova audience](images/mobile-targetvec-audienceList.png)

1. Name the Audience `Launches < 5`
1. Click **Add Rule &gt; Custom**

   ![Selezionare l'opzione Personalizzato](images/mobile-targetvec-custom.png)

1. Nel primo elenco a discesa, selezionate il parametro **a.Launches** . Tutti i parametri della metrica Ciclo di vita iniziano con "a". prefix. Il contenuto verrà indirizzato al pubblico in base al numero di avvii dell'app di cui dispone l'utente, il che rappresenta un modo eccellente per eseguire il targeting dei nuovi utenti dell'app con un'esperienza di primo utilizzo (FTUE) di tipo istruttivo.
1. Nel menu a discesa successivo, seleziona **è minore di**
1. Nel terzo menu a discesa, digitate **5**
1. Fai clic su **Salva**

   ![Pubblico per avvii &lt;= 4](images/mobile-targetvec-LaunchesLessThan5.png)

In Target sono disponibili numerose opzioni per la creazione di audience pronte all'uso. Inoltre, puoi inviare dati personalizzati nella richiesta Target per la creazione di audience, utilizzare audience condivise da altre soluzioni Experience Cloud come Audience Manager e Analytics e dati CRM condivisi con Target tramite la funzione Attributi cliente del servizio core Persone.

[Next "Add Adobe Target" (Aggiungi Adobe Target) &gt;](target.md)