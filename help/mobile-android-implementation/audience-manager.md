---
title: Implementazione di Adobe Audience Manager con Launch
description: Scopri come implementare Adobe Audience Manager sul tuo sito Web utilizzando l’inoltro e il lancio lato server. Questa lezione fa parte dell'esercitazione Implementazione di Experience Cloud nelle applicazioni Android per dispositivi mobili.
seo-description: null
seo-title: Implementazione di Adobe Audience Manager con Launch
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: e9dee6d0aa3b775d0ce617e2b2c57b56de491b8d

---


# Aggiungi Adobe Audience Manager

Questa lezione illustra i passaggi necessari per implementare Adobe Audience Manager nell’SDK di Experience Platform Mobile tramite l’inoltro lato server.

[Adobe Audience Manager](https://docs.adobe.com/content/help/en/audience-manager/user-guide/aam-home.html) (AAM) offre servizi leader di settore per la gestione online dei dati di audience, fornendo agli inserzionisti e agli editori digitali gli strumenti necessari per controllare e sfruttare le risorse di dati per favorire il successo delle vendite.

## Obiettivi di apprendimento

Alla fine di questa lezione, potrai:

1. Descrivete i due modi principali per implementare Audience Manager in un'app mobile
1. Aggiunta di Audience Manager tramite l'inoltro lato server del beacon Analytics
1. Convalida dell’implementazione di Audience Manager

## Prerequisiti 

Per completare questa lezione, è necessario:

1. Per completare le lezioni nella sezione Configurazione del lancio, vale a dire [Crea una proprietà](launch-create-a-property.md)di avvio, [Aggiungi estensioni](launch-add-extensions.md), [Crea una libreria](launch-create-a-library.md)e [Installa l’SDK](launch-install-the-mobile-sdk.md)Mobile.

1. L'amministratore può accedere ad Adobe Analytics per abilitare l'inoltro lato server per la suite di rapporti utilizzata per questa esercitazione. In alternativa, puoi chiedere a un amministratore esistente nella tua compagnia di farlo, seguendo le istruzioni di seguito.

## Opzioni di implementazione

Esistono due modi per implementare Audience Manager in un'app:

* SLL (Server-Side Forwarding): per i clienti con Adobe Analytics, questo è il modo più semplice e consigliato per implementare. Adobe Analytics inoltra i dati ad AAM sul back-end di Adobe, in modo da non dover effettuare richieste dall'app direttamente ad Audience Manager. Questo consente inoltre di ottenere caratteristiche di integrazione chiave e si conforma alle nostre best practice per l’implementazione e la distribuzione del codice di Audience Manager.

* DIL lato client: questo approccio è rivolto ai clienti che non dispongono di Adobe Analytics. I metodi di Audience Manager nell'app inviano i dati direttamente ad Audience Manager. In questo caso, quando configuri la proprietà Lancio mobile, puoi utilizzare l’estensione Audience Manager in Launch.

Quando precedentemente impostavi l’estensione Analytics nella sezione [Aggiungi estensioni](launch-add-extensions.md) di questa esercitazione, selezionavi la casella per avviare l’inoltro lato server dei dati da Analytics ad Audience Manager. Questo inserirà dinamicamente il codice necessario per gestire la risposta dei segmenti Audience Manager nuovamente nell'app. In questa esercitazione non verrà aggiunta l'estensione Audience Manager, perché anche in questo caso si tratta solo del caso d'uso in cui NON disponete di Adobe Analytics.

## Abilita Server-Side Forwarding

L'attuazione dell'SSF è articolata in tre fasi:

1. Aggiunta dell’SDK Experience Cloud Mobile e dell’estensione Analytics all’app, ***già** eseguito nelle lezioni di configurazione del lancio
1. Abilitazione dell'inoltro di Audience Manager nella configurazione dell'estensione di Analytics, ***come già fatto*** durante la lezione [](launch-add-extensions.md) Aggiungi estensioni, semplicemente selezionando una casella.
1. Attivando uno "switch" nell'Admin Console di Analytics per inoltrare i dati da Analytics ad Audience Manager *per suite* di rapporti, che verrà rivisto nel resto della lezione.

### Abilita Server-Side Forwarding in Analytics Admin Console

Per iniziare a inoltrare i dati da Adobe Analytics ad Adobe Audience Manager è necessaria una configurazione nell’Admin Console di Adobe Analytics. È consigliabile che il sistema richieda fino a quattro ore per iniziare a inoltrare i dati, in modo da tenere presente che durante la risoluzione dei problemi di inoltro.

#### Per abilitare SSF nell'Admin Console di Analytics

1. Accedi ad Analytics tramite l’interfaccia utente di Experience Cloud. Se non disponi dell'accesso dell'amministratore ad Analytics, dovrai rivolgerti al tuo amministratore Experience Cloud o Analytics per assegnarti l'accesso o completare questi passaggi.

   ![Accesso all’interfaccia utente di Adobe Analytics](images/mobile-aam-logIntoAnalytics.png)

1. Dalla navigazione superiore in Analytics, scegliete **[!UICONTROL Amministratore &gt; Suite]** di rapporti e, dall’elenco, selezionate (o selezionate più volte) le suite di rapporti da inoltrare ad Audience Manager.

   ![Fai clic su Admin Console](images/mobile-aam-analyticsAdminConsoleReportSuites.png)

1. Dalla schermata Suite di rapporti e con le suite di rapporti selezionate, scegliete **[!UICONTROL Modifica impostazioni &gt; Generale &gt; Inoltro]** lato server.

   ![Selezionare il menu SSF](images/mobile-aam-selectSSFmenu.png)

   >[!WARNING] Come indicato sopra, per visualizzare questa voce di menu dovrai disporre delle facoltà di amministratore.

1. Una volta visualizzata la pagina Inoltro lato server, leggete le informazioni e selezionate la casella **[!UICONTROL Abilita inoltro]** lato server per le suite di rapporti.

1. Fai clic su **[!UICONTROL Salva]**

   ![Configurazione SSF completa](images/mobile-aam-enableSSFcomplete.png)

>[!NOTE] Poiché SSF deve essere abilitato per ogni suite di rapporti, non dimenticare di ripetere questo passaggio per le suite di rapporti reali quando distribuisci SSF nella suite di rapporti dell'app effettiva.
>
>Inoltre, se l'opzione SSF è disattivata, per abilitare l'opzione dovrete "mappare le suite di rapporti sull'organizzazione Experience Cloud". Questo è spiegato [nella documentazione](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/report-suite-mapping.html).

Questo switch avvia l’effettivo inoltro dei dati ad AAM, purché Adobe Experience Platform Identity Service sia stato implementato. Il resto dell'implementazione SSF avviene nel codice, che è stato gestito in Launch quando si seleziona la casella nell'estensione Analytics per l'inoltro ad AAM.

Il codice di inoltro lato server è ora implementato per la tua app!

[Avanti "Pubblica la tua proprietà" &gt;](publish.md)