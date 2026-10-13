import pandas as pd
import joblib

from sklearn.model_selection import StratifiedKFold, cross_validate, train_test_split
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import (
    accuracy_score,
    precision_score,
    recall_score,
    f1_score,
    confusion_matrix
)

# Load dataset
df = pd.read_csv("audience_engagement_dataset.csv")

# Input features
features = [
    "Age",
    "Watch_Time_Minutes",
    "Likes",
    "Comments",
    "Shares",
    "Clicks",
    "Session_Duration_Minutes"
]

X = df[features]
y = df["Engagement_Level"]

# Split dataset into training and testing data
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42,
    stratify=y
)

# Create Decision Tree model
model = DecisionTreeClassifier(
    max_depth=5,
    min_samples_split=10,
    random_state=42
)

# 5-Fold Stratified Cross-Validation
cv = StratifiedKFold(
    n_splits=5,
    shuffle=True,
    random_state=42
)

cv_results = cross_validate(
    model,
    X_train,
    y_train,
    cv=cv,
    scoring=[
        "accuracy",
        "precision_macro",
        "recall_macro",
        "f1_macro"
    ]
)

# Train model on training data
model.fit(X_train, y_train)

# Predict test data
y_pred = model.predict(X_test)

# Cross-validation results
print("\n===== 5-FOLD CROSS-VALIDATION =====")
print("CV Accuracy:", cv_results["test_accuracy"].mean())
print("CV Precision:", cv_results["test_precision_macro"].mean())
print("CV Recall:", cv_results["test_recall_macro"].mean())
print("CV F1 Score:", cv_results["test_f1_macro"].mean())

# Test results
print("\n===== TEST SET RESULTS =====")
print("Test Accuracy:", accuracy_score(y_test, y_pred))
print(
    "Test Precision:",
    precision_score(y_test, y_pred, average="macro", zero_division=0)
)
print(
    "Test Recall:",
    recall_score(y_test, y_pred, average="macro", zero_division=0)
)
print(
    "Test F1 Score:",
    f1_score(y_test, y_pred, average="macro", zero_division=0)
)

# Confusion Matrix
print("\n===== CONFUSION MATRIX =====")
print(
    confusion_matrix(
        y_test,
        y_pred,
        labels=["Low", "Medium", "High"]
    )
)

# Save trained model
joblib.dump(model, "engagement_model.pkl")

print("\nModel saved successfully as engagement_model.pkl")
