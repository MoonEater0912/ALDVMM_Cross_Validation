# Adjusted Limited Dependent Variable Mixture Model (ALDVMM)

This code uses the package ["aldvmm"](https://cran.r-project.org/web/packages/aldvmm/aldvmm.pdf) in R. ALDVMM is a specifically designed model to map into EQ-5D instrument, however, it also shows relatively good performance in mapping into SF-6D.

This code creates a function, mapping the kdqol-36 sub-scales (PCS, MCS, KDCS; or PCS, MCS, Burden, Effect, Symptom) together with sex and age as forced control variables, into general HRQoL instruments (like EQ-5D or SF-6D).

Before runing the function, you need to set the range of HRQoL values according to region-specific value set. This function returns a series of results of k-fold cross calidation (ME, MAE and RMSE), so that you can compare the model performances. In the returned dataframe, there should be the results of 6 models:
- using only main effect of PCS, MCS, KDCS;
- using only main effect of PCS, MCS, Burden, Effect, Symptom;
- using main and square effect of PCS, MCS, KDCS;
- using main and square effect of PCS, MCS, Burden, Effect, Symptom;
- using main, square and interaction effect of PCS, MCS, KDCS;
- using main, square and interaction effect of PCS, MCS, Burden, Effect, Symptom.

## Preparation of Dataset

To use the function, you need to include several columns in your dataset:
- utility: the targeted variable
- age, gender: control variables
- pcs, mcs, kdcs, effect, burden, symptom: main effects of KDQoL-36 scales
- x_sq, for x in [pcs, mcs, kdcs, effect, burden, symptom]: square effects
- x_y, for x in [pcs, mcs, kdcs, effect, burden, symptom] and y in [pcs, mcs, kdcs, effect, burden, symptom]: interaction effects
