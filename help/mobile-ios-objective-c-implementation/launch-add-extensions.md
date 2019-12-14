---
title: Aggiungere estensioni a una proprietà di avvio mobile
description: Scopri come aggiungere estensioni a una proprietà Lancio mobile. Questa lezione fa parte dell'esercitazione Implementazione di Experience Cloud nelle applicazioni iOS Objective-C per dispositivi mobili.
seo-description: null
seo-title: Aggiungere estensioni a una proprietà di avvio mobile
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 7166d2933cc99bcbbd4713fba8f87fb0826b711e

---


# Aggiungi estensioni

In questa lezione verranno aggiunte estensioni alla proprietà Launch.

Launch è una piattaforma che consente ad Adobe e ai fornitori di terze parti di creare estensioni per semplificare l'implementazione delle proprie soluzioni tramite Launch. Un'estensione è un pacchetto di codice che estende l'interfaccia Launch e la funzionalità client. Le estensioni consentono di scegliere solo le parti dell’SDK Adobe Experience Platform Mobile necessarie per la tua app specifica.  Se si paragona Launch a un sistema operativo, le estensioni sono paragonabili alle applicazioni che consentono di eseguire determinate attività.

Poiché state implementando le soluzioni Adobe (ad esempio Target, Analytics e Audience Manager), aggiungete le estensioni necessarie per supportarle.

>[!WARNING] Per aggiungere e rimuovere estensioni nelle proprietà di avvio mobile è necessario aggiornare l'app. Questa funzione è diversa dalle proprietà di avvio Web, in cui è possibile aggiungere o rimuovere estensioni in qualsiasi momento, senza dover aggiornare il sito Web.

## Prerequisiti 

Per completare la lezione, l'account utente di Launch necessita dell'autorizzazione "Gestisci estensioni". Se non riesci a completare nessuno di questi passaggi perché le opzioni dell'interfaccia utente non sono disponibili, rivolgiti al tuo amministratore Experience Cloud per avere accesso. For more information on Launch permissions, see [the documentation](https://docs.adobe.com/content/help/en/launch/using/reference/admin/user-permissions.html).

Saranno necessari i seguenti dettagli della soluzione:

* Almeno un ID suite di rapporti di Analytics. La suite di rapporti deve avere rapporti [app abilitati](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/mobile-management.html). If you don't have a test/dev report suite that you can use for this tutorial, please [create one](https://docs.adobe.com/content/help/en/analytics/admin/manage-report-suites/new-report-suite/new-report-suite.html). Una suite di rapporti è sufficiente per questa esercitazione, ma nel mondo reale si desidera utilizzare suite di rapporti diverse per gli ambienti di sviluppo, gestione delle fasi e produzione.

* Il server di tracciamento di Analytics. Puoi recuperare il server di tracciamento dall’implementazione corrente, dal consulente Adobe o dal rappresentante dell’assistenza clienti.

## Obiettivi di apprendimento

Alla fine di questa lezione, potrai:

* Aggiungere estensioni a una proprietà di avvio mobile
* Configura l'estensione Analytics
* Configurare le estensioni VEC Target e Target

>[!NOTE] Adobe Audience Manager può essere implementato tramite una configurazione nell’estensione Analytics, pertanto non dovrai aggiungere l’estensione Audience Manager in questa esercitazione

## Esaminare le estensioni preinstallate

1. Fare clic sulla scheda **[!UICONTROL Estensioni]** per passare alla pagina delle estensioni
1. Nota: Mobile Core e `Profile` le estensioni sono preinstallate nella nuova proprietà mobile
1. Fate clic sul pulsante **[!UICONTROL Configura]** nell’estensione Core per esaminarne le impostazioni

   ![Vai alla scheda delle estensioni](images/mobile-extensions-installed-default.png)

1. L'estensione Mobile Core rappresenta l'SDK principale di Adobe Experience Platform Mobile richiesto per qualsiasi implementazione dell'app. Il core contiene un set comune di funzionalità e framework quali servizi Experience Cloud Identity, hub eventi dati, motore delle regole, rete riutilizzabile, routine di accesso al disco ecc., richiesti da tutte le estensioni Adobe e di terze parti.  Per ulteriori informazioni sull'estensione Mobile Core, consulta [la documentazione](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core).

   1. Il tuo ID organizzazione Experience Cloud viene rilevato automaticamente e precompilato
   1. Il campo Experience Cloud Server consente di specificare un endpoint personalizzato per le richieste del servizio ID visitatori. Per questa esercitazione, utilizzate l'impostazione predefinita (lasciatela vuota).
   1. Il campo Timeout sessione consente di specificare il timeout di una sessione del ciclo di vita dell’app. Per impostazione predefinita, il timeout dell'app si verifica se l'app è in background per 300 secondi. Utilizzate l'impostazione predefinita per questa esercitazione.

