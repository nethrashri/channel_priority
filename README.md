# channel_priority


from sklearn.model_selection import StratifiedShuffleSplit

# Perform a stratified train-test split
strat_split = StratifiedShuffleSplit(n_splits=1, test_size=0.2, random_state=42)
for train_idx, test_idx in strat_split.split(X, y):
    X_train, X_test = X.iloc[train_idx], X.iloc[test_idx]
    y_train, y_test = y.iloc[train_idx], y.iloc[test_idx]



# Check class distribution in y_train and y_test
print("Class distribution in y_train:", np.unique(y_train, return_counts=True))
print("Class distribution in y_test:", np.unique(y_test, return_counts=True))



# Continue with model training and evaluation as before
grid_search.fit(X_train, y_train)
best_rf = grid_search.best_estimator_




# Evaluate with classification report and confusion matrix
y_pred = best_rf.predict(X_test)
print("\nClassification Report:\n", classification_report(y_test, y_pred, labels=[0, 1, 2], target_names=['Low', 'Medium', 'High']))
print("\nConfusion Matrix:\n", confusion_matrix(y_test, y_pred, labels=[0, 1, 2]))

