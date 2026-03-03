# Evolution of Data Leakage Attack Vectors and Mitigation Strategies  
## A Scopus-Based Meta-Landscape Analysis Using Machine Learning

This repository provides the datasets and implementation scripts supporting the paper:

> **"Evolution of Data Leakage Attack Vectors and Mitigation Strategies:  
A Scopus-Based Meta-Abstraction Analysis Using Machine Learning"**

The study performs a large-scale longitudinal meta-analysis of cybersecurity research trends related to data leakage attacks and mitigation strategies using abstract-level text mining and topic modeling.

---

## 📌 Repository Purpose

This repository ensures:

- 🔎 Reproducibility of computational experiments  
- 📊 Transparency of topic modeling and trend estimation  
- 📈 Verification of Attack–Mitigation comparative analysis  
- 🔁 Robustness validation across random LDA initializations  

All quantitative results reported in the paper are derived from the notebook and datasets included here.

---

## 📂 Repository Structure
├── 217_attack_vector.csv
├── 2738_attack_mitigation.csv
├── DataLeakageAttackDataset.ipynb
└── README.md


---

## 📊 Datasets

### 1️⃣ `217_attack_vector.csv`

Contains 217 journal articles focused on major data leakage attack vectors:

- Credential leakage  
- Insider threat  
- Cloud misconfiguration  

These articles were retrieved from Scopus using a focused keyword query.

Each record includes:
- Title  
- Abstract  
- Publication year  
- DOI (when available)

This dataset is used for:
- Attack theme extraction
- Topic modeling (k=3)
- Temporal trend estimation

---

### 2️⃣ `2738_attack_mitigation.csv`

Contains 2,738 journal articles focused on mitigation strategies:

- Detection mechanisms  
- Prevention approaches  
- Access control  
- Security monitoring  

This broader dataset captures solution-oriented research.

This dataset is used for:
- Mitigation theme extraction
- Topic modeling (k=6)
- Growth comparison against attack trends

---

## 🧠 Methodological Workflow (Implemented in `DataLeakageAttackDataset.ipynb`)

The notebook implements the following pipeline:

### 1️⃣ Text Preprocessing
- Lowercasing
- Stopword removal
- Tokenization
- Noise reduction

### 2️⃣ Feature Representation
- Term Frequency / Count-based vectorization
- TF-IDF (where applicable)

### 3️⃣ Topic Modeling
- Latent Dirichlet Allocation (LDA)
- Coherence score evaluation
- Optimal topic selection:
  - k = 3 (attack dataset)
  - k = 6 (mitigation dataset)

### 4️⃣ Temporal Aggregation
- Year-wise topic probability averaging
- Normalization by total publications per year

### 5️⃣ Growth Estimation
Linear regression applied to normalized yearly topic distributions:

\[
NTF_{k,y} = \alpha_k + \beta_k y + \epsilon_y
\]

The slope \( \beta_k \) represents long-term thematic growth.

### 6️⃣ Attack–Mitigation Ratio (AMR)

\[
AMR_y = \frac{A_y}{M_y}
\]

Used as a proportional indicator of research focus balance.

### 7️⃣ Trend Divergence Index (TDI)

\[
TDI = \beta_{\text{attack}} - \beta_{\text{mitigation}}
\]

Used to operationalize the concept of *research response lag*.

If the notebook won't open, visit https://drive.google.com/file/d/18LHnvjryBiUSXAwLK_UCW8glfAU4QoPF/view?usp=sharing for direct access to Google Colab.
---

## 🔁 Robustness Check

To evaluate topic stability:

- LDA models were retrained using multiple random seeds:
  `{0, 10, 42, 100, 123}`
- Top-10 keywords per topic were extracted
- Keyword overlap across seeds was computed

Results indicate stable semantic structure across initialization conditions, supporting the robustness of the extracted themes.

---

## 📈 Key Outputs Reproducible from Notebook

Running the notebook reproduces:

- Topic keyword tables
- Temporal evolution curves
- Regression slope estimates
- Attack vs mitigation growth comparison
- Trend Divergence Index (TDI)
- Robustness overlap statistics

---

## ⚠️ Important Notes

- The study uses abstract-level data only (not full text).
- Publication coverage: 2000–2026 (effective data coverage: 2013–2025).
- Growth is modeled using linear regression for interpretability.
- All metrics are operational indicators derived from normalized topic distributions.

---

## 🧩 Conceptual Contribution

This repository supports a computational operationalization of:

- Cybersecurity research co-evolution
- Attack–defense asymmetry
- Research response lag in cloud-centric security landscapes

The introduced TDI metric is not a novel mathematical construct, but a derived indicator based on regression slope differences.


---

## 🔐 Ethical Considerations

All data were retrieved from publicly indexed bibliographic records (Scopus).
No personal or sensitive data were processed.

---

## 📎 Contact

For questions or collaboration inquiries, please contact the corresponding author.

