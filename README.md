# LLM Response Evaluation Framework

A Python project demonstrating how to build an automated scoring system to evaluate Large Language Model (LLM) outputs. This framework assesses response quality by programmatically checking for the presence of predefined, expected keywords, reducing the need for manual inspection.

## 📌 Project Overview
As LLMs are integrated into various applications, verifying the accuracy and completeness of their outputs becomes critical. This project introduces a foundational evaluation metric: exact keyword matching. By defining test cases with expected factual keywords, this script acts as a basic unit-testing suite for LLM prompts, ensuring that generated responses hit all the required informational marks.

## 🚀 Features
* **Custom Test Cases**: Easily define prompts alongside their expected factual keywords.
* **Automated Scoring Logic**: Programmatically scans LLM responses (case-insensitive) to calculate an exact match score.
* **Granular Tracking**: Logs both the `expected_keywords` and the successfully `found_keywords` to help pinpoint exactly where an LLM failed.
* **Automated Reporting**: Compiles all evaluation metrics into a structured dataset and exports it to a CSV file for further analysis.

## 🛠️ Prerequisites
This project requires Python 3.x and relies on the `pandas` library for data manipulation.

    pip install pandas

## 💻 Usage

1. **Clone or Download the Repository:** Ensure the `LLM_Response_Evaluation_Framework.ipynb` file is saved to your local machine.
2. **Open the Notebook:** Launch Jupyter Notebook, Jupyter Lab, or upload the file to Google Colab.
3. **Run the Cells:** Execute the notebook sequentially. 
    * The script initializes the mock dataset containing prompts, responses, and target keywords.
    * It iterates through the dataset, evaluating each response against the keyword list.
    * It scores the response and formats the results into a clean table.
4. **View the Output:** The script automatically generates an output file named `llm_evaluation_results.csv` in your working directory.

## 🧠 How It Works (The Logic)
The core evaluation loop relies on string normalization and substring matching:
1. **Data Ingestion**: Iterates row-by-row through the provided prompt-response pairs.
2. **Normalization**: Converts both the expected keywords and the generated LLM response to lowercase to prevent case-sensitive mismatches.
3. **Substring Search**: Checks if each expected keyword exists within the string of the LLM's response.
4. **Score Calculation**: Increments a `score` counter for every successful match and tracks the total possible points (`max_score`).

## 📄 Output Data Structure
The exported `llm_evaluation_results.csv` contains the following columns:
* `prompt`: The user's original query.
* `llm_response`: The generated text being evaluated.
* `expected_keywords`: The list of words required for a perfect score.
* `found_keywords`: The list of required words that were successfully detected.
* `score`: The number of keywords successfully found.
* `max_score`: The total number of expected keywords (the perfect score).