1. Poiché non avete modificato nessuna delle impostazioni, fate clic su **[!UICONTROL Annulla]** per uscire dalla configurazione dell'estensione

   ![Fate clic su Annulla per uscire dalla configurazione](images/mobile-extensions-core-cancel.png)

1. L’estensione Profile consente all’SDK di archiviare i dati in un profilo lato client. Non ha configurazioni, quindi non c'è niente da guardare. Per ulteriori informazioni sull’estensione Profilo, consulta [la documentazione](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/profile).

## Aggiungere le estensioni della soluzione

È ora di iniziare ad aggiungere le estensioni per le soluzioni da implementare in questa esercitazione. Quando si utilizza Launch con applicazioni mobili, l'app deve essere aggiornata ogni volta che viene aggiunta o rimossa un'estensione. Per risparmiare tempo in seguito, aggiungeremo tutte le estensioni in questa lezione. È sufficiente saltare le soluzioni per le quali la società non ha concesso la licenza.

### Aggiungere l’estensione Adobe Analytics

>[!NOTE] Se non disponete di una licenza per Adobe Analytics, potete saltare questa sezione. Al momento, l'estensione Analytics per le proprietà dei dispositivi mobili viene utilizzata solo per gestire le impostazioni SDK e non aggiunge opzioni di interfaccia a Launch, come le azioni Regola.

**Per aggiungere l'estensione**

1. Fate clic sulla scheda Catalogo per visualizzare le estensioni _disinstallate_

