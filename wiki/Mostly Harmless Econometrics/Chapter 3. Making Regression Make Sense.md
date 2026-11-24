Chapter 3 covers the conditional expectation function, regression, inference, causal interpretation, matching, weighting, limited dependent variables, marginal effects, and regression to the mean. This file includes the chapter through its printed page 110, including section 3.4.3 and the appendix opening on average-derivative weighting.

> Mostly Harmless Econometrics - Chapter 3, pages 27–110

## 3.1 Regression Fundamentals

### 3.1.1 Economic Relationships and the Conditional Expectation Function

#### **Conditional expectation function**

The population mean of an outcome at each fixed value of the covariates; written E[y_i|X_i].

$$
\mathbb{E}[y_i\mid X_i=x]=\int t f_y(t\mid X_i=x)\,dt
\text{(for continuous }y_i);\qquad \mathbb{E}[y_i\mid X_i=x]=\sum_t tP(y_i=t\mid X_i=x)
\text{(for discrete }y_i)
$$

> pages 30–31

#### **Law of iterated expectations**

An unconditional expectation equals the average of the conditional expectation function over the covariate distribution.

$$
\mathbb{E}[y_i]=\mathbb{E}\!\left[\mathbb{E}[y_i\mid X_i]\right]
$$

> pages 31

#### **CEF decomposition property**

The outcome equals its conditional expectation given covariates plus a residual with conditional mean zero. This residual is uncorrelated with any function of those covariates.

$$
y_i=\mathbb{E}[y_i\mid X_i]+\varepsilon_i,\qquad \mathbb{E}[\varepsilon_i\mid X_i]=0
$$

> pages 32–33

#### **CEF prediction property**

Among all functions of the covariates, the conditional expectation function minimizes expected squared prediction error; it is the MMSE predictor.

$$
\mathbb{E}[y_i\mid X_i]=\underset{m(X_i)}{\arg\min}\;\mathbb{E}\!\left[(y_i-m(X_i))^2\right]
$$

> pages 33

#### **ANOVA theorem**

The outcome variance equals the variance of its conditional expectation plus the average conditional variance.

$$
V(y_i)=V\!\left(\mathbb{E}[y_i\mid X_i]\right)+\mathbb{E}\!\left[V(y_i\mid X_i)\right]
$$

> pages 33–34

### 3.1.2 Linear Regression and the CEF

#### **Population regression function**

The linear function minimizing population expected squared error. Its residual is uncorrelated with the regressors by construction.

$$
\beta=\underset{b}{\arg\min}\;\mathbb{E}\!\left[(y_i-X_i'b)^2\right]=\mathbb{E}[X_iX_i']^{-1}\mathbb{E}[X_iy_i]
$$

> pages 35

#### **Regression anatomy**

A multiple-regression coefficient equals the bivariate slope after removing the linear association of the other covariates from the regressor of interest.

$$
\beta_k=\frac{\operatorname{Cov}(y_i,\widetilde{x}_{ki})}{V(\widetilde{x}_{ki})}
$$

> pages 35–36

#### **Linear CEF theorem**

When the conditional expectation function is linear, the population regression function equals it.

$$
\mathbb{E}[y_i\mid X_i]=X_i'\beta^*\quad\Longrightarrow\quad \beta=\beta^*
$$

> pages 37

#### **Best linear predictor theorem**

The population regression function is the minimum mean squared error predictor among linear functions of the covariates.

$$
X_i'\beta=\underset{b}{\arg\min}\;\mathbb{E}\!\left[(y_i-X_i'b)^2\right]
$$

> pages 37–38

#### **Regression CEF theorem**

The population regression function is the MMSE linear approximation to the conditional expectation function, whether or not that function is itself linear.

