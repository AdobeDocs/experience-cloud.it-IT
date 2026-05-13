---
title: Branding
description: Scopri come assegnare il tuo marchio
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="DISPONIBILITÀ LIMITATA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Limitato agli utenti di Campaign Standard migrati"
exl-id: 8f6a5255-0245-497b-880f-d91ea82ee19e
TQID: https://experienceleague.adobe.com/aL-I6JknWhDoCob136gJB5Ier2a-T0oMiVFn1ZnRw0s
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
feature_v2: id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 513
ht-degree: 17%

---

# Assegnare il brand {#branding-assign}

## Collegare un brand a un modello {#linking-a-brand-to-a-template}

Per utilizzare i parametri definiti per un brand, questo deve essere collegato a un modello di consegna. A tal fine, devi creare o modificare un modello.

Il modello verrà collegato al brand. Nell’editor e-mail, gli elementi come l’**Email address of default sender**, **Default sender name** o **Logo** utilizzeranno i dati del brand configurato.

>[!BEGINTABS]

>[!TAB Adobe Campaign V8]

Per creare un modello di consegna, puoi duplicare un modello incorporato, convertire una consegna esistente in un modello o creare un modello di consegna da zero. [Ulteriori informazioni](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/create-templates)

Una volta creato il modello, puoi collegarlo a un brand. Per eseguire questa operazione:

1. Cerca **[!UICONTROL Risorse]** `>` **[!UICONTROL Modelli]** `>` **[!UICONTROL Modelli di consegna]** in Adobe Campaign Explorer.

1. Seleziona un modello di consegna o duplicane uno esistente.

   ![](assets/branding_assign_V8_1.png)

1. Accedi a **[!UICONTROL Proprietà]** del modello di consegna selezionato.

   ![](assets/branding_assign_V8_2.png)

1. Dalla scheda **[!UICONTROL Generale]**, seleziona il tuo marchio dal menu a discesa **[!UICONTROL Marchio]**.

   ![](assets/branding_assign_V8_3.png)

1. Una volta configurata, selezionare **OK**.

Ora puoi utilizzare questo modello per inviare le consegne.

>[!TAB Adobe Campaign Web]

Per creare un modello di consegna, puoi duplicare un modello incorporato, convertire una consegna esistente in un modello o creare un modello di consegna da zero. [Ulteriori informazioni](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/delivery-template)

Una volta creato il modello, puoi collegarlo a un brand. Per eseguire questa operazione:

1. Passa alla scheda **[!UICONTROL Modelli]** dal menu a sinistra **[!UICONTROL Consegne]** e seleziona un modello di consegna.

   ![](assets/branding_assign_web_1.png)

1. Fare clic su **[!UICONTROL Impostazioni]**.

   ![](assets/branding_assign_web_2.png)

1. Dalla scheda **[!UICONTROL Consegna]**, accedi al campo **[!UICONTROL Branding]** e seleziona il brand da collegare al modello.

   ![](assets/branding_assign_web_3.png)

1. Conferma la selezione e salva il modello.

Ora puoi utilizzare questo modello per inviare le consegne.

>[!ENDTABS]

## Assegnare un brand alla consegna {#assigning-a-brand-to-an-email}

>[!BEGINTABS]

>[!TAB Adobe Campaign V8]

Per creare una nuova consegna autonoma, segui i passaggi indicati di seguito.

1. Per creare una nuova consegna, passa alla scheda **[!UICONTROL Campagne]**.

1. Fai clic su **[!UICONTROL Consegne]** e fai clic sul pulsante **[!UICONTROL Crea]** sopra l&#39;elenco delle consegne esistenti.

   ![](assets/branding_assign_V8_4.png)

1. Seleziona un modello di consegna.

1. Accedi a **[!UICONTROL Proprietà]** del modello di consegna selezionato.

   ![](assets/branding_assign_V8_5.png)

1. Dalla scheda **[!UICONTROL Generale]**, seleziona il tuo marchio dal menu a discesa **[!UICONTROL Marchio]**.

   ![](assets/branding_assign_V8_6.png)

1. Una volta configurata, selezionare **OK**.

1. Personalizza ulteriormente le consegne. Per ulteriori informazioni sulla creazione di un&#39;e-mail, consulta la sezione [Progettare e inviare e-mail](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/email/create-email).

>[!TAB Adobe Campaign Web]

Per creare una nuova consegna autonoma, segui i passaggi indicati di seguito.

1. Passa al menu **[!UICONTROL Consegne]** nella barra a sinistra e fai clic sul pulsante **[!UICONTROL Crea consegna]**.

   ![](assets/branding_assign_web_4.png)

1. Seleziona E-mail o notifica push come canale e scegli un modello di consegna dall’elenco.

1. Fai clic sul pulsante **[!UICONTROL Crea una consegna]** per confermare.

1. Nella pagina **[!UICONTROL Proprietà]**, fare clic su **[!UICONTROL Impostazioni]**.

   ![](assets/branding_assign_web_5.png)

1. Dalla scheda **[!UICONTROL Consegna]**, accedi al campo **[!UICONTROL Branding]**.

   ![](assets/branding_assign_web_6.png)

1. Seleziona il brand da collegare al modello.

   ![](assets/branding_assign_web_7.png)

1. Personalizza ulteriormente le consegne. Per ulteriori informazioni sulla creazione di un&#39;e-mail, consulta la sezione [Creare la prima e-mail](https://experienceleague.adobe.com/en/docs/campaign-web/v8/msg/email/create-email).

>[!ENDTABS]
