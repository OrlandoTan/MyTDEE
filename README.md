# Estimating Personal TDEE from Self-Tracked Nutrition and Bodyweight Data

**By Orlando Dylan Tan**

---

## The Problem

Generic calorie calculators like the Mifflin-St Jeor formula are the standard starting point for dieting. In practice, they rarely reflect individual reality. During my first weeks of dieting I was eating on an aggressively low deficit, not because I wanted to, but because I had no reliable estimate of my own maintenance calories. This project is the data-driven answer to that uncertainty.

## What I Did

Over 95 days I logged my daily bodyweight, calorie intake, macronutrients (protein, carbs, fat), step count, sleep, and gym attendance. Using that dataset I:

- Derived a personalised TDEE estimate from observed energy balance trends
- Engineered lag and rolling average features to account for the delayed physiological response to food intake
- Analysed which variables best explain short-term weight fluctuations beyond calorie balance
- Applied Ridge and Lasso regularised regression with time-series cross-validation to model unexplained (residual) weight change

## Key Findings

| Metric | Value |
| :-- | :-- |
| Personal TDEE (data-derived) | **2,481 kcal/day** |
| Mifflin-St Jeor estimate | 2,697 kcal/day |
| Difference from formula | −216 kcal/day |
| Average weekly weight loss | **0.56 kg/week** |
| Total weight lost | 7.4 kg |
| Carbohydrate effect on scale | ~0.064 kg per 100g (next-day) |

The data-derived TDEE sits **216 kcal below** the formula estimate, a gap large enough to meaningfully affect whether a given day produces a deficit or not. Carbohydrate intake emerged as the single most consistent driver of short-term scale weight fluctuation across every analytical approach used, ranging from correlation analysis, scatter plots, distributions, and the machine learning models.

## Limitations

The dataset is self-collected, relatively small (95 observations), and spans two meaningfully different dietary phases, a structured deficit and a two-week vacation to Indonesia where I was eating whatever I wanted. This behavioral regimes limits the ability to isolate individual variable effects and contributes to the model's failure to generalise beyond training data. These limitations are acknowledged and discussed throughout the notebook.

## What I used

`Python`, `Pandas`, `NumPy`, `Matplotlib`, `Scikit-learn`, `Jupyter`

## File Structure

```
MyTDEE.ipynb     # Main analysis notebook
WeightData.csv   # Raw self-tracked dataset
```
