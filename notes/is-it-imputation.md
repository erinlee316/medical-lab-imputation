Curve fitting can *function as* a form of imputation under certain conditions, but it's not traditionally categorized as such. The distinction is subtle but important, especially in a modeling context.

### Conceptual Difference

**Imputation** generally refers to techniques for estimating missing data values using either simple statistical assumptions (mean, median, KNN, MICE) or model-based predictions (e.g., using other variables in the dataset to regress or classify the missing one). These are typically used to fill missing entries in a structured way while preserving the statistical properties of the data.

**Curve fitting**, on the other hand, constructs a continuous function—often parametric or piecewise—that models the relationship between independent and dependent variables. When used to estimate values at unobserved points, especially between known data points, it effectively performs **interpolation**, and when used to estimate values outside the observed range, it's doing **extrapolation**.

### When Curve Fitting *Is* Imputation

In the context of **longitudinal sparse data**, especially in clinical settings (e.g., labs measured irregularly over time), curve fitting becomes one of the few viable strategies for imputation. For example, fitting a spline or kernel-smoothed curve over time to estimate a missing biomarker value at a particular timestamp is imputation by another name. Gaussian Process Regression is a principled, probabilistic version of this idea.

Formally, if your observations are:

$$
\{(t_i, y_i)\}_{i=1}^n, \quad \text{with missing } y_j \text{ at } t_j
$$

You might fit a curve $f_\theta(t)$ to observed $(t_i, y_i)$ and use $\hat{y}_j = f_\theta(t_j)$ to impute. In that context, the curve fitting is an imputation operator:

$$
\hat{y}_j = \arg\min_{\theta} \sum_{i \in \text{obs}} (y_i - f_\theta(t_i))^2 + \lambda R(\theta)
$$

where $R(\theta)$ is a regularizer (e.g., smoothness). The function $f_\theta$ can be a polynomial, spline, Gaussian process, or neural ODE.

### When It Is *Not*

Curve fitting is **not imputation** when you're modeling data for purposes other than filling in missing values—e.g., constructing a physical model of growth, decay, or dose-response, or forecasting.

Also, curve fitting doesn’t inherently take into account the **correlations between features** unless it's multivariate or part of a structured model like multivariate GPs or structured autoencoders. In contrast, model-based imputation methods like MICE or VAE-based imputation explicitly use joint distributions.

### Practical Implications

If your data is sparse in a temporal or functional domain (like longitudinal EHR, sensor data, etc.), curve fitting may be the **only meaningful form of imputation** because conventional methods fail without local support. But it requires modeling assumptions—temporal continuity, smoothness, functional form—that must be validated.

So yes, in such settings, curve fitting is a type of imputation. But it's more general than that—it's a modeling tool that becomes imputation when used to fill in missing data.

If you’re thinking of applying this to patient trajectories, happy to riff on possible functional forms and estimation procedures.

