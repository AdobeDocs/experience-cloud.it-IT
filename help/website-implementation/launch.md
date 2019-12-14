---
title: Creare una proprietà Launch
description: Scopri come accedere all'interfaccia di Launch e creare una proprietà Launch. Questa lezione fa parte dell’esercitazione Implementazione di Experience Cloud nei siti Web con Launch.
seo-description: null
seo-title: Creare una proprietà Launch
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 7166d2933cc99bcbbd4713fba8f87fb0826b711e

---


# Creare una proprietà Launch

In questa lezione verrà creata la prima proprietà Launch.

Una proprietà è fondamentalmente un contenitore che riempi con estensioni, regole, elementi dati e librerie durante la distribuzione di tag sul sito.

## Prerequisiti 

Per completare le lezioni successive, è necessario disporre dell'autorizzazione per sviluppare, approvare, pubblicare, gestire le estensioni e gestire gli ambienti in Launch. Se non riesci a completare nessuno di questi passaggi perché le opzioni dell'interfaccia utente non sono disponibili, contatta il tuo amministratore Experience Cloud per richiedere l'accesso. For more information on Launch permissions, see [the documentation](https://docs.adobe.com/content/help/en/launch/using/reference/admin/user-permissions.html).

## Obiettivi di apprendimento

Alla fine di questa lezione, potrai:

* Accedere all'interfaccia utente di Launch
* Creare una nuova proprietà Launch
* Configurare una proprietà Launch

## Vai a Launch

**Per accedere a Launch**

1. Accedi ad [Adobe Experience Cloud](https://experiencecloud.adobe.com)

1. Fate clic sull'icona ![dello switch della](images/launch-solutionSwitcher.png) soluzione per aprire lo switcher della soluzione

1. Selezionate **[!UICONTROL Avvia]** dal menu ![Apri lo switcher della soluzione utilizzando l'icona e fai clic su Attivazione](images/launch-solutionSwitcherActivation.png)

1. In **[!UICONTROL Adobe Experience Cloud Launch]**, fai clic sul pulsante **[!UICONTROL Vai al lancio]**

   ![Fate clic sul pulsante Avvia](images/launch-goToLaunch.png)

You should now see the `Properties` screen (if no properties have ever been created in the account, this screen might be empty):

![Schermata Proprietà](images/launch-propertiesScreen.png)

Se utilizzate frequentemente Launch, potete anche inserire nei segnalibri il seguente URL ed effettuare l'accesso direttamente [https://launch.adobe.com](https://launch.adobe.com)

## Creare una proprietà

Una proprietà è fondamentalmente un contenitore che riempi con estensioni, regole, elementi dati e librerie durante la distribuzione di tag sul sito. Una proprietà può essere un raggruppamento di uno o più domini e sottodomini. Puoi gestire e tenere traccia di queste risorse in modo simile. Ad esempio, supponi di disporre di più siti Web basati su un modello e di voler tenere traccia delle stesse risorse su tutti. Puoi applicare una proprietà a più domini. Per ulteriori informazioni sulla creazione di proprietà, vedere ["Aziende e proprietà"](https://docs.adobe.com/content/help/en/launch/using/reference/admin/companies-and-properties.html) nella documentazione del prodotto.

**Per creare una proprietà**

1. Fate clic sul pulsante **[!UICONTROL Nuova proprietà]** :

   ![Fare clic su Nuova proprietà](images/launch-addNewProperty.png)

1. Denominate la proprietà (ad esempio `Launch Tutorial` o `Daniel's Launch Tutorial`)
1. Come dominio, immettete `enablementadobe.com` perché si tratta del dominio in cui è ospitato il sito dimostrativo Luma. Anche se il campo "Dominio" è obbligatorio, la proprietà Launch funziona su qualsiasi dominio in cui è implementato. Lo scopo principale di questo campo è precompilare le opzioni di menu nel generatore di regole.
1. Fate clic sul pulsante **[!UICONTROL Salva]**

   ![Creare una nuova proprietà](images/launch-newProperty.png)

La nuova proprietà deve essere visualizzata nella pagina Proprietà. Note that if you check the box next to the property name, options to **[!UICONTROL Configure]** or **[!UICONTROL Delete]** the property appear above the property list. Fate clic sul nome della proprietà (ad es. `Launch Tutorial`) per aprire la `Overview` schermata.
![Fate clic sul nome della proprietà per aprirla](images/launch-openProperty.png)

["Aggiungi il codice di incorporamento del lancio" &gt;](launch-add-embed.md)
