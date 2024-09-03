---
title: Branding
description: Scopri come configurare il brand
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
exl-id: 7afc802d-e90c-48c8-aa04-3ea543dfdfbc
source-git-commit: 62c2f2e7a6f5dd347749e963a655b717cd5c7310
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 42%

---

# Configurare i brand {#branding-configure}

>[!IMPORTANT]
>
>I brand non possono essere creati o modificati dagli utenti finali: queste operazioni devono essere eseguite dall’amministratore tecnico di Adobe Campaign. Per qualsiasi richiesta, contatta l’Assistenza cliente di Adobe.

In Adobe Campaign V8, i Marchi si trovano nel menu **[!UICONTROL Amministrazione > Piattaforma > Marchio]**.

Un **[!UICONTROL Brand]** è definito dalle seguenti caratteristiche:

* Una **[!UICONTROL Identity]**, che definisce e personalizza il brand. Questa sezione contiene i seguenti campi:

   * **[!UICONTROL Label]**, visibile nell’interfaccia
   * **[!UICONTROL ID]**
   * **[!UICONTROL Brand name]**
   * **[!UICONTROL Website URL]** e **[!UICONTROL Website label]** del brand
   * **[!UICONTROL Logo del brand]**

  ![](assets/branding_1.png)

* **[!UICONTROL Parametri di intestazione delle e-mail inviate]** che personalizzano i contenuti visualizzati dai destinatari delle campagne. Questa sezione contiene i seguenti campi:

   * **[!UICONTROL Sender (email address)]**, che contiene l’indirizzo e-mail del brand.
   * **[!UICONTROL Sender (name)]**, che contiene il nome del brand.
   * **[!UICONTROL Reply to (email address)]**, che contiene l’indirizzo e-mail a cui il cliente può rispondere.
   * **[!UICONTROL Reply to (name)]**, che contiene il nome del brand.
   * **[!UICONTROL Error (email address)]**, che contiene l’indirizzo e-mail da utilizzare in caso di errore.

  >[!IMPORTANT]
  >
  >Dopo aver aggiornato i parametri di intestazione delle e-mail, se il nome e l’indirizzo e-mail del mittente non sono cambiati nell’e-mail creata dal modello, controlla le impostazioni avanzate del modello.

  ![](assets/branding_2.png)

* **[!UICONTROL Brand configs]** definisce i server utilizzati per il tracciamento anche per l&#39;accesso alle pagine di destinazione. Questa sezione contiene i seguenti campi:

   * **[!UICONTROL Il sottodominio del marchio]** fa riferimento all&#39;URL del sottodominio designato specifico per questo marchio, richiesto per la delega da Adobe.

  Si noti che la configurazione per i server di monitoraggio, mirroring e applicazioni viene memorizzata in account esterni separati associati al routing. Queste impostazioni vengono applicate durante il provisioning e non devono essere modificate. Per visualizzare gli URL, accedi alla scheda **[!UICONTROL Prefissi di branding]** dal tuo account esterno.

  ![](assets/branding_3.png)

* Il menu **[!UICONTROL Configurazioni URL di tracciamento]** consente di migliorare il tracciamento degli URL definendo parametri aggiuntivi per l&#39;integrazione con strumenti di analisi web come Adobe Analytics e Google Analytics.

  Utilizza il menu **[!UICONTROL Parametri URL aggiuntivi]** per creare parametri aggiuntivi come coppie chiave-valore insieme alle relative condizioni di applicabilità. Ogni nome di parametro deve essere univoco e non vuoto e ogni valore di parametro non deve essere vuoto. La condizione di applicabilità può essere vuota, ma nessuno di questi valori può includere tag JST.

  Questi parametri verranno applicati agli URL tracciati che corrispondono a qualsiasi nome di dominio specificato nell&#39;**[!UICONTROL Elenco di nomi di dominio]**, che può includere espressioni regolari.
