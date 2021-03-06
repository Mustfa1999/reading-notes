# Reading: Class 13

> [Back to the main](./README.md)

---

## What Is Regression?

Regression searches for relationships among variables.

For example, you can observe several employees of some company and try to understand how their salaries depend on the features, such as experience, level of education, role, city they work in, and so on.

This is a regression problem where data related to each employee represent one observation. The presumption is that the experience, education, role, and city are the independent features, while the salary depends on them.

Similarly, you can try to establish a mathematical dependence of the prices of houses on their areas, numbers of bedrooms, distances to the city center, and so on.

Generally, in regression analysis, you usually consider some phenomenon of interest and have a number of observations. Each observation has two or more features. Following the assumption that (at least) one of the features depends on the others, you try to establish a relation among them.

In other words, you need to find a function that maps some features or variables to others sufficiently well.

The dependent features are called the dependent variables, outputs, or responses.

The independent features are called the independent variables, inputs, or predictors.

Regression problems usually have one continuous and unbounded dependent variable. The inputs, however, can be continuous, discrete, or even categorical data such as gender, nationality, brand, and so on.

It is a common practice to denote the outputs with ๐ฆ and inputs with ๐ฅ. If there are two or more independent variables, they can be represented as the vector ๐ฑ = (๐ฅโ, โฆ, ๐ฅแตฃ), where ๐ is the number of inputs.

---

## Simple Linear Regression
Simple or single-variate linear regression is the simplest case of linear regression with a single independent variable

The estimated regression function has the equation ๐(๐ฅ) = ๐โ + ๐โ๐ฅ. Your goal is to calculate the optimal values of the predicted weights ๐โ and ๐โ that minimize SSR and determine the estimated regression function. The value of ๐โ, also called the intercept, shows the point where the estimated regression line crosses the ๐ฆ axis. It is the value of the estimated response ๐(๐ฅ) for ๐ฅ = 0. The value of ๐โ determines the slope of the estimated regression line.

The predicted responses are the points on the regression line that correspond to the input values. For example, for the input ๐ฅ = 5, the predicted response is ๐(5) = 8.33 (represented with the leftmost red square).

The residuals can be calculated as ๐ฆแตข - ๐(๐ฑแตข) = ๐ฆแตข - ๐โ - ๐โ๐ฅแตข for ๐ = 1, โฆ, ๐. They are the distances between the green circles and red squares. When you implement linear regression, you are actually trying to minimize these distances and make the red squares as close to the predefined green circles as possible.

--- 

## Multiple Linear Regression

Multiple or multivariate linear regression is a case of linear regression with two or more independent variables.

If there are just two independent variables, the estimated regression function is ๐(๐ฅโ, ๐ฅโ) = ๐โ + ๐โ๐ฅโ + ๐โ๐ฅโ. It represents a regression plane in a three-dimensional space. The goal of regression is to determine the values of the weights ๐โ, ๐โ, and ๐โ such that this plane is as close as possible to the actual responses and yield the minimal SSR.

---

## Underfitting and Overfitting

One very important question that might arise when youโre implementing polynomial regression is related to the choice of the optimal degree of the polynomial regression function.

There is no straightforward rule for doing this. It depends on the case. You should, however, be aware of two problems that might follow the choice of the degree: underfitting and overfitting.

Underfitting occurs when a model canโt accurately capture the dependencies among data, usually as a consequence of its own simplicity. It often yields a low ๐ยฒ with known data and bad generalization capabilities when applied with new data.

Overfitting happens when a model learns both dependencies among data and random fluctuations. In other words, a model learns the existing data too well. Complex models, which have many features or terms, are often prone to overfitting. When applied to known data, such models usually yield high ๐ยฒ. However, they often donโt generalize well and have significantly lower ๐ยฒ when used with new data.

---

## Implementing Linear Regression in Python

```
import numpy as np
from sklearn.linear_model import LinearRegression

# provid data
x = np.array([5, 15, 25, 35, 45, 55]).reshape((-1, 1))
y = np.array([5, 20, 14, 32, 22, 38])

# Create a model and fit it
model = LinearRegression()
model.fit(x, y)
model = LinearRegression().fit(x, y)

# Get results
model.score(x, y)

# Predict response
model.predict(x)

# Predict response over linear regression
model.intercept_ + model.coef_ * x

```




