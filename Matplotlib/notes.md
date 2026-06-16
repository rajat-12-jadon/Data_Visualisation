# 📊 Matplotlib Notes

## What is Matplotlib?

Matplotlib is a Python library used for creating static, animated, and interactive visualizations. It is one of the most widely used libraries for data visualization in Python.

### Importing Matplotlib

```python
import matplotlib.pyplot as plt
```

---

# 1. Basic Plotting

The `plot()` function is used to create line graphs.

```python
plt.plot(x, y)
plt.title("Graph Title")
plt.xlabel("X-Axis")
plt.ylabel("Y-Axis")
```

### Common Functions

| Function       | Purpose          |
| -------------- | ---------------- |
| `plt.plot()`   | Create line plot |
| `plt.title()`  | Add title        |
| `plt.xlabel()` | Label x-axis     |
| `plt.ylabel()` | Label y-axis     |

---

# 2. Subplots

Subplots allow multiple graphs in the same figure.

```python
plt.subplot(rows, columns, position)
```

Example:

```python
plt.subplot(2,2,1)
plt.plot(x,y)
```

Meaning:

* 2 rows
* 2 columns
* Graph placed at position 1

---

# 3. Object-Oriented Interface

Preferred method for creating professional visualizations.

### Create Figure

```python
fig = plt.figure(figsize=(20,8), dpi=100)
```

### Add Axes

```python
ax = fig.add_axes([0.1,0.1,0.8,0.8])
```

### Plot

```python
ax.plot(x,y)
```

### Advantages

* Better control over plots
* Easier customization
* Suitable for complex visualizations

---

# 4. Figure Size and DPI

### Figure Size

```python
fig = plt.figure(figsize=(10,5))
```

### DPI (Dots Per Inch)

```python
fig = plt.figure(dpi=100)
```

Higher DPI produces better image quality.

---

# 5. Scatter Plot

Used to show relationships between two variables.

```python
plt.scatter(x,y)
```

Applications:

* Correlation analysis
* Data distribution
* Outlier detection

---

# 6. Histogram

Used to visualize data distribution.

```python
plt.hist(data)
```

Applications:

* Frequency analysis
* Distribution analysis
* Data spread visualization

---

# 7. Box Plot

Used to identify spread and outliers.

```python
plt.boxplot(data)
```

Shows:

* Minimum
* Maximum
* Median
* Quartiles
* Outliers

---

# 8. Saving Plots

Save plots as image files.

```python
plt.savefig("plot.png")
```

Common formats:

* PNG
* JPG
* PDF

---

# 9. Working with Images

### Read Image

```python
import matplotlib.image as mpimg

img = mpimg.imread("image.jpg")
```

### Display Image

```python
plt.imshow(img)
```

### Remove Axes

```python
plt.axis("off")
```

---

# 10. Image Cropping

Crop specific portions of an image.

```python
cropped_img = img[50:200, 100:300]
```

Syntax:

```python
img[row_start:row_end, col_start:col_end]
```

Display:

```python
plt.imshow(cropped_img)
```

---

# 11. Plot Customization

## Colors

```python
plt.plot(x,y,color="red")
```

## Line Width

```python
plt.plot(x,y,linewidth=2)
```

## Line Style

```python
plt.plot(x,y,linestyle="--")
```

Common styles:

* `-` Solid
* `--` Dashed
* `-.` Dash-dot
* `:` Dotted

---

# 12. Markers

Markers highlight data points.

```python
plt.plot(x,y,marker='o')
```

Examples:

| Marker | Symbol |
| ------ | ------ |
| `'o'`  | Circle |
| `'+'`  | Plus   |
| `'*'`  | Star   |
| `'s'`  | Square |

---

# 13. Marker Customization

```python
plt.plot(
    x,
    y,
    marker='o',
    markersize=8,
    markerfacecolor='red',
    markeredgecolor='black'
)
```

---

# Key Functions Practiced

```python
plt.plot()
plt.scatter()
plt.hist()
plt.boxplot()

plt.subplot()
plt.subplots()

plt.figure()
fig.add_axes()

plt.title()
plt.xlabel()
plt.ylabel()

plt.savefig()

plt.imshow()
plt.axis()

mpimg.imread()
```

---

# Learning Outcome

After completing Matplotlib fundamentals, you should be able to:

* Create basic visualizations
* Use subplots effectively
* Work with the Object-Oriented interface
* Customize plots professionally
* Save visualizations
* Display and crop images
* Prepare for advanced visualization libraries such as Seaborn and Plotly
