# Azure AI Language Service with Kaggle

This notebook demonstrates how to use Azure AI Language Service from a Kaggle Notebook to perform text analytics tasks using the Azure REST API.

The notebook securely retrieves Azure credentials using Kaggle Secrets and analyzes text using multiple Natural Language Processing (NLP) capabilities.

---

# 🚀 Features

This notebook showcases:

### 😊 Sentiment Analysis

Determines the overall sentiment of a piece of text as:

* Positive
* Negative
* Neutral
* Mixed

### 🔑 Key Phrase Extraction

Extracts the most important phrases and topics from the text.

### 🏷️ Entity Recognition

Identifies entities such as:

* People
* Organizations
* Locations
* Products
* Dates and more

---

# 🛠 Technologies Used

* Python
* Kaggle Notebooks
* Azure AI Language Service
* Azure REST API
* Requests Library
* Kaggle Secrets

---

# 📋 Prerequisites

Before running the notebook, you need:

1. An Azure account
2. An Azure AI Language Service resource
3. API Key
4. Endpoint URL

---

# 🔐 Setting Up Kaggle Secrets

To securely store Azure credentials:

1. Open your Kaggle Notebook.
2. Click **Add-ons → Secrets**.
3. Add the following secrets:

| Secret Name       | Value                   |
| ----------------- | ----------------------- |
| LANGUAGE_KEY      | Your Azure API Key      |
| LANGUAGE_ENDPOINT | Your Azure Endpoint URL |

Example Endpoint:

```text
https://your-language-resource.cognitiveservices.azure.com/
```

⚠️ Never hardcode API keys inside notebooks that may be shared publicly.

---

# ⚙️ How the Notebook Works

The notebook:

1. Reads credentials from Kaggle Secrets.
2. Sends text to Azure AI Language Service.
3. Performs:

   * Sentiment Analysis
   * Key Phrase Extraction
   * Entity Recognition
4. Returns structured JSON responses.

---

# 🧪 Example Input

```python
review = "Camera is amazing but battery life is disappointing."
```

---

# 📊 Expected Analysis

### Sentiment Analysis

The service may classify the review as:

```text
Mixed
```

because:

* Positive: "Camera is amazing"
* Negative: "battery life is disappointing"

---

### Key Phrase Extraction

Example output:

```text
Camera
battery life
```

---

### Entity Recognition

Example entities:

```text
Camera
battery life
```

depending on Azure's entity classification model.

---

# 💻 Core Function

```python
def analyze(kind, text):
    url = f"{ENDPOINT}language/:analyze-text?api-version=2023-04-01"
    headers = {"Ocp-Apim-Subscription-Key": KEY}

    body = {
        "kind": kind,
        "analysisInput": {
            "documents": [
                {
                    "id": "1",
                    "language": "en",
                    "text": text
                }
            ]
        }
    }

    return requests.post(
        url,
        headers=headers,
        json=body
    ).json()
```

---

# 🎯 Learning Outcomes

After completing this notebook, learners will be able to:

* Understand Azure AI Language Service
* Securely manage API credentials using Kaggle Secrets
* Perform text analytics using REST APIs
* Analyze customer reviews using AI
* Extract meaningful insights from unstructured text
* Integrate Azure AI services into Python applications

---

# 📚 Azure Capabilities Demonstrated

* Sentiment Analysis
* Key Phrase Extraction
* Named Entity Recognition (NER)

---

# 🔮 Possible Extensions

You can further enhance this notebook by:

* Building a review dashboard
* Analyzing large datasets of customer reviews
* Visualizing sentiment distributions
* Creating a product feedback analyzer
* Integrating with Azure OpenAI for advanced summarization

---

# 👨‍💻 Workshop Information

**SOI 2.0 – Session 2**

This notebook is part of the hands-on exercises designed to introduce participants to Azure AI Language Service and practical NLP applications using Python and Kaggle.

---

# 📜 License

This project is intended for educational and learning purposes.
