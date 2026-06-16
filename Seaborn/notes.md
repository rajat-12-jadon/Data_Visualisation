# 🎨 Seaborn Notes

## What is Seaborn?

Seaborn is a Python data visualization library built on top of Matplotlib.

While Matplotlib gives complete control over plots, Seaborn makes it easier to create beautiful and statistical visualizations with less code.

### Why Use Seaborn?

* Better looking plots by default
* Works directly with Pandas DataFrames
* Useful for Exploratory Data Analysis (EDA)
* Helps identify patterns, trends, and relationships in data

---

# 1. Distribution Plots

## What is a Distribution?

Distribution tells us how data is spread.

Questions it answers:

* Where do most values lie?
* Is the data symmetric?
* Are there outliers?
* Is the data normally distributed?

---

## Histplot

### Purpose

Used to visualize the distribution of a single numerical variable.

### Real Life Example

Suppose we have restaurant bills.

We want to know:

* What bill amount occurs most frequently?
* Do customers generally spend less or more?

### Code

```python
sns.histplot(df['total_bill'], bins=20, kde=True)
```

### Important Observation

* Bars represent frequency.
* KDE curve shows the overall shape of the distribution.
* Peaks indicate common values.

---

## Jointplot

### Purpose

Used to analyze the relationship between two numerical variables.

### Questions It Answers

* Does one variable affect another?
* Is there a positive or negative relationship?
* Are there any outliers?

### Example

```python
sns.jointplot(
    x='total_bill',
    y='tip',
    data=df,
    kind='scatter'
)
```

### Observation

Customers with larger bills generally leave larger tips.

---

### Jointplot with Regression

```python
sns.jointplot(
    x='total_bill',
    y='tip',
    data=df,
    kind='reg'
)
```

### Why Use It?

The regression line helps identify trends.

If the line moves upward:

* Positive correlation

If the line moves downward:

* Negative correlation

---

## Pairplot

### Purpose

Shows relationships between all numerical columns simultaneously.

### Why Is It Useful?

Instead of creating:

```text
A vs B
A vs C
B vs C
```

manually, Pairplot creates all combinations automatically.

### Code

```python
sns.pairplot(df)
```

### Best Use

Exploratory Data Analysis before Machine Learning.

### Observation

Helps quickly identify:

* Correlated features
* Outliers
* Clusters

---

## Rugplot

### Purpose

Displays every individual observation as a small line.

### Code

```python
sns.rugplot(df['tip'])
```

### Why Use It?

Shows exact locations of observations.

Useful for understanding data density.

---

# 2. Categorical Plots

Categorical plots are used when one variable contains categories.

Examples:

```text
Male / Female
Smoker / Non-Smoker
Monday / Tuesday / Wednesday
```

---

## Countplot

### Purpose

Counts occurrences of each category.

### Example

```python
sns.countplot(
    x='sex',
    hue='smoker',
    data=df
)
```

### Questions It Answers

* How many males?
* How many females?
* How many smokers?

### Real Life

Used for customer segmentation.

---

## Barplot

### Purpose

Shows an aggregated numerical value for each category.

### Default Behavior

Barplot shows the mean.

### Example

```python
sns.barplot(
    x='sex',
    y='total_bill',
    data=df
)
```

### Question It Answers

Who spends more on average?

* Male customers?
* Female customers?

---

### Custom Aggregations

```python
sns.barplot(
    x='sex',
    y='tip',
    data=df,
    estimator=np.sum
)
```

Possible aggregations:

* Mean
* Median
* Sum
* Count
* Maximum
* Minimum

---

## Boxplot

### Purpose

Visualize data distribution using quartiles.

### Questions It Answers

* What is the median?
* What is the spread?
* Are there outliers?

### Code

```python
sns.boxplot(
    x='tip',
    y='day',
    data=df
)
```

### Understanding the Box

* Middle Line → Median
* Box → Interquartile Range
* Whiskers → Data Range
* Dots → Outliers

### Real Life

Used heavily in Data Analysis and Statistics.

