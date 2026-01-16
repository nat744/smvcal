# Empirically-Calibrated Mate Selection Model

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Standard](https://img.shields.io/badge/standard-ES6%2B-yellow.svg)
![Dependencies](https://img.shields.io/badge/dependencies-none-brightgreen.svg)

A distinct, browser-based simulation engine that models human mate selection dynamics. Unlike arbitrary "attractiveness calculators," this model relies strictly on peer-reviewed evolutionary psychology data to estimate **Sexual Market Value (SMV)**, pursuit probabilities, and assortative mating likelihoods.

## 🧬 Key Features

* **Empirical Calibration:** All scoring formulas are derived from specific research findings regarding height preferences, Waist-to-Hip Ratio (WHR), and facial symmetry.
* **Regional Context Awareness:** Calibrated for 6 distinct global regions (Western, East Asia, South Asia, MENA, Africa, South America) with specific adjustments for local anthropological norms (e.g., WHR variations cited from *Marlowe & Wetsman, 2001*).
* **Monte Carlo Simulation:** Runs 12,000 iterations per calculation against a simulated population using correlated normal distributions (Gaussian) to generate accurate percentile rankings.
* **Dynamic Context Switching:**
    * **Initial/Short-Term:** Heavily weighted toward physical markers (WHR, Height, SWR).
    * **Long-Term:** Introduces resource acquisition (Wealth) using power-law scaling.
* **Diagnostics Suite:** Built-in unit tests and regional sensitivity diagnostics to ensure model stability across different parameter inputs.

## 📚 Scientific Basis & Data Sources

This model implements exact formulas and penalty curves based on the following literature:

* **Height Assortative Mating:** *Stulp et al. (2013)* — Implements female preference for males ~21cm taller and the "male-not-too-tall" norm (>25cm height gap penalties).
* **Waist-to-Hip Ratio (WHR):** *Singh (1993)* — Establishes 0.7 as the Western optimum, with regional variants derived from *Dixson et al. (2007)*.
* **Acceptance Probabilities:** *Kurzban & Weeden (2005)* — Calibrates baseline acceptance rates for speed dating (34% female acceptance vs. 49% male acceptance).
* **Revealed vs. Stated Preferences:** *Fisman et al. (2006)* — Adjusts stated preferences to match actual behavioral data from dating markets.

## 🛠 Technical Implementation

The application is built in vanilla HTML/CSS/JS with no external dependencies.

### Core Logic
1.  **Input Normalization:** User inputs are clamped and normalized against healthy physiological ranges.
2.  **Attractiveness Scoring:** Inputs are passed through non-linear penalty curves (e.g., Gaussian falloff for breast firmness, asymmetric penalties for body fat).
3.  **Population Generation:** The `estimateSMV` function generates a synthetic population of 12,000 competitors using `correlatedNormal` functions to account for biological correlations (e.g., taller individuals usually weighing more).
4.  **Pairing Probability:** Calculates the likelihood of a mutual match based on the intersection of male and female pursuit probabilities.

## 🚀 Usage

This is a client-side application. No build step or server is required.

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/nat744/smvcal.git](https://github.com/nat744/smvcal.git)
    ```
2.  **Run:**
    Simply open `smv_attraction_model.html` in any modern web browser.

3.  **Run Tests:**
    Open the browser console or click "Run Automated Tests" in the UI to trigger the `runRegionalDiagnostics()` and `runEmpiricalBenchmarks()` functions.

## 🤝 Contributing

Contributions are welcome, particularly those that refine the regional datasets with more recent anthropological studies.

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/NewRegionData`)
3.  Commit your Changes (`git commit -m 'Add valid citation for MENA height prefs'`)
4.  Push to the Branch (`git push origin feature/NewRegionData`)
5.  Open a Pull Request

## ⚠️ Disclaimer

This software is a theoretical model intended for educational and sociological interest. It relies on population-level statistical averages and does not determine individual human worth or the complexity of real-world romantic chemistry.
