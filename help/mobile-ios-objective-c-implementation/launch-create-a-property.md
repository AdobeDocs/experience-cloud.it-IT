---
title: Creare una proprietà Launch per le app mobili
description: Scopri come accedere all’interfaccia di Launch e creare una proprietà Launch mobile. Questa lezione fa parte dell'esercitazione Implementazione di Experience Cloud nelle applicazioni iOS Objective-C per dispositivi mobili.
seo-description: null
seo-title: Creare una proprietà Launch per le app mobili
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 7166d2933cc99bcbbd4713fba8f87fb0826b711e

---


# Creare una proprietà Launch

Adobe Experience Platform Launch è la nuova generazione di funzionalità SDK per dispositivi mobili e gestione tag per siti Web. Launch offre ai clienti un modo semplice per implementare e gestire tutte le soluzioni di analisi, marketing e pubblicità necessarie per sviluppare esperienze cliente rilevanti. Non è previsto alcun costo aggiuntivo per Launch. È disponibile per qualsiasi cliente Adobe Experience Cloud.

In questa lezione verrà creata una proprietà Launch per le app mobili.

## Prerequisiti 

Per completare le lezioni successive, è necessario disporre dell'autorizzazione per sviluppare, approvare, pubblicare, gestire le estensioni e gestire gli ambienti in Launch. Se non riesci a completare nessuno di questi passaggi perché le opzioni dell'interfaccia utente non sono disponibili, contatta il tuo amministratore Experience Cloud per richiedere l'accesso. For more information on Launch permissions, see [the documentation](https://docs.adobe.com/content/help/en/launch/using/reference/admin/user-permissions.html).

## Obiettivi di apprendimento

Alla fine di questa lezione, potrai:

* Accedere all'interfaccia utente di Launch
* Creare una nuova proprietà Launch mobile
* Configurare una proprietà mobile Launch

## Vai a Launch

**Per accedere a Launch**

1. Accedi ad [Adobe Experience Cloud](https://experiencecloud.adobe.com)

1. Fate clic sull'icona ![dello switch della](images/mobile-launch-solutionSwitcher.png) soluzione per aprire lo switcher della soluzione

1. Select **[!UICONTROL Launch]** from the menu

   ![Apri lo switcher della soluzione utilizzando l'icona e fai clic su Activation](images/mobile-launch-solutionSwitcherActivation.png)

1. In **[!UICONTROL Adobe Experience Cloud Launch]**, fai clic sul pulsante **[!UICONTROL Vai al lancio]**

   ![Fate clic sul pulsante Avvia](images/mobile-launch-goToLaunch.png)

You should now see the `Properties` screen (if no properties have ever been created in the account, this screen might be empty):

![Schermata Proprietà](images/mobile-launch-propertiesScreen.png)

Se utilizzate frequentemente Launch, potete anche inserire nei segnalibri il seguente URL ed effettuare l'accesso direttamente [https://launch.adobe.com](https://launch.adobe.com)

## Creare una proprietà

Una proprietà è fondamentalmente un contenitore a cui si possono aggiungere estensioni, regole, elementi dati e librerie durante la distribuzione dei tag nell'app. Un'unica proprietà mobile può essere utilizzata su più piattaforme di app (ad esempio, iOS e Android) a condizione che le app contengano funzionalità simili e richiedano l'implementazione delle stesse soluzioni.  Per ulteriori informazioni sulla creazione di proprietà, consultate ["Configurare una proprietà mobile"](https://aep-sdks.gitbook.io/docs/getting-started/create-a-mobile-property) nella documentazione del prodotto.

**Per creare una proprietà**

1. Fate clic sul pulsante **[!UICONTROL Nuova proprietà]** :

   ![Fare clic su Nuova proprietà](images/mobile-launch-addNewProperty.png)

1. Denominate la proprietà (ad es. `Mobile Tutorial`)
1. Come piattaforma, fai clic su **[!UICONTROL Mobile]**
1. Fate clic sul pulsante **[!UICONTROL Salva]**

   ![Creare una nuova proprietà](images/mobile-launch-newProperty.png)

La nuova proprietà deve essere visualizzata nella pagina Proprietà. Note that if you check the box next to the property name, options to **[!UICONTROL Configure]** or **[!UICONTROL Delete]** the property appear above the property list. Fate clic sul nome della proprietà (ad es. `Mobile Tutorial`) per aprire la `Overview` schermata.
![Fate clic sul nome della proprietà per aprirla](images/mobile-launch-openProperty.png)

[Next "Add Extensions" &gt;](launch-add-extensions.md)
