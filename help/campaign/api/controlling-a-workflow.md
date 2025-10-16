---
title: Controllo di un flusso di lavoro
description: Scopri come controllare un flusso di lavoro con le API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti di Campaign Standard migrati"
exl-id: 79eacc31-d5a2-4e13-aa0b-744d7ab7004f
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 10%

---

# Controllo di un flusso di lavoro {#controlling-a-workflow}

Puoi controllare un flusso di lavoro direttamente dall’API REST, tramite una richiesta POST contenente l’ID del flusso di lavoro e il comando di esecuzione richiesto:

`POST https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID>/commands`

>[!CAUTION]
>
>Se l’ID del flusso di lavoro viene modificato in Adobe Campaign, la richiesta API non funzionerà più.

Per controllare un flusso di lavoro sono disponibili quattro comandi di esecuzione:

* Inizio
* Pausa
* Riprendi
* Interruzione

Per ulteriori informazioni sui comandi di esecuzione, consulta la [documentazione di Campaign](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/executing-a-workflow/about-workflow-execution.html).

<br/>

***Richieste di esempio***

* Avvia un flusso di lavoro.

  ```
  -X POST https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID>/commands \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>' \
  -i
  -d '{"method":"start"}'
  ```

  <!-- + réponse -->

* Interrompere un flusso di lavoro.

  ```
  -X POST https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID>/commands \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>' \
  -i
  -d '{"method":"stop"}'
  ```

  <!-- + réponse -->
