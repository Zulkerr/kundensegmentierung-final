# Kundensegmentierung mit Machine Learning

Eine umfassende Analyse zur Kundensegmentierung im E-Commerce mit verschiedenen Clustering-Algorithmen.

## Inhaltsverzeichnis

- [Projectübersicht](#projectübersicht)
- [Dataset](#dataset)
- [Methoden](#methoden)
- [Projectstruktur](#projectstruktur)
- [Installation](#installation)
- [Verwendung](#verwendung)
- [Ergebnisse](#ergebnisse)
- [Technologien](#technologien)
- [Autor](#autor)
   
## Projectübersicht  

Dieses Projekt implementiert verschiedene **Clustering-Algorithmen** zur Segmentierung von E-Commerce-Kunden basierend auf ihrem Kaufverhalten. Ziel ist es, verschiedene Kundensegmente zu identifizieren und maßgeschneiderte Marketing-Strategien zu entwickeln.  

### Geschäftsziele

- Identifikation verschiedener Kundengruppen
- Optimierung von Marketing-Ressourcen
- Personalisierte Kundenansprache
- Steigerung der Kundenbindung und des Umsatzes

## Dataset 

**Quelle:** [Online Retail Dataset](https://www.kaggle.com/code/hellbuoy/online-retail-k-means-hierarchical-clustering)

### Datenbeschreibung

- **Transaktionen:** ~540.000 Datensätze
- **Zeitraum:** Dezember 2010 - Dezember 2011
- **Kunden:** ~4.300 einzigartige Kunden
- **Herkunft:** UK-Basierter Online-Einzelhändler

### Features
| Feature | Beschreibung |
|----------|--------------|
| InvoiceNo | Rechnungsnummer |
| StockCode | Produktcode | 
| Description | Produktbeschreibung |
| Quantity  | Bestellmenge | 
| InvoiceDate | Bestelldatum |
| UnitPrice | StückPrice  |
| CustomerID | Kundennummer |
| Country | Land | 

## Methoden

Das Projekt implementiert **vier verschiedene Clustering-Algorithmen** und vergleicht ihre Ergebnisse:

### 1. **K-Means Clustering**
- Schnell und effizient
- Gut für sphärische Cluster
- Anzahl der Cluster muss vorgegeben werden
- Optimierung mit Elbow-Methode und Silhouette-Score


### 2. **Hierarchical Agglomerative Clustering (HAC)**
- Keine vorgegebene Cluster-Anzahl nötig
- Dendrogram-Visualisierung
- Verschiedene Linkage-Methoden (Ward, Complete, Average)
- Rechenintensiv bei großen Datensätzen

### 3. **OPTICS (Ordering Points To Identify the Clustering Structure)**
- Findet Cluster variabler Dichte
- Keine eps-Parameter nötig
- Reachability-Plot-Visualisierung
- Komplexer zu interpretieren

### 4. **DBSCAN(Density-Based Spatial Clustering)**
- Findet Cluster beliebiger Form
- Identifiziert Ausreißer automatisch
- Robust gegenüber Noise
- sensitive Parameter-Wahl (eps, min_samples)

## Projektstruktur 

````
kundensegmentierung/  

├── data/  
│   └── raw/  
│       └── OnlineRetail.csv             # Original-Datensatz

├── notebooks/   
│   ├── 01_hac_clustering.ipynb           # Hierarchical Clustering Notebook
│   ├── 02_k-means_clustering.ipynb         # K-Means Clustering Notebook
│   ├── 03_optics_clustering.ipynb          # OPTICS Clustering Notebook
│   ├── 04_dbscan_clustering.ipynb          # DBSCAN Clustering Notebook
│   ├── cluster_examples_kmeans.csv             # Beispieldaten K-Means
│   ├── cluster_summary_kmeans.csv              # Zusammenfassung K-Means Ergebnisse
│   └── customer_segments_kmeans.csv              # K-Means Kundensegmente

├── results/   
│   └── figures/   
│       ├── 02_Dendrogramme.png                       
│       ├── 02_rfm_correlation.png                       
│       ├── 03_Empfehlende_Cluster.png     
│       ├── 03_transformation_comparison.png     
│       ├── 04_k_distance_plot.png     
│       ├── 05_optics_reachability_plot.png      
│       ├── 06_epsilon_analysis.png      
│       ├── 07_cluster_profiles_boxplot.png      
│       ├── 08_cluster_visualization_3d.png      
│       ├── hac_cluster_distribution.png      
│       └── hac_clustering_final.png       
│
│   ├── cluster_summary_optics.csv                 # Zusammenfassung OPTICS Ergebnisse
│   ├── customer_segments_optics.csv                   # OPTICS Kundensegmente
│   └── noise_customers_optics.csv          # OPTICS Noise Kunden

├── requirements/                       # Anforderungen bzw. Abhängigkeiten

````

## Installation

### Voraussetzungen

- Python 3.8+
- Jupyter Notebook

### Schritt 1: Repository klonen

```bash
git clone https://github.com/Zulkerr/kundensegmentierung.git
oder Zip-Datei herunterladen und extraiehren
````

### Schritt 2: Virtual Environment erstellen
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# Mac/Linux
source venv/bin/activate
````

### Schritt 3: Abhängigkeiten installieren
```bash
pip install -r requirements.txt
````
### Requirements.txt
```bash
pandas>=2.0.0
numpy>=1.24.0
matplotlib>=3.7.0
seaborn>=0.12.0
scikit-learn>=1.3.0
scipy>=1.11.0
openpyxl>=3.1.0
jupyter>=1.0.0
````
### Schritt 4: Jupyter lab im Terminal aufrufen

```bash
jupyter lab
````

## Verwendung

-  Daten laden und Vorbereiten
-  Clustering Methoden anwenden
-  Cluster Evaluieren & Analysieren
-  Intepretieren & Visualisieren
-  Ergebnisse Exportieren
   
## Ergebnisse

### RFM-Analyse  
Das Projekt verwendet RFM-Analyse(Recency, Frequency, Monetary) als Grundlage:
- Recency (R): Tage seit letztem Kauf
- Frequency (F): Anzahl der Bestellungen
- Monetary (M): Gesamtumsatz

### Identifizierte Kundensegmente (Ein Beispiel von DBSCAN)


| Segment             | Größe        | Ø Recency | Ø Frequency | Ø Monetary   | Beschreibung                            |
|---------------------|--------------|-----------|-------------|-------------|---------------------------------------|
|  Champions        | 1918 (44.2%) | 44 Tage   | 6.6         | £2,456.64   | VIP-Kunden, die häufig und viel kaufen|
|  Hibernating       | 1472 (33.9%) | 157 Tage  | 1.0         | £342.43     | Lange inaktive Kunden mit geringem Umsatz |
|  Potential Loyalists | 827 (19.1%) | 94 Tage   | 2.0         | £656.19     | Kürzlich aktiv, Potenzial für Stammkunden |
|  Extreme Customers | 121 (2.8%)   | 67 Tage   | 22.4        | £25,856.65  | Ausreißer: B2B-Kunden oder Großhändler|


### Algorithmen-Vergleich

| Algorithmus | Cluster  | Slihouette Score  | Noise    | Best Parameter | Vorteile    |
|-------------|----------|-------------------|----------|----------------| ------------|
|  K-Means    |  4       | ~0.45             |  0%      | k=4            | Schnell,Klar interpretierbar|
|  HAC        | 4-5      | ~0.42             |  0%      | Ward Linkage   | Dendrogram-Visualisierung|
|  OPTICS     | 3-5      | ~0.38             | 2-5%     | min_samples=5  | Variable Dichte-Cluster |
| DBSCAN      | 3        |  0.153            | 2.8%     | eps=0.4,min_samples=6| Ausreißer-Identifikation| 

### Business Impact

#### Geschätzer ROI durch Segmentierung
- Champions: Umsatzsteigerung durch Loyalitätsprogramme (+15-20%)
- Hibernating: Reaktivierung von 20% = 294 Kunden * £342 = £100.548 zusätzlicher Umsatz
- Potential Loyalists: Conversion zu Stammkunden (+30%) = £162.733 zusätzlicher Umsatz
- Extreme Customers: B2B-Verträge = £3,1M Gesamtumsatz sichern

## Technologien
- Python
- pandas — Datenmanipulation
- Numpy  — Numerische Berechnung
- scikit-learn — Machine Learning Algorithmen
- matplotlib & seaborn  — Visualisierung
- Jupyter Notebook — Interaktive Entwicklung

 
