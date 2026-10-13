<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Audience Engagement Classifier</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header class="navbar">
    <div class="brand">
      <div class="brand-mark">AE</div>
      <div>
        <h1>Audience Engagement</h1>
        <span>Decision Tree Classifier</span>
      </div>
    </div>
    <a href="#about" class="nav-link">About Project</a>
  </header>

  <main>
    <section class="hero">
      <div class="hero-copy">
        <p class="eyebrow">MACHINE LEARNING PROJECT</p>
        <h2>Predict audience engagement<br><span>in a few seconds.</span></h2>
        <p class="hero-text">
          Enter audience behavior data and classify the engagement level
          using a Decision Tree model with Cross-Validation.
        </p>
        <div class="hero-tags">
          <span>Decision Tree</span>
          <span>K-Fold Cross-Validation</span>
          <span>Classification</span>
        </div>
      </div>

      <div class="hero-stat">
        <div class="mini-tree">
          <div class="tree-node root">Audience Data</div>
          <div class="branches">
            <div class="branch"><i></i><span>Watch Time</span></div>
            <div class="branch"><i></i><span>Interactions</span></div>
            <div class="branch"><i></i><span>Activity</span></div>
          </div>
          <div class="tree-result">Engagement Level</div>
        </div>
      </div>
    </section>

    <section class="workspace">
      <div class="form-card">
        <div class="section-heading">
          <div>
            <p class="eyebrow">INPUT DATA</p>
            <h3>Audience behavior</h3>
          </div>
          <span class="required">All fields required</span>
        </div>

        <form id="predictionForm">
          <div class="grid">
            <label>
              Age
              <input type="number" id="age" min="1" max="100" placeholder="e.g. 20" required>
            </label>
            <label>
              Watch Time (minutes)
              <input type="number" id="watch_time" min="0" step="0.1" placeholder="e.g. 35" required>
            </label>
            <label>
              Likes
              <input type="number" id="likes" min="0" step="1" placeholder="e.g. 15" required>
            </label>
            <label>
              Comments
              <input type="number" id="comments" min="0" step="1" placeholder="e.g. 4" required>
            </label>
            <label>
              Shares
              <input type="number" id="shares" min="0" step="1" placeholder="e.g. 2" required>
            </label>
            <label>
              Clicks
              <input type="number" id="clicks" min="0" step="1" placeholder="e.g. 8" required>
            </label>
            <label class="full">
              Session Duration (minutes)
              <input type="number" id="session_duration" min="0" step="0.1" placeholder="e.g. 42" required>
            </label>
          </div>

          <button type="submit" id="predictBtn">
            <span>Classify Engagement</span>
            <span class="arrow">→</span>
          </button>
        </form>
      </div>

      <aside class="result-card" id="resultCard">
        <div class="result-top">
          <p class="eyebrow">PREDICTION</p>
          <span class="status-dot"></span>
        </div>

        <div id="emptyState">
          <div class="result-icon">◎</div>
          <h3>Waiting for data</h3>
          <p>Fill in the audience behavior fields to receive an engagement classification.</p>
        </div>

        <div id="predictionState" class="hidden">
          <p class="result-label">Predicted engagement</p>
          <div id="predictionLabel" class="prediction-label">HIGH</div>
          <p id="predictionText" class="prediction-text"></p>
          <div class="confidence-box">
            <div class="confidence-row">
              <span>Model confidence</span>
              <strong id="confidence">--%</strong>
            </div>
            <div class="progress"><span id="progressBar"></span></div>
          </div>
          <div class="model-note">
            <span>Model</span>
            <strong id="modelName">Decision Tree</strong>
          </div>
          <div class="model-note">
            <span>Validation</span>
            <strong>K-Fold Cross-Validation</strong>
          </div>
        </div>
      </aside>
    </section>

    <section id="about" class="about">
      <div>
        <p class="eyebrow">ABOUT THE PROJECT</p>
        <h3>How the system works</h3>
      </div>
      <div class="pipeline">
        <div><b>01</b><span>Audience Data</span></div>
        <div><b>02</b><span>Preprocessing</span></div>
        <div><b>03</b><span>Decision Tree</span></div>
        <div><b>04</b><span>Cross-Validation</span></div>
        <div><b>05</b><span>Prediction</span></div>
      </div>
    </section>
  </main>

  <footer>
    <span>Audience Engagement Classification</span>
    <span>Machine Learning Project</span>
  </footer>

  <script src="script.js"></script>
</body>
</html>
