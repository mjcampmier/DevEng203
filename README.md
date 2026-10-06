# Digital Transformation of Development — DevEng 203

Course materials and in-class breakout notebooks for **DevEng 203: Digital Transformation of Development**, a 3-unit graduate course in the [Development Engineering Program](https://deveng.berkeley.edu/) at **UC Berkeley**.

> As technology use proliferates globally, there exists significant potential to leverage such technology and associated data streams to further understand and improve the lives and livelihoods of people in low-resource settings. This course introduces students to data-intensive approaches to development, drawing on development economics, machine learning, information science, and computational social science.

This repository holds the hands-on Python notebooks used during class breakouts. The course pairs technical training with the critical judgment development practitioners need: while novel technology has the potential to materially improve lives, poverty and social inequality have persisted despite advances in data availability, analytical techniques, and automation.

---

## Course at a Glance

| | |
|---|---|
| **Term** | Fall 2026 |
| **Units** | 3 |
| **Meeting time** | Mondays, 9:00 AM – 12:00 PM (Noon) Pacific |
| **Location** | Blum Hall B100 |
| **Format** | In-person required (no hybrid or asynchronous attendance) |
| **First class** | Monday, 31 August 2026 |
| **Instructor** | Mark Campmier, PhD — Lecturer, College of Engineering; Postdoctoral Researcher, School of Public Health · [mark_campmier@berkeley.edu](mailto:mark_campmier@berkeley.edu) |
| **GSI** | Noam Aberin Anglo — [nanglo@berkeley.edu](mailto:nanglo@berkeley.edu) |

---

## Learning Objectives

1. **Use automated data analysis and data engineering tools ethically and efficiently.** Gain hands-on experience judging the technical, economic, and social impacts of novel technologies.
2. **Present complex, state-of-the-science findings for broad and expert audiences.** Practice data visualization and scientific communication through oral presentations, long-form papers, and short-form lab reports.
3. **Manage large and diverse data pipelines for engineering-based interventions.** Lead, propose, and execute a data project using multiple measurement and modeling techniques in the development sector.

Supporting catalog objectives: hands-on experience in data sourcing, cleaning, analysis, and visualization; using data to make informed decisions around development challenges; strengthening programming and analysis skills; and developing a "systems" perspective on how data is used in a development context.

---

## Repository Structure

```
DevEng203/
├── Week3/                        # Hypothesis Testing & Data Visualization
│   ├── DataViz_Part1.ipynb       # NumPy, distributions, matplotlib, statistical tests
│   └── DataViz_Part2.ipynb       # pandas on real survey data; parametric vs. non-parametric tests
├── Week4/                        # Unsupervised Learning & Big Data
│   ├── DataExploration.ipynb     # Correlation (Pearson/Spearman/Kendall), heatmaps, standardization
│   └── UnsupervisedLearning.ipynb# StandardScaler, PCA, and K-Means with diagnostics
├── Week5/                        # Supervised Learning
│   ├── LinearRegression.ipynb    # Train/test, metrics, residuals, coefficient interpretation
│   ├── DecisionTree.ipynb        # Tree regression, feature importance, depth tuning
│   └── InteractiveModeling.ipynb # Interactive plotly + ipywidgets explorer; cross-validation
├── LICENSE                       # BSD 3-Clause
└── README.md
```

Notebooks follow a consistent teaching style: a titled introduction, Markdown section headers with explanatory prose, and clean code cells with outputs cleared. Data is loaded through a `pathlib` placeholder (`path_to_file = Path('your/path')`) so you only edit the path in one place.

---

## Notebook Catalog

### Week 3 — Hypothesis Testing & Data Visualization
- **`DataViz_Part1.ipynb`** — Builds statistical tooling from scratch with NumPy: importing libraries, generating distributions, descriptive statistics (mean, median, std, IQR), histograms and boxplots in Matplotlib, and statistical testing with `scipy.stats` (one-sample/independent/paired *t*-tests, plus Mann–Whitney U, Wilcoxon, and Kruskal–Wallis).
- **`DataViz_Part2.ipynb`** — Applies the same ideas to **real survey data** with pandas: `.describe()`, built-in boxplots/histograms, ranked comparisons, parametric vs. non-parametric hypothesis testing, and pairwise scatter matrices.

### Week 4 — Unsupervised Learning & Big Data
- **`DataExploration.ipynb`** — Correlation analysis (Pearson, Spearman, Kendall), building a correlation-matrix heatmap from a rough first pass to a masked, publication-ready figure, and feature standardization (z-scores).
- **`UnsupervisedLearning.ipynb`** — A full `scikit-learn` workflow: `StandardScaler` → **PCA** (scree plot, cumulative explained variance, component loadings) → **K-Means** (elbow method, silhouette analysis, cluster visualization, and interpreting clusters via per-cluster profiles).

### Week 5 — Supervised Learning
- **`LinearRegression.ipynb`** — Supervised regression predicting life expectancy from development indicators: feature/target split, train/test split, R²/MAE/RMSE, predicted-vs-actual and residual plots, and coefficient interpretation.
- **`DecisionTree.ipynb`** — Decision tree regression on the same task, with feature importances, full tree visualization, and a depth-tuning diagnostic (train vs. test R²) that illustrates overfitting.
- **`InteractiveModeling.ipynb`** — An interactive dashboard (`ipywidgets` + `plotly`) to pick the target, choose which features enter the model, and switch model types, plus a **cross-validation** module that visualizes how KFold, shuffled KFold, and ShuffleSplit partition the data and compares models by cross-validated score.

---

## Getting Started

### 1. Clone the repository
```bash
git clone <your-fork-or-repo-url>
cd DevEng203
```

### 2. Create an environment and install dependencies
Python 3.10+ is recommended. Using a virtual environment:
```bash
python3 -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install --upgrade pip
pip install jupyterlab numpy pandas matplotlib scipy scikit-learn plotly ipywidgets
```

<details>
<summary>Save as <code>requirements.txt</code></summary>

```
jupyterlab
numpy
pandas
matplotlib
scipy
scikit-learn
plotly
ipywidgets
```
</details>

### 3. Launch Jupyter
```bash
jupyter lab      # or: jupyter notebook
```

`Week5/InteractiveModeling.ipynb` requires `plotly` and `ipywidgets` and must be run in a live kernel — the widgets and Plotly charts will not render in a static preview.

### 4. Point the notebooks at your data
Each notebook sets a path near the top:
```python
from pathlib import Path
path_to_file = Path('your/path')          # ← edit this to your local data folder
df = pd.read_csv(path_to_file / 'country_data.csv')
```
Change `'your/path'` to the directory that contains the dataset for that week.

---

## Datasets

The notebooks reference two CSV files that are **not committed** to the repository (bring your own copy and set `path_to_file` accordingly):

| File | Used in | Description |
|---|---|---|
| `country_data.csv` | Weeks 4 & 5 | Country-level development indicators — `child_mort`, `exports`, `health`, `imports`, `income`, `inflation`, `life_expec`, `total_fer`, `gdpp` (all numeric). |
| `survey_results.csv` | Week 3 (Part 2) | Anonymized class survey of self-reported skill levels (0–5 scale) across several topics. |

---

## Course Schedule

Weeks with 📓 have breakout materials in this repository.

| Date | Week | Topic | |
|---|:---:|---|:---:|
| 31-Aug-2026 | 1 | Course Intro, Ethical AI Usage, & Programming Intro | |
| 07-Sep-2026 | 2 | *Labor Day Holiday — No Class* | |
| 14-Sep-2026 | 3 | Hypothesis Testing & Data Visualization | 📓 |
| 21-Sep-2026 | 4 | Unsupervised Learning & Big Data | 📓 |
| 28-Sep-2026 | 5 | Supervised Learning & Time Series Data | 📓 |
| 05-Oct-2026 | 6 | Embedded Systems & Microcontrollers | |
| 12-Oct-2026 | 7 | Data Acquisition: Sensors & Logging | |
| 19-Oct-2026 | 8 | Sensors at Scale & APIs | |
| 26-Oct-2026 | 9 | Ergodicity & Dynamics-Informed Modeling | |
| 02-Nov-2026 | 10 | Final Project Proposal Presentation | |
| 09-Nov-2026 | 11 | Geographic Information Systems (GIS) | |
| 16-Nov-2026 | 12 | Remote Sensing | |
| 23-Nov-2026 | 13 | Final Project Presentation | |
| 30-Nov-2026 | 14 | Policy Translation & Implementation Science | |

---

## Grading

| Activity | Count | % of Final Grade |
|---|:---:|:---:|
| Discussion Participation | — | 30% |
| Lecture Introduction Presentation | 1 | 5% |
| Course Surveys | 3 | 5% |
| Lab Assignments | 15 | 30% |
| Final Project Proposal | 1 | 10% |
| Final Project Presentation | 1 | 10% |
| Final Project Paper | 1 | 10% |
| **Total** | | **100%** |

There are opportunities for extra credit on each lab assignment.

---

## Policies

**Late work & absences.** Deadlines are posted on the course webpage. Work submitted within 24 hours of the deadline is penalized 10%; within 24–48 hours, 30%; after 48 hours it is not accepted. Extension requests for excused circumstances must be made at least 24 hours before the deadline. Attendance is required to receive participation credit and credit for days with assigned presentations or lab work. Excused absences are limited to religious holidays, major/recurring illness, or pregnancy/childcare obligations.

**Academic integrity & generative AI.** Plagiarism — using another's intellectual contribution without attribution — is subject to University disciplinary action, and includes paraphrasing without significant original contribution and improper citation. Acceptable and unacceptable AI usage is discussed on the first day of class. Because no tool reliably detects AI-generated text, use of AI writing tools is not penalized by itself, but responses, presentations, or papers that lack originality or critical thinking will be. **Using AI to generate images is prohibited.** As with professional practice, you are accountable for any inaccuracies in your reports, presentations, or code — "the AI hallucinated" is not an excuse.

**Community values.** The course affirms UC Berkeley's statements on community values and protections against bullying, harassment, and violence. Development Engineering succeeds in building more equitable societies only when the communities impacted by inequity and injustice are represented in design and decision-making.

**Disabled Students' Program (DSP).** If you require access accommodations, contact the [DSP](https://dsp.berkeley.edu/) and request that accommodation letters be sent to the instructor and GSI.

**Additional support & resources.**
- [University Health Services — Tang Center](https://uhs.berkeley.edu/)
- [Mental Health Counseling](https://uhs.berkeley.edu/student-mental-health)
- [Off-Campus Rental Services](https://och.berkeley.edu/) · [Emergency Housing](https://basicneeds.berkeley.edu/get-support/housing)
- [Food — Immediate Need (Pantry)](https://basicneeds.berkeley.edu/pantry) · [CalFresh](https://basicneeds.berkeley.edu/calfresh)

---

## License

Released under the **BSD 3-Clause License**. Copyright © 2026, Mark Campmier. See [`LICENSE`](LICENSE) for details.

---

*This README summarizes the course syllabus for orientation. If anything here conflicts with the official syllabus or the course webpage, the official syllabus governs.*
