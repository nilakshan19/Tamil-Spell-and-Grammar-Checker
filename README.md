
# Tamil Spell and Grammar Checker

This project aims to build a **Tamil Spell and Grammar Checker** using a combination of traditional and modern approaches. The system is divided into two main components: **Spell Checker** and **Grammar Checker**. It leverages rule-based methods, machine learning (Random Forest), deep learning approaches (LSTM), and the Stanza library for part-of-speech tagging and error detection.

---

## Features

### Spell Checker

- **Prefix and Suffix Suggestion**: 
  - Suggests corrections based on prefix and suffix similarity to handle common word mistakes in Tamil.
  - Reduces computational complexity before applying the **Levenshtein Distance** algorithm.
  
- **Levenshtein Distance**:
  - Calculates the minimum edit distance between the input word and valid Tamil words.
  - Suggests the most probable correct word based on the smallest edit distance.

- **Corpus**: 
  - Processes a large corpus of Tamil words, sourced from Kaggle datasets, containing nearly 1 lakh unique words.

### Grammar Checker

- **Habitual Tense Rule**:
  - Ensures habitual actions are in the correct future tense. For example, "நான் தினமும் ஐந்து மணிக்கு எழுந்திருப்பேன்" (I will get up at five every day).

- **Subject-Verb Agreement**:
  - Validates that verbs agree with the subject in terms of form and tense. For example, "அவன் படித்தான்" (He read) vs "அவன் படிக்கிறேன்" (Incorrect, should be "அவன் படித்தான்").

- **Methods**:
  - **Rule-Based**: Hard-coded grammar rules are applied for simple and deterministic checks.
  - **Machine Learning**: A Random Forest classifier is used to predict grammatical correctness.
  - **Deep Learning**: An LSTM model is trained to detect and correct grammatical errors by capturing contextual dependencies in Tamil sentences.
  - **Part-of-Speech Tagging**: Using **Stanza** for accurate part-of-speech tagging, enhancing grammar detection.

---

## Methods and Workflow

### Spell Checker

#### Data Collection and Preprocessing

1. **Dataset**:
   - The project uses Tamil paragraph datasets from **Kaggle**.
   - Extracted and cleaned nearly **1 lakh** unique words from the dataset.
   - Preprocessed text by tokenizing and normalizing words.

2. **Prefix and Suffix Matching**:
   - Before applying **Levenshtein Distance**, the system generates word suggestions based on prefix and suffix matching.
   - Example: For the input word "அரசன", the system might suggest words like "அரசன்", "அரசின்", etc.

3. **Levenshtein Distance**:
   - The **Levenshtein Distance** algorithm calculates the minimum number of edits (insertions, deletions, substitutions) required to convert one word into another.
   - The system suggests the word with the smallest edit distance as the correct word.

4. **Evaluation Metrics**:
   - **Accuracy**: Proportion of correctly identified words.
   - **Precision**: Correct suggestions out of all suggestions made.
   - **Recall**: Correct suggestions out of all possible corrections.
   - **F1 Score**: A balance between precision and recall.

---

### Grammar Checker

#### Rules Implemented

1. **Habitual Tense Rule**:
   - Ensures habitual actions follow the correct tense forms.
   - Example: "நான் தினமும் ஐந்து மணிக்கு எழுந்திருப்பேன்" (I will wake up at five every day) vs. "நான் தினமும் ஐந்து மணிக்கு எழுந்திருகிறேன்" (Incorrect, habitual action should be in the future tense).

2. **Subject-Verb Agreement**:
   - Verbs must match the subject's tense and form.
   - Example:
     - **Valid**: "அவன் படித்தான்" (He read).
     - **Invalid**: "அவன் படிக்கிறேன்" (Incorrect, should be "அவன் படித்தான்").

#### Approaches Used

1. **Rule-Based Approach**:
   - Hard-coded grammar rules for highly structured and deterministic checks.
   - Suitable for errors with well-defined patterns, such as subject-verb agreement and tense usage.

2. **Machine Learning Approach**:
   - A **Random Forest** classifier is trained to learn and predict grammatical correctness.
   - The system uses a labeled dataset with examples of correct and incorrect Tamil grammar.

3. **Deep Learning Approach**:
   - A simple **LSTM** model is trained to detect grammatical errors in Tamil sentences.
   - The model captures **contextual dependencies** in sentences, improving the detection of complex grammatical mistakes.

4. **Part-of-Speech Tagging**:
   - The **Stanza** library is used for part-of-speech tagging, improving accuracy in identifying sentence components (subjects, verbs, objects, etc.).
   - This helps in better understanding grammatical structures and error detection.

#### Example of Grammar Rules:

| **Rule**                    | **Valid Example**                                   | **Invalid Example**                                  | **Explanation**                                                   |
|-----------------------------|-----------------------------------------------------|------------------------------------------------------|-------------------------------------------------------------------|
| Habitual Tense Rule         | நான் தினமும் ஐந்து மணிக்கு எழுந்திருப்பேன்          | நான் தினமும் ஐந்து மணிக்கு எழுந்திருகிறேன்          | Ensures habitual actions are in the correct future tense.         |
| Subject-Verb Agreement      | அவன் படித்தான்                                    | அவன் படிக்கிறேன்                                   | Verbs must agree with the subject in terms of tense and form.     |
| Habitual Tense Rule         | நான் தினமும் தேநீர் குடிப்பேன்                      | நான் தினமும் தேநீர் குடித்தேன்                      | Ensures habitual action of future tense with the correct verb.    |
| Subject-Verb Agreement      | நான் மரத்தை வெட்டினேன்                             | நான் மரத்தை வெட்டினான்                             | Verbs must agree with the subject in terms of tense and form.     |

---

## Evaluation

Models were evaluated using standard metrics:

- **Accuracy**: Measures the proportion of correctly identified words or grammatical structures.
- **Precision**: The percentage of correct suggestions made by the system out of all suggestions.
- **Recall**: The percentage of correct suggestions made out of all possible corrections.
- **F1 Score**: A harmonic mean of precision and recall.

---

## Installation

To install the required dependencies for this project, run the following command:

```bash
pip install -r requirements.txt
```

### Requirements:
- `stanza`
- `sklearn`
- `nltk`
- `numpy`
- `tensorflow` (for deep learning models)
- `pandas`

---

## Contributors

- **[Your Name]** - Project Creator & Maintainer
- Contributions from various collaborators in the areas of NLP and deep learning.

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

