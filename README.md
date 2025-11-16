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

## 📂 Projektstruktur

kundensegmentierung/

├── data/
│   └── raw/
│       └── OnlineRetail.csv          # Original-Datensatz

├── notebooks/
│   ├── 01_hac_clustering.ipynb          # Hierarchical Clustering Notebook
│   ├── 02_k-means_clustering.ipynb      # K-Means Clustering Notebook
│   ├── 03_optics_clustering.ipynb       # OPTICS Clustering Notebook
│   ├── 04_dbscan_clustering.ipynb       # DBSCAN Clustering Notebook
│   ├── cluster_examples_kmeans.csv           # Beispieldaten K-Means
│   ├── cluster_summary_kmeans.csv            # Zusammenfassung K-Means Ergebnisse
│   └── customer_segments_kmeans.csv           # K-Means Kundensegmente

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
│   ├── cluster_summary_optics.csv            # Zusammenfassung OPTICS Ergebnisse
│   ├── customer_segments_optics.csv           # OPTICS Kundensegmente
│   └── noise_customers_optics.csv    # OPTICS Noise Kunden

├── requirements/                    # Anforderungen bzw. Abhängigkeiten




  