1. Trovate l’estensione **[!UICONTROL Adobe Analytics]** e fate clic su **[!UICONTROL Installa]**

   ![Andate al catalogo Estensioni e fate clic su Installa per aggiungere l'estensione Analytics](images/mobile-extensions-catalog-installAnalytics.png)

1. Selezionate le suite di **[!UICONTROL rapporti]** dagli elenchi precompilati. Sono le suite di rapporti a cui l'app invierà i dati. Puoi selezionare diverse suite di rapporti per i tuoi ambienti di sviluppo, gestione delle fasi e produzione.
1. Il server **[!UICONTROL di tracciamento]** Analytics potrebbe essere precompilato oppure potrebbe essere necessario selezionarlo da un elenco precompilato o immetterlo manualmente. Si tratta del dominio a cui verranno inviati i beacon, in genere nel formato `yoursite.sc.omtrdc.net`.
1. Selezionare la casella per **[!UICONTROL Offline Enabled]**. Quando la casella di controllo Abilitato offline è selezionata, gli hit di Analytics vengono messi in coda quando il dispositivo è offline e inviati successivamente quando il dispositivo è nuovamente online. Per utilizzare il tracciamento offline, **accertati** che le marche temporali siano abilitate nella suite di rapporti. For more information, see the [documentation](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/offline-tracking.html).
1. Selezionate la casella per l'inoltro **[!UICONTROL di]** Audience Manager. In questo modo i dati di Analytics verranno inoltrati ad Audience Manager, in modo da non dover effettuare una chiamata aggiuntiva dall'app ad Audience Manager. In questo esercizio supponiamo che tu disponga di Audience Manager e pertanto invii i dati da Analytics. Se non disponete di Audience Manager, non selezionate questa casella quando configurate Analytics per la vostra implementazione.
1. Selezionare la casella per **[!UICONTROL retrodatare le informazioni sulla sessione precedente]**
1. Fate clic sul pulsante **[!UICONTROL Salva]**

   ![Andate al catalogo Estensioni e fate clic su Installa per aggiungere l'estensione Analytics](images/mobile-extensions-analytics-settings.png)

### Aggiungi l'estensione Target

Adobe Target dispone di due estensioni ufficiali, l'estensione Adobe Target e l'estensione Adobe Target VEC. Adobe Target supporta tutte le API familiari agli utenti dei nostri SDK mobili precedenti. L'estensione Adobe Target VEC aggiunge il supporto per Target Visual Experience Composer (Compositore esperienza visivo), che consente agli esperti di marketing di creare semplici attività che modificano elementi di immagine e testo sulla pagina in un'interfaccia WYSIWYG (What-You-See-Is-What-You-Get). In questa esercitazione verranno utilizzati entrambi.

>[!NOTE] Se non disponete di una licenza per Adobe Target, potete ignorare questa sezione. Al momento, l'estensione Target per le proprietà dei dispositivi mobili viene utilizzata solo per gestire le impostazioni SDK e non aggiunge opzioni di interfaccia a Launch, come le azioni Regola.

**Per aggiungere l'estensione**

1. Fate clic sulla scheda Catalogo per visualizzare le estensioni _disinstallate_

1. Individuate l'estensione **[!UICONTROL Adobe Target]** e fate clic su **[!UICONTROL Installa]**

   ![Andate al catalogo Estensioni e fate clic su Installa per aggiungere l'estensione Target](images/mobile-extensions-catalog-installTarget.png)

1. Il codice **** client verrà precompilato.
1. Lasciate vuoto l'ID **** ambiente. Questa impostazione viene utilizzata insieme alla funzione [Ospitanti](https://docs.adobe.com/help/en/target/using/administer/hosts.html) di Adobe Target, che consente di inviare i dati a diversi ambienti di reporting (ad esempio Dev, Staging, Production). Per impostazione predefinita, i dati vengono inviati all'ambiente di produzione.
1. Lasciate vuota la proprietà **[!UICONTROL dell'area di lavoro di]** Target. Questa impostazione viene utilizzata insieme alla funzione Autorizzazioni [utente](https://docs.adobe.com/content/help/en/target/using/administer/manage-users/enterprise/property-channel.html) Enterprise di Target Premium.
1. Lasciate **[!UICONTROL Timeout]** impostato su 5 secondi. Questa impostazione controlla per quanto tempo l'app deve attendere la risposta di Target prima di visualizzare il contenuto predefinito.
1. Fate clic sul pulsante **[!UICONTROL Salva]**

   ![Configurare le impostazioni di Target](images/mobile-extensions-target-settings.png)

### Aggiungere l'estensione VEC di Target

Dopo aver aggiunto l'estensione Target, potete aggiungere l'estensione VEC di Target.

>[!NOTE] Se non disponete di una licenza per Adobe Target, potete ignorare questa sezione. Al momento, l'estensione VEC di Target per le proprietà dei dispositivi mobili viene utilizzata solo per gestire le impostazioni SDK e non aggiunge opzioni di interfaccia a Launch, come le azioni Regola.

**Per aggiungere l'estensione**

1. Fate clic sulla scheda Catalogo per visualizzare le estensioni _disinstallate_

1. Trovate l'estensione VEC **[!UICONTROL di]** Adobe Target e fate clic su **[!UICONTROL Installa]**

   ![Andate al catalogo Estensioni e fate clic su Installa per aggiungere l'estensione Target](images/mobile-extensions-catalog-installTargetVEC.png)

1. Attiva **[!UICONTROL automaticamente le campagne]** Target`ON` . In questo modo tutte le attività Target verranno prerecuperate al primo caricamento dell'app, riducendo il numero di richieste da effettuare.
1. Lasciate **[!UICONTROL Recupero In Background]**`OFF`. Questa impostazione viene visualizzata solo quando `Auto-Fetch Target Campaigns` viene utilizzata.  Lasciando questa impostazione `OFF` sarà possibile eseguire attività VEC nella schermata iniziale dell'app, ma sarà anche aggiunto un ritardo all'avvio dell'app per verificare che la richiesta Target sia stata completata o scaduta prima che venga visualizzata la schermata iniziale. È consigliabile lasciare questa impostazione `OFF` quando si eseguono attività nella schermata principale e attivarla `ON` quando non lo si è.  Questa impostazione può essere modificata in qualsiasi momento nell'interfaccia di Launch senza aggiornare l'app.
1. Fate clic sul pulsante **[!UICONTROL Salva]**

   ![Configurare le impostazioni VEC di destinazione](images/mobile-extensions-targetVEC-settings.png)

Tutto qui. Dopo aver aggiunto le estensioni alla proprietà, potete aggiungerle a una libreria:

[Successivo "Crea una libreria" &gt;](launch-create-a-library.md)