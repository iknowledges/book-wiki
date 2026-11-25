# Chapter 3: Making Regression Make Sense

Chapter 3 covers the conditional expectation function, regression, inference, causal interpretation, matching, weighting, limited dependent variables, marginal effects, and regression to the mean. This file includes the chapter through its printed page 110, including the appendix opening on average-derivative weighting.

## 3.1 Regression Fundamentals

### 3.1.1 Economic Relationships and the Conditional Expectation Function

#### **Conditional expectation function**

The CEF for a dependent variable $y_i$, given a $k × 1$ vector of covariates $X_i$ (with elements $x_{ki}$), is the expectation, or population average, of $y_i$, with $X_i$ held fixed.

$$
\mathbb{E}[y_i\mid X_i=x]=\int t f_y(t\mid X_i=x)\,dt
\text{(for continuous }y_i);\\
\mathbb{E}[y_i\mid X_i=x]=\sum_t tP(y_i=t\mid X_i=x)
\text{(for discrete }y_i).
$$

> page 30

#### **Law of iterated expectations**

This law says that an unconditional expectation can be written as the unconditional average of the CEF.

$$
\mathbb{E}[y_i]=\mathbb{E}\!\left[\mathbb{E}[y_i\mid X_i]\right]
$$

> page 31

#### **CEF decomposition property**

$$
y_i=\mathbb{E}[y_i\mid X_i]+\varepsilon_i
$$

where (i) $\varepsilon_i$ is mean independent of $X_i$, that is, $E[\varepsilon_i\mid X_i]=0$, and therefore (ii) $\varepsilon_i$ is uncorrelated with any function of $X_i$.

> page 32

#### **CEF prediction property**

Let $m(X_i)$ be any function of $X_i$. The CEF solves

$$
\mathbb{E}[y_i\mid X_i]=\underset{m(X_i)}{\arg\min}\;\mathbb{E}\!\left[(y_i-m(X_i))^2\right],
$$

so it is the MMSE predictor of $y_i$ given $X_i$.

> page 33

#### **ANOVA theorem**

$$
V(y_i)=V\!\left(\mathbb{E}[y_i\mid X_i]\right)+\mathbb{E}\!\left[V(y_i\mid X_i)\right]
$$

where $V(\cdot)$ denotes variance and $V(y_i\mid X_i)$ is the conditional variance of $y_i$ given $X_i$.

> page 33

### 3.1.2 Linear Regression and the CEF

#### **Population regression coefficients**

This section is concerned with the vector of population regression coefficients, defined as the solution to a population least squares problem.

