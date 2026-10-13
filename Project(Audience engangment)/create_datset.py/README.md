import pandas as pd
import numpy as np

np.random.seed(42)

n = 1000

age = np.random.randint(18, 61, n)
watch_time = np.random.randint(5, 121, n)
likes = np.random.randint(0, 101, n)
comments = np.random.randint(0, 41, n)
shares = np.random.randint(0, 31, n)
clicks = np.random.randint(0, 61, n)
session_duration = np.random.randint(5, 151, n)

# Calculate an engagement score from audience behavior
engagement_score = (
    watch_time * 0.95
    + likes * 1.25
    + comments * 2.2
    + shares * 2.6
    + clicks * 0.85
    + session_duration * 0.65
)

# Use the score distribution to create balanced engagement classes
low_threshold = np.percentile(engagement_score, 33)
high_threshold = np.percentile(engagement_score, 67)

engagement_level = np.where(
    engagement_score < low_threshold,
    "Low",
    np.where(
        engagement_score < high_threshold,
        "Medium",
        "High"
    )
)

data = pd.DataFrame({
    "Age": age,
    "Watch_Time_Minutes": watch_time,
    "Likes": likes,
    "Comments": comments,
    "Shares": shares,
    "Clicks": clicks,
    "Session_Duration_Minutes": session_duration,
    "Engagement_Level": engagement_level
})

data.to_csv("audience_engagement_dataset.csv", index=False)

print("Dataset created successfully!")
print("Total records:", len(data))

print("\nFirst 5 records:")
print(data.head())

print("\nEngagement distribution:")
print(data["Engagement_Level"].value_counts())

print("\nPercentage distribution:")
print(data["Engagement_Level"].value_counts(normalize=True) * 100)