$$
\beta=\underset{b}{\arg\min}\;\mathbb{E}\!\left[(\mathbb{E}[y_i\mid X_i]-X_i'b)^2\right]
$$

> pages 38

### 3.1.3 Asymptotic OLS Inference

#### **Ordinary least squares estimator**

The sample analogue of the population regression coefficients, obtained by replacing expectations with sample averages; it minimizes the sample sum of squared residuals.

$$
\widehat{\beta}=\left(\sum_{i=1}^{N}X_iX_i'\right)^{-1}\sum_{i=1}^{N}X_iy_i
$$

> pages 42

#### **Law of large numbers**

Sample moments converge in probability to corresponding population moments as sample size grows.

> pages 43

#### **Central limit theorem**

Centered and appropriately scaled sample moments are asymptotically normal, with covariance determined by the underlying random variable's variance.

> pages 43

#### **Slutsky’s theorem**

Combining a statistic with an asymptotic distribution and one converging in probability to a constant leaves the asymptotic distribution unchanged if the latter is replaced by that constant.

$$
a_N\xrightarrow{d}A,\quad b_N\xrightarrow{p}b\quad\Longrightarrow\quad a_N+b_N\xrightarrow{d}A+b,\qquad a_Nb_N\xrightarrow{d}Ab
$$

> pages 43

#### **Continuous mapping theorem**

A continuous function of a statistic converging in probability converges to that function evaluated at the statistic's probability limit.

$$
b_N\xrightarrow{p}b,\quad h\text{ continuous at }b\quad\Longrightarrow\quad h(b_N)\xrightarrow{p}h(b)
$$

> pages 44

#### **Delta method**

A continuously differentiable function of an asymptotically normal vector is asymptotically normal; its covariance is determined by the vector covariance and the function's gradient.

$$
\sqrt{N}\bigl(h(b_N)-h(b)\bigr)\xrightarrow{d}\mathcal{N}\!\left(0,\nabla h(b)'\Omega\nabla h(b)\right)
$$

> pages 44

#### **Consistent estimator**

An estimator that converges in probability to its target parameter.

$$
\widehat{\beta}\xrightarrow{p}\beta
$$

> pages 45

#### **Heteroskedasticity-consistent standard errors**

Large-sample OLS standard errors that remain valid without assuming constant conditional residual variance; also called White or Eicker–White (robust) standard errors.

$$
\operatorname{Avar}(\widehat{\beta})=\mathbb{E}[X_iX_i']^{-1}\,\mathbb{E}[X_iX_i'e_i^2]\,\mathbb{E}[X_iX_i']^{-1}
$$

> pages 45–46

#### **Homoskedasticity**

The condition that residual variance given the regressors is constant.

$$
\mathbb{E}[e_i^2\mid X_i]=\sigma^2
$$

> pages 46

#### **Linear probability model**

A regression with a binary zero-one dependent variable. When its conditional expectation function is linear, it is the conditional probability of a one. The book notes that its residuals are generally heteroskedastic, even with a saturated model.

$$
y_i\in\{0,1\},\qquad \mathbb{E}[y_i\mid X_i]=P(y_i=1\mid X_i)=X_i'\beta
$$

> pages 47, 93

#### **Unbiasedness**

An estimator is unbiased when its expected value equals the target parameter. The book distinguishes this from consistency, a large-sample convergence property.

$$
\mathbb{E}[\widehat{\beta}]=\beta
$$

> pages 47–48

### 3.1.4 Saturated Models, Main Effects, and Other Regression Talk

#### **Saturated regression model**

For discrete explanatory variables, a model with a separate parameter for every possible combination of their values; it fits the conditional expectation function at those values.

$$
y_i=\alpha+\sum_{j=1}^{\tau}\beta_j d_{ji}+\varepsilon_i,\qquad d_{ji}=\mathbf{1}[s_i=j]
$$

> pages 48–51

#### **Main effects and interaction term**

In the two-dummy example, coefficients on each dummy are main effects; the coefficient on their product is an interaction, allowing one effect to vary with the other covariate.

$$
\mathbb{E}[y_i\mid x_{1i},x_{2i}]=\alpha+\beta_1x_{1i}+\gamma x_{2i}+\delta_1(x_{1i}x_{2i})
$$

> pages 49–51

## 3.2 Regression and Causality

### 3.2.1 The Conditional Independence Assumption

#### **Conditional independence assumption**

Conditional on observed covariates, treatment or schooling is independent of potential outcomes. This selection-on-observables assumption allows conditional comparisons to have a causal interpretation.

$$
\{y_{0i},y_{1i}\}\perp c_i\mid X_i,\qquad y_{si}\perp s_i\mid X_i\;\text{ for all }s
$$

> pages 53–55

#### **Potential outcomes for schooling**

f_i(s) denotes the outcome individual i would receive at schooling level s; the observed outcome is the potential outcome for the schooling actually received.

$$
y_{si}=f_i(s),\qquad y_i=f_i(s_i)
$$

> pages 55

### 3.2.2 The Omitted Variables Bias Formula

#### **Omitted variables bias formula**

The short-regression coefficient equals the long-regression coefficient plus the effect of omitted variables multiplied by their regression on included variables. Omission changes the coefficient when omitted and included variables are related.

$$
\frac{\operatorname{Cov}(y_i,s_i)}{V(s_i)}=\rho+\gamma'\delta_{As}
$$

> pages 60–61

### 3.2.3 Bad Control

#### **Bad controls**

Variables that are themselves outcomes in the causal process being studied. Conditioning on them can make comparisons noncausal; controls fixed before treatment is determined are conceptually different.

$$
\mathbb{E}[y_i\mid w_i=1,c_i=1]-\mathbb{E}[y_i\mid w_i=1,c_i=0]
=\mathbb{E}[y_{1i}-y_{0i}\mid w_{1i}=1]
+\left\{\mathbb{E}[y_{0i}\mid w_{1i}=1]-\mathbb{E}[y_{0i}\mid w_{0i}=1]\right\}
$$

> pages 64–66

#### **Proxy control**

An observed variable used instead of an unavailable control. If the proxy is itself affected by the variable of interest, controlling for it can shift the coefficient away from the desired causal effect.

$$
a_{li}=\pi_0+\pi_1s_i+\pi_2a_i,\qquad \text{proxy-control coefficient on }s_i=\rho-\frac{\gamma\pi_1}{\pi_2}
$$

> pages 67–68

## 3.3 Heterogeneity and Nonlinearity

### 3.3.1 Regression Meets Matching

#### **Average treatment effect on the treated**

The average difference between treated individuals' potential outcomes under treatment and without treatment; it describes the effect for those treated.

$$
\delta_{TOT}=\mathbb{E}[y_{1i}-y_{0i}\mid d_i=1]
$$

> pages 70–71

#### **Matching estimator**

An estimator that compares treated and untreated observations at the same covariate values, then averages those covariate-specific differences using chosen weights.

$$
\mathbb{E}[y_{1i}-y_{0i}\mid d_i=1]=\sum_x\delta_x\,P(X_i=x\mid d_i=1)
$$

> pages 71–72

#### **Average treatment effect**

The population average difference between potential outcomes under treatment and without treatment.

$$
\delta_{ATE}=\mathbb{E}[y_{1i}-y_{0i}]=\sum_x\delta_x\,P(X_i=x)
$$

> pages 72

#### **Common support**

Covariate values where treated and control observations both occur. Comparisons outside this overlap require extrapolation.

$$
0<P(d_i=1\mid X_i=x)<1
$$

> pages 76–77, 90

**Even More on Regression and Matching: Ordered and Continuous Treatments**

#### **Average derivative**

For normally distributed treatment, the simple regression slope equals the unconditional average derivative of the conditional expectation function.

$$
\frac{\operatorname{Cov}(y_i,s_i)}{V(s_i)}=\mathbb{E}[h'(s_i)]\quad\text{when }s_i\text{ is normally distributed}
$$

> pages 78–80

### 3.3.2 Control for Covariates Using the Propensity Score

#### **Propensity score**

The conditional probability of treatment given covariates.

$$
p(X_i)=\mathbb{E}[d_i\mid X_i]=P(d_i=1\mid X_i)
$$

> pages 80–81

#### **Propensity score theorem**

If potential outcomes are independent of treatment conditional on the full covariates, they are also independent conditional on the propensity score.

$$
\{y_{0i},y_{1i}\}\perp d_i\mid X_i\quad\Longrightarrow\quad\{y_{0i},y_{1i}\}\perp d_i\mid p(X_i)
$$

> pages 80–81

#### **Horvitz–Thompson weighting**

An inverse-probability weighting approach that uses treatment probabilities (often estimated from the propensity score) to estimate treatment effects without a separate matching step.

$$
\mathbb{E}[y_{1i}-y_{0i}]=\mathbb{E}\!\left[\frac{y_id_i}{p(X_i)}-\frac{y_i(1-d_i)}{1-p(X_i)}\right]
$$

> pages 82–83

### 3.3.3 Propensity Score Methods versus Regression

## 3.4 Regression Details

### 3.4.1 Weighting Regression

#### **Weighted least squares**

A regression estimator minimizing a weighted sum of squared errors. The chapter discusses inverse conditional-variance weights as a way to address heteroskedasticity.

$$
\widehat{\beta}_{WLS}=\underset{b}{\arg\min}\;\sum_i w_i(y_i-X_i'b)^2,\qquad w_i=\widehat{\mathbb{E}[e_i^2\mid X_i]}^{-1}
$$

> pages 92–93

### 3.4.2 Limited Dependent Variables and Marginal Effects

#### **Limited dependent variable**

An outcome restricted to a limited set of values, such as a binary indicator or a nonnegative measure.

$$
y_i\in\{0,1\}\quad\text{or}\quad y_i\ge 0
$$

> pages 94–95

#### **Probit model**

A model for a binary outcome built from a latent index with normally distributed error; the observed outcome is one when the index exceeds zero, yielding a normal-CDF conditional mean.

$$
y_i^*=\beta_0^*+\beta_1^*d_i-\nu_i,\quad \nu_i\sim\mathcal{N}(0,\sigma_\nu^2),\quad y_i=\mathbf{1}[y_i^*>0]
$$

> pages 97–98

#### **Participation effect**

For a nonnegative outcome, the component of an overall treatment-group difference attributable to the change in the probability that the outcome is positive.

$$
P(y_i>0\mid d_i=1)-P(y_i>0\mid d_i=0)
$$

> page 98

**Good COP, Bad COP: Conditional-on-Positive Effects**

#### **Conditional-on-positive effect**

The difference in mean outcomes between treatment groups among observations whose outcome is positive. The chapter cautions that this comparison can include selection bias because positivity is itself affected by treatment.

$$
\mathbb{E}[y_i\mid y_i>0,d_i=1]-\mathbb{E}[y_i\mid y_i>0,d_i=0]
$$

> pages 98–100

#### **Two-part model**

An approach that separately models treatment effects on participation and on the outcome conditional on participation.

$$
\mathbb{E}[y_i\mid d_i]=\mathbb{E}[y_i\mid y_i>0,d_i]\,P(y_i>0\mid d_i)
$$

> page 99

#### **Tobit model**

A censored-regression model in which the observed nonnegative outcome is zero when a normally distributed latent outcome is not positive, and otherwise equals that latent outcome.

$$
y_i=\mathbf{1}[y_i^*>0]y_i^*,\qquad y_i^*\text{ is a normally distributed latent outcome}
$$

> pages 100–101

#### **True censoring**

A situation where a latent variable has an empirical counterpart and is the outcome of primary interest, but observed data limit its recorded value, as with topcoded earnings.

> page 102

**Covariates Lead to Nonlinearity**

#### **Marginal effect**

The average change in the conditional expectation function implied by a nonlinear model. For a binary regressor, the chapter describes calculating it either as a finite difference between regressor values or as an average derivative.

$$
\mathbb{E}\!\left[\mathbb{E}[y_i\mid X_i,d_i=1]-\mathbb{E}[y_i\mid X_i,d_i=0]\right]\quad\text{or}\quad\mathbb{E}\!\left[\frac{\partial\mathbb{E}[y_i\mid X_i,d_i]}{\partial d_i}\right]
$$

> pages 102–105

### 3.4.3 Why Is Regression Called Regression, and What Does Regression to the Mean Mean?

#### **Regression to the mean**

When a variable is stationary across generations and the conditional expectation is linear, the expected outcome for an unusually high or low observation is a weighted average of that value and the population mean. The outcome is therefore expected to be less extreme on average.

$$
\mathbb{E}[y_i\mid x_i]=\mu(1-\rho_{xy})+\rho_{xy}x_i
$$

> pages 108–109

## 3.5 Appendix: Derivation of the Average Derivative Weighting Function

#### **Average derivative weighting function**

The function μ_t assigns nonnegative weights across treatment values in the average-derivative representation of a regression slope; the weights reflect differences in treatment means above and below each value and treatment probability on either side.

$$
\mu_t=\left(\mathbb{E}[s_i\mid s_i\ge t]-\mathbb{E}[s_i\mid s_i<t]\right)\left(P(s_i\ge t)[1-P(s_i\ge t)]\right)
$$

> page 110



