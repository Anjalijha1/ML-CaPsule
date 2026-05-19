# Diabetes Variant Analysis & Classification

An AI-driven data analytics and machine learning solution designed to classify diabetes variants and map metabolic interactions. This project focuses on identifying complex patterns across clinical indicators through robust data ingestion, deep data quality profiling, and statistical visualizations.

---

## 🚀 Key Architectural Features

* **Automated & Safe Data Ingestion:** An isolated pipeline engineered to extract compressed archive sources, validate CSV payloads, and load records into memory with explicit multi-layered fallback exception handling.
* **Intelligent Data Triage Engine:** A deep-scanning data profiling module built to systematically catch hidden anomalies, structural omissions, and unmapped placeholders before modeling pipelines run.
* **Dynamic Statistical Charting:** A visualization suite leveraging automated data structuring and customized palette mappings to expose analytical patterns at a glance.

---

## 📊 Deep-Dive: Data Profiling & Quality Analysis

The core of this repository features a tailored data profiling algorithm. Instead of deploying basic missing-value checks, this pipeline is designed around a fundamental reality in health informatics: **the presence of hidden missing indicators disguised as valid numerical zeros.**

### 🔍 Comprehensive Visual Observations & Insights

1. **The "Hidden Missing Data" Phenomenon**
   In physiological datasets (such as clinical diabetes distributions), foundational biometric markers like **Insulin**, **Skin Thickness**, **Blood Pressure**, and **Glucose** can never biologically hit an absolute value of zero in a living patient. A standard `df.isnull().sum()` check completely misses these records because zero is recognized as a valid number. 
   
   The code successfully exposes this by treating $0$ and `NaN` as unified missing elements, bringing the true dataset vulnerability to light.

2. **Visual Feature Triage & Model Risk Evaluation**
   * **High Anomaly Thresholds (Critical Risk Columns):** Features like *Insulin* and *Skin Thickness* typically return massive bars on the generated chart, often representing a $30\%$ to $50\%+$ corruption rate in standard clinical data. The graph immediately warns the engineer that a simple "drop rows" approach (`dropna()`) will decimate the dataset volume, making statistical imputation techniques (such as K-Nearest Neighbors or Median values) absolutely non-negotiable.
   * **Low Anomaly Thresholds (Clean Baselines):** Columns like *Age* or *Pregnancies* (where a value of zero is a biologically flawless, normal data point) correctly project as tiny or zero-height bars on the plot, signaling that they require no mathematical transformations.

3. **Optimized Risk Palette & Metric Overlays**
   * **Precision Labels:** The bar chart systematically calculates and prints exact percentage strings on top of each corresponding column bar, meaning stakeholders can extract hard numeric ratios instantly without looking at a single line of raw data.
   * **Visual Prioritization:** By rendering the data across an ordered severity spectrum, the visualization behaves like a dashboard. The taller and more pronounced a bar is, the more mathematical noise it introduces into down-stream machine learning classification algorithms.

---

## 🛠️ Tech Stack & Frameworks

* **Core Language:** Python
* **Data Processing:** NumPy, Pandas
* **Visualization Suite:** Matplotlib, Seaborn
* **Data Extraction & OS Interaction:** `os`, `zipfile`

---

## 🧬 End-to-End Execution Workflow

1. **Extraction and Directory Mounting:** The script verifies local pathways, initializes a secure data directory `./extracted_data`, extracts the `.zip` target, and verifies its internal architecture.
2. **DataFrame Hydration:** Streamlines raw text characters into memory as a structured Pandas DataFrame, echoing structural metadata (`shape`) directly to the logging console.
3. **Multi-Feature Quality Sweep:** Isolates non-string structures, runs iterative scanning for zeros and null flags, and translates counts into clean relative percentages.
4. **Data Aggregation:** Packs calculations into a standalone analytical summary DataFrame (`anomaly_df`) to feed the drawing canvas.
5. **Canvas Optimization & Plotting:** Generates an adjusted, rotated chart configuration to guarantee zero character overlaps on text-heavy medical categories.
6.
