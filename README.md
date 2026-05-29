[README.md](https://github.com/user-attachments/files/28382128/README.md)
# Blutdruck & Herzfrequenz — PWA

Eine datenschutzfreundliche Progressive Web App zur Erfassung und Auswertung von Blutdruck, Herzfrequenz und Medikamenten. Alle Daten bleiben ausschließlich lokal auf dem Gerät — keine Cloud, keine Konten, keine Freigaben.

---

## Funktionen

### Übersicht
- Halbkreisförmiges Gauge-Diagramm mit aktueller Klassifikation nach ESC-Leitlinie 2018
- Farbiger Zonenbalken (Optimal → Grad 3 Hypertonie)
- Durchschnittswerte der letzten 7 Messungen (Systole, Diastole, Herzfrequenz)
- Mini-Sparkline der letzten 7 Messungen (Sys/Dia/HF in einem Diagramm)

### Eingabe
- Datum, Uhrzeit, Systole, Diastole, Herzfrequenz, optionale Notiz
- Live-Klassifikationsvorschau während der Eingabe
- Automatische Validierung der Eingabewerte

### Verlauf
- Liniendiagramm Blutdruck (Systole + Diastole) der letzten 30 Messungen
- Liniendiagramm Herzfrequenz der letzten 30 Messungen
- Gestrichelte Referenzlinien für klinische Grenzwerte

### Messungen
- Chronologische Liste aller Messungen (neueste zuerst)
- ESC-Klassifikations-Badge pro Eintrag
- Einzelne Einträge löschbar
- **CSV-Export** (kompatibel mit Excel, Numbers, LibreOffice)
- **JSON-Backup** und **JSON-Import** (geräteübergreifende Sicherung)

### Medikamente
- Suche mit Autocomplete aus 150+ Wirkstoffen und Handelsnamen
- Erfassung von Dosis und Einnahmehäufigkeit
- **Automatische Wechselwirkungsprüfung** gegen 30+ klinische Regeln
- Warnhinweise in zwei Stufen: 🚨 Wichtiger Hinweis (Kontraindikation) / ⚡ Hinweis (Überwachung erforderlich)

---

## Enthaltene Medikamentengruppen

| Bereich | Gruppen |
|---|---|
| Blutdruck | ACE-Hemmer, Sartane, Kalziumantagonisten, Betablocker, Thiazid- und Schleifendiuretika, Kaliumsparende Diuretika, Alphablocker, Zentral wirkend, Renin-Inhibitoren, Vasodilatatoren |
| Antidepressiva | SSRIs, SNRIs, Trizyklische AD, MAO-Hemmer, Bupropion, Mirtazapin, Lithium u.a. |
| Schilddrüse | Levothyroxin, Liothyronin, Thyreostatika (Thiamazol, Carbimazol u.a.) |
| ADHS | Methylphenidat, Lisdexamfetamin, Atomoxetin, Guanfacin |
| Cholesterin | Statine, Fibrate, Ezetimib, PCSK9-Inhibitoren, Gallensäurebinder |
| Diabetes | Metformin, Sulfonylharnstoffe, DPP-4-Hemmer, SGLT2-Hemmer, GLP-1-Agonisten, Insulin, Glitazone, Glinide |

---

## Ausgewählte Wechselwirkungsregeln (Beispiele)

| Kombination | Schwere | Grund |
|---|---|---|
| SSRI + MAO-Hemmer | 🚨 Kontraindiziert | Serotonin-Syndrom |
| Stimulanzien + MAO-Hemmer | 🚨 Kontraindiziert | Hypertensive Krise |
| ACE-Hemmer + Sartan | 🚨 Gefährlich | Duale RAAS-Blockade, Nierenversagen |
| Statin + Fibrat (Gemfibrozil) | 🚨 Gefährlich | Rhabdomyolyse |
| Betablocker + Verapamil/Diltiazem | 🚨 Gefährlich | AV-Block |
| Betablocker + Insulin/Sulfonylharnstoff | ⚡ Überwachung | Hypoglykämie-Maskierung |
| SGLT2-Hemmer + Diuretikum | ⚡ Überwachung | Dehydratation |
| Levothyroxin + Gallensäurebinder | 🚨 Gefährlich | Resorptionsstörung |
| SSRI + Trizyklika | ⚡ Überwachung | TCA-Spiegel-Anstieg |
| Atomoxetin + SSRI | ⚡ Überwachung | CYP2D6-Hemmung |

---

## Datenspeicherung

- Messwerte: `localStorage` Key `bp_v2`
- Medikamente: `localStorage` Key `bp_meds_v1`
- Kein Netzwerkzugriff, keine externen APIs
- Daten überleben das Löschen des Browser-Cache wenn als PWA installiert
- Für Gerätewechsel: JSON-Export/Import verwenden

---

## Dateien

| Datei | Funktion |
|---|---|
| `index.html` | Gesamte App (HTML, CSS, JavaScript) |
| `manifest.json` | PWA-Manifest (Name, Icons, Darstellung) |
| `sw.js` | Service Worker (Offline-Fähigkeit) |
| `icon-192.png` | App-Icon 192×192 px |
| `icon-512.png` | App-Icon 512×512 px |

---

## Installation als PWA (Android)

1. URL in **Chrome** auf Android öffnen
2. Menü (drei Punkte) → **„App installieren"**
3. Bestätigen → App erscheint auf dem Homescreen
4. Startet fortan ohne Browser-UI als eigenständige App

---

## Klassifikation nach ESC 2018

| Kategorie | Systole | Diastole |
|---|---|---|
| Optimal | < 120 | < 80 |
| Normal | 120–129 | 80–84 |
| Hochnormal | 130–139 | 85–89 |
| Grad 1 Hypertonie | 140–159 | 90–99 |
| Grad 2 Hypertonie | 160–179 | 100–109 |
| Grad 3 Hypertonie | ≥ 180 | ≥ 110 |

---

## Haftungsausschluss

Die Wechselwirkungshinweise basieren auf einer eingebetteten Datenbank klinisch bekannter Interaktionen. Sie ersetzen **keine ärztliche oder pharmazeutische Beratung**. Nicht alle Medikamente sind erfasst. Unbekannte Wirkstoffe werden nicht erkannt. Alle Hinweise sind mit dem behandelnden Arzt oder Apotheker zu besprechen.

Die App ist ausschließlich zur persönlichen Orientierung bestimmt und stellt keine medizinische Diagnose.
