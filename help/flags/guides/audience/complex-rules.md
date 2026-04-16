---
title: Regole di pubblico complesse
description: Scopri come utilizzare nei flag set di regole per il pubblico complessi o di grandi dimensioni, inclusi i limiti per i valori in blocco e come suddividere le regole in più condizioni.
hide: true
exl-id: 37e037b6-45eb-4261-b580-30d94d8e55da
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Regole di pubblico complesse {#complex-rules}

## Limiti del valore bulk {#bulk-value-limits}

Quando si aggiunge un numero elevato di valori a una singola regola di pubblico, ad esempio un lungo elenco di indirizzi e-mail, è possibile che si verifichi un errore che indica che la regola ha superato la dimensione massima consentita.

Ogni regola di pubblico ha un limite di dimensione per attributo. Per gli indirizzi e-mail, il limite dipende dalla lunghezza totale dei caratteri delle voci, anziché da un conteggio fisso. Come linea guida generale, utilizza circa **100-115 indirizzi e-mail per regola**.

Se devi eseguire il targeting di più voci di quanto consenta questo limite, suddivide l’elenco in blocchi più piccoli e applicali come condizioni separate connesse con OR utilizzando una logica nidificata.

## Utilizzo della logica nidificata per le regole complesse {#nested-logic}

La logica nidificata consente di combinare più condizioni di pubblico con un controllo AND/OR preciso. Per abilitarlo:

1. Aggiungi le condizioni di pubblico necessarie.
2. Abilita **Logica annidata** nella sezione Regole pubblico.
3. A ogni condizione viene assegnato un numero. Immetti un’espressione logica che faccia riferimento a questi numeri, ad esempio:
   * `1 and (2 or 3)`
   * `(1 and 2) or 3`
   * `(1 and 2) or (3 and 4)`

Si tratta dello stesso meccanismo utilizzato per le regole percentuali in combinazione con altri criteri. Consulta [Aggiungere regole di percentuale nei criteri di pubblico](adding-percentage-rules.md) per esempi funzionanti.

## Vedi anche {#see-also}

* [Pubblico nei flag di funzione e nei gruppi di funzioni](audience-in-feature-flags-and-feature-groups.md)
* [Aggiungere regole di percentuale nei criteri di pubblico](adding-percentage-rules.md)

<!-- -->
