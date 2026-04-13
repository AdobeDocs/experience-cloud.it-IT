---
title: Modalità Rollout esperienza
description: Scopri le due modalità di targeting delle funzioni nei Rollout esperienza di Adobe, targeting a livello di utente e targeting a livello di organizzazione, e quando utilizzarle.
hide: true
exl-id: 0fdfa429-d9bd-4990-8f96-cd9deb273aa0
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 3%

---

# Modalità Rollout esperienza {#modes}

I Rollout esperienza forniscono due diverse modalità di targeting delle funzioni. Ciascuno ha uno scopo diverso di controllo della versione ed è progettato per un tipo specifico di applicazione o caso d’uso.

>[!TIP]
>
>Scegli la modalità in base a ciò che controlli: singole sessioni utente oppure organizzazione e ambito dell’ambiente.

## Targeting a livello di utente {#user-level}

### Panoramica {#user-level-overview}

Il targeting a livello di utente consente il rollout delle funzioni a livello di singolo utente. Supporta il targeting preciso di utenti specifici, tester interni, utenti canary e rollout graduali basati su percentuali.

Questa modalità è particolarmente adatta per le applicazioni che devono variare l’esperienza in base a chi ha effettuato l’accesso.

### Quando utilizzare {#user-level-when}

Utilizza il targeting a livello di utente quando desideri:

* Abilitare una funzione per utenti specifici
* Eseguire esperimenti A/B
* Esegui il test dei canarini con un piccolo gruppo prima di un rollout più ampio
* Distribuire gradualmente una funzione in base alla percentuale di utenti
* Ottimizza l’esperienza in base agli attributi dei singoli utenti (come il dominio e-mail o i dati del profilo)

### Limitazioni {#user-level-limitations}

Il targeting a livello di utente non è progettato per i seguenti scenari:

* Non controlla le funzioni a livello di organizzazione, ambiente o area geografica
* Non destinato all’abilitazione di funzioni o all’acquisizione di diritti a livello di tenant

## Organizzazione e targeting a livello di ambiente {#org-level}

### Panoramica {#org-level-overview}

Il targeting a livello di organizzazione consente il rollout delle funzioni nell’organizzazione, nell’ambiente e nell’ambito dell’area geografica. Controlla la disponibilità delle funzioni per intere organizzazioni o ambienti di distribuzione specifici, anziché per singoli utenti.

Questa modalità è progettata per il controllo delle funzioni a livello aziendale e per i rollout specifici dell’ambiente.

### Quando utilizzare {#org-level-when}

Utilizza il targeting a livello di organizzazione quando desideri:

* Abilitare una funzione per un&#39;intera organizzazione
* Controllare la disponibilità delle funzioni in base all’ambiente (ad esempio, stadio rispetto alla produzione)
* Eseguire un rollout regionale
* Funzioni gate basate sul livello di adesione o abbonamento

### Limitazioni {#org-level-limitations}

Il targeting a livello di organizzazione e di ambiente non è progettato per i seguenti scenari:

* Non supporta il targeting basato su profili utente avanzati
* Non supporta il rollout basato su percentuali a livello di singolo utente
* Non destinato alla sperimentazione o ai test A/B

## Confronto {#comparison}

| Dimensione | Targeting a livello di utente | Organizzazione e targeting a livello di ambiente |
|---|---|---|
| Ambito di controllo | Utente singolo | Organizzazione, ambiente, area geografica |
| Base di targeting | Profilo utente e attributi | Contesto dell’organizzazione e dell’ambiente |
| Percentuale rollout | Sì | No |
| Test A/B | Sì | No |
| Gating Enterprise | No | Sì |

## Scelta della modalità corretta {#choosing}

* Se la domanda è *&quot;Quali utenti dovrebbero visualizzare questa funzionalità?&quot;* → Usa **targeting a livello di utente**
* Se la domanda è *&quot;Quali organizzazioni o ambienti dovrebbero avere questa funzione?&quot;* → Utilizzare **org e il targeting a livello di ambiente**

<!-- -->
