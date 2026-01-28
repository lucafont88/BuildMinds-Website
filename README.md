# Build Minds - Sito Web

Sito web professionale per Build Minds S.R.L., software house specializzata in sviluppo software personalizzato per PMI.

## 📁 Struttura File

```
build-minds-website/
├── index.html          # Homepage
├── servizi.html        # Pagina servizi dettagliata
├── chi-siamo.html      # Chi siamo e valori aziendali
├── portfolio.html      # Portfolio e case study
├── blog.html           # Blog con articoli SEO
├── contatti.html       # Form contatti e informazioni
├── style.css           # CSS principale (responsive)
├── logo-512.jpg        # Logo su fondo chiaro
├── logo-512-negative.jpg  # Logo su fondo scuro (favicon)
└── README.md           # Questo file
```

## 🚀 Come Utilizzare

### 1. Setup Locale

1. Scarica tutti i file in una cartella
2. Aggiungi le immagini logo:
   - `logo-512.jpg` (logo su fondo chiaro per header)
   - `logo-512-negative.jpg` (logo su fondo scuro per favicon)
3. Apri `index.html` nel browser per testare

### 2. Personalizzazione Necessaria

Prima di pubblicare, sostituisci i placeholder:

**In tutti i file HTML:**
- `+39 352 047 6725` → numero di telefono reale
- `XXXXXXXXXXX` → P.IVA e Codice Fiscale reali
- `buildminds@pec.it` → indirizzo PEC reale
- `MB-XXXXXX` → numero Registro Imprese reale

**In contatti.html:**
- Implementa il backend per il form contatti (vedi sezione Backend)

**In blog.html:**
- Sostituisci URL placeholder delle immagini con immagini reali
- Gli articoli sono già titolati, crea i contenuti

**In portfolio.html:**
- Inserisci nomi clienti reali (quando disponibili Q2-Q3 2026)
- Aggiungi screenshot progetti reali

### 3. Hosting e Pubblicazione

