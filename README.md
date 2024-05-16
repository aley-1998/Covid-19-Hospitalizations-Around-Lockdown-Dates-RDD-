# Regression Project

[Regression discontinuity design](https://en.wikipedia.org/wiki/Regression_discontinuity_design) (RDD) is a method used to identify the effect of a change implemented at a cutoff point. This usually leads to pretty diagrams like this one:

<img src="./assets/rdd1.png" style="max-width: 600px"/>

The regression equation for this is

$$y = const + b1 * x + b2 * c$$

Where `const` is the Y intercept, `x` is the independent (feature) variable, and `c` is a dummy variable which indicates if `x > cutoff`. Then, the parameter on `b2` can be t-tested to see if the cutoff had an effect on `y`.

It can also be used with a polynomial regression on both sides:

<img src="./assets/rdd2.png" style="max-width: 600px"/>

Here both sides have a different polynomial degree 2 regression, so the equation uses interaction variables:

$$y = const + b1 * x + b2 * x^2 + b3 * c + b4 * x * c + b5 * x^2 * c$$

Note that you can always overfit the regressions on each to make sure that the gap seems meaningful when it's not. [Gelman & Imbens (2018)](./resources/2018_gelman_jbes.pdf) argue that you should never use more than degree 2 polynomials in RDD. Even degree 2 is sometimes an overfit.

This method has even been used to estimate the effect of lockdown measures, lie in [this CDC study](https://www.cdc.gov/mmwr/volumes/69/wr/mm6947e2.htm?s_cid=mm6947e2_w). For reference on RDD design, [Lee & Lemieux's book chapter](./resources/RDDEconomics.pdf) on RDD is a good technical reference.