---

## Violinplot

### Purpose

Combination of:

* Boxplot
* Distribution Plot

### Code

```python
sns.violinplot(
    x='day',
    y='total_bill',
    data=df
)
```

### Why Use It?

Shows:

* Median
* Distribution Shape
* Density

More informative than Boxplot.

---

## Stripplot

### Purpose

Shows every observation.

### Code

```python
sns.stripplot(
    x='day',
    y='total_bill',
    data=df
)
```

### Limitation

Points may overlap.

---

## Swarmplot

### Purpose

Improved version of Stripplot.

### Code

```python
sns.swarmplot(
    x='day',
    y='total_bill',
    data=df
)
```

### Advantage

Points automatically adjust to avoid overlapping.

Makes distributions easier to understand.

---

# 3. Matrix Plots

Matrix plots help visualize relationships between multiple variables.

---

## Heatmap

### Purpose

Visualize correlation values.

### Code

```python
sns.heatmap(
    tips_corr.corr(),
    annot=True
)
```

### Understanding Correlation

```text
+1  → Strong Positive Correlation
0   → No Correlation
-1  → Strong Negative Correlation
```

### Example

total_bill vs tip

High positive correlation means:

Customers who spend more generally tip more.

---

### Why Heatmaps Matter?

Before Machine Learning:

We want to know:

* Which features are related?
* Which features are redundant?

Heatmaps answer these questions quickly.

---

## Clustermap

### Purpose

Groups similar variables together.

### Code

```python
sns.clustermap(
    tips_corr.corr()
)
```

### Use Case

Feature analysis and clustering.

---

## Pivot Table Heatmap

### Example

```python
pvt = flights.pivot_table(
    values='passengers',
    index='month',
    columns='year'
)

sns.heatmap(pvt)
```

### What Does It Show?

Passenger trends across:

* Months
* Years

### Real Life

Useful for:

* Sales Analysis
* Traffic Analysis
* Business Dashboards

---

# 4. Regression Plots

Regression plots show relationships between variables and fit a trend line.

---

## lmplot()

### Purpose

Visualize correlation and trend.

### Code

```python
sns.lmplot(
    x='total_bill',
    y='tip',
    data=tips
)
```

### Observation

If the line slopes upward:

Higher bill → Higher tip

---

## Using hue

```python
sns.lmplot(
    x='total_bill',
    y='tip',
    data=tips,
    hue='sex'
)
```

### Why Use hue?

Creates separate regression lines for categories.

Example:

* Male customers
* Female customers

---

## Custom Markers

```python
sns.lmplot(
    x='total_bill',
    y='tip',
    data=tips,
    hue='sex',
    markers=['o','v']
)
```

Makes categories visually distinguishable.

---

# Quick Revision

## Distribution Plots

| Plot      | Purpose                           |
| --------- | --------------------------------- |
| Histplot  | Distribution                      |
| Jointplot | Relationship between 2 variables  |
| Pairplot  | Relationships among all variables |
| Rugplot   | Individual observations           |

---

## Categorical Plots

| Plot       | Purpose                |
| ---------- | ---------------------- |
| Countplot  | Count categories       |
| Barplot    | Aggregated values      |
| Boxplot    | Quartiles + Outliers   |
| Violinplot | Distribution + Density |
| Stripplot  | Individual points      |
| Swarmplot  | Non-overlapping points |

---

## Matrix Plots

| Plot          | Purpose                   |
| ------------- | ------------------------- |
| Heatmap       | Correlation visualization |
| Clustermap    | Similarity grouping       |
| Pivot Heatmap | Pattern analysis          |

---

## Regression Plots

| Plot   | Purpose                   |
| ------ | ------------------------- |
| lmplot | Relationship + Trend Line |

---

# Learning Outcome

After completing Seaborn:

✅ Understand data distributions

✅ Analyze categorical data

✅ Detect correlations

✅ Perform visual EDA

✅ Understand feature relationships

✅ Prepare data for Machine Learning

✅ Create professional visualizations with minimal code
