---
title: Pubblicare la proprietà Launch
description: Scopri come pubblicare la proprietà Launch dall'ambiente di sviluppo agli ambienti di gestione e produzione. Questa lezione fa parte dell’esercitazione Implementazione di Experience Cloud nei siti Web con Launch.
seo-description: null
seo-title: Pubblicare la proprietà Launch
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: aacd691c176da6ae5b247a19051de57289c128c5

---


# Pubblicare la proprietà Launch

Ora che hai implementato alcune soluzioni chiave di Adobe Experience Cloud nel tuo ambiente di sviluppo, è il momento di imparare il flusso di lavoro di pubblicazione.

## Obiettivi di apprendimento

Alla fine di questa lezione, potrai:

1. Pubblicare una libreria di sviluppo nell'ambiente di staging
1. Mappare una libreria Gestione temporanea nel sito Web di produzione utilizzando il debugger
1. Pubblicare una libreria di sviluppo nell'ambiente di produzione

## Pubblicare nell'ambiente di staging

Dopo aver creato e convalidato la libreria nell'ambiente di sviluppo, è ora di pubblicarla su Gestione temporanea.

1. Go to the **[!UICONTROL Publishing]** page

1. Aprite il menu a discesa accanto alla libreria e selezionate **[!UICONTROL Invia per approvazione]**

   ![Invia per approvazione](images/publishing-submitForApproval.png)

1. Fate clic sul pulsante **[!UICONTROL Invia]** nella finestra di dialogo:

   ![Fare clic su Invia nel modale](images/publishing-submit.png)

1. La libreria verrà ora visualizzata nella colonna [!UICONTROL Inviato] in uno stato non generato:

1. Aprite il menu a discesa e selezionate **[!UICONTROL Genera per gestione temporanea]**:

   ![Generazione per staging](images/publishing-buildForStaging.png)

1. Quando l'icona del puntino diventa verde, la libreria può essere visualizzata in anteprima nell'ambiente di staging.

In uno scenario reale, il passaggio successivo nel processo in genere consisterebbe nel far sì che il team di QA convalidi le modifiche nella libreria di staging. Possono farlo utilizzando il Debugger.

**Convalida delle modifiche nella libreria Gestione temporanea**

1. Nella proprietà Launch, apri la pagina [!UICONTROL Ambienti]

1. Nella [!UICONTROL riga Staging] , fate clic sull'icona ![](images/launch-installIcon.png) Installa per aprire la finestra modale

   ![Vai alla pagina Ambienti e fai clic per aprire la modalità](images/publishing-getStagingCode.png)

1. Fate clic sull’icona ![Copia (Copy)](images/launch-copyIcon.png) IconaCopia (Copy) per copiare il codice da incorporare negli Appunti

1. Click **[!UICONTROL Close]** to close the modal

   ![Icona di installazione](images/publishing-copyStagingCode.png)

1. Open the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html) in your Chrome browser

1. Apri l'estensione [](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) Experience Cloud Debugger facendo clic sull'icona dell'icona ![del](images/icon-debugger.png) debugger

   ![Fate clic sull'icona Debugger](images/switchEnvironments-openDebugger.png)

1. Vai alla scheda Strumenti

1. Fai clic su **[!UICONTROL Adobe Launch &gt; Inserisci dinamicamente lancio &gt; Pulsante Incorpora codice]** per aprire il campo di immissione del testo (potrebbe attualmente avere l'URL del codice da incorporare per lo sviluppo):

   ![Fate clic sul pulsante Adobe Launch &gt; Inserisci dinamicamente lancio &gt; Incorpora codice](images/switchEnvironments-debugger-editEmbedCode.png)

1. Incollare il codice da incorporare temporaneo presente negli Appunti

1. Fai clic sull'icona del disco per salvare

   ![Ambiente di avvio mostrato in Debugger](images/switchEnvironments-debugger-save.png)

1. Ricarica e seleziona la scheda Riepilogo del debugger. Nella sezione Launch (Lancio) è ora possibile vedere come la proprietà Staging sia implementata e che mostri il nome della proprietà (ad es. "Esercitazione di avvio" o qualsiasi altra cosa che hai chiamato la tua proprietà)!

   ![Ambiente di avvio mostrato in Debugger](images/publishing-debugger-staging.png)

In tempo reale, una volta che il team di controllo qualità ha effettuato l'accesso rivedendo i cambiamenti nell'ambiente di gestione temporanea, è ora di pubblicare i dati in produzione.

## Pubblicare in produzione

1. Go to the [!UICONTROL Publishing] page

1. Dal menu a discesa, fate clic su **[!UICONTROL Approva per la pubblicazione]**:

   ![Approva per la Pubblicazione](images/publishing-approveForPublishing.png)

1. Fate clic sul pulsante **[!UICONTROL Approva]** nella finestra di dialogo:

   ![Fate clic su Approva](images/publishing-approve.png)

1. La libreria verrà ora visualizzata nella colonna [!UICONTROL Approvato] nello stato non generato (punto giallo):

1. Aprite il menu a discesa e selezionate **[!UICONTROL **Genera e pubblica in produzione]**:

   ![Fate clic su Genera e pubblica in produzione](images/publishing-buildAndPublishToProduction.png)

1. Fate clic su **[!UICONTROL Pubblica]** nella finestra di dialogo:

   ![Fate clic su Pubblica](images/publishing-publish.png)

1. La libreria verrà ora visualizzata nella colonna [!UICONTROL Pubblicato] :

   ![Pubblicato](images/publishing-published.png)

È tutto! Hai completato l'esercitazione e pubblicato la tua prima proprietà in Launch!