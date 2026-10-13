from flask import Flask, request, jsonify
from flask_cors import CORS
import joblib
import numpy as np
import os

app = Flask(__name__)
CORS(app)

# Load the trained Decision Tree model
MODEL_PATH = os.path.join(
    os.path.dirname(__file__),
    "engagement_model.pkl"
)

model = joblib.load(MODEL_PATH)

# Features expected by the trained model
FEATURES = [
    "age",
    "watch_time",
    "likes",
    "comments",
    "shares",
    "clicks",
    "session_duration"
]


@app.route("/")
def home():
    return jsonify({
        "message": "Audience Engagement Classification API",
        "status": "running",
        "model": "Decision Tree Classifier"
    })


@app.route("/predict", methods=["POST"])
def predict():

    data = request.get_json(silent=True) or {}

    # Check for missing inputs
    missing = [feature for feature in FEATURES if feature not in data]

    if missing:
        return jsonify({
            "error": "Missing fields: " + ", ".join(missing)
        }), 400

    # Convert inputs to numbers
    try:
        values = [float(data[feature]) for feature in FEATURES]
    except (TypeError, ValueError):
        return jsonify({
            "error": "All input fields must be numeric."
        }), 400

    # Convert input into model format
    input_data = np.array([values])

    # Make prediction
    prediction = model.predict(input_data)[0]

    # Get prediction confidence
    probabilities = model.predict_proba(input_data)[0]
    confidence = float(np.max(probabilities) * 100)

    return jsonify({
        "prediction": str(prediction),
        "confidence": round(confidence, 2),
        "model": "Decision Tree Classifier",
        "validation": "5-Fold Stratified Cross-Validation"
    })


if __name__ == "__main__":
    app.run(debug=True)
