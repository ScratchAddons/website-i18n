---
title: Migliori Pratiche
description: Segui queste migliori pratiche quand scrivi o rivedi gli userstyles.
---

Segui queste migliori pratiche quand scrivi o rivedi gli userstyles.


<!-- TODO: ## Supporto addon modalità scura -->
<!-- Esempio di come riferire variabili CSS degli addon editor-dark-mode, dark-www e scratchr2 -->


## Internazionalizzazione

### Tieni conto delle lingue con parole lunghe

RIcorda che in alcune lingue gli elementi dell'interafaccia, ad esempi i pulsanti, potrebbero risultare più stretti o più larghi.

<!-- TODO: ### Supporto per le lingue scritte da destra a sinistra (right-to-left, RTL) -->


## Definire lo stile dell'attuale IU di Scratch


### Evita di fare riferimento ai nomi di classi che iniziano con hash

L'editor di progetti di Scratch contiene di solito nomi di classi che seguono il formato `nome_classe_{hash}`. Ad esempio, `green-flag_green-flag_1kiAo`.

Siccome gli hash possono cambiare in futuro e possono differire tra i diversi fork di Scratch, dovresti evitare di usarli nei tuoi userstyle.

{{< admonition error >}}
```css
/* Questo non va fatto: */
.green-flag_green-flag_1kiAo {
  visibility: hidden;
}
```
{{< /admonition >}}

{{< admonition success >}}
```css
/* Eccom come va fatto: */
[class*="green-flag_green-flag_"] {
  visibility: hidden;
}
```
{{< /admonition >}}

### Evita `!important`, a meno che non sia assolutamente necessario

Invece di usare `!important`, se possibile, usa la [specificità CSS](https://web.dev/learn/css/specificity/) per rendere il suo selettore più specifico.
<!-- Potrebbe essere più dettagliato -->


## Assegnare uno stile agli elementi dell'IU dell'addon


### Fai iniziare con `sa-` i nomi delle classi che definisci per gli addon 

{{< admonition info >}}
Quando definiamo i nomi delle nostre classi, usiamo sempre il formato `kebab-case`.
{{< /admonition >}}

Raccomandiamo che i nomi delle classi definite per gli addon inizino sempre con `sa-` per evitare potenziali conflitti con Scratch o con altre estensioni.

Raccomandiamo anche di includere l'ID dell'addon (o una parte) nel nome della classe.

<!-- TODO: ### spiega l'uso dello z-index nell0'editor di Scratch editor e alcuni concetti correlati -->
