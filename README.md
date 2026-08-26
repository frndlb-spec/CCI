# Customer Care Italia — sito one page

Sito vetrina a pagina singola di **Customer Care Italia** (Francesco Del Buono, Lucca).
Tema scuro blu/nero, calendario di prenotazione zcal integrato nella pagina e avatar virtuale conversazionale.

**Live:** https://www.customercareit.it

---

## Cosa contiene

| File | Descrizione |
|---|---|
| `Customer Care Italia.dc.html` | Sorgente del sito: markup, stili e logica (carosello recensioni, menu mobile, overlay del calendario) |
| `Nuovo Sito Customer Care Italia.html` | Build autonoma: un unico file con immagini e codice incorporati, apribile con doppio clic |
| `Customer Care Italia v1 chiaro.dc.html` | Prima versione, palette chiara — conservata come riferimento |
| `assets/` | Immagini ottimizzate (WebP + JPEG) |
| `support.js` | Runtime necessario ai file `.dc.html` |

## Struttura della pagina

1. **Hero** — headline, ritratto scontornato, card "avatar virtuale attivo"
2. **01 Valori** — i quattro benefici del servizio
3. **02 Recensioni** — carosello di citazioni C-Level (rotazione automatica ogni 8s, frecce e indicatori)
4. **03 Risultati** — galleria: CRM, dashboard performance, chat dal vivo, operatore al telefono
5. **04 Parliamone** — foto in call + CTA
6. **05 Prenota** — calendario zcal integrato + contatti + ancore di approfondimento
7. **Footer** — contatti, navigazione, pagine legali

Ogni sezione ha un pulsante **Prenota 30 minuti** che porta all'ancora `#prenota`.

## Integrazioni di terze parti

**Calendario — zcal**
Iframe inline nella sezione Prenota. La prenotazione si completa senza uscire dal sito.

```
https://zcal.co/i/R3x1dN-X?embed=1
```

> Va usato l'URL **canonico dell'invito** (`/i/<id>`), non lo slug pubblico `zcal.co/fdb/30min`: quest'ultimo, dentro un iframe, si comporta da pagina autonoma e invita ad aprire una nuova scheda.

**Avatar virtuale — myagencycoach**
Script nell'`<head>`, widget flottante in basso a destra (`data-ab-id="KL34YRjV"`).

## Pubblicazione

È un sito statico: nessun build step, nessuna dipendenza da installare.

- **GitHub Pages** — carica il repository, attiva Pages sul branch `main`. Rinomina `Nuovo Sito Customer Care Italia.html` in `index.html`.
- **Netlify / Vercel / Cloudflare Pages** — trascina la cartella, nessuna configurazione.
- **Hosting classico** — carica il singolo file via FTP.

Per un dominio personalizzato aggiungi un file `CNAME` con `www.customercareit.it`.

## Performance

Le immagini sono compresse e ridimensionate (**~570 KB in totale**, contro i 9,2 MB degli originali):
hero in WebP con trasparenza, resto in JPEG, `width`/`height` dichiarati per evitare salti di layout, `loading="lazy"` su tutto tranne l'hero.

Pesano invece sul caricamento, e non sono ottimizzabili da qui: iframe zcal, widget avatar, Google Fonts (Archivo, Caveat, IBM Plex Mono).

## Responsive

Quattro soglie: **1130px** (valori 4→2 colonne, calendario a piena larghezza), **900px** (hero in colonna, menu burger), **700px** (colonna singola, padding e tipografia ridotti, CTA a piena larghezza), **420px** (adattamenti minimi per schermi molto stretti).

## Da sistemare prima del go-live

- [ ] **Cookie banner** — zcal e l'avatar caricano script di terze parti: in UE serve il consenso preventivo
- [ ] **Recensioni anonime** — `L.R.`, `D.B.`, `G.E.` indeboliscono la prova sociale: servono nome, azienda e foto almeno per una
- [ ] **Pagine legali** — Terms, Privacy e Accessibility puntano ancora al vecchio sito Wix
- [ ] **Offerta** — la pagina non dice cosa si compra, come e a quali condizioni

## Modifiche

Modifica `Customer Care Italia.dc.html`, non il file compilato: quest'ultimo va rigenerato dal sorgente.
Gli stili sono inline sugli elementi; nel blocco `<style>` in testa stanno solo reset, `@keyframes` e media query.

---

© 2026 Customer Care Italia — 1 idea di FDB
