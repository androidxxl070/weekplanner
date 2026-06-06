# weekplanner
🗓️ Offline/Online weekplanner — dagdelen, categorieën &amp; urgentie. Pure HTML/CSS/JS, geen installatie nodig.

# 🗓️ Weekplanner

Een persoonlijke weekplanner als standalone HTML bestand. Geen installatie, geen server, geen framework — open het bestand in je browser en begin met plannen.

## ✨ Functies

- **Weekgrid** met Ochtend / Middag / Avond per dag
- **9 categorieën** — Werk, Onderhoud, Lichaam, Geest, Inchecken, Educatie, Contacten, Communicatie, Vrije tijd
- **Urgentie per activiteit** — Laag / Normaal / Hoog / Urgent (kleurcodering)
- **Eigen activiteiten** toevoegen naast de vaste opties
- **Weekoverzicht** met statistieken en dag-voor-dag samenvatting
- **Exporteer PDF** — via browser printfunctie
- **Exporteer / Importeer JSON** — backup en herstel, meerdere weken tegelijk
- **Opslag in localStorage** — data blijft staan na herladen
- **Dark mode** — volgt systeemvoorkeur automatisch
- **Zelfhostten** — werkt als statische pagina achter Nginx

## 🚀 Gebruik

### Lokaal
Download `weekplanner.html` en open het in je browser. Geen installatie nodig.

### Zelfhosten (Nginx)
```nginx
server {
    listen 80;
    server_name weekplanner.jouwdomein.nl;

    root /var/www/weekplanner;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

## 💾 Data & backup

Data wordt opgeslagen in `localStorage` van je browser, gekoppeld aan de domeinnaam.

| Actie | Knop |
|-------|------|
| Opslaan | Automatisch bij elke wijziging |
| Backup maken | ⬇ Exporteer JSON |
| Terugzetten | ⬆ Importeer JSON (meerdere bestanden tegelijk) |
| PDF exporteren | 🖨 Exporteer PDF → "Opslaan als PDF" in printvenster |

## 🛠️ Technisch

- Pure HTML / CSS / JavaScript — geen dependencies
- `localStorage` als key-value opslag per week (`week_YYYY-MM-DD`)
- `FileReader` API voor JSON import
- `@media print` voor PDF layout
- `<details>` / `<summary>` voor inklapbare infobox

## 📋 Licentie

MIT — vrij te gebruiken en aan te passen.
