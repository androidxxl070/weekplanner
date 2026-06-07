# 🗓️ Weekplanner

Een persoonlijke weekplanner als standalone HTML bestand. Geen installatie,
geen server, geen framework — open het bestand in je browser en begin met plannen.

## ✨ Functies

- **Weekgrid** met Ochtend / Middag / Avond per dag
- **9 categorieën** — Werk, Onderhoud, Lichaam, Geest, Inchecken, Educatie,
  Contacten, Communicatie, Vrije tijd
- **Urgentie per activiteit** — Laag / Normaal / Hoog / Urgent (kleurcodering)
- **Eigen activiteiten toevoegen** — via tekstveld in het keuzemenu, automatisch
  opgeslagen in de categorie en meegenomen bij export
- **Weekoverzicht** met statistieken en dag-voor-dag samenvatting
- **Categorieën aanpassen** — importeer/exporteer je eigen categorieën als JSON
- **Exporteer PDF** — via browser printfunctie, nette print-layout
- **Exporteer / Importeer week JSON** — meerdere weken tegelijk (Ctrl+select)
- **Opslag in localStorage** — weekdata én categorieën blijven staan na herladen
- **Dark mode** — volgt systeemvoorkeur automatisch
- **Zelfhosten** — werkt als statische pagina achter Nginx

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

Data wordt opgeslagen in `localStorage`, gekoppeld aan de domeinnaam.

| Actie | Knop |
|-------|------|
| Week opslaan | Automatisch bij elke wijziging |
| Week exporteren | ⬇ Week JSON |
| Weken terugzetten | ⬆ Week JSON (meerdere bestanden via Ctrl+select) |
| Categorieën exporteren | ⬇ Categorieën |
| Categorieën importeren | ⬆ Categorieën |
| PDF exporteren | 🖨 Exporteer PDF → kies "Opslaan als PDF" |

### Categorieën bestand formaat
```json
{
  "type": "weekplanner_cats",
  "cats": {
    "Werk": { "icon": "💼", "opts": ["Werkzaamheden", "Vergadering"] },
    "Vrije tijd": { "icon": "🎯", "opts": ["Herstellen", "Hobby's"] }
  }
}
```

## 🛠️ Technisch

- Pure HTML / CSS / JavaScript — geen dependencies
- `localStorage` voor weekdata (`week_YYYY-MM-DD`) en categorieën (`weekplanner_cats`)
- `FileReader` API voor JSON import (meerdere bestanden parallel)
- `@media print` voor PDF layout
- `<details>` / `<summary>` voor inklapbare infobox
- Toast notificaties zonder externe library
- Custom activiteiten worden via `Array.includes()` gecontroleerd en
  via `push()` aan de categorie toegevoegd bij bevestigen

## 📋 Licentie

MIT — vrij te gebruiken en aan te passen.
