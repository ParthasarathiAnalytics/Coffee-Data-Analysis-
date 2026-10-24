# Exploratory Data Analysis of Coffee Quality ☕

**A Python-based exploratory data analysis project investigating the
factors associated with coffee quality.**

**Author:** Parthasarathi A\
**Course:** Data Analytics & Data Science\
**Project:** Exploratory Affecting Factors of Coffee Quality

------------------------------------------------------------------------

## 📌 Project Overview

Coffee quality varies with bean characteristics, growing conditions,
processing methods, and sensory attributes. This project explores a
Coffee Quality dataset to understand how sensory scores and farm/bean
metadata relate to overall cup quality.

The analysis uses Python for data cleaning, feature engineering,
exploratory data analysis (EDA), visualization, descriptive statistics,
and hypothesis testing. It focuses on attributes such as Aroma, Flavor,
Aftertaste, Acidity, Body, Balance, Moisture, and Total Cup Points,
alongside Species, Processing Method, Country of Origin, and altitude
information.

> **Scope note:** This README is based on the project documentation
> supplied with this repository. Exact dataset size, source URL, and
> some hypothesis-test output values were not specified in that
> documentation.

## 🎯 Objectives

-   Explore the factors associated with coffee quality and Total Cup
    Points.
-   Clean missing, inconsistent, and irrelevant data.
-   Standardize bag-weight and bag-count fields.
-   Create altitude-derived features for further analysis.
-   Compare sensory scores across coffee species and processing methods.
-   Investigate relationships between species, processing methods, and
    countries of origin.
-   Communicate findings through statistical summaries and
    visualizations.
-   Develop practical recommendations for coffee growers, buyers, and
    quality teams.

## 🧩 Business Problem

Coffee producers, exporters, and buyers need to understand which
characteristics are associated with higher-quality coffee. Without
systematic analysis, decisions about cultivation, processing, and
quality control may rely on assumptions.

This project examines the available sensory ratings and production
metadata to identify useful patterns and relationships. The findings can
support further investigation and quality-management decisions;
observational relationships should not be interpreted as proof of
causation.

## 🛠️ Tools and Technologies

-   **Python**
-   **Pandas** --- data cleaning, transformation, grouping, and analysis
-   **NumPy** --- numerical operations
-   **Matplotlib** --- charts and plots
-   **Seaborn** --- statistical visualizations and heatmaps
-   **SciPy (`scipy.stats`)** --- hypothesis testing
-   **Jupyter Notebook** --- interactive analysis workflow

## 📂 Dataset Overview

The dataset documentation describes three broad groups of fields.

### Sensory and quality attributes

-   Aroma
-   Flavor
-   Aftertaste
-   Acidity
-   Body
-   Balance
-   Uniformity
-   Cup Cleanliness
-   Sweetness
-   Moisture
-   Defects
-   Total Cup Points

### Bean metadata

-   Species (for example, Arabica and Robusta)
-   Processing Method
-   Colour
-   Bag Weight
-   Number of Bags

### Farm and origin metadata

-   Owner
-   Country of Origin
-   Farm Name
-   Lot Number
-   Mill
-   Company
-   Altitude low and high measurements
-   Region

The exact number of rows, number of columns, and original dataset source
should be added once confirmed from the actual dataset file.

## 🔄 Project Workflow

1.  Load and inspect the data.
2.  Review data types, non-null counts, and missing values.
3.  Clean missing values and standardize formats.
4.  Remove irrelevant or redundant columns.
5.  Detect and handle numeric outliers using the IQR method.
6.  Create derived altitude features.
7.  Perform descriptive statistical analysis.
8.  Conduct univariate, bivariate, and multivariate EDA.
9.  Apply selected hypothesis tests.
10. Summarize findings, limitations, and recommendations.

## 🧹 Data Cleaning and Preparation

The project documentation describes the following preparation steps:

-   **Missing values:** inspected null values; imputed missing
    `Number.of.Bags` values using the median and converted the column to
    nullable `Int64`.
-   **Bag weight:** extracted numeric values from `Bag.Weight` and
    converted them to a floating-point type.
-   **Column selection:** removed unnamed columns and selected
    non-essential certification or metadata columns.
