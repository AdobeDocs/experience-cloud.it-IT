---
title: Creare un gruppo di funzioni
description: Scopri come creare un gruppo di funzioni in Adobe Experience Rollout per gestire più flag di funzioni tra le applicazioni del team come un’unica unità.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---


# Creare un gruppo di funzioni {#create-feature-group}

## Prerequisiti {#prerequisites}

Prima di creare un gruppo di feature, effettuate le seguenti operazioni:

* Hai accesso alla console Rollout esperienza. Vedi [Accedi alla console](../console/log-in-to-the-console.md)
* Appartieni a un team. Vedi [Gestione team](../teams/manage-teams.md)
* L&#39;applicazione è stata integrata. Vedere [Eseguire l&#39;installazione dell&#39;applicazione](../applications/onboard-your-application.md)
* Hai il ruolo **Sviluppatore** o **Proprietario versione prodotto**. Vedi [Ruoli utente](../teams/user-roles.md)
* Sono stati creati i flag di funzionalità che si desidera aggiungere al gruppo. Vedere [Creare il primo flag di funzionalità](create-your-first-feature-flag.md)

Per un&#39;introduzione ai gruppi di funzionalità, vedere [Gruppi di funzionalità per controllare più funzionalità](../../concepts/feature-groups-to-control-multiple-features.md).

## Passaggio 1: creare il gruppo di funzioni {#create}

Apri la console e inizia un nuovo gruppo di funzioni:

1. Accedi alla console Rollout esperienza e passa a **Test delle funzionalità > Gruppi di funzionalità**.
2. Selezionare **Nuovo gruppo di caratteristiche**.

## Passaggio 2: dettagli di base {#basic-details}

Configurate le impostazioni generali per il gruppo di funzioni:

1. Specifica un titolo, una chiave, una descrizione e, facoltativamente, un tag.
2. Imposta un rollout **percentuale** per il gruppo di funzioni.
3. Se desideri eseguire un test A/B, seleziona più di una variante. Altrimenti, lascialo in una variante. Per ulteriori dettagli, vedere [Test A/B con flag di funzionalità](a-b-testing.md).

## Passaggio 3: pubblico {#audience}

Definisci chi riceverà le funzionalità di questo gruppo:

1. Nella scheda **Pubblico**, aggiungi i criteri di pubblico per definire quali utenti ricevono la funzione.
2. In **Applicazioni**, aggiungi una o più applicazioni dal tuo team. I gruppi di funzioni possono estendersi su più applicazioni a condizione che appartengano tutti allo stesso team.

>[!NOTE]
>
>Il ruolo **Sviluppatore** è in modalità sandbox. Aggiungi il tuo ID utente in **Pubblico > Profilo > ID utente** per testarlo privatamente. Per eseguire il targeting degli utenti esterni, è necessario il ruolo **Proprietario versione prodotto**.

## Passaggio 4: Caratteristiche {#features}

Assegna i flag di funzione che saranno controllati da questo gruppo:

1. Nella scheda **Funzionalità** viene visualizzata una casella per ogni applicazione selezionata.
2. Aggiungere flag di funzionalità per ogni applicazione.
3. Se hai selezionato più varianti (per il test A/B), vengono visualizzate le schede per ogni variante. Aggiungi i flag di funzione appropriati a ciascuno di essi.

>[!IMPORTANT]
>
>Un flag di funzione può essere gestito solo tramite un metodo, direttamente come flag di funzione, attraverso un gruppo di funzioni o attraverso una release. Quando aggiungi un flag di funzione a un gruppo di funzioni, tutti i tipi di pubblico e le percentuali di rollout impostati su tale flag vengono rimossi. I flag di funzioni già assegnati a un’altra versione o a un altro gruppo di funzioni non verranno visualizzati nell’elenco.

## Passaggio 5: pianificazione (facoltativo) {#schedule}

È possibile pianificare l&#39;attivazione del gruppo di funzioni in una data e in un&#39;ora future. Per informazioni dettagliate, consulta [Pianificazione](schedule.md).

## Vedi anche {#see-also}

* [Impostare un gruppo di funzioni per il rollout graduale](set-feature-group-gradual-rollout.md)
* [Test A/B con flag di funzione](a-b-testing.md)
* [Gruppi di feature per controllare più feature](../../concepts/feature-groups-to-control-multiple-features.md)
