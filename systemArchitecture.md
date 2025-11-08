# ⚙️ System Architecture: Typing Insight

## Product Overview

[cite_start]The Typing Insight feature is an extension built into an existing smartphone keyboard application[cite: 8]. [cite_start]Its primary function is to analyze behavioral typing data already collected by the keyboard [cite: 4, 13] [cite_start]to generate an actionable, visualized communication report[cite: 10, 12]. [cite_start]The core technical constraint is to perform all data processing and analysis **locally** on the user's device to ensure maximum **data privacy**[cite: 10].

## System Stack

| Component | Technology/Platform | Rationale |
| :--- | :--- | :--- |
| **Frontend (Dashboard)** | Native Mobile UI (Kotlin/Swift) | Seamless integration into the existing keyboard app for a native and fast user experience. [cite_start]Displays the simple dashboard[cite: 10]. |
| **Analysis Engine (Backend Logic)** | Optimized Mobile Library (C++/Rust) | Necessary for fast, efficient, and resource-friendly data processing of large datasets (typing history) directly on the device's CPU. |
| **Data Storage** | Local Mobile Storage (SQLite/Realm) | [cite_start]Used for securely storing the raw behavioral data and the weekly analysis results on the device[cite: 10]. |

## System Architecture and Component Communication

The architecture is **client-side centric** (on-device processing) to meet the core privacy requirement.

### 1. Keyboard Input Handler (Data Collection)
* [cite_start]The existing keyboard application captures and logs specific behavioral data points with user permission[cite: 9].
* [cite_start]**Data Captured:** Keystroke timings, completed words, errors (spelling mistakes like 'recieve' instead of 'receive' [cite: 74, 75][cite_start]), and frequently used phrases[cite: 9].

### 2. On-Device Analysis Engine (Processing)
* [cite_start]This engine processes the raw data locally[cite: 10].
* **Processing Functions:**
    * [cite_start]**Linguistic Analysis:** Calculates the **Vocabulary Diversity Score** [cite: 24] [cite_start]and generates the **Personal Phrasebook** of most used expressions[cite: 37].
    * [cite_start]**Error Mapping:** Aggregates error data to create the **Error Heatmap** (showing frequent mistyping keys [cite: 51][cite_start]) and lists **Most Common Spelling Errors**[cite: 71].
    * [cite_start]**Behavioral Correlation:** Tracks typing speed changes [cite: 9] [cite_start]and correlates them with context (e.g., time of day/mood [cite: 11, 96]).

### 3. Insight Dashboard (Output)
* [cite_start]The native UI consumes the processed weekly data[cite: 11].
* [cite_start]**Access:** The app uses a floating widget for easy access to prevent a long navigation process[cite: 20, 21].
* [cite_start]**Display:** Presents the results in a clear dashboard with scores, lists, and a heatmap[cite: 12].

## Technical Feasibility

* [cite_start]**Data Source:** The product utilizes behavioral data (typing habits, phrases, errors) that is already accessible to the keyboard app[cite: 4, 13].
* [cite_start]**Privacy:** The commitment to local processing [cite: 10] removes the complexity of cloud infrastructure and data transmission.
* [cite_start]**Efficiency:** The solution lies in adding a layer of analysis to an existing action [cite: 103][cite_start], proving feasibility[cite: 13].