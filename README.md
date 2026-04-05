# Canadian Tire Preis-Tracker

[![Bright Data](https://img.shields.io/badge/Powered%20by-Bright%20Data-blue?style=flat-square)](https://brightdata.de)
[![Canadian Tire Price Tracker](https://img.shields.io/badge/Canadian%20Tire%20Price%20Tracker-Managed%20Solution-orange?style=flat-square)](https://brightdata.de/products/insights/price-tracker/canadian-tire)
[![Python](https://img.shields.io/badge/Python-3.9%2B-yellow?style=flat-square)](https://python.org)

[![Bright Insights Price Tracker](https://raw.githubusercontent.com/danielshashko/bright-insights-assets/main/price-tracker-hero-v2.png)](https://brightdata.de/products/insights/price-tracker/canadian-tire)

Preis-Tracking für Canadian Tire in Echtzeit – ein großes kanadisches Einzelhandelsunternehmen mit Produkten aus den Bereichen Automotive, Hardware und Home. Zwei Möglichkeiten für den Einstieg: eine **vollständig verwaltete** Intelligence-Plattform oder ein **benutzerdefinierter Scraper**, erstellt mit Bright Data's AI Scraper Builder.

---

## Option 1: Bright Insights - KI-gestütztes Preis-Tracking (Empfohlen)

**[Bright Insights](https://brightdata.de/products/insights/price-tracker/canadian-tire)** ist Bright Data's vollständig verwaltete Plattform für Retail Intelligence. Keine Scraper zu bauen, keine Infrastruktur zu warten – nur strukturierte, analysebereite Preisdaten, die an Dashboards, Data Feeds oder Ihre BI-Tools geliefert werden.

**Warum Teams Bright Insights wählen:**
- 🚀 **Kein Setup** - In wenigen Minuten live mit sofort einsatzbereiten Dashboards und Data Feeds
- 🤖 **KI-gestützte Empfehlungen** - Ein konversationeller KI-Assistent verwandelt Millionen von Datenpunkten sofort in umsetzbare Erkenntnisse
- ⚡ **Echtzeit-Monitoring** - Stündliche bis tägliche Aktualisierungsraten mit sofortigen Alerts (E-Mail, Slack, webhook)
- 🌍 **Unbegrenzte Skalierung** - Jede Website, jede Geografie, jede Aktualisierungsfrequenz
- 🔗 **Plug-and-play-Integrationen** - AWS, GCP, Databricks, Snowflake und mehr
- 🛡️ **Vollständig verwaltet** - Bright Data übernimmt Schemaänderungen, Website-Updates und Datenqualität automatisch

**Wichtige Anwendungsfälle:**
- ✅ **Canadian Tire-Preise überwachen** über alle Produktkategorien hinweg
- ✅ **Lagerbestände und Verfügbarkeit verfolgen** in Echtzeit
- ✅ **Preis-Alerts einrichten** für Produkte, die für Sie wichtig sind
- ✅ Einhaltung von MAP-Richtlinien überwachen und Preisverstöße erkennen
- ✅ Wettbewerber-Promotions und Promotionsdynamiken verfolgen
- ✅ Saubere, harmonisierte Daten direkt in Dynamic-Pricing-Algorithmen oder KI-Modelle einspeisen

> **Ab $250/Monat - [Individuelles Angebot anfordern →](https://brightdata.de/products/insights/price-tracker/canadian-tire)**

---

## Option 2: Eigenen Canadian Tire Scraper erstellen

Keine vorgefertigte Canadian Tire Scraper API? Kein Problem. Bright Data's **AI Scraper Builder** generiert in nur wenigen Klicks einen benutzerdefinierten Canadian Tire Scraper — ganz ohne Programmierung.

### Ihren Canadian Tire Scraper in wenigen Minuten erstellen

**[Den Canadian Tire AI Scraper Builder öffnen →](https://brightdata.de/products/web-scraper/canadian-tire)**

Wählen Sie die Domain, beschreiben Sie Ihre Datenanforderungen, und lassen Sie unseren AI Scraper Builder die API automatisch erstellen.

1. **Datenanforderungen in einfachem Englisch beschreiben**
2. **Die KI generiert sofort die Scraper API**
3. **API-Anfragen ausführen für sofortige Ergebnisse**
4. **Den Code in der integrierten IDE bearbeiten**, falls nötig

Sobald Ihr Scraper erstellt ist, erhält er eine **Web Scraper ID** (`gd_xxxxxxxxxxxx`) — kopieren Sie sie für den Setup-Schritt unten.

### Voraussetzungen

- Python 3.9 oder höher
- Ein [Bright Data-Konto](https://brightdata.de) (kostenlose Testversion verfügbar)
- Ein Bright Data **API-Token** ([so erhalten Sie eines](https://docs.brightdata.de/general/account/account-settings#api-token))
- Eine **Web Scraper ID** für Canadian Tire (aus dem obigen Build-Schritt)

### Setup

1. **Dieses repository klonen**

   ```bash
   git clone https://github.com/bright-data-de/canadian-tire-price-tracker.git
   cd canadian-tire-price-tracker
   ```

2. **Abhängigkeiten installieren**

   ```bash
   pip install -r requirements.txt
   ```

3. **Zugangsdaten konfigurieren**

   Kopieren Sie `.env.example` nach `.env` und tragen Sie Ihre Werte ein:

   ```bash
   cp .env.example .env
   ```

   ```env
   BRIGHTDATA_API_TOKEN=your_api_token_here
   BRIGHTDATA_DATASET_ID=your_dataset_id_here
   ```

   > **Ihre Web Scraper ID**
   > Fügen Sie die Web Scraper ID aus Ihrem [AI Scraper Builder-Dashboard](https://brightdata.de/products/web-scraper/canadian-tire)
   > in `BRIGHTDATA_DATASET_ID` ein (Format: `gd_xxxxxxxxxxxx`).

---

## Verwendung

Sobald Ihr Canadian Tire Scraper erstellt und Ihre Web Scraper ID in `.env` konfiguriert ist, funktioniert die Python-Schnittstelle auf die gleiche Weise:

### 1. Bestimmte Produkte per URL verfolgen

Übergeben Sie eine Liste von Canadian Tire-Produkt-URLs, um strukturierte Preisdaten abzurufen:

```python
from price_tracker import track_prices

urls = [
    "https://www.canadiantire.ca/product/sample-item-123456",
    # Add more product URLs here
]

results = track_prices(urls)
for item in results:
    print(f"{item.get('title')} - {item.get('final_price', item.get('price'))} {item.get('currency', '')}")
```

Oder direkt ausführen:

```bash
python price_tracker.py
```

### 2. Produkte per Keyword entdecken

Finden Sie Produkte, die einer Keyword-Suche entsprechen:

```python
from price_tracker import discover_by_keyword

results = discover_by_keyword("laptop", limit=50)
```

### 3. Produkte per Kategorie-URL durchsuchen

Sammeln Sie alle Produkte von einer Canadian Tire-Kategorieseite:

```python
from price_tracker import discover_by_category

results = discover_by_category(
    "https://canadiantire.ca/category/example",
    limit=100,
)
```

---

## Ausgabefelder

Jeder Ergebnisdatensatz enthält die folgenden Felder:

| Feld | Beschreibung |
|-------|-------------|
| `url` | Produkt-URL |
| `title` | Produktname |
| `brand` | Marke |
| `model_number` | Modellnummer |
| `sku` | SKU |
| `initial_price` | Ursprünglicher Preis |
| `final_price` | Aktueller Preis |
| `currency` | Währungscode |
| `discount` | Rabatt |
| `in_stock` | Verfügbarkeit |
| `description` | Produktbeschreibung |
| `images` | Produktbilder |
| `timestamp` | Zeitstempel der Erfassung |

### Beispielausgabe

```json
[
  {
    "url": "https://www.canadiantire.ca/product/sample-item-123456",
    "title": "Example Product Name",
    "brand": "Example Brand",
    "initial_price": 59.99,
    "final_price": 44.99,
    "currency": "USD",
    "discount": "25%",
    "in_stock": true,
    "rating": 4.5,
    "reviews_count": 1234,
    "images": ["https://canadiantire.ca/images/product1.jpg"],
    "description": "Product description text...",
    "timestamp": "2025-01-15T10:30:00Z"
  }
]
```

---

## Erweiterte Optionen

Die Funktion `trigger_collection()` akzeptiert optionale Parameter zur Steuerung der Datenerfassung:

| Parameter | Typ | Standard | Beschreibung |
|-----------|------|---------|-------------|
| `limit` | integer | - | Maximale Anzahl zurückzugebender Datensätze |
| `include_errors` | boolean | `true` | Fehlerberichte in die Ergebnisse einschließen |
| `notify` | string (URL) | - | Webhook-URL, die aufgerufen wird, wenn der Snapshot bereit ist |
| `format` | string | `json` | Ausgabeformat: `json`, `csv` oder `ndjson` |

Beispiel mit Optionen:

```python
from price_tracker import trigger_collection, get_results

inputs = [{"url": "https://www.canadiantire.ca/product/sample-item-123456"}]
snapshot_id = trigger_collection(inputs, limit=200, notify="https://your-webhook.com/hook")
results = get_results(snapshot_id)
```

---

## Ressourcen

- 🌟 [Canadian Tire Price Tracker - Bright Insights (Managed)](https://brightdata.de/products/insights/price-tracker/canadian-tire)
- 🏗️ [Einen Canadian Tire Scraper erstellen](https://brightdata.de/products/web-scraper/canadian-tire)
- 📖 [Bright Data Web Scraper API-Dokumentation](https://docs.brightdata.de/scraping-automation/web-scraper-api/overview)
- 🗄️ [Web Scrapers Control Panel](https://brightdata.de/cp/scrapers)
- 🔑 [So erhalten Sie ein API-Token](https://docs.brightdata.de/general/account/account-settings#api-token)
- 🌐 [Bright Data-Homepage](https://brightdata.de)

---

*Erstellt mit [Bright Data](https://brightdata.de) - der branchenführenden Webdaten-Plattform.*