---
title: Associare ambienti a un’applicazione
description: Scopri come collegare le istanze dell’applicazione in ambienti diversi in Adobe Experience Rollout per gestire i flag di funzione in modo coerente dallo sviluppo alla produzione.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 1%

---


# Associare ambienti a un’applicazione {#associate-environments}

Il collegamento delle istanze dell’applicazione tra ambienti diversi consente la visibilità tra ambienti diversi e l’importazione dei flussi di lavoro. Per configurarlo è necessario avere il ruolo **Amministratore**. Se devi verificare il tuo ruolo, consulta [Ruoli utente](../teams/user-roles.md).

Per informazioni generali sull&#39;utilità di questa impostazione, vedere [Concetto per più ambienti](cross-environment-concept.md).

## Passaggio 1: aprire le impostazioni dell&#39;applicazione {#step-1}

1. Accedi alla console Rollout esperienza.
2. Passa a **Amministratore > Applicazioni**.
3. Seleziona **Nuova applicazione** per integrare una nuova app oppure seleziona un&#39;applicazione esistente per modificarla.

## Passaggio 2: configurare la sezione Ambienti associati {#step-2}

Nel modulo dell&#39;applicazione, scorri fino alla sezione **Ambienti associati**. Ogni riga di questa sezione definisce uno degli ambienti di distribuzione dell&#39;applicazione. Per ogni ambiente, configura i campi seguenti:

| Campo | Descrizione |
|---|---|
| **Ambiente** | Selezionate un identificatore di ambiente standard dall&#39;elenco: QA1, QA2, STG1, STG2, PROD1 o PROD2. In questo modo viene indicato ai Rollout esperienza se l’ambiente è di produzione o non di produzione e viene determinato il codice colore utilizzato nella console. |
| **Etichetta ambiente** | Nome personalizzato per l&#39;ambiente con il riferimento del team, ad esempio `Dev`, `Staging` o `Production`. Questo è in formato libero e non deve corrispondere all’identificatore standard. |
| **Ambiente rollout esperienza** | L’ambiente della piattaforma (stage o produzione) in cui è ospitata questa istanza dell’applicazione. Prepopolato in base alla console in cui ti trovi attualmente. |
| **ID applicazione** | ID client dell&#39;istanza dell&#39;applicazione in questo ambiente. Viene compilata automaticamente quando si seleziona un&#39;applicazione dal menu a discesa. |

## Passaggio 3: collegare le istanze dell’applicazione tra gli ambienti {#step-3}

Per collegare le istanze tra ambienti diversi, segui questi passaggi per ogni ambiente aggiuntivo:

1. Crea l’istanza dell’applicazione nel suo ambiente di destinazione (ad esempio, crea l’app di controllo qualità nella console Stage).
2. Torna all&#39;applicazione che stai configurando e aggiungi una nuova riga in **Ambienti associati**.
3. Dall&#39;elenco a discesa **ID applicazione**, selezionare l&#39;istanza dell&#39;applicazione appena creata. I tag e le etichette dell’ambiente vengono compilati automaticamente.
4. Seleziona **Aggiorna** per salvare.

Ripeti questo processo per ogni ambiente da collegare, ad esempio, collegando istanze di controllo qualità, stage e produzione della stessa applicazione.

## Note importanti {#important-notes}

* Gli ambienti di controllo qualità e di staging possono essere ospitati nell’ambiente Experience Rollout Stage o nell’ambiente della piattaforma di produzione.
* Gli ambienti di produzione (PROD1, PROD2) possono essere ospitati solo nell’ambiente di produzione dei rollout di esperienza.
* Puoi collegarti a un ambiente inferiore solo da uno superiore. Ad esempio, da Produzione è possibile collegarsi a un’istanza Stage o QA, ma il contrario è di sola lettura.

## Vedi anche {#see-also}

* [Concetto di ambienti diversi](cross-environment-concept.md)
* [Visualizzare i flag di funzione in tutti gli ambienti](view-feature-flags-across-environments.md)
* [Importa flag di funzione](import-feature-flags.md)
