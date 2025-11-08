# System Architecture: Typing Insight

## Product Overview

The Typing Insight feature is an extension built into an existing smartphone keyboard application. Its primary function is to analyze behavioral typing data already collected by the keyboard to generate an actionable, visualized communication report. The core technical constraint is to perform all data processing and analysis **locally** on the user's device to ensure maximum **data privacy**.

## System Stack

| Component | Technology/Platform | Rationale |
| :--- | :--- | :--- |
| **Frontend (Dashboard)** | Native Mobile UI (Kotlin/Swift) | Seamless integration into the existing keyboard app for a native and fast user experience. Displays the simple dashboard. |
| **Analysis Engine (Backend Logic)** | Optimized Mobile Library (C++/Rust) | Necessary for fast, efficient, and resource-friendly data processing of large datasets (typing history) directly on the device's CPU. |
| **Data Storage** | Local Mobile Storage (SQLite/Realm) | Used for securely storing the raw behavioral data and the weekly analysis results on the device. |

## System Architecture and Component Communication

The architecture is **client-side centric** (on-device processing) to meet the core privacy requirement.

### 1. Keyboard Input Handler (Data Collection)
* The existing keyboard application captures and logs specific behavioral data points with user permission.
* **Data Captured:** Keystroke timings, completed words, errors (spelling mistakes like 'recieve' instead of 'receive'), and frequently used phrases.

### 2. On-Device Analysis Engine (Processing)
* This engine processes the raw data locally.
* **Processing Functions:**
    * **Linguistic Analysis:** Calculates the **Vocabulary Diversity Score** and generates the **Personal Phrasebook** of most used expressions.
    * **Error Mapping:** Aggregates error data to create the **Error Heatmap** (showing frequent mistyping keys) and lists **Most Common Spelling Errors**.
    * **Behavioral Correlation:** Tracks typing speed changes and correlates them with context (e.g., time of day/mood).

### 3. Insight Dashboard (Output)
* The native UI consumes the processed weekly data.
* **Access:** The app uses a floating widget for easy access to prevent a long navigation process.
* **Display:** Presents the results in a clear dashboard with scores, lists, and a heatmap.

## Technical Feasibility

* **Data Source:** The product utilizes behavioral data (typing habits, phrases, errors) that is already accessible to the keyboard app.
* **Privacy:** The commitment to local processing removes the complexity of cloud infrastructure and data transmission.

* **Efficiency:** The solution lies in adding a layer of analysis to an existing action, proving feasibility.
