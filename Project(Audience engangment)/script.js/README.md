const form = document.getElementById("predictionForm");
const button = document.getElementById("predictBtn");
const emptyState = document.getElementById("emptyState");
const predictionState = document.getElementById("predictionState");
const predictionLabel = document.getElementById("predictionLabel");
const predictionText = document.getElementById("predictionText");
const confidence = document.getElementById("confidence");
const progressBar = document.getElementById("progressBar");
const modelName = document.getElementById("modelName");
const statusDot = document.querySelector(".status-dot");

form.addEventListener("submit", async (event) => {
  event.preventDefault();

  const payload = {
    age: Number(document.getElementById("age").value),
    watch_time: Number(document.getElementById("watch_time").value),
    likes: Number(document.getElementById("likes").value),
    comments: Number(document.getElementById("comments").value),
    shares: Number(document.getElementById("shares").value),
    clicks: Number(document.getElementById("clicks").value),
    session_duration: Number(document.getElementById("session_duration").value)
  };

  button.disabled = true;
  button.querySelector("span").textContent = "Analyzing...";

  try {
    const response = await fetch("http://127.0.0.1:5000/predict", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(payload)
    });

    if (!response.ok) throw new Error("Backend returned an error.");

    const data = await response.json();

    emptyState.classList.add("hidden");
    predictionState.classList.remove("hidden");

    predictionLabel.textContent = data.prediction.toUpperCase();
    predictionText.textContent = data.message;
    confidence.textContent = `${data.confidence}%`;
    progressBar.style.width = `${data.confidence}%`;
    modelName.textContent = data.model || "Decision Tree";

    statusDot.style.background =
      data.prediction.toLowerCase() === "high" ? "#2f9b71" :
      data.prediction.toLowerCase() === "medium" ? "#d98a38" : "#d65c61";

    predictionLabel.style.color =
      data.prediction.toLowerCase() === "high" ? "#2f9b71" :
      data.prediction.toLowerCase() === "medium" ? "#d98a38" : "#d65c61";

  } catch (error) {
    emptyState.classList.remove("hidden");
    predictionState.classList.add("hidden");
    alert("Could not connect to the backend. Make sure the Flask server is running on port 5000.");
  } finally {
    button.disabled = false;
    button.querySelector("span").textContent = "Classify Engagement";
  }
});
