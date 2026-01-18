# Titanic Survival Analysis

Exploratory data analysis (EDA) and visualization on the Kaggle Titanic dataset to understand how **age**, **sex**, **passenger class**, **fare**, and **cabin deck (level)** relate to survival outcomes. [file:16]

---

## Project story

The sinking of the RMS Titanic (1912) is a classic real-world example where survival was not random. [file:16]  
This notebook explores which passenger groups were more likely to survive by combining data cleaning, simple feature engineering, and visual analysis. [file:16]

---

## Dataset

- Source: Kaggle “Titanic - Machine Learning from Disaster”. [file:16]
- Target column: `Survived` (1 = survived, 0 = did not survive). [file:16]
- Key fields used: `Age`, `Fare`, `Sex`, `Pclass`, `Cabin`. [file:16]

---

## Objectives

- Inspect data quality and handle missing values (especially `Age`). [file:16]
- Explore how `Age` and `Fare` relate to survival, split by `Sex`. [file:16]
- Compare `Fare` distributions across `Pclass` and `Sex`. [file:16]
- Compare survival rates across `Pclass` and `Sex`. [file:16]
- Create a simple “deck/level” feature from `Cabin` and analyze survival patterns by deck (with a focus on first class and Deck A). [file:16]

---

## Approach (what was done)

### 1) Data loading & basic inspection
The dataset is loaded and basic checks are performed to understand missing values and column types before analysis. [file:16]

### 2) Missing value handling (Age)
Two imputation strategies for `Age` are compared: [file:16]
- `fillna(mean(Age))`: fills missing ages with the column mean. [file:16]
- `ffill`: forward-fills missing ages using the previous observed value. [file:16]

**Observation:** Mean-imputation concentrates ages around the center, which can make the distribution look more “peaked” and can increase outliers on both sides of a boxplot, while `ffill` typically spreads values based on existing neighboring entries and may produce fewer outliers. [file:16]

### 3) Exploratory analysis & visualizations
The notebook uses common EDA plots (scatterplots, boxplots, barplots) to answer questions such as: [file:16]
- Is `Age` correlated with `Fare`? [file:16]
- Do passengers who paid more have a better chance of survival, and does this differ by `Sex`? [file:16]
- How does `Fare` vary across `Pclass` and `Sex`? [file:16]
- How does survival rate change across `Pclass` for different sexes? [file:16]

### 4) Children vs adults
A separate analysis is performed for passengers under a child threshold (e.g., `Age < 14`) to compare survival patterns across passenger classes and sex. [file:16]

### 5) Deck (Cabin level) feature engineering
Rows with missing `Cabin` are removed for this part, then the first character of `Cabin` is used as a “Level/Deck” feature (A, B, C, ...). [file:16]  
Deck-level statistics are explored (e.g., average fare and survival rate by deck), with extra attention to first class and Deck A (noted in the notebook as the lifeboat deck). [file:16]

---

## Key findings (from the notebook)

- **Age vs Fare:** Age does not show a strong correlation with fare in the plots. [file:16]
- **Fare vs survival:** Higher fares broadly align with higher survival probability, especially among females; for males the evidence is weaker and the pattern is not consistently strong. [file:16]
- **Sex & class effect:** Survival rate is generally higher for females than for males across classes, and female survival tends to increase with higher passenger class. [file:16]
- **Children:** In the notebook’s subset analysis, survival patterns for children vary by class, and the reliability can be affected by missing values (notably in `Age` and/or `Survived` subsets). [file:16]
- **Deck analysis:** Creating a deck/level feature from `Cabin` allows a deeper look into location-related survival differences, and deck composition (including gender mix) can help explain observed survival rates on certain decks (e.g., Deck A). [file:16]

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
