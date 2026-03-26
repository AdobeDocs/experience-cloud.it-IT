---
title: Utilizzare i dati dell’organizzazione aziendale nelle regole per il pubblico
description: Scopri come utilizzare gli ID organizzazione Enterprise come criteri di pubblico in Rollout esperienza di Adobe per rivolgerti a specifiche organizzazioni di clienti.
exl-id: 74f97ec7-a809-41bf-a41d-bb57f033040f
source-git-commit: 4a3133f014a9bb9d6ed26eb9d9f763db79ce63b3
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 1%

---

# Utilizzare i dati dell’organizzazione aziendale nelle regole per il pubblico {#enterprise-org-data}

I Rollout esperienza supportano il targeting degli utenti in base all’ID della loro organizzazione (org) aziendale. Questo consente di implementare funzioni per specifiche organizzazioni di clienti prima di renderle ampiamente disponibili.

## Aggiunta di un’organizzazione in una regola per il pubblico {#adding-org-rule}

Il targeting per l&#39;organizzazione Enterprise è disponibile nella scheda **Pubblico** in **Regole pubblico > Profilo > Organizzazione**.

Sono supportati due tipi di organizzazione:

### Organizzazioni DME {#dme-orgs}

Le organizzazioni DME sono identificate dal relativo ID organizzazione. Quando crei la regola, immetti solo l&#39;ID organizzazione, non includere un&#39;origine di autenticazione.

### Organizzazioni DMA {#dma-orgs}

Le organizzazioni DMA utilizzano gli ID organizzazione nel formato `XXXXXXXXXXXXXXXXXXXXXXXX@ADOBEORG`. Quando si immette un ID organizzazione DMA:

* Utilizza l&#39;ID organizzazione completo, incluso il suffisso `@ADOBEORG`.
* Inserisci `ADOBEORG` in maiuscolo.

**Esempio:** `57F22B5D5A5F83AE0A495E6E@ADOBEORG`

## Note importanti {#important-notes}

* Il targeting basato su organizzazione viene valutato in base all’organizzazione associata alla sessione autenticata dell’utente. Assicurati che l’utente sia connesso all’organizzazione corretta durante il test.
* Se un’organizzazione che prevedi di trovare non viene visualizzata nei criteri di pubblico o se le funzioni non vengono restituite come previsto per una specifica organizzazione, contatta il supporto dei Rollout esperienza.
* Gli ambienti di stage e produzione possono variare in base alle organizzazioni disponibili. Verifica le regole del pubblico in Stage prima di promuoverle in Produzione.

## Vedi anche {#see-also}

* [Pubblico nei flag di funzione e nei gruppi di funzioni](audience-in-feature-flags-and-feature-groups.md)
* [Regole di pubblico complesse](complex-rules.md)