-   **Outliers:** used the Interquartile Range (IQR) rule on numeric
    columns.
-   **Derived features:** calculated altitude range and average altitude
    from low/high altitude measurements.
-   **Cleaned output:** the notebook documentation shows the cleaned
    data being saved as `coffeequality_cleaned.csv`.

**Reproducibility note:** Removing outliers from every numeric column
can also remove valid observations. For a production analysis, review
outliers by variable and business context, and compare results before
and after treatment. Avoid using a derived feature unless both source
columns are available and valid.

## 🧮 Feature Engineering

  ------------------------------------------------------------------------------------------------------
  Derived field             Calculation / treatment                              Purpose
  ------------------------- ---------------------------------------------------- -----------------------
  `altitude_range_meters`   `altitude_high_meters - altitude_low_meters`         Represents the recorded
                                                                                 altitude range

  `altitude_avg_meters`     `(altitude_low_meters + altitude_high_meters) / 2`   Represents the midpoint
                                                                                 of the recorded
                                                                                 altitude range

  Standardized `Bag.Weight` Extract numeric component and convert to float       Enables consistent
                                                                                 numeric analysis

  Standardized              Median imputation followed by nullable integer       Supports analysis where
  `Number.of.Bags`          conversion                                           bag counts are missing
  ------------------------------------------------------------------------------------------------------

## 📊 Exploratory Data Analysis

### 1. Univariate analysis

The project examined individual variables using descriptive statistics,
histograms, boxplots, bar charts, and pie charts.

Areas explored: - Distribution and spread of sensory scores. - Potential
extreme values in numeric attributes. - Sample distribution by species,
processing method, and country of origin.

The project documentation reports that Arabica represented the larger
share of the dataset and that most sensory scores were relatively high.
Exact sample counts and proportions were not provided.

### 2. Bivariate analysis

The project compared pairs of variables using scatter plots, boxplots,
and categorical comparisons.

Examples include: - Aroma versus Total Cup Points. - Flavor and other
sensory scores versus Total Cup Points. - Species versus Total Cup
Points. - Processing Method versus Aroma. - Species and Processing
Method across countries of origin.

The documented scatter plot shows a positive relationship between Aroma
and Total Cup Points. The analysis also reports positive relationships
for Flavor and other sensory attributes.

### 3. Multivariate analysis

A correlation heatmap and pairwise plots were used to examine
relationships among several quality measures together.

The documentation reports positive correlations among Aroma, Flavor,
Aftertaste, Acidity, Body, Balance, and Total Cup Points. Moisture had a
weak negative correlation with Total Cup Points in the displayed heatmap
(approximately **-0.19**). Correlation indicates association, not
causation.

## 🧪 Statistical Analysis

The project documentation describes descriptive statistics and three
hypothesis-testing approaches.

### Descriptive statistics

Mean, median, standard deviation, minimum, maximum, and quartiles were
used to summarize numeric attributes.

The documentation gives approximate examples: - Aroma mean:
approximately **7.3** - Aroma median: approximately **7.4** - Total Cup
Points mean: approximately **82** - Total Cup Points median:
approximately **82.5**

These are reported approximate values, not a guarantee that every rerun
will reproduce them after data cleaning.

### Species versus Total Cup Points

-   **Test described:** t-test comparing Arabica and Robusta.
-   **Reported p-value:** **0.0621**
-   **Significance threshold:** (`\alpha `{=tex}= 0.05)
-   **Interpretation:** Since 0.0621 is greater than 0.05, the
    documented result does not establish a statistically significant
    difference in mean Total Cup Points between the two species at the
    5% level.

### Processing Method versus Aroma

-   **Test described:** one-way ANOVA.
-   **Reported p-value:** **0.9713**
-   **Significance threshold:** (`\alpha `{=tex}= 0.05)
-   **Interpretation:** Since 0.9713 is greater than 0.05, the
    documented result does not establish a statistically significant
    difference in mean Aroma scores across processing methods at the 5%
    level.

### Species versus Country of Origin

-   **Test described:** Chi-square test of independence.
-   **Purpose:** Examine whether species and country of origin are
    associated.
-   **Decision rule:** Compare the test p-value with 0.05.
-   **Result limitation:** The documentation describes this relationship
    as significant but does not provide the exact p-value or test
    statistic in the extracted results. Re-run the notebook to report
    the verified value.

