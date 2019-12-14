---
title: Passaggio di ambienti di lancio con Adobe Experience Cloud Debugger
description: Scopri come utilizzare Experience Cloud Debugger per caricare diversi codici di incorporamento Launch. Questa lezione fa parte dell’esercitazione Implementazione di Experience Cloud nei siti Web con Launch.
seo-description: null
seo-title: Passaggio di ambienti di lancio con Adobe Experience Cloud Debugger
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 79d5274d09d66b80a49aba5db3e0a997d0f0ff61

---


# Passaggio di ambienti di lancio con Experience Cloud Debugger

In this lesson you will use the [Adobe Experience Cloud Debugger extension](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) to replace the Launch property hardcoded on the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html) with your own property.

Questa tecnica è chiamata "cambio di ambiente" e sarà utile in seguito, quando lavorate con Launch sul vostro sito Web. Potrai caricare il tuo sito Web di produzione nel browser, ma con il tuo ambiente di *sviluppo* Launch. Questo consente di apportare e convalidare in modo sicuro le modifiche di Launch indipendentemente dalle release del codice.  Dopo tutto, questa separazione tra rilasci di tag di marketing e rilasci di codice è uno dei motivi principali per cui i clienti utilizzano Launch in primo luogo!

## Obiettivi di apprendimento

Alla fine di questa lezione, potrai:

* Utilizzare il debugger per caricare un ambiente Launch alternativo
* Utilizzare il debugger per verificare di aver caricato un ambiente Launch alternativo

## Ottenere l’URL del proprio ambiente di sviluppo

1. In your Launch property, open the `Environments` page

1. In the **[!UICONTROL Development]** row, click the Install icon ![Install icon](images/launch-installIcon.png) to open the modal

1. Fate clic sull’icona ![Copia (Copy)](images/launch-copyIcon.png) IconaCopia (Copy) per copiare il codice da incorporare negli Appunti

1. Click **[!UICONTROL Close]** to close the modal

   ![Icona di installazione](images/launch-copyInstallCode.png)

## Sostituisce l’URL del lancio sul sito Demo luma

1. Open the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html) in your Chrome browser

1. Apri l'estensione [](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) Experience Cloud Debugger facendo clic sull'icona dell'icona ![del](images/icon-debugger.png) debugger

   ![Fate clic sull'icona Debugger](images/switchEnvironments-openDebugger.png)

1. La proprietà Launch attualmente implementata viene visualizzata nella scheda Riepilogo

   ![Ambiente di avvio mostrato in Debugger](images/switchEnvironments-debuggerOnWeRetail-prod.png)

1. Vai alla scheda Strumenti

1. Scorri fino alla sezione **[!UICONTROL Sostituisci codice di incorporamento lancio]**

1. Verificate che la scheda Chrome con il sito Luma sia attiva dietro al Debugger (non la scheda con questa esercitazione o la scheda con l'interfaccia Launch).  Incolla nel campo di input il codice da incorporare presente negli Appunti

1. Attivate la funzione "Applica a luma.enablementadobe.com" in modo che tutte le pagine del sito Luma vengano mappate sulla proprietà Launch

1. Fate clic sul pulsante **[!UICONTROL Salva]**

   ![Ambiente di avvio mostrato in Debugger](images/switchEnvironments-debugger-save.png)

1. Ricaricate il sito Luma e selezionate la scheda Riepilogo del debugger. Nella sezione Launch (Lancio) è ora possibile vedere la proprietà Development utilizzata. Verificate che il nome della proprietà corrisponda al vostro e che l'ambiente dica "development".

   ![Ambiente di avvio mostrato in Debugger](images/switchEnvironments-debuggerOnWeRetail.png)

>[!NOTE] Il Debugger salverà questa configurazione e sostituirà i codici di incorporamento Launch ogni volta che si torna al sito Luma. Non influirà sugli altri siti visitati in altre schede aperte. To stop the Debugger from replacing the embed code, click the **[!UICONTROL Remove]** button next to the embed code in the Tools tab of the Debugger.

Continuando l'esercitazione, si utilizzerà questa tecnica per mappare il sito Luma sulla propria proprietà Launch per convalidare l'implementazione Launch. Quando iniziate a utilizzare Launch sul sito Web di produzione, potete usare la stessa tecnica per convalidare le modifiche.

["Aggiungi il servizio identità Adobe Experience Platform" &gt;](id-service.md)