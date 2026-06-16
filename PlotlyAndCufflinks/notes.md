# Plotly and Cufflinks

## Imports and Setup

```python
import seaborn as sns
import pandas as pd
import cufflinks as cf
import plotly.express as px
from plotly.offline import iplot

cf.go_offline()
cf.set_config_file(offline=True)

tips = sns.load_dataset('tips')
tips.head()
```

---

# Version Check

```python
import cufflinks as cf
import plotly
import sys

print("Cufflinks:", cf.__version__)
print("Plotly:", plotly.__version__)
print("Python:", sys.version)
```

### Note

Cufflinks is not fully compatible with newer Plotly versions (6.x). Therefore, some `.iplot()` functions may throw errors. Modern Plotly Express alternatives are provided below.

---

# 1. Line Plot

## Cufflinks

```python
tips['total_bill'].iplot()
```

## Plotly Express Alternative

```python
fig = px.line(
    tips,
    y='total_bill',
    title='Total Bill'
)

fig.show()
```

### Purpose

- Shows trends in data
- Useful for time-series visualization

---

# 2. Bar Plot

## Cufflinks

```python
tips.groupby('day')['tip'].mean().iplot(kind='bar')
```

## Plotly Express Alternative

```python
avg_tip = tips.groupby('day')['tip'].mean().reset_index()

fig = px.bar(
    avg_tip,
    x='day',
    y='tip',
    title='Average Tip by Day'
)

fig.show()
```

### Purpose

- Compare categories
- Find highest and lowest values

### Question Answered

Which day has the highest average tip?

---

# 3. Scatter Plot

## Cufflinks

```python
tips.iplot(
    kind='scatter',
    x='total_bill',
    y='tip',
    mode='markers'
)
```

## Plotly Express Alternative

```python
fig = px.scatter(
    tips,
    x='total_bill',
    y='tip',
    title='Total Bill vs Tip'
)

fig.show()
```

### Purpose

- Analyze relationship between variables
- Detect correlation and outliers

### Question Answered

Do customers who spend more generally tip more?

---

# 4. Box Plot

## Cufflinks

```python
tips[['total_bill','tip']].iplot(kind='box')
```

## Plotly Express Alternative

```python
fig = px.box(
    tips,
    x='day',
    y='total_bill',
    title='Total Bill Distribution by Day'
)

fig.show()
```

## Seaborn Alternative

```python
sns.boxplot(
    x='day',
    y='total_bill',
    data=tips
)
```

### Purpose

- Visualize distribution
- Detect outliers
- Compare categories

### Question Answered

On which day do customers spend the most?

---

# Summary

| Plot | Purpose |
|--------|---------|
| Line Plot | Trends |
| Bar Plot | Category Comparison |
| Scatter Plot | Relationship Analysis |
| Box Plot | Distribution and Outliers |

---

# Learning Outcome

✅ Learned Cufflinks syntax

✅ Learned modern Plotly Express alternatives

✅ Created interactive visualizations

✅ Compared Cufflinks and Plotly approaches

✅ Understood when to use each plot type