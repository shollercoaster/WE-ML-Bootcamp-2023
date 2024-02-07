# Bank Marketing project Gotcha's
- Colon-separated data is just normal csv, use pd.read_csv with delimiter=";".
- I left the unknown values as it is to be taken as a separate category.
- Yes/No columns were fixed with categorical encoding, for other better columns I needed to do EDA to figure out custom encoding or one-hot encoding.
- The problem we found initially was that we would have too many features.
- To figure out influence of education on data, we made a barchart and saw illiterate category had lesser count, so 
- SKLearn onehotencoder gives tuples of the new encoded columns, DO NOT use it for decision trees or any algos that require homogenous column names, use pd.get_dummies instead. No column name overlapping, str name columns, and can process multiple columns at a time.
- Using LR you got 91.08 for training and 91.1 for testing.
- Only using Decision Tree on 7 features: ``'cons.price.idx', 'euribor3m', 'nr.employed', 'contact_encoded', 'month_jun', 'month_jul', 'month_may', 'y_encoded'`` gave a training accuracy of 90.5% and testing accuracy of 89.4%. Precision of 58%
- On adding y_encoded in dt_df I was somehow getting an extra NaN label in y, and so it was calling a multiclass classification problem. Solved by adding y_encoded from main df directly.