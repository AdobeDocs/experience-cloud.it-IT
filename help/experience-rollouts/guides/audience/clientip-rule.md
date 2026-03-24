---
title: Regola del pubblico con variabile di contesto IP client
description: Scopri come utilizzare la variabile di contesto IP del client nelle regole del pubblico in Rollout esperienza di Adobe, incluso il supporto per indirizzi IP, blocchi CIDR e intervalli di rete.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 1%

---


# Regola del pubblico con variabile di contesto IP client {#clientip-rule}

La variabile di contesto `clientip` consente di eseguire il targeting degli utenti in base al loro indirizzo IP client. Ciò è utile per limitare o abilitare le funzionalità in base alla rete dalla quale gli utenti accedono all&#39;applicazione, ad esempio per limitare l&#39;accesso anticipato agli utenti di una rete aziendale.

## Tipi di input supportati {#input-types}

La variabile di contesto `clientip` supporta tre tipi di valori di input:

| Tipo di input | Descrizione | Operatori supportati |
|---|---|---|
| **Indirizzo IP** | Un singolo indirizzo IPv4 o IPv6 | Is, Is not equal to, In |
| **Blocco CIDR** | Un intervallo di indirizzi IP in notazione CIDR (ad esempio, `192.168.1.0/24`) | Is, In, Is not equal to |
| **Intervallo di rete** | Intervallo di rete predefinito gestito dalla piattaforma | Fa parte di |

## Aggiunta di una regola IP client {#adding-rule}

1. Apri il flag di funzione, il gruppo di funzioni o il gruppo di funzioni cross-team nella console.
2. Passa alla scheda **Pubblico**.
3. In **Contesto**, aggiungi una condizione utilizzando la variabile **clientip**.
4. Seleziona l’operatore e immetti il valore (indirizzo IP, blocco CIDR o seleziona un intervallo di rete predefinito).

## Vedi anche {#see-also}

* [Usa contesto nelle regole del pubblico](using-context-in-audience-rules.md)
* [Pubblico nei flag di funzione e nei gruppi di funzioni](audience-in-feature-flags-and-feature-groups.md)
* [Regole di pubblico complesse](complex-rules.md)
