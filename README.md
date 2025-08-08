# CrossFit Gym Attendance Analysis

This repository accompanies the ST606 dissertation project titled **"Quantifying Consistency in CrossFit Attendance: A Longitudinal Client Segmentation Approach"**, carried out as part of the MSc in Data Science & Analytics at University College Cork. The project investigates weekly attendance behaviour across four CrossFit gyms in Ireland, using over two years of timestamped visit data (January 2023 to March 2025) to develop quantitative insights into client engagement, consistency, and retention.

The analysis focuses on going beyond basic frequency-based segmentation by incorporating metrics of **attendance stability** such as the **Inverse Coefficient of Variation (ICV)**. The final output includes clustering results, consistency-based profiles, visual summaries of attendance behaviour, and targeted analysis of a unique client subgroup – the **Low Volume, High Consistency (LVHC)** segment.

---

## 📂 Repository Structure

| File | Description |
|------|-------------|
| `Crossfit-Analysis-Code.Rmd` | The complete R Markdown script used for data cleaning, clustering, metric computation, and all figures in the report. |
| `CrossFit_Gym_Dataset.csv` | The anonymised attendance dataset used in the study. |

---

## 🔧 How to Run This Project

To reproduce the entire analysis and generate the plots locally, follow these steps:

### 1. Clone the Repository

```bash
git clone https://github.com/Raghul-3121/Crossfit-thesis.git
cd Crossfit-thesis
```

### 2. Open the R Markdown Script

Open the file `Crossfit-Analysis-Code.Rmd` in **RStudio** (recommended) or any other IDE that supports R Markdown.

⚠️ Make sure to **download both the R Markdown file and the dataset** (`Crossfit-Analysis-Code.Rmd` and `CrossFit_Gym_Dataset.csv`) to the **same folder** on your local machine.  
Then, **update the file path in the `read_csv()` function** if needed, so R can correctly locate the dataset when running the script.

### 3. Install Required R Packages

Ensure the following R packages are installed before running the code:

```r
install.packages(c(
  "tidyverse", "lubridate", "cluster",
  "factoextra", "ggplot2", "viridis",
  "tidyr", "forcats"
))
```

### 4. Run the Analysis

You can either run all code chunks line by line or click **"Knit"** in RStudio to generate the notebook output (in HTML or PDF).

---

## Overview of Analysis Workflow

This project follows a clear and replicable workflow:

1. **Data Cleaning & Filtering**  
   Preprocess the raw timestamped dataset, excluding incomplete entries and non-target locations.

2. **Exploratory Data Analysis (EDA)**  
   Visualise day-of-week trends, seasonal client onboarding, and drop-off behaviours across gym locations.

3. **Weekly Matrix Construction**  
   Aggregate attendance at the client-week level to construct a wide-format matrix for clustering.

4. **Unsupervised Clustering (K-means)**  
   Segment clients based on their weekly attendance patterns. Cluster validation is done using the Elbow and Silhouette methods.

5. **Consistency Metrics**  
   Calculate mean weekly visits, presence ratio (weeks attended / total weeks), and Inverse Coefficient of Variation (ICV) for each client.

6. **LVHC Analysis**  
   Identify and analyse the **Low Volume, High Consistency** clients:  
   - ≤ 2 visits/week  
   - Presence ratio ≥ 70%  
   - ICV ≥ 1.0  
   Explore their behaviour through heatmaps and churn pattern plots.

7. **Churn Detection**  
   Detect disengaged LVHC clients by identifying a break in attendance (≥4 consecutive weeks missed) and visualise drop-off trajectories.

---

## 📌 Key Figures Generated

- **Figure 1–3**: Day-of-week and monthly attendance trends  
- **Figure 4**: Elbow plot for K-means cluster selection  
- **Figure 6**: PCA scatterplot of attendance patterns  
- **Figure 8**: Density plot of ICV by cluster  
- **Figure 9**: Bar chart of top 5 LVHC clients per gym  
- **Figure 10**: Weekly heatmap of top LVHC clients  
- **Figure 11**: Drop-off patterns of churned LVHC clients

All figures were generated using `ggplot2` and `viridis`, and can be found directly in the R Markdown notebook.

---

## 📁 Dataset Schema

The dataset used is a pre-cleaned CSV containing 175,961 records across the following fields:

| Column | Description |
|--------|-------------|
| `Client ID` | Anonymised identifier for each gym client |
| `Start Datetime` | Timestamp of the class attended |
| `Location` | Gym branch (e.g., Bua Santry, Bua Naas) |
| `Status` | Visit status (filtered to include only 'Attended') |
| `Membership Type` | Type of plan the client is enrolled in |

Note: Only attendance data was available. No demographic, billing, or cancellation information was included in the analysis.

---

## ⚠️ Limitations

- The clustering assumes spherical group separation, which may not reflect more complex behavioural patterns.
- Client churn is inferred solely from attendance gaps, without qualitative reasoning or exit survey data.
- Attendance consistency is calculated only for clients who have at least some regularity – outliers or inconsistent long-term members may be underrepresented.

---

## Key Contributions

- Developed and validated a repeatable segmentation approach using unsupervised clustering on weekly behavioural data.
- Introduced ICV as a practical metric to distinguish between erratic and consistent attendees, regardless of frequency.
- Isolated a reliable subgroup (LVHC) with potential strategic value to gym management based on low churn risk and stable attendance.

---

## Author

**Raghul Senthilvel**  
MSc Data Science & Analytics, UCC  
📧 [LinkedIn Profile](https://www.linkedin.com/in/raghul-senthil/)

---

## Acknowledgements

Grateful thanks to **Dr. Niamh Cahill** for her constructive guidance and consistent feedback throughout this research process.
