# channel_priority


# Check if there are any non-numeric columns in X after encoding
non_numeric_columns = X_train.select_dtypes(include=['object', 'category']).columns
print("Non-numeric columns in X_train:", non_numeric_columns)

# Apply encoding if there are any non-numeric columns left
if len(non_numeric_columns) > 0:
    print("Encoding remaining non-numeric columns.")
    for col in non_numeric_columns:
        le = LabelEncoder()
        X_train[col] = le.fit_transform(X_train[col])
        X_test[col] = le.transform(X_test[col])

# Now proceed with fitting the model
param_grid = {
    'n_estimators': [50, 100],
    'max_depth': [None, 10],
    'min_samples_split': [2, 5],
    'min_samples_leaf': [1, 2]
}
rf = RandomForestClassifier(random_state=42, class_weight='balanced')
grid_search = GridSearchCV(estimator=rf, param_grid=param_grid, cv=3, scoring='f1_weighted', n_jobs=-1, verbose=2)
grid_search.fit(X_train, y_train)
best_rf = grid_search.best_estimator_
