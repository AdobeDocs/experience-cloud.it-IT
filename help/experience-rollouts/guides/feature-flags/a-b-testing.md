---
title: Test A/B con flag di funzione
description: Scopri come eseguire test A/B utilizzando i gruppi di funzioni nei Rollout esperienza di Adobe configurando più varianti per un set di flag di funzione.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 1%

---


# Test A/B con flag di funzione {#a-b-testing}

I test A/B nei rollout di esperienza vengono eseguiti utilizzando **gruppi di funzionalità**. Configurando più varianti in un gruppo di funzioni, puoi distribuire versioni diverse di una funzione a sottoinsiemi diversi del pubblico e confrontare i risultati.

## Prerequisiti {#prerequisites}

* Accesso alla console. Vedere [Accesso alla console](../console/log-in-to-the-console.md)
* Appartieni a un team e la tua applicazione è integrata
* Hai il ruolo **Sviluppatore** o **Proprietario versione prodotto**. Vedi [Ruoli utente](../teams/user-roles.md)
* Sono stati creati i flag di funzionalità da testare. Vedere [Creare il primo flag di funzionalità](create-your-first-feature-flag.md)

## Passaggio 1: creare un gruppo di funzioni con più varianti {#create}

1. Passa a **Test delle funzionalità > Gruppi di funzionalità** e seleziona **Nuovo gruppo di funzionalità**.
2. In **Dettagli di base**, fornisci titolo, chiave e descrizione.
3. Imposta un rollout di **percentuale** per definire la percentuale di partecipazione del pubblico al test.
4. Imposta **Varianti** su un valore maggiore di uno (ad esempio, due varianti per un test A/B classico).
5. Consulta [Impostare un gruppo di funzioni per il rollout graduale](set-feature-group-gradual-rollout.md) per capire come la percentuale di esposizione viene distribuita tra le varianti.

## Passaggio 2: impostare il pubblico {#audience}

Nella scheda **Pubblico**, aggiungi i criteri di pubblico e seleziona le applicazioni da includere. I gruppi di funzioni possono essere distribuiti su più applicazioni all’interno dello stesso team.

>[!NOTE]
>
>Per eseguire il targeting degli utenti esterni in un test A/B, è necessario avere il ruolo **Proprietario della versione del prodotto**. Il ruolo Sviluppatore è in modalità sandbox ed è limitato ai test privati.

## Passaggio 3: aggiungere funzioni per variante {#features}

Nella scheda **Funzioni**, ogni variante ha la propria scheda. Aggiungi i flag di funzione appropriati a ogni variante per definire le diverse esperienze che desideri confrontare.

>[!IMPORTANT]
>
>Un flag di funzione può essere gestito solo tramite un metodo alla volta: flag di funzione, gruppo di funzioni o versione. L’aggiunta di un flag a un gruppo di funzioni rimuove tutti i tipi di pubblico e le percentuali di rollout impostati direttamente sul flag.

## Passaggio 4: salvare e attivare {#save}

Salvate le impostazioni del gruppo di feature. Quando siete pronti per iniziare il test, impostate il gruppo di feature sullo stato attivo.

## Vedi anche {#see-also}

* [Creare un gruppo di funzioni](create-a-feature-group.md)
* [Impostare un gruppo di funzioni per il rollout graduale](set-feature-group-gradual-rollout.md)
* [Analytics](analytics.md)
