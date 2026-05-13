---
title: Branding
description: Scopri tutti gli strumenti disponibili per gestire le tue identità di branding
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti di Campaign Standard migrati"
exl-id: f6438303-5ae8-47c6-8c34-8e586f4b6fe7
TQID: https://experienceleague.adobe.com/El7fE2aveS9C67b8B8fkMpiwMaMx-9aWpW4-3Ev7mG4
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
feature_v2:
  - id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 363
ht-degree: 23%

---

# Introduzione al branding {#branding-gs}

>[!IMPORTANT]
>
>I brand non possono essere creati o modificati dagli utenti finali: queste operazioni devono essere eseguite dall’amministratore tecnico di Adobe Campaign. Per qualsiasi richiesta, contatta l’Assistenza cliente di Adobe.

Ogni azienda dispone di linee guida per il brand che definiscono sia gli elementi visivi che i dettagli tecnici. Adobe Campaign ti consente di gestire queste linee guida a livello centrale, in modo da poter presentare ai clienti un’immagine del brand coerente in tutte le attività, dai loghi nelle e-mail agli URL e ai domini utilizzati nelle campagne.

Gli amministratori tecnici possono creare e gestire più marchi all’interno di Adobe Campaign. Questo ti consente di definire tutti gli elementi che compongono la tua brand identity, compresi i loghi e anche le impostazioni di tracciamento delle e-mail. Una volta creati, questi marchi possono essere facilmente collegati alle consegne.

In Campaign puoi aggiungere nuove entità della tua organizzazione o creare un nuovo tipo di e-mail da inviare in un sottodominio diverso. Per farlo, segui la procedura indicata di seguito:

1. **Configura un nuovo sottodominio**. Per utilizzare un nuovo sottodominio da parte di Adobe, devi innanzitutto configurarlo. Puoi eseguire questa operazione tramite [Pannello di controllo Campaign della campagna](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/subdomains-branding.html?lang=it) o rivolgerti al tuo contatto tecnico Adobe. Ulteriori informazioni sulla configurazione del sottodominio [in questa pagina](https://experienceleague.adobe.com/it/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/ac-domain-name-setup).

   >[!NOTE]
   >
   >Il Pannello di controllo è accessibile a tutti gli utenti amministratori. I passaggi per concedere a un utente l’accesso come amministratore sono descritti in[questa pagina](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=it#discover-control-panel).

1. **Crea un modello di consegna** - Una volta che il nuovo brand è disponibile, è consigliabile creare almeno un nuovo modello di consegna vuoto che faccia riferimento a questo nuovo brand. [Ulteriori informazioni](branding-assign.md).

1. **Verifica le linee guida per il recapito messaggi** - Prima di iniziare a utilizzare il nuovo dominio, discuti la strategia con il team di recapito messaggi di Adobe. Aiuteranno a definire le best practice, ad esempio se è necessario creare una nuova affinità per suddividere gli IP tra domini e/o se è necessario definire un piano di aumento graduale.
