Linear regression is a branch of [[Regression Analysis|regression]] used within [[Machine Learning|machine learning]] as to create models that predict data based upon a linear [[Relations|relation]]. These models can be used to find a rule that designates a **hyperplane** that allows for prediction. This rule is found through a minimization of the associated error called the **error term**. This term can be written as:
$$Error= \sum actual-prediction$$
This is used to find a [[Linear Equations|linear equation]] which satisfies this minimised [[Functions|function]]. This will usually result in the creation of a simple linear model: 
$$E[Y|x]=\hat y=f(x)=\beta_0+\beta_1x$$
Where $\beta_0$ is called the intercept, and $\beta_0$ is called the **regression coefficient**. This model can be expanded to a **multiple regression model** which uses multiple predictors. This uses $x_{i,j}$ to denote the predictors $j$ for an individual $i$. This can be written as: 
$$E[Y_i|x_{i,1},\dots,x_{i,p}]=\hat y=B_0+\sum_{j=1}^p\beta_jx_{i,j}$$
Treating all coefficients as a vector $\beta=(\beta_1,\dots,\beta_p)$, and all variable/predictors as a vector $x_j=(x_{1,j},\dots,x_{n,j})$ we can take all $p$ vectors to form a single matrix of predictors: 
$$X=(x_1',x_2',\dots,x_n')=\begin{bmatrix}x_{1,1}&x_{1,2}&\cdots&x_{1,p}\\x_{2,1}&x_{2,2}&\cdots&x_{2,p}\\\vdots&\vdots&\ddots&\vdots\\x_{n,1}&x_{n,2}&\cdots&x_{n,p}\\\end{bmatrix}$$
This is called the **design matrix**. Using this matrix we can write an expression for the prediction $\hat y=X\beta+\beta_01_n$, where $1_n$ denotes a vector of $n$ ones.

# Principle of Least Squares
Given a linear model with parameters $\beta$ a residual error $e_i$ can be calculated for each observation of $y_i$ and predictions $\hat y_i$.   
$$\text{RSS}(\beta)=\sum_{i=1}^N (y_i -b_0-\sum_{j=1}^p\beta_jx_{i,j})^2$$
This measures the goodness-of-fit of a linear model. The principle of least squares further says that the "best" estimate of all coefficients for a linear model. Therefore: 
$$(\hat\beta_0,\hat\beta_1,\dots,\hat\beta_p)=\arg\min_{\beta_0,\beta_1,\dots,\beta_p}\{RSS(\beta_0,\beta_1,\dots,\beta_p)\}$$

# $R^2$ Value
While the residual sum-of-squares provides a way to fit the data it doesn't provide a scale of measurement for how good a model is compared to others. The $R^2$ value does this by finding the ratio of RSS to TSS. Where the total sum-of-squares is found using the mean of the data $\bar y$  to find: 
$$\text{TSS}=\sum_{i=1}^n(y_i-\bar y)^2$$
This allows the $R^2$ value to be defined as: 
$$R^2=1-\frac{\text{RSS}}{\text{TSS}}$$

# Extensions
Linear regression models can easily be modified to represent a variety of different problems.

## Categorical Predictors
Categorical predictors are the result of certain predictors being categorical rather than continuous. To find a categorical predictor first encode categorical variables as numbers. This can then be transformed by creating $K-1$ new predictors where $K$ is the number of different categories the variable can take. For example for a predictor with $4$ categories three new columns are added with each one being $0$ or $1$ if the value is of that category.

## Nonlinear Effects
When nonlinear predictors are used it is a common method to transform the data into a linear form as to use linear regression techniques. Some common transformations are:
- **Logarithmic transformations** which are used if a predictor has a higher variance when the predictor takes on larger values. This scales the ratios. The transformation is defined as $x_{i,j}\Rightarrow\log x_{i,j}$, and is valid if all $x_i>0$. 
- **Polynomial transformations** offer a general purpose approach to nonlinear data fitting. This transformation is defined as $x_{i,j}\Rightarrow x_{i,j},x_{i,j}^2,\dots,x_{i,j}^q$, where $q$ is the maximum order of polynomial used, with greater $q$'s suffering from overfitting.


