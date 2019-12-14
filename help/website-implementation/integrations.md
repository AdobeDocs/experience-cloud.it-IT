---
title: Implementazione delle integrazioni Experience Cloud con Launch
description: Scopri come convalidare le integrazioni Audiences, A4T e Attributi del cliente nell’implementazione di Adobe Experience Cloud. Questa lezione fa parte dell’esercitazione Implementazione di Experience Cloud nei siti Web con Launch.
seo-description: null
seo-title: Implementazione delle integrazioni Experience Cloud con Launch
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: e9dee6d0aa3b775d0ce617e2b2c57b56de491b8d

---


# Integrazioni di Experience Cloud

In questa lezione verranno esaminate le integrazioni chiave tra le soluzioni appena implementate. La buona notizia è che completando le lezioni precedenti, hai già implementato gli aspetti del codice delle integrazioni! Non è necessario eseguire ulteriori operazioni in questa lezione oltre a leggere e convalidare.

## Obiettivi di apprendimento

Alla fine di questa lezione, potrai:

1. Spiegate i casi di utilizzo di base per le integrazioni di condivisione di pubblico, analisi per Target (A4T) e attributi cliente
1. Convalidare gli aspetti dell'implementazione di base lato client di queste integrazioni

## Prerequisiti

Prima di seguire le istruzioni fornite in questa lezione, è necessario completare tutte le lezioni precedenti.

