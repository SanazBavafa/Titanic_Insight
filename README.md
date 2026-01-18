# Titanic Survival Analysis

Exploratory data analysis (EDA) and visualization on the Kaggle Titanic dataset to understand how **age**, **sex**, **passenger class**, **fare**, and **cabin deck (level)** relate to survival outcomes.

---

## Project story

The sinking of the RMS Titanic (1912) is a classic real-world example where survival was not random.
This notebook explores which passenger groups were more likely to survive by combining data cleaning, simple feature engineering, and visual analysis.

---

## Dataset

- Source: Kaggle “Titanic - Machine Learning from Disaster” (https://www.kaggle.com/c/titanic).
- Target column: `Survived` (1 = survived, 0 = did not survive).
- Key fields used: `Age`, `Fare`, `Sex`, `Pclass`, `Cabin`.

---

## Objectives

- Inspect data quality and handle missing values (especially `Age`).
- Explore how `Age` and `Fare` relate to survival, split by `Sex`. 
- Compare `Fare` distributions across `Pclass` and `Sex`.
- Compare survival rates across `Pclass` and `Sex`.
- Create a simple “deck/level” feature from `Cabin` and analyze survival patterns by deck (with a focus on first class and Deck A).

---

## Approach (what was done)

### 1) Data loading & basic inspection
The dataset is loaded and basic checks are performed to understand missing values and column types before analysis.

### 2) Missing value handling (Age)
Two imputation strategies for `Age` are compared:
- `fillna(mean(Age))`: fills missing ages with the column mean.
- `ffill`: forward-fills missing ages using the previous observed value.

**Observation:** Mean-imputation concentrates ages around the center, which can make the distribution look more “peaked” and can increase outliers on both sides of a boxplot, while `ffill` typically spreads values based on existing neighboring entries and may produce fewer outliers.

### 3) Exploratory analysis & visualizations
The notebook uses common EDA plots (scatterplots, boxplots, barplots) to answer questions such as:
- Is `Age` correlated with `Fare`?
- Do passengers who paid more have a better chance of survival, and does this differ by `Sex`?
- How does `Fare` vary across `Pclass` and `Sex`?
- How does survival rate change across `Pclass` for different sexes?

### 4) Children vs adults
A separate analysis is performed for passengers under a child threshold (e.g., `Age < 14`) to compare survival patterns across passenger classes and sex.

### 5) Deck (Cabin level) feature engineering
Rows with missing `Cabin` are removed for this part, then the first character of `Cabin` is used as a “Level/Deck” feature (A, B, C, ...).  
Deck-level statistics are explored (e.g., average fare and survival rate by deck), with extra attention to first class and Deck A (noted in the notebook as the lifeboat deck).

---

## Key findings (from the notebook)

- **Age vs Fare:** Age does not show a strong correlation with fare in the plots.
- **Fare vs survival:** Higher fares broadly align with higher survival probability, especially among females; for males the evidence is weaker and the pattern is not consistently strong.
- **Sex & class effect:** Survival rate is generally higher for females than for males across classes, and female survival tends to increase with higher passenger class.
- **Children:** In the notebook’s subset analysis, survival patterns for children vary by class, and the reliability can be affected by missing values (notably in `Age` and/or `Survived` subsets).
- **Deck analysis:** Creating a deck/level feature from `Cabin` allows a deeper look into location-related survival differences, and deck composition (including gender mix) can help explain observed survival rates on certain decks (e.g., Deck A).
---

## Repository structure (recommended)

```text
titanic-survival-analysis-lab2/
  README.md
  notebooks/
    Group10_lab2.ipynb
  data/
    (optional) train.csv / titanic.csv
  .gitignore
  requirements.txt
