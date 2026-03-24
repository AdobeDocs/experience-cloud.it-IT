---
title: Passaggi dell’integrazione
description: Segui i passaggi di integrazione per il tipo di applicazione per collegare i rollout di esperienza Adobe al servizio web, all’app web o mobile o all’applicazione desktop.
source-git-commit: b82520eebe0070b5f76e0f7daeb2bb79a4bccca0
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 3%

---


# Passaggi dell’integrazione {#integration-steps}

Scegli il percorso di integrazione che corrisponde al tipo di applicazione.

## Servizi web {#web-services}

I servizi back-end si integrano utilizzando un SDK lato server. Scegli il SDK per il tuo stack tecnologico.

**Java**

Segui la [Guida all&#39;integrazione di Java SDK](../sdk-releases/java/java-sdk-integration-guide.md) per l&#39;installazione, la configurazione delle dipendenze e l&#39;inizializzazione.

**Node.js**

Segui la [Guida all&#39;integrazione di Node.js con SDK](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md) per l&#39;installazione e l&#39;inizializzazione.

**Altre lingue**

Se lo stack non è elencato in precedenza, eseguire l&#39;integrazione direttamente con **Feature API V3** (vedere la sezione Feature API di questa guida). Se hai bisogno di assistenza, contatta il supporto per i rollout di esperienza.

## Applicazioni web e mobili {#web-mobile}

Le applicazioni Web e mobili chiamano l&#39;**API delle funzionalità V3** per recuperare i flag di funzionalità per l&#39;utente corrente e applicare la logica condizionale nell&#39;applicazione.

Consulta **API di funzionalità GET V3** nella sezione API di funzionalità di questa guida per il riferimento API completo.

## Applicazioni desktop {#desktop}

Le applicazioni desktop chiamano l&#39;**API di funzionalità V2** per recuperare i flag di funzionalità.

Consulta **API di funzionalità GET V2** nella sezione API di funzionalità di questa guida per il riferimento API completo.

>[!IMPORTANT]
>
>I client desktop devono rispettare il valore TTL nella risposta API e implementare una corretta gestione degli errori in caso di indisponibilità dell’API. Per informazioni sui requisiti, vedere [Applicazioni desktop](desktop-applications.md).

## Vedi anche {#see-also}

* [Guida all’avvio](startup-guide.md)
* [SDK](sdks.md)
* [Servizi web](web-services.md)
* [Applicazioni desktop](desktop-applications.md)