>[!NOTE] Esistono molti requisiti di autorizzazioni utente, configurazioni account e passaggi di provisioning necessari per utilizzare completamente queste integrazioni e che vanno oltre l'ambito di questa esercitazione. Se non usi già queste integrazioni nell'implementazione corrente di Experience Cloud, tieni presente quanto segue:
>
> * Verifica tutti i requisiti delle [integrazioni dei Servizi Core](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html)
> * Verifica i requisiti completi dell'[integrazione di Analytics for Target](https://docs.adobe.com/content/help/en/target/using/integrate/a4t/before-implement.html)
> * Have an Administrator of your Experience Cloud Organization [request provisioning of these integrations](https://www.adobe.com/go/audiences)


## Tipi di pubblico

[Audiences](https://docs.adobe.com/content/help/en/core-services/interface/audiences/audience-library.htm) fa parte del servizio di base Persone e consente di condividere i tipi di pubblico tra le soluzioni. Ad esempio, puoi creare un'audience in Audience Manager e utilizzarla per distribuire contenuti personalizzati con Target.

I requisiti principali per implementare A4T, che avete già fatto, sono i seguenti:

1. Implementazione di Adobe Experience Platform Identity Service
1. Implementazione di Audience Manager
1. Implementate altre soluzioni che desiderate ricevere o creare audience, come Target e Analytics

### Convalida dell'integrazione Audiences

Il modo migliore per convalidare l'integrazione di Audiences è quello di creare effettivamente un'audience, condividerla con un'altra soluzione e quindi utilizzarla completamente nell'altra soluzione (ad esempio, per verificare che un visitatore idoneo per un segmento AAM possa qualificarsi per un'attività Target mirata a quel segmento). Tuttavia, questo va oltre l'ambito dell'esercitazione.

Questi passaggi di convalida si concentreranno sulla parte critica visibile nell’implementazione lato client, ovvero l’ID visitatore.

1. Open the [Luma site](https://luma.enablementadobe.com/content/luma/us/en.html)

1. Make sure the Debugger is mapping the Launch property to *your* Development environment, as described in the [earlier lesson](launch-switch-environments.md)

   ![L'ambiente di sviluppo Launch mostrato in Debugger](images/switchEnvironments-debuggerOnWeRetail.png)

1. Vai alla scheda Rete del Debugger

1. Fai clic su **[!UICONTROL Cancella tutte le richieste]** solo per ripulire le cose

1. Ricarica la pagina Luma, accertandoti di visualizzare sia le richieste Target che quelle Analytics nel Debugger

1. Ricaricare di nuovo la pagina Luma

1. Dovresti ora visualizzare quattro richieste nella scheda Rete del Debugger, due per Target e due per Analytics

1. Cerca nella riga con l’etichetta "Experience Cloud Visitor ID". Gli ID in tutte le richieste di ogni soluzione devono essere sempre gli stessi.

   ![Conferma gli SDID corrispondenti](images/integrations-matchingECIDs.png)

1. Gli ID sono univoci per visitatore. Puoi confermarli chiedendo a un collega di ripetere questi passaggi.

## Analytics for Target (A4T)

The [Analytics for Target (A4T)](https://docs.adobe.com/content/help/en/target/using/integrate/a4t/a4t.html) integration allows you to leverage your Analytics data as the source for reporting metrics in Target.

I requisiti principali per implementare A4T, che avete già fatto, sono i seguenti:

1. Implementazione di Adobe Experience Platform Identity Service
1. Avvia la richiesta di caricamento della pagina di Target prima del beacon di visualizzazione della pagina di Analytics

A4T funziona unendo una richiesta lato server da Target ad Analytics con il beacon di visualizzazione pagina di Analytics, che chiamiamo "hit-stitching".  L'unione di hit richiede che la richiesta Target che distribuisce l'attività (o incrementa una metrica di obiettivo basata su Target) abbia un parametro che corrisponda a un parametro nel beacon di visualizzazione della pagina di Analytics. Questo parametro è chiamato ID dati supplementare (SDID).

### Convalidare l'implementazione di A4T

Il modo migliore per convalidare l'integrazione A4T consiste nel creare effettivamente un'attività Target utilizzando A4T e convalidare i dati di reporting, ma questo va oltre l'ambito di questa esercitazione. Questa esercitazione vi mostrerà come confermare che gli ID dati supplementari corrispondono tra le chiamate della soluzione.

**Convalida degli SDID**

1. Open the [Luma site](https://luma.enablementadobe.com/content/luma/us/en.html)

1. Make sure the Debugger is mapping the Launch property to *your* Development environment, as described in the [earlier lesson](launch-switch-environments.md)

   ![L'ambiente di sviluppo Launch mostrato in Debugger](images/switchEnvironments-debuggerOnWeRetail.png)

1. Vai alla scheda Rete del Debugger

1. Fai clic su **[!UICONTROL Cancella tutte le richieste]** solo per ripulire le cose

1. Ricarica la pagina Luma, accertandoti di visualizzare sia le richieste Target che quelle Analytics nel Debugger

1. Ricaricare di nuovo la pagina Luma

1. Dovresti ora visualizzare quattro richieste nella scheda Rete del Debugger, due per Target e due per Analytics

1. Osserva la riga "Supplemental Data ID". Gli ID dal caricamento della prima pagina devono corrispondere tra Target e Analytics. Anche gli ID del secondo caricamento della pagina devono corrispondere, ma sono diversi da quelli del primo caricamento.

   ![Conferma gli SDID corrispondenti](images/integrations-matchingSDIDs.png)

Se effettui richieste Target aggiuntive nell'ambito di un caricamento di pagina (escludendo le app a pagina singola) che fanno parte di attività A4T, è opportuno assegnare loro nomi univoci (non target-global-mbox) in modo che continuino ad avere gli stessi SDID delle richieste Target e Analytics iniziali.

## Attributi cliente

[Attributi](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html) cliente è una parte del servizio core Persone che consente di caricare dati dal database CRM (Customer Relationship Management) e di sfruttarli in Adobe Analytics e Adobe Target.

I requisiti principali per l'implementazione degli attributi cliente, che hai già fatto, sono i seguenti:

1. Implementazione di Adobe Experience Platform Identity Service
1. Set Customer Ids via the Id Service *before* Target and Analytics fire their requests (which you accomplished using the rule ordering feature in Launch)

### Convalida dell'implementazione degli attributi cliente

Hai già verificato che gli ID cliente vengano passati sia al servizio identità che a Target nelle lezioni precedenti. Puoi anche convalidare l'ID cliente nell'hit Analytics.
Al momento, l'ID cliente è uno dei pochi parametri che non vengono visualizzati nel debugger Experience Cloud, pertanto per visualizzarlo dovrai utilizzare la console JavaScript del browser.

1. Aprire il sito Luma
1. Apri gli strumenti per sviluppatori del browser
1. Vai alla scheda Rete
1. Nel campo del filtro, digita `b/ss` che limiterà il contenuto visualizzato alle richieste di Adobe Analytics

   ![Aprite gli Strumenti per sviluppatori e filtrate la scheda Rete per visualizzare solo le richieste di Analytics](images/aam-openTheJSConsole.png)

1. Fate clic sul collegamento **[!UICONTROL LOGIN]** nell'angolo superiore destro del sito

   ![Fate clic su Login nella navigazione superiore](images/idservice-loginNav.png)

1. Inserisci `test@adobe.com` come nome utente
1. Immettere `test` come password
1. Fare clic sul pulsante **[!UICONTROL LOGIN]**

   ![Immettere le credenziali e fare clic su login](images/idservice-login.png)

1. Dovrebbe tornare alla home page, che attiverà anche un beacon visibile negli strumenti per sviluppatori. Se siete portati alla pagina delle informazioni sull'account, fate clic sul logo WE.RETAIL per tornare alla pagina principale.
1. Fate clic sulla richiesta e selezionate la scheda Intestazioni
1. Scorri verso il basso fino a visualizzare alcuni parametri nidificati
   1. cid: delimitatore standard per la parte ID cliente della richiesta
   1. crm_id - Questo è il codice di integrazione personalizzato, specificato nella lezione Servizio identità
   1. id - Il valore ID cliente proviene dall’elemento `Email (Hashed)` dati
   1. as - Stato di autenticazione, con il significato "1" registrato
   ![Convalida ID cliente Analytics](images/integrations-analyticsCustomerIDValidation.png)

[Avanti "Pubblica la tua proprietà" &gt;](publish.md)