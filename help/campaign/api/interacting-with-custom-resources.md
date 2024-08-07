---
title: Interazione con risorse personalizzate
description: Ulteriori informazioni sulla gestione delle risorse personalizzate con API/
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
exl-id: 19bfeecb-da60-479c-a929-0cfb72ef59e3
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Interazione con risorse personalizzate {#interacting-with-custom-resources}

L&#39;endpoint **/customResources** consente di esporre le risorse personalizzate di Campaign in REST. In base a questa API, è disponibile un’integrazione tra entità personalizzate ed endpoint esterni.

L’endpoint /customResources ha esattamente lo stesso comportamento dell’endpoint /profileAndServices.

Le risorse personalizzate esposte all’interno di questa API sono:

* tutte le entità non esposte in /profileAndServicesExt
* tutte le entità non collegate al profilo e, per tali entità, i figli e i nipoti.
* per impostazione predefinita, tutte le entità non collegate a nulla, nonché i relativi figli e nipoti.

>[!NOTE]
>Le risorse personalizzate disponibili in /profileAndServicesExt non sono esposte nell’API /customResources.


Di seguito è riportato un esempio per recuperare i metadati da una risorsa personalizzata:

```
GET /customResources/resourceType/<customResourceName>
```

Per eseguire una creazione, un aggiornamento o un’eliminazione, vengono utilizzati GET, POST, PATCH e DELETE.

```
POST /customResources/<customResourceName>
```
