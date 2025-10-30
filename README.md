# FPL Points Predictor (Static Deployment)

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live%20Demo-brightgreen?style=for-the-badge&logo=github)](https://dragonballsuper-1995.github.io/FPL_Points_Predictor/)

A web-based dashboard for Fantasy Premier League (FPL) managers that uses machine learning to predict player points.

This version is deployed as a static site. It requires the user to manually run the Python scripts locally to generate a `predictions.json` file, which is then uploaded to the repository to update the live website.



## ✨ Key Features

* **Player vs. Player Comparison:** A side-by-side dashboard to compare player stats, upcoming fixtures, and predicted points.
* **Dynamic Watchlists:** Automatically generated "Top 5" lists for Forwards, Midfielders, Defenders, Goalkeepers, and "Best Value" (points-per-million).
* **Optimal Squad Builder:** A tool to build a 15-man squad within the £100m budget, based on the highest predicted points for a selected formation.
* **Visual Pitch Display:** See your optimized "Starting XI" in a familiar pitch layout, complete with Captain (C), Vice-Captain (V), and Top 3 (★) badges.
* **List View Toggle:** Switch between the visual pitch display and a simple list view for your squad.
* **Multi-Model Predictions:** Leverages multiple ML models (XGBoost, Random Forest, Ridge, etc.) to provide a range of predictions.

## 🛠️ Tech Stack

* **Backend (Data & ML):** Python
    * `pandas` for data manipulation.
    * `scikit-learn` & `xgboost` for machine learning models.
* **Frontend:** HTML, CSS, JavaScript
    * `Tailwind CSS` for styling.
    * `Chart.js` for data visualization.
* **Deployment:**
    * `GitHub Pages` for static site hosting.

---

## 🚀 How to Run & Deploy (Manual Method 1)

This project relies on a static `predictions.json` file. To update the website, you must generate this file locally and then push it to GitHub.

### Step 1: Run Python Scripts Locally

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/Dragonballsuper-1995/FPL_Points_Predictor.git](https://github.com/Dragonballsuper-1995/FPL_Points_Predictor.git)
    cd FPL_Points_Predictor
    ```
2.  **Install Dependencies:**
    ```bash
    pip install pandas scikit-learn xgboost joblib
    ```
3.  **Get Latest Data:**
    * Download the latest CSV files (e.g., `merged_gw.csv`, `players_raw.csv`, etc.) from the [Vaastav FPL data repository](https://github.com/vaastav/Fantasy-Premier-League/tree/master/data).
    * Save them in your project folder.
    * Ensure the filenames in `config.py` match the files you downloaded.

4.  **Run the Scripts:**
    This will use your local CSVs to generate a new `predictions.json` file.
    ```bash
    # (Optional) Re-train models if you have new historical data
    python train_offline.py
    
    # Generate new predictions
    python main.py
    ```

### Step 2: Deploy to GitHub Pages

1.  **Commit the New Prediction File:**
    After running the scripts, you will have an updated `predictions.json`. Commit this new file to your repository.
    ```bash
    git add predictions.json
    git commit -m "Update predictions for new Gameweek"
    git push origin main
    ```
2.  **Enable GitHub Pages:**
    * In your repository's **"Settings"** tab, go to **"Pages"**.
    * Set the "Source" to **"Deploy from a branch"**.
    * Select the **`main`** branch and the **`/(root)`** folder. Click **Save**.

Your website will be live at `https://<your-username>.github.io/<your-repo-name>/`. The site will now show the data from the `predictions.json` you just uploaded.

## 🙏 Acknowledgments

This project is made possible by the data generously provided by **Vaastav Bhatia** and all contributors to the [Fantasy-Premier-League](https://github.com/vaastav/Fantasy-Premier-League) data repository.
