---
title: Implementazione di Adobe Analytics con Launch
description: Scopri come implementare Adobe Analytics utilizzando l’estensione Adobe Analytics Launch, inviare un beacon per la visualizzazione a schermo, aggiungere variabili, tenere traccia degli eventi e aggiungere plug-in. Questa lezione fa parte dell'esercitazione Implementazione di Experience Cloud nelle applicazioni Android per dispositivi mobili.
seo-description: null
seo-title: Implementazione di Adobe Analytics con Launch
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: e9dee6d0aa3b775d0ce617e2b2c57b56de491b8d

---


# Aggiungere Adobe Analytics

In questa lezione, avrai abilitato il tracciamento di Adobe Analytics nella tua app.

[Adobe Analytics](https://docs.adobe.com/content/help/en/analytics/landing/home.html) è una soluzione leader di settore che ti consente di comprendere i tuoi clienti come persone e gestire la tua attività grazie alle informazioni sul cliente.

Nelle lezioni [Aggiungi estensioni](launch-add-extensions.md) e [Installa l’SDK](launch-install-the-mobile-sdk.md) Mobile, hai aggiunto l’estensione Adobe Analytics alla proprietà Launch e l’hai importata nell’applicazione di esempio.  Ora è sufficiente aggiungere codice per tenere traccia degli stati e delle azioni nell’app!

## Obiettivi di apprendimento

Alla fine di questa lezione, potrai:

* Verifica che le metriche del ciclo di vita vengano inviate ad Adobe Analytics
* Aggiunta di codice per tenere traccia degli stati nell'app con dati aggiuntivi
* Aggiunta di codice per tenere traccia delle azioni nell'app con dati aggiuntivi

Ci sono molte cose che potrebbero essere implementate per Analytics in Launch. Questa lezione non è esaustiva, ma dovrebbe fornire una panoramica completa delle tecniche principali necessarie per l'implementazione nella vostra app.

## Prerequisiti 

You should have already completed the lessons in the [Configure Launch](launch-create-a-property.md) section. In questa sezione hai aggiunto l’estensione Analytics e configurato il server di tracciamento e gli ID suite di rapporti.

## Metriche del ciclo di vita e Adobe Analytics

Le metriche del ciclo di vita sono metriche e dimensioni basate sull'ambiente che possono essere facilmente abilitate in un'app tramite l'SDK di Experience Platform Mobile.

Hai già attivato le metriche del ciclo di vita quando hai aggiunto l’estensione Core alla tua proprietà e hai seguito le istruzioni di installazione mobile fornite nell’interfaccia. Queste metriche e dimensioni, comprese metriche specifiche per l'ambiente e l'app come la versione dell'app, il numero di utenti coinvolti, la versione del sistema operativo, la suddivisione del tempo, i giorni dall'ultimo utilizzo, ecc. può essere molto utile nell'analisi dell'app, soprattutto quando crei segmenti Analytics da essi da applicare a tutti i tuoi report. L'elenco completo delle metriche è disponibile nella [documentazione](https://docs.adobe.com/content/help/en/mobile-services/android/metrics.htmlh).

## Importazione della libreria ACPCore

Nella precedente lezione denominata ["Install the Mobile SDK"](launch-install-the-mobile-sdk.md), hai aggiunto un'istruzione import per rendere disponibile la libreria AdobeCore nel file BusBookingActivity. La stessa libreria verrà utilizzata per chiamate API aggiuntive nelle attività di questa lezione. Negli esercizi successivi, utilizzerai le API per monitorare gli stati ("trackState") e le azioni ("trackAction") nell'app, che sono definite nella libreria AdobeCore.  Nella nuova SDK Experience Cloud Platform Mobile, le API trackState e trackAction sono state spostate dalla libreria Analytics alla libreria Core, consentendo di sfruttare queste API per scopi diversi dal tracciamento di Adobe Analytics.

## Stati traccia

Nell'app, puoi avere diverse schermate di contenuto che fornisci agli utenti. Sono l’equivalente delle pagine di un sito Web. Adobe Analytics fornisce un metodo che consente di inviare questi "hit di visualizzazione delle pagine" e di visualizzarli negli stessi report utilizzati per le proprietà Web. Questo metodo è denominato "trackState".

In questa esercitazione inserirai il codice per una chiamata trackState in una sola schermata (pagina) dell’app. Nella vita reale, questo verrà replicato su tutti gli altri schermi/stati dell'app.

Di seguito sono riportati sintassi ed esempio di codice dalla documentazione che puoi copiare e incollare in questa esercitazione o nella tua app.

**Sintassi:**

```java
public static void trackState(final String state, final Map<String, String> contextData)
```

**Esempio:**

```java
HashMap cData = new HashMap<String, String>();
contextData.put("key", "value");
MobileCore.trackState("state name",contextData);
```

### Tracciare uno stato senza dati

1. Con l'app di esempio aperta in Android Studio, andate a BusBookingActivity e scorrete verso il basso vicino alla funzione onResume
1. Aggiunta di una chiamata al metodo trackState
1. Impostare `state name` su "Schermata di prenotazione"
1. Invece di aggiungere altri dati, aggiungi `null` come segnaposto nella chiamata API
1. Oppure copiate e incollate i seguenti elementi:

   ```java
   MobileCore.trackState("Booking Screen", null);
   ```

![Chiamata trackState di base](images/android/mobile-analytics-basicTrackStateCall2.png)

**Per convalidare trackState**

1. Salvare, generare ed eseguire il progetto
1. Quando il simulatore viene eseguito e apre la schermata iniziale dell'app, visualizzate la console di debug Logcat di Android Studio
1. Cercare nella console `pageName=Booking%20Screen`
1. Si noti che la variabile pageName è impostata su `Booking Screen` (con %20 come spazio codificato) e che non sono presenti altre coppie di dati personalizzate. Anche se tecnicamente state impostando un "nome stato" e non un "nome pagina", il nome del parametro utilizzato è `pageName` allo scopo di fornire coerenza con le implementazioni del sito Web.

   ![Risultato trackState di base](images/android/mobile-analytics-basicTrackStateResult.png)

### Tracciare uno stato con i dati

1. Tornate a BusBookingActivity e aggiungete un'importazione nella parte superiore del file `import java.util.HashMap;` sotto le importazioni esistenti
1. Nella `onResume()` funzione, aggiungi un commento o elimina la chiamata trackState di base dall’ultimo esercizio
1. Aggiungi una nuova chiamata del metodo trackState, stavolta con i dati creando e denominando una HashMap, utilizzando il comando "put" per includere alcune coppie chiave/valore, e quindi chiamando HashMap nella chiamata a trackState
1. Lasciare `state name` come "Schermata di prenotazione"
1. Oppure copiate e incollate in:

   ```java
   HashMap cData = new HashMap<String, String>();
   cData.put("cd.section", "Bus Booking");
   cData.put("cd.subSection", "Booking");
   cData.put("cd.conversionType", "Landing");
   MobileCore.trackState("Booking Screen", cData);
   ```

   ![trackState Call with Data](images/android/mobile-analytics-trackStateWithData.png)

**Convalida di trackState con i dati**

1. Salvate, create ed eseguite nuovamente il progetto
1. Quando il simulatore viene eseguito e apre la schermata iniziale dell'app, visualizzate la console di debug Logcat di Android Studio
1. Cercare `subSection` (o una delle chiavi o dei valori inseriti nel codice)
1. Ora puoi vedere che oltre all’impostazione pageName, hai anche le coppie chiave/valore che sono state inviate all’hit

   ![trackState con risultato dei dati](images/android/mobile-analytics-trackStateWithDataResult.png)

>[!NOTE] Se hai familiarità con "prop ed eVar" in Analytics, noterai che questi nomi di variabili non sono nell’SDK. Tutti i dati chiave/valore provenienti dall’SDK saranno inviati come variabili [](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/variables-analytics-reporting/context-data-variables.html)contextData e come tali dovranno essere mappati su proprietà o eVar (o altre variabili) utilizzando le regole [di](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html) elaborazione nell’interfaccia utente di Analytics.

## Tracciare le azioni

Simile al tracciamento delle azioni non caricate di pagina su un sito Web, spesso si desidera tracciare un’azione eseguita da un utente nell’app, ad esempio clic su elementi che non caricano un’altra schermata. Questo viene gestito in modo molto simile a trackState utilizzato in precedenza, con la differenza che questo metodo viene chiamato `trackAction`.

Di seguito sono riportati la sintassi e un esempio di codice dalla documentazione.

**Sintassi:**

```java
public static void trackAction(final String action, final Map<String, String> contextData) data;
```

**Esempio:**

```java
HashMap<String, String> contextData = new HashMap<String, String>();
contextData.put("key", "value");
MobileCore.trackAction("action taken", contextData);
```

### Tracciare l’interazione con il commutatore di destinazione

In questa app di prenotazione bus di esempio, potete cambiare la città di origine con la città di destinazione facendo clic sulla freccia tra questi due valori. Hai deciso di monitorare l'interazione con questa funzione in Adobe Analytics.

![Switcher di destinazione](images/android/mobile-analytics-destinationSwitcher.png)

Questo switcher è controllato nel file BusBookingActivity nel progetto di esempio. In questo esercizio, invierai un hit trackAction ogni volta che qualcuno fa clic su di esso.

#### Per aggiungere il codice trackAction

1. Con il progetto di esempio aperto in Android Studio, andate a BusBookingActivity
1. Individuare la funzione "mBtnFlip.setOnClickListener", sulla riga 57 o intorno
1. Espandere la funzione se necessario, in modo da visualizzare tutto il codice
1. Nella funzione onClick, sotto la chiamata a `flipSourceDesti()`, aggiungere una `trackAction()` chiamata
1. Impostate il nome dell’azione su "Capovolgi destinazione" e aggiungete "null" per il parametro contextData (in quanto non è necessario inviare informazioni aggiuntive al momento)
1. Potete copiare e incollare il seguente codice

   ```java
   MobileCore.trackAction("Flip Destination", null);
   ```

La funzione ora si presenta così:

![Codice del commutatore di destinazione](images/android/mobile-analytics-destinationSwitcherCode.png)

#### Convalida del codice trackAction

1. Dopo aver aggiunto il codice, salvate il progetto, eseguite e create
1. Fate clic sull’icona del cestino per cancellare la console Logcat
1. Fate clic sulla freccia del commutatore di destinazione nel simulatore, notando che viene visualizzata una nuova richiesta (o più) nella console.
1. Cerca `Flip%20Destination` in Logcat
1. Tenere presente che i parametri action e pev2 Flip%20Destination (con spazio codificato)
1. Osserva il `pe=lnk_o` tasto/valore sulla stessa riga, che indica che si tratta di un hit "collegamento personalizzato", attivato da trackAction

   <!--![trackAction Result in Debugger](images/android/mobile-analytics-trackActionResult1.png)-->

Bel lavoro! Hai completato la lezione di Analytics. Naturalmente, ci sono molte altre cose che potete fare per migliorare la nostra implementazione di Analytics, ma spero che questo vi abbia dato alcune delle competenze fondamentali che avrete bisogno di affrontare il resto delle vostre esigenze.

## Ulteriori vantaggi di trackState e trackAction

In questi ultimi esercizi, è stato possibile inviare dati dall’app ad Adobe Analytics utilizzando le API trackState e trackAction. Poiché l’SDK di Experience Platform Mobile si basa su Launch, nell’interfaccia Launch sono disponibili molte altre operazioni che puoi eseguire sfruttando il codice appena aggiunto.

In Launch è possibile creare regole attivate dalle API trackState e trackAction e farle eseguire azioni aggiuntive, ad esempio richieste ad altre soluzioni Adobe o ad altri partner esterni.

[Successivo "Aggiungi Adobe Audience Manager" &gt;](audience-manager.md)