#### Opzione A: Netlify (Consigliato - Gratis)
1. Crea account su [Netlify](https://netlify.com)
2. Trascina la cartella con i file nel pannello Netlify
3. Configura dominio personalizzato `buildminds.it`
4. SSL automatico attivato

#### Opzione B: Vercel (Alternativa - Gratis)
1. Crea account su [Vercel](https://vercel.com)
2. Importa progetto da cartella locale
3. Configura dominio personalizzato

#### Opzione C: SiteGround o altro hosting tradizionale
1. Acquista piano hosting (€50-100/anno)
2. Carica file via FTP nella cartella `public_html/`
3. Configura dominio

### 4. Backend Form Contatti

Il form in `contatti.html` necessita di un backend. Opzioni:

#### A. Netlify Forms (Più Semplice)
```html
<!-- In contatti.html, aggiungi attributi al form: -->
<form name="contact" method="POST" data-netlify="true">
```
Netlify gestisce automaticamente l'invio via email.

#### B. Formspree (Alternativa)
1. Registrati su [Formspree](https://formspree.io)
2. Crea endpoint form
3. Sostituisci `action="#"` con URL Formspree

#### C. PHP personalizzato
```php
<?php
// contact-handler.php
if($_POST) {
    $to = "info@buildminds.it";
    $subject = "Nuovo contatto dal sito";
    $message = $_POST['message'];
    mail($to, $subject, $message);
    header('Location: thank-you.html');
}
?>
```

## 🎨 Personalizzazione Design

### Colori
I colori sono definiti in `style.css` nelle variabili CSS:

```css
:root {
    --primary-color: #2B7A9F;      /* Blu principale */
    --secondary-color: #1E3A5F;    /* Blu scuro */
    --accent-color: #4AC4D4;       /* Teal accent */
    --text-dark: #333333;
    --text-light: #666666;
    --bg-light: #F5F7FA;
    --white: #FFFFFF;
}
```

### Tipografia
Font utilizzati (Google Fonts):
- **Heading:** Poppins (bold)
- **Body:** Inter (regular, medium, semibold)

## 📱 Responsive

Il sito è completamente responsive con breakpoint a 768px:
- Desktop: layout a griglia multi-colonna
- Tablet/Mobile: layout a singola colonna con menu hamburger

## 🔍 SEO

### Meta Tag Implementati
Ogni pagina ha:
- Title tag unico (50-60 caratteri)
- Meta description (150-160 caratteri)
- Keywords pertinenti
- Open Graph tags (da aggiungere per social)

### Da Fare per SEO Completo

1. **Google Search Console**
   - Verifica proprietà sito
   - Invia sitemap.xml

2. **Google Analytics**
   - Crea proprietà GA4
   - Aggiungi tracking code prima di `</head>`

3. **Sitemap.xml**
   Crea file `sitemap.xml`:
   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
     <url>
       <loc>https://buildminds.it/</loc>
       <priority>1.0</priority>
     </url>
     <url>
       <loc>https://buildminds.it/servizi.html</loc>
       <priority>0.9</priority>
     </url>
     <!-- ... altre pagine ... -->
   </urlset>
   ```

4. **robots.txt**
   Crea file `robots.txt`:
   ```
   User-agent: *
   Allow: /
   Sitemap: https://buildminds.it/sitemap.xml
   ```

5. **Schema Markup**
   Aggiungi JSON-LD per Organization:
   ```html
   <script type="application/ld+json">
   {
     "@context": "https://schema.org",
     "@type": "Organization",
     "name": "Build Minds",
     "url": "https://buildminds.it",
     "logo": "https://buildminds.it/logo-512.jpg",
     "contactPoint": {
       "@type": "ContactPoint",
       "telephone": "+39-XXX-XXXXXXX",
       "contactType": "Sales"
     },
     "address": {
       "@type": "PostalAddress",
       "addressLocality": "Vimercate",
       "addressRegion": "Lombardia",
       "addressCountry": "IT"
     }
   }
   </script>
   ```

## 🔒 Privacy e GDPR

### Da Implementare:
1. **Cookie Banner**
   - Usa [Cookiebot](https://www.cookiebot.com/it/) o [iubenda](https://www.iubenda.com/it/)
   - Integra banner con consenso cookie

2. **Privacy Policy**
   - Genera con iubenda o altro generatore
   - Crea pagina `privacy-policy.html`

3. **Cookie Policy**
   - Documenta cookie utilizzati
   - Crea pagina `cookie-policy.html`

## 📧 Email Marketing

Per la newsletter in `blog.html`:
- Integra con Mailchimp, Sendinblue o Brevo
- Sostituisci form con form embed del servizio scelto

## 🎯 Google My Business

1. Crea profilo Google My Business
2. Categoria: "Software house" / "Servizi di sviluppo software"
3. Aggiungi foto logo, sede (se applicabile), progetti
4. Richiedi recensioni clienti

## 📊 Performance

### Ottimizzazioni Implementate:
- CSS minificato e organizzato
- Font preconnect per Google Fonts
- Immagini lazy loading (da implementare con attributo `loading="lazy"`)

### Test Consigliati:
- [Google PageSpeed Insights](https://pagespeed.web.dev/)
- Target: >90 mobile e desktop

## 🛠️ Manutenzione

### Contenuti da Aggiornare Periodicamente:
- **Blog:** 1-2 articoli/mese per SEO
- **Portfolio:** Aggiungi nuovi case study ogni 2-3 mesi
- **Servizi:** Aggiorna prezzi annualmente

## 📞 Supporto Tecnico

Per problemi o domande:
- Email: [inserire email tecnica]
- Documentazione: Questo README

## 📝 Note sul Business Plan

Questo sito rispecchia completamente il business plan Build Minds:
- **Servizi principali:** Sviluppo 60%, Consulenza 15%, Formazione 5%, SaaS 20%
- **Target:** PMI lombarde 10-100 dipendenti
- **Budget:** Sviluppo low-cost €200-400 (Netlify gratis + dominio €15/anno)
- **SEO locale:** Focus su keywords Vimercate, Monza, Brianza, Lombardia

## ✅ Checklist Pre-Lancio

- [ ] Sostituiti tutti i placeholder (tel, P.IVA, email)
- [ ] Aggiunti loghi reali (logo-512.jpg e logo-512-negative.jpg)
- [ ] Form contatti collegato a backend
- [ ] Cookie banner implementato
- [ ] Privacy policy e cookie policy create
- [ ] Google Analytics installato
- [ ] Google Search Console configurato
- [ ] Dominio buildminds.it acquistato e configurato
- [ ] SSL attivo (https://)
- [ ] Test su mobile e desktop completati
- [ ] Google My Business creato
- [ ] Email info@buildminds.it configurata

## 📅 Roadmap Contenuti (Q1-Q2 2026)

**Febbraio 2026:**
- Pubblicazione sito online
- Primi 3 articoli blog
- SEO locale attivo

**Marzo-Aprile 2026:**
- Primo case study reale
- 2 nuovi articoli blog
- Campagna LinkedIn

**Maggio-Giugno 2026:**
- Secondo case study
- 3 nuovi articoli blog
- Testimonianze clienti

---

**Build Minds** - Trasformiamo le idee in soluzioni software
Vimercate (MB), Lombardia - 2026