$$
\beta=\underset{b}{\arg\min}\;\mathbb{E}\!\left[(y_i-X_i'b)^2\right]=\mathbb{E}[X_iX_i']^{-1}\mathbb{E}[X_iy_i]
$$

> page 34

#### **Regression anatomy**

In the simple bivariate case where the regression vector includes only the single regressor, $x_i$, and a constant, the slope coefficient is

$$
\beta_1=\frac{\operatorname{Cov}(y_i,x_i)}{V(x_i)}
$$

In the multivariate case, with more than one nonconstant regressor, the slope coefficient for the kth regressor is given below:

$$
\beta_k=\frac{\operatorname{Cov}(y_i,\widetilde{x}_{ki})}{V(\widetilde{x}_{ki})}
$$

where $\widetilde{x}_{ki}$ is the residual from a regression of $x_{ki}$ on all the other covariates.

It shows us that each coefficient in a multivariate regression is the bivariate slope coefficient for the corresponding regressor after partialing out all the other covariates.

> page 35

#### **Linear CEF theorem (Regression Justification I)**

Suppose the CEF is linear. Then the population regression function is it.

$$
\mathbb{E}[y_i\mid X_i]=X_i'\beta^*\quad\Longrightarrow\quad \beta=\beta^*
$$

> page 37

#### **Best linear predictor theorem (Regression Justification II)**

The function $X_i'\beta$ is the best linear predictor of $y_i$ given $X_i$ in a MMSE sense.

> page 37

#### **Regression CEF theorem (Regression Justification III)**

The function $X_i'\beta$ provides the MMSE linear approximation to $E[y_i\mid X_i]$, that is,

$$
\beta=\underset{b}{\arg\min}\;\mathbb{E}\!\left[(\mathbb{E}[y_i\mid X_i]-X_i'b)^2\right]
$$

> page 38

### 3.1.3 Asymptotic OLS Inference

#### **Ordinary least squares estimator**


$$
\widehat{\beta}=\left(\sum_{i=1}^{N}X_iX_i'\right)^{-1}\sum_{i=1}^{N}X_iy_i
$$

Although we derived $\hat\beta$ as a method of moments estimator, it is called the OLS estimator of $\beta$ because it solves the sample analog of the least squares problem.

> page 42

#### **Law of large numbers**

Sample moments converge in probability to the corresponding population moments. In other words, the probability that the sample mean is close to the population mean can be made as high as you like by taking a large enough sample.

> page 43

#### **Central limit theorem**

Sample moments are asymptotically normally distributed (after subtracting the corresponding population moment and multiplying by the square root of the sample size). The asymptotic covariance matrix is given by the variance of the underlying random variable. In other words, in large enough samples, appropriately normalized sample moments are approximately normally distributed.

> page 43

#### **Slutsky’s theorem**

1. Consider the sum of two random variables, one of which converges in distribution (in other words, has an asymptotic distribution) and the other converges in probability to a constant: the asymptotic distribution of this sum is unaffected by replacing the one that converges to a constant by this constant. Formally, let $a_N$ be a statistic with an asymptotic distribution and let $b_N$ be a statistic with probability limit $b$. Then $a_N +b_N$ and $a_N +b$ have the same asymptotic distribution.
2. Consider the product of two random variables, one of which converges in distribution and the other converges in probability to a constant: the asymptotic distribution of this product is unaffected by replacing the one that converges to a constant by this constant. Formally, let $a_N$ be a statistic with an asymptotic distribution and let $b_N$ be a statistic with probability limit $b$. Then $a_N b_N$ and $a_N b$ have the same asymptotic distribution.

$$
a_N\xrightarrow{d}A,\quad b_N\xrightarrow{p}b\quad\Longrightarrow\quad a_N+b_N\xrightarrow{d}a_N+b,\qquad a_Nb_N\xrightarrow{d}a_Nb
$$

> page 43

#### **Continuous mapping theorem**

Probability limits pass through continuous functions. For example, the probability limit of any continuous function of a sample moment is the function evaluated at the corresponding population moment. Formally, the probability limit of $h(b_N)$ is $h(b)$, where $\text{plim } b_N = b$ and $h(\cdot)$ is continuous at $b$.

$$
b_N\xrightarrow{p}b,\quad h\text{ continuous at }b\quad\Longrightarrow\quad h(b_N)\xrightarrow{p}h(b)
$$

> page 44

#### **Delta method**

Consider a vector-valued random variable that is asymptotically normally distributed. Continuously differentiable scalar functions of this random variable are also asymptotically normally distributed, with covariance matrix given by a quadratic form with the covariance matrix of the random variable on the inside and the gradient of the function evaluated at the probability limit of the random variable on the outside. Formally, the asymptotic distribution of $h(b_N)$ is normal with covariance matrix $\nabla h(b)'\Omega\nabla h(b)$, where $\text{plim } b_N = b$, $h(\cdot)$ is continuously differentiable at $b$ with gradient $\nabla h(b)$, and $b_N$ has asymptotic covariance matrix $\Omega$.

$$
\sqrt{N}\bigl(h(b_N)-h(b)\bigr)\xrightarrow{d}\mathcal{N}\!\left(0,\nabla h(b)'\Omega\nabla h(b)\right)
$$

> page 44

#### **Consistent estimator**

An estimator is said to be consistent when it converges in probability to the target parameter.

$$
\widehat{\beta}\xrightarrow{p}\beta
$$

> page 44

#### **Heteroskedasticity-consistent standard errors**

$$
\mathbb{E}[X_iX_i']^{-1}\,\mathbb{E}[X_iX_i'e_i^2]\,\mathbb{E}[X_iX_i']^{-1} \quad (3.1.7)
$$
The theoretical standard errors used to construct t-statistics are the square roots of the diagonal elements of (3.1.7). In practice these standard errors are estimated by substituting sums for expectations and using the estimated residuals, $\hat{e}_i=y_i-X_i^{\prime}\hat\beta$ to form the empirical fourth moment matrix, $\sum[X_iX_i\hat{e}_i^2]/N$.

Asymptotic standard errors computed in this way are known as heteroskedasticity-consistent standard errors, White (1980a) standard errors, or Eicker-White standard errors, in recognition of Eicker’s (1967) derivation. They are also known as "robust" standard errors (e.g., in Stata).

> page 45

#### **Homoskedasticity**

Default standard errors are derived under a homoskedasticity assumption, specifically, that $E[e_i^2\mid X_i]=\sigma^2$, a constant.

> page 46

#### **Linear probability model (LPM)**

A linear probability model is any regression where the dependent variable is zero-one, that is, a dummy variable such as an indicator for labor force participation.

$$
y_i\in\{0,1\},\qquad \mathbb{E}[y_i\mid X_i]=P(y_i=1\mid X_i)=X_i'\beta
$$

> page 47

#### **Unbiasedness**

Unbiasedness of the OLS estimators means that $E[\hat{\beta}]=\beta$, a property that holds in a sample of any size and is stronger than consistency, which means only that we can expect $\hat{\beta}$ to be close to $β$ in large samples.

> page 47

### 3.1.4 Saturated Models, Main Effects, and Other Regression Talk

#### **Saturated regression model**

Saturated regression models are regression models with discrete explanatory variables, where the model includes a separate parameter for all possible values taken on by the explanatory variables.

Suppose that $s_i = 0,1,2,\dots,\tau$ . A saturated regression model for $s_i$ is
$$
y_i=\alpha+\sum_{j=1}^{\tau}\beta_j d_{ji}+\varepsilon_i,
$$
where $d_{ji}=\mathbf{1}[s_i=j]$ is a dummy variable indicating schooling level $j$, and $\beta_j$ is said to be the jth-level schooling effect.

> page 48

#### **Main effects and interaction term**

The coefficients on the dummies are known as main effects, while the product is called an interaction term.

$$
\mathbb{E}[y_i\mid x_{1i},x_{2i}]=\alpha+\beta_1x_{1i}+\gamma x_{2i}+\delta_1(x_{1i}x_{2i})
$$
a parameterization with two main effects and one interaction term.

> page 49

## 3.2 Regression and Causality

### 3.2.1 The Conditional Independence Assumption

#### **Conditional independence assumption**

The CIA asserts that conditional on observed characteristics, $X_i$, selection bias disappears.

$$
\{y_{0i},y_{1i}\}\perp c_i\mid X_i,\qquad y_{si}\perp s_i\mid X_i\;\text{ for all }s
$$

> page 54

#### **Potential outcomes for schooling**

We therefore use the individual-specific functional notation, $y_{si}\equiv f_i(s)$, to denote the potential earnings that person i would receive after obtaining s years of education.

$$
y_{si}=f_i(s),\qquad y_i=f_i(s_i)
$$

> page 55

### 3.2.2 The Omitted Variables Bias Formula

#### **Omitted variables bias formula**

The omitted variables bias (OVB) formula describes the relationship between regression estimates in models with different sets of control variables.

$$
\frac{\operatorname{Cov}(y_i,s_i)}{V(s_i)}=\rho+\gamma'\delta_{As}
$$

> page 59

### 3.2.3 Bad Control

#### **Bad controls**

Bad controls are variables that are themselves outcome variables in the notional experiment at hand. That is, bad controls might just as well be dependent variables too. Good controls are variables that we can think of as having been fixed at the time the regressor of interest was determined.

$$
\mathbb{E}[y_i\mid w_i=1,c_i=1]-\mathbb{E}[y_i\mid w_i=1,c_i=0]
=\mathbb{E}[y_{1i}-y_{0i}\mid w_{1i}=1]
+\left\{\mathbb{E}[y_{0i}\mid w_{1i}=1]-\mathbb{E}[y_{0i}\mid w_{0i}=1]\right\}
$$

> page 64

#### **Proxy control**

A second version of the bad control scenario involves proxy control, that is, the inclusion of variables that might partially control for omitted factors but are themselves affected by the variable of interest.

$$
a_{li}=\pi_0+\pi_1s_i+\pi_2a_i,\qquad \text{proxy-control coefficient on }s_i=\rho-\frac{\gamma\pi_1}{\pi_2}
$$

> page 66

## 3.3 Heterogeneity and Nonlinearity

### 3.3.1 Regression Meets Matching

#### **Matching estimator**

Matching estimators are appealingly simple: at bottom, matching amounts to covariate-specific treatment-control comparisons, weighted together to produce a single overall average treatment effect.

$$
\mathbb{E}[y_{1i}-y_{0i}\mid d_i=1]=\sum_x\delta_x\,P(X_i=x\mid d_i=1)
$$

> page 69

#### **Average treatment effect on the treated**

This tells us the difference between the average earnings of soldiers, $E[y_{1i}\mid d_i=1]$, an observable quantity, and the counterfactual average earnings they would have obtained if they had not served, $E[y_{0i}\mid d_i=1]$.

$$
\delta_{TOT}=\mathbb{E}[y_{1i}-y_{0i}\mid d_i=1]
$$

> page 70


#### **Average treatment effect**

$δ_TOT$ tells us how much the typical soldier gained or lost as a consequence of military service, while $δ_ATE$ tells us how much the typical applicant to the military gained or lost (since the Angrist, 1998, population consists of applicants.)

$$
\delta_{ATE}=\mathbb{E}[y_{1i}-y_{0i}]=\sum_x\delta_x\,P(X_i=x)
$$

> page 72

#### **Common support**

In the language of the econometric literature on matching, with saturated control for covariates both the regression and matching estimands impose common support, that is, they are limited to covariate values where both treated and control observations are found.

$$
0<P(d_i=1\mid X_i=x)<1
$$

> page 76

**Even More on Regression and Matching: Ordered and Continuous Treatments**

#### **Average derivative weighting function**

This formula (derived by Yitzhaki, 1996) weights each possible value of $s_i$ in proportion to the difference in the conditional mean of $s_i$ above and below that value. More weight is also given to points close to the median of $s_i$, since $P(s_i\ge t)\,[1-P(s_i\ge t)]$ is maximized there.

$$
\mu_t=\left(\mathbb{E}[s_i\mid s_i\ge t]-\mathbb{E}[s_i\mid s_i<t]\right)\left(P(s_i\ge t)[1-P(s_i\ge t)]\right)
$$

> page 78

#### **Average derivative**

In other words, when $s_i$ is normal, the regression of $y_i$ on $s_i$ is the unconditional average derivative, $E[h'(s_i)]$.

$$
\frac{\operatorname{Cov}(y_i,s_i)}{V(s_i)}=\mathbb{E}[h'(s_i)]\quad\text{when }s_i\text{ is normally distributed}
$$

> page 80

### 3.3.2 Control for Covariates Using the Propensity Score

#### **Propensity score**

the propensity score, defined as $p(X_i)\equiv E[d_i\mid X_i]=P(d_i=1\mid X_i)$

$$
p(X_i)=\mathbb{E}[d_i\mid X_i]=P(d_i=1\mid X_i)
$$

> page 80

#### **Propensity score theorem**

The propensity score theorem says that if potential outcomes are independent of treatment status conditional on a multivariate covariate vector $X_i$, then potential outcomes are independent of treatment status conditional on a scalar function of covariates, the propensity score, defined as $p(X_i)\equiv E[d_i\mid X_i]=P(d_i=1\mid X_i)$.

$$
\{y_{0i},y_{1i}\}\perp d_i\mid X_i\quad\Longrightarrow\quad\{y_{0i},y_{1i}\}\perp d_i\mid p(X_i)
$$

> page 80

#### **Horvitz–Thompson weighting**

The Horvitz-Thompson version of the propensity score approach is appealing, since the estimator is essentially automated, with no cumbersome matching required.

$$
\mathbb{E}[y_{1i}-y_{0i}]=\mathbb{E}\!\left[\frac{y_id_i}{p(X_i)}-\frac{y_i(1-d_i)}{1-p(X_i)}\right]
$$

> page 82

### 3.3.3 Propensity Score Methods versus Regression

## 3.4 Regression Details

### 3.4.1 Weighting Regression

#### **Weighted least squares**

A more precise estimator of the linear CEF is WLS—that is, the estimator that minimizes the sum of squared errors weighted by an estimate of $E[e_i^2\mid X_i]^{-1}$.

$$
\widehat{\beta}_{WLS}=\underset{b}{\arg\min}\;\sum_i w_i(y_i-X_i'b)^2,\qquad w_i=\widehat{\mathbb{E}[e_i^2\mid X_i]}^{-1}
$$

> page 93

### 3.4.2 Limited Dependent Variables and Marginal Effects

#### **Limited dependent variable**

Many empirical studies involve dependent variables that take on only a limited number of values.

$$
y_i\in\{0,1\}\quad\text{or}\quad y_i\ge 0
$$

> page 94

#### **Probit model**

The probit model is usually motivated by the assumption that participation is determined by a latent variable, $y_i$*, that satisfies

$$
y_i^*=\beta_0^*+\beta_1^*d_i-\nu_i,\quad \nu_i\sim\mathcal{N}(0,\sigma_\nu^2),\quad y_i=\mathbf{1}[y_i^*>0]
$$

> page 97

#### **Participation effect**

So, the overall difference in average expenditure can be broken into two parts: the difference in the probability that expenditures are positive (often called a participation effect) and the difference in means conditional on participation, a conditional-on-positive (COP) effect.

$$
P(y_i>0\mid d_i=1)-P(y_i>0\mid d_i=0)
$$

> page 98

**Good COP, Bad COP: Conditional-on-Positive Effects**

#### **Conditional-on-positive effect**

So, the overall difference in average expenditure can be broken into two parts: the difference in the probability that expenditures are positive (often called a participation effect) and the difference in means conditional on participation, a conditional-on-positive (COP) effect.

$$
\mathbb{E}[y_i\mid y_i>0,d_i=1]-\mathbb{E}[y_i\mid y_i>0,d_i=0]
$$

> page 98

#### **Two-part model**

In fact, many use a two-part model, in which the first part is an evaluation of the effect on participation and the second part looks at COP effects (see, e.g., Duan et al., 1983 and 1984, for such models applied to the HIE).

$$
\mathbb{E}[y_i\mid d_i]=\mathbb{E}[y_i\mid y_i>0,d_i]\,P(y_i>0\mid d_i)
$$

> page 99

#### **Tobit model**

A traditional Tobit formulation for the expenditure problem stipulates that the observed $y_i$ is generated by

$$
y_i=\mathbf{1}[y_i^*>0]y_i^*,\qquad y_i^*\text{ is a normally distributed latent outcome}
$$

> page 100

#### **True censoring**

True censoring means the latent variable has an empirical counterpart that is the outcome of primary interest.

> page 102

**Covariates Lead to Nonlinearity**

#### **Marginal effect**

Marginal effects are the (average) changes in CEF implied by a nonlinear model.

$$
\mathbb{E}\!\left[\mathbb{E}[y_i\mid X_i,d_i=1]-\mathbb{E}[y_i\mid X_i,d_i=0]\right]\quad\text{or}\quad\mathbb{E}\!\left[\frac{\partial\mathbb{E}[y_i\mid X_i,d_i]}{\partial d_i}\right]
$$

> page 103

### 3.4.3 Why Is Regression Called Regression, and What Does Regression to the Mean Mean?

#### **Regression to the mean**

The child of tall parents will therefore not be as tall as they are, on average. Likewise, for the short.

$$
\mathbb{E}[y_i\mid x_i]=\mu(1-\rho_{xy})+\rho_{xy}x_i
$$

> page 108

## 3.5 Appendix: Derivation of the Average Derivative Weighting Function


