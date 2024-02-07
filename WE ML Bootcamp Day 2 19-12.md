### ML Pipeline steps
- 1 problem definition -> 2 data collection -> 3 data prep -> 4 data visualization -> 5 ML modeling -> 6 feature engineering -> 7 model deployment
3, 4, 5, 6 = Proof of Concept (PoC)
2 -> what data? how much? which source? time and quality?
-  pre-processing = resizing
-  feature generation and data modeling = which classifier? 

1. **K-fold Cross-Validation:**
    - Divides the dataset into k subsets for model training and evaluation.
    - Provides a more robust estimate of model performance.
    - Consider computational cost and time dependence for suitability.
    
1. **Leave-One-Out Cross-Validation (LOOCV):**
    - Special case of k-fold where k equals the dataset size.
    - Uses each data point as a test set in iterations.
    - Useful for small datasets but computationally expensive.
    - High variance and bias in small datasets.
    
1. **Other Cross-Validation Techniques:**
    - **Stratified K-Fold:** Maintains class distribution in each fold, useful for imbalanced datasets.
    - **Shuffle-Split:** Randomly shuffles and splits data for efficiency.
    - **Time Series:** For time-dependent data.
    - **Group K-Fold:** Considers groups in the dataset.
    - **Repeated and Monte Carlo:** Repeatedly or randomly applies other methods.
    
1. **Stratified K-Fold Cross-Validation:**
    - Maintains class distribution in each fold.
    - Best for imbalanced datasets.
    - Not necessary for well-balanced datasets.
    - Pros: Better class representation, reduced bias.
    - Cons: Computational cost, dependence on dataset size and implementation.


## Asokan Notes

2 important points in ML:
- We can differentiate a mapping (function) represented by 2 points (x, y) values.
- In ML, x and y are constants and m and c are variables

E(m,c) Error function is a function of the weights. We want the derivative to be 0 (minima). It is an estimation of how close my model is to the actual function.

https://colab.research.google.com/drive/1qgxCsocfLyzz5vYfe2jfa0h9yTMxd-gk#scrollTo=nfJouODf2gdX Linear regression notebook + the newton raphson iteration code to get cuberoot and squareroot.
