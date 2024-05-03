---
title: Branding
description: Scopri come configurare il brand
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti Campaign Standard migrati"
source-git-commit: 56f2d2ff4b2ba4184629615a14724e6640df6961
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 57%

---

# Configurare i brand {#branding-configure}

>[!IMPORTANT]
>
>I brand non possono essere creati o modificati dagli utenti finali: queste operazioni devono essere eseguite dall’amministratore tecnico di Adobe Campaign. Per qualsiasi richiesta, contatta l’Assistenza cliente di Adobe.

In Adobe Campaign V8, i Marchi si trovano nella sezione **[!UICONTROL Amministrazione > Piattaforma > Marchio]** menu.

Un **[!UICONTROL Brand]** è definito dalle seguenti caratteristiche:

* Una **[!UICONTROL Identity]**, che definisce e personalizza il brand. Questa sezione contiene i seguenti campi:

   * **[!UICONTROL Label]**, visibile nell’interfaccia
   * **[!UICONTROL ID]**
   * **[!UICONTROL Brand name]**
   * **[!UICONTROL Website URL]** e **[!UICONTROL Website label]** del brand
   * **[!UICONTROL Logo del brand]**

  ![](assets/branding_1.png)

* **[!UICONTROL Parametri di intestazione delle e-mail inviate]** che personalizza i contenuti visualizzati dai destinatari delle campagne. Questa sezione contiene i seguenti campi:

   * **[!UICONTROL Sender (email address)]**, che contiene l’indirizzo e-mail del brand.
   * **[!UICONTROL Sender (name)]**, che contiene il nome del brand.
   * **[!UICONTROL Reply to (email address)]**, che contiene l’indirizzo e-mail a cui il cliente può rispondere.
   * **[!UICONTROL Reply to (name)]**, che contiene il nome del brand.
   * **[!UICONTROL Error (email address)]**, che contiene l’indirizzo e-mail da utilizzare in caso di errore.

  >[!IMPORTANT]
  >
  >Dopo aver aggiornato i parametri di intestazione delle e-mail, se il nome e l’indirizzo e-mail del mittente non sono cambiati nell’e-mail creata dal modello, controlla le impostazioni avanzate del modello.

  ![](assets/branding_2.png)

* **[!UICONTROL Configurazioni del brand]** definisce i server utilizzati per il tracciamento e per l’accesso alle pagine di destinazione. Questa sezione contiene i seguenti campi:

   * **[!UICONTROL Sottodominio del brand]** fa riferimento all’URL del sottodominio designato specifico per questo brand, richiesto per la delega da Adobe.

  Si noti che la configurazione per i server di monitoraggio, mirroring e applicazioni viene memorizzata in account esterni separati associati al routing. Queste impostazioni vengono applicate durante il provisioning e non devono essere modificate. Per visualizzare gli URL, accedi a **[!UICONTROL Prefissi di branding]** dal tuo account esterno.

  ![](assets/branding_3.png)

<!--![](assets/branding_05.png)-->

<!--
* **[!UICONTROL Tracking URL configs]**, which defines the configuration of the URLs tracking for your brand.

  The additional parameters that allow the links to be tracked on external systems such as Web Analytics tools like Adobe Analytics or Google Analytics are defined here.
-->
