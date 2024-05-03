---
title: Branding
description: Scopri tutti gli strumenti disponibili per gestire le tue identità di branding
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
source-git-commit: 51abadc86b97097d13824651d8c50d4ddd014a51
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 18%

---

# Introduzione al branding {#branding-gs}

>[!IMPORTANT]
>
>I brand non possono essere creati o modificati dagli utenti finali: queste operazioni devono essere eseguite dall’amministratore tecnico di Adobe Campaign. Per qualsiasi richiesta, contatta l’Assistenza cliente di Adobe.

Ogni azienda dispone di linee guida per il brand che definiscono sia gli elementi visivi che i dettagli tecnici. Adobe Campaign ti consente di gestire queste linee guida a livello centrale, in modo da poter presentare ai clienti un’immagine del brand coerente in tutte le attività, dai loghi nelle e-mail agli URL e ai domini utilizzati nelle campagne.

Gli amministratori tecnici possono creare e gestire più marchi all’interno di Adobe Campaign. Questo ti consente di definire tutti gli elementi che compongono la tua brand identity, compresi i loghi e anche le impostazioni di tracciamento delle e-mail. Una volta creati, questi marchi possono essere facilmente collegati alle consegne.

In Campaign puoi aggiungere nuove entità della tua organizzazione o creare un nuovo tipo di e-mail da inviare in un sottodominio diverso. Per farlo, segui la procedura indicata di seguito:

1. **Configurare un nuovo sottodominio** : per utilizzare un nuovo sottodominio come Adobe, il primo passaggio consiste nella sua configurazione. Puoi eseguire questa operazione tramite [Pannello di controllo Campaign della campagna](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/subdomains-branding.html?lang=it) o contatta il tuo contatto tecnico Adobe. Ulteriori informazioni sulla configurazione dei sottodomini [in questa pagina](https://experienceleague.adobe.com/en/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/ac-domain-name-setup).

   >[!NOTE]
   >
   >Il Pannello di controllo è accessibile a tutti gli utenti amministratori. I passaggi per concedere a un utente l’accesso come amministratore sono descritti in[questa pagina](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=it#discover-control-panel).

1. **Creare un modello di consegna** - Una volta che il nuovo brand è disponibile, la best practice prevede di creare almeno un nuovo modello di consegna vuoto che faccia riferimento a questo nuovo brand. [Ulteriori informazioni](branding-assign.md).

1. **Verifica le linee guida per il recapito messaggi** - Prima di iniziare a utilizzare il nuovo dominio, la strategia deve essere discussa con il team Deliverability di Adobe. Aiuteranno a definire le best practice, ad esempio se è necessario creare una nuova affinità per suddividere gli IP tra domini e/o se è necessario definire un piano di aumento graduale.

