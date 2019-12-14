---
title: Implementazione di Adobe Experience Cloud nei siti Web con Adobe Experience Platform Launch
description: L’implementazione di Experience Cloud in siti Web con Launch è il punto di partenza ideale per gli sviluppatori front-end o per gli esperti di marketing tecnico che desiderano imparare a implementare le soluzioni Adobe Experience Cloud sul loro sito Web.
seo-description: null
seo-title: Implementazione di Adobe Experience Cloud nei siti Web con Adobe Experience Platform Launch
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 7166d2933cc99bcbbd4713fba8f87fb0826b711e

---


# Panoramica

_L’implementazione di Experience Cloud in siti Web con Launch_ è il punto di partenza ideale per gli sviluppatori front-end o per gli esperti di marketing tecnico che desiderano imparare a implementare le soluzioni Adobe Experience Cloud sul loro sito Web.

Ogni lezione contiene esercitazioni e informazioni di base utili per implementare Experience Cloud e comprenderne il valore.  Vengono fornite delle didascalie per evidenziare le informazioni che potrebbero essere utili per i clienti che si spostano dal vecchio gestore di tag, Gestione tag dinamica. Sono disponibili siti di dimostrazione per completare l'esercitazione e apprendere le tecniche di base in un ambiente sicuro. Dopo aver completato questa esercitazione, dovresti essere pronto a iniziare a implementare tutte le tue soluzioni di marketing tramite Launch sul tuo sito web.

Dopo aver completato questo sarà in grado di:

* Creare una proprietà Launch

* Installare una proprietà Launch su un sito Web

* Aggiungi le seguenti soluzioni Adobe Experience Cloud:
   * **[Servizio Adobe Experience Platform Identity](id-service.md)**
   * **[Adobe Target](target.md)**
   * **[Adobe Analytics](analytics.md)**
   * **[Adobe Audience Manager](audience-manager.md)**

* Creare regole ed elementi di dati per inviare dati alle soluzioni Adobe

* Convalida dell'implementazione tramite Adobe Experience Cloud Debugger

* Pubblicare le modifiche in Launch attraverso ambienti di sviluppo, staging e produzione

>[!NOTE] Sono disponibili esercitazioni simili per più soluzioni anche per le seguenti piattaforme:
>
> * [Implementazione di Experience Cloud nelle applicazioni iOS Swift™ per dispositivi mobili](/help/mobile-ios-swift-implementation/index.md)
* [Implementazione di Experience Cloud nelle applicazioni iOS Objective-C per dispositivi mobili](/help/mobile-ios-objective-c-implementation/index.md)
* [Implementazione di Experience Cloud nelle applicazioni Android per dispositivi mobili](/help/mobile-android-implementation/index.md)


## Prerequisiti 

In queste lezioni, si presume che abbiate un Adobe ID e le autorizzazioni necessarie per completare gli esercizi. In caso contrario, potresti dover contattare l’amministratore di Experience Cloud per richiedere l’accesso.

* Per Launch, devi disporre dell’autorizzazione per sviluppare, approvare, pubblicare, gestire estensioni e gestire ambienti. For more information on Launch permissions, see [the documentation](https://docs.adobe.com/content/help/en/launch/using/reference/admin/user-permissions.html).
* Per Adobe Analytics devi conoscere il server di tracciamento e le suite di rapporti che utilizzerai per completare questa esercitazione
* Per Audience Manager, devi conoscere il tuo sottodominio Audience Manager (noto anche come "Nome partner" "ID partner" o "Sottodominio partner")

Inoltre, si presume che tu abbia familiarità con linguaggi di sviluppo front-end come HTML e JavaScript. Non devi essere un esperto di questi linguaggi per completare le lezioni, ma ti saranno più utili se sei in grado di leggere e comprendere il codice senza difficoltà.

## Informazioni su Launch

Adobe Experience Platform Launch è la nuova generazione di funzionalità di gestione di tag per siti Web e SDK per dispositivi mobili di Adobe. Launch offre ai clienti un modo semplice per implementare e gestire tutte le soluzioni di analisi, marketing e pubblicità necessarie per sviluppare esperienze cliente rilevanti. Non è previsto alcun costo aggiuntivo per Launch. È disponibile per qualsiasi cliente Adobe Experience Cloud.

Launch per i siti Web consente di gestire centralmente tutti i JavaScript relativi alle soluzioni di analisi, marketing e pubblicità utilizzate sui siti desktop e mobili. Ad esempio, se distribuisci Adobe Analytics, Launch gestirà la libreria JavaScript AppMeasurement, comporrà le variabili e le richieste di attivazione.

Il tag contenitore di Launch è più leggero del 60% rispetto a DTM e del 40% rispetto a Google Tag Manager. Il contenuto del contenitore è ridotto al minimo, compreso il tuo codice personalizzato. Ogni caratteristica è modulare. Se non hai bisogno di un elemento, non verrà incluso nella libreria. Il risultato è un'implementazione veloce e compatta.

Launch è anche una piattaforma che consente ai fornitori di terze parti di creare estensioni per semplificare l'implementazione delle proprie soluzioni tramite Launch. Un’estensione è un pacchetto di codice (JavaScript, HTML e CSS) che estende l’interfaccia utente e le funzionalità client di Launch. Se si paragona Launch a un sistema operativo, le estensioni sono paragonabili alle applicazioni che consentono di eseguire determinate attività.

## Informazioni sulle lezioni

In queste lezioni, implementerai Adobe Experience Cloud in un falso sito Web per la vendita al dettaglio denominato Luma. Il sito [](https://luma.enablementadobe.com/content/luma/us/en.html) Luma dispone di un livello dati avanzato e di funzionalità che consentono di realizzare un'implementazione realistica. Potrai creare la tua proprietà Launch, nella tua organizzazione Experience Cloud e mapparla sul nostro sito Luma in hosting tramite Experience Cloud Debugger.

[![Sito Web Luma](images/overview-luma.png)](https://luma.enablementadobe.com/content/luma/us/en.html)

## Procurati gli strumenti

1. Poiché utilizzerai alcune estensioni specifiche per il browser, è consigliabile completare l'esercitazione tramite il [browser Web Chrome](https://www.google.com/chrome/)
1. Add the [Adobe Experience Cloud Debugger](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) extension to your Chrome browser
1. Download the [sample html page](https://www.enablementadobe.com/multi/web/basic-sample.html) (right-click on this link and click "Save Link As")
1. Ottenete un editor di testo in cui potete apportare modifiche alla pagina HTML di esempio. (Se non ne avete uno, consigliamo di provare [le parentesi](http://brackets.io/))
1. Segnalibro del sito [Luma](https://luma.enablementadobe.com/content/luma/us/en.html)

>[!NOTE] Potrebbe essere più facile completare questa esercitazione con il sito Luma aperto in Chrome, mentre si legge questa esercitazione e completare i passaggi dell'interfaccia Launch in un altro browser.

Cominciamo!

[Next "Create a Launch Property" (Crea proprietà lancio) &gt;](launch.md)