The documentation also discusses a paired t-test comparing Aroma and
Flavor. Its result fields appear as placeholders, so no specific p-value
or conclusion is asserted here.

## 🔍 Key Findings Documented in the Project

1.  **Sensory attributes are closely related to overall cup scores.**
    Aroma, Flavor, Aftertaste, and Balance are reported as positively
    correlated with Total Cup Points.
2.  **No statistically significant species difference was reported.**
    The documented comparison has a p-value of 0.0621, above the 0.05
    threshold.
3.  **No statistically significant Aroma difference across processing
    methods was reported.** The documented ANOVA p-value is 0.9713.
4.  **Moisture showed a weak relationship with Total Cup Points** in the
    displayed correlation heatmap.
5.  **Species and processing methods show geographic patterns** in the
    dataset, according to the project documentation. These patterns
    describe the available sample and should not automatically be
    generalized to all coffee production.
6.  **Data cleaning and standardization were important preparation
    steps** before visualization and statistical testing.

## 💡 Business Recommendations

-   **Monitor sensory attributes:** Track Aroma, Flavor, Aftertaste, and
    Balance as part of quality evaluation.
-   **Avoid relying on species alone:** The documented test did not find
    a statistically significant difference in mean cup points between
    Arabica and Robusta.
-   **Avoid assuming processing method determines Aroma:** The
    documented ANOVA did not find a significant mean difference.
    Consider additional farm, environmental, and handling variables.
-   **Strengthen data quality controls:** Standardize units, document
    missing-value decisions, and validate unusual measurements.
-   **Investigate growing conditions:** Explore altitude, climate, soil,
    and farm practices in a follow-up analysis.
-   **Validate before operational decisions:** Re-run tests on the final
    cleaned dataset and report sample sizes, effect sizes, confidence
    intervals, and exact p-values.

## ⚠️ Limitations and Next Steps

-   The supplied documentation does not state the exact dataset size or
    provide a verifiable dataset source URL.
-   Some statistical outputs in the documentation are placeholders
    rather than numeric results.
-   Outlier removal may affect distributions and statistical
    conclusions; compare analyses with and without this step.
-   Correlation does not demonstrate causation.
-   The documented analysis is exploratory and does not establish that
    the observed relationships generalize to every coffee-growing
    region.

### Future work

-   Build a predictive model for Total Cup Points and evaluate it on
    held-out data.
-   Add more samples and processing methods.
-   Study changes across harvest seasons if time-series data is
    available.
-   Explore consumer preferences alongside expert sensory ratings.
-   Investigate additional environmental and farm-level variables.

## ▶️ How to Run the Project

1.  Clone or download this repository.
2.  Open the project notebook in Jupyter Notebook, JupyterLab, or Google
    Colab.
3.  Place the original dataset in the path expected by the notebook, or
    update the file path.
4.  Install the required libraries.
5.  Run the notebook cells in order.
6.  Review the generated charts, statistical outputs, and cleaned
    dataset.

Install the main dependencies:

``` bash
pip install pandas numpy matplotlib seaborn scipy jupyter
```

Start Jupyter Notebook:

``` bash
jupyter notebook
```

**Expected cleaned output documented by the project:**
`coffeequality_cleaned.csv`

> The notebook filename and original dataset filename were not specified
> in the supplied documentation. Update the instructions above if your
> repository uses different filenames or folders.

## 📁 Suggested Repository Structure

``` text
Coffee-Data-Analysis-/
├── README.md
├── <analysis-notebook>.ipynb
├── <original-dataset>.csv
└── coffeequality_cleaned.csv
```

This is a suggested structure; replace the placeholder filenames with
the actual files in your repository.

## 👤 Author

**Parthasarathi A**\
Data Analytics & Data Science

-   GitHub:
    [ParthasarathiAnalytics](https://github.com/ParthasarathiAnalytics)
-   Portfolio:
    [parthasarathi-analytics.vercel.app](https://parthasarathi-analytics.vercel.app/)

------------------------------------------------------------------------

*This project demonstrates a Python EDA workflow covering data
preparation, feature engineering, statistical analysis, visualization,
and business interpretation.*
