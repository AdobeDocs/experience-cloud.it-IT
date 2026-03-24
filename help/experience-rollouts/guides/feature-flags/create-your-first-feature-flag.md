---
title: Creare il primo flag di funzione
description: Scopri come creare un flag di funzione nei rollout di esperienza di Adobe, impostare un pubblico e testarlo prima di distribuirlo agli utenti.
source-git-commit: ae420329b94b24fcd173734b414aecf1c5fc16ca
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Creare il primo flag di funzione {#create-feature-flag}

## Prerequisiti {#prerequisites}

Prima di creare un flag di feature, effettuate le seguenti operazioni:

* Hai accesso alla console Rollout esperienza. Vedi [Accedi alla console](../console/log-in-to-the-console.md)
* Appartieni a un team. Vedi [Gestione team](../teams/manage-teams.md)
* L&#39;applicazione è stata integrata. Vedere [Eseguire l&#39;installazione dell&#39;applicazione](../applications/onboard-your-application.md)
* Hai il ruolo **Sviluppatore** o **Proprietario versione prodotto**. Vedi [Ruoli utente](../teams/user-roles.md)

## Passaggio 1: creare il flag di funzione {#create}

Per creare un nuovo flag di funzione, effettua le seguenti operazioni nella console:

1. Accedi alla console Rollout esperienza e passa a **Funzionalità e versioni > Flag di funzionalità**.
2. Seleziona l&#39;applicazione dal menu a discesa **Applicazione**.
3. Seleziona **Nuova funzionalità**.
4. Specifica un titolo, una chiave, una descrizione e, facoltativamente, un tag.
5. Facoltativamente, aggiungi un criterio di pubblico (vedi Passaggio 2).
6. Salva le impostazioni dei flag di funzione.

## Passaggio 2: aggiungere un criterio di pubblico {#audience}

I criteri di pubblico controllano quali utenti visualizzano la funzione. Puoi aggiungere criteri in base a:

* Attributi del profilo (come paese, dominio e-mail, ID utente)
* Variabili di contesto
* Segmenti di pubblico predefiniti

Per aggiungere criteri di pubblico, vai alla scheda **Pubblico** durante la creazione o la modifica di un flag di funzione.

>[!NOTE]
>
>Il ruolo **Sviluppatore** è in modalità sandbox. Gli sviluppatori possono esporre una funzionalità solo a se stessi aggiungendo il proprio ID utente in **Pubblico > Profilo > ID utente**. Per esporre una funzionalità a utenti esterni, è necessario il ruolo **Proprietario della versione del prodotto**.

## Passaggio 3: calcolare la dimensione del pubblico {#audience-size}

Dopo aver aggiunto i criteri di pubblico, seleziona **Calcola** nella barra inferiore per ottenere un conteggio stimato degli utenti idonei per la funzione. Questo consente di convalidare il targeting prima della pubblicazione.

## Passaggio 4: pianificazione (facoltativo) {#schedule}

È possibile pianificare l&#39;attivazione di un flag di funzione in una data e in un&#39;ora future. Per informazioni dettagliate, consulta [Pianificazione](schedule.md).

## Domande frequenti: non è possibile aggiungere un flag di funzione come sviluppatore {#faq}

Il ruolo **Sviluppatore** è in modalità sandbox. Gli sviluppatori possono testare le funzionalità privatamente aggiungendo il proprio ID utente al pubblico. Non possono esporre funzionalità a utenti esterni. Utilizza il ruolo **Proprietario versione prodotto** per rilasciare funzionalità a utenti esterni. Contatta l’amministratore del team per aggiornare il ruolo.

## Vedi anche {#see-also}

* [Impostare una funzione per il rollout graduale](set-feature-gradual-rollout.md)
* [Creare un gruppo di funzioni](create-a-feature-group.md)
* [Ruoli utente](../teams/user-roles.md)
