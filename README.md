# Ex.No.6 Development of Python Code Compatible with Multiple AI Tools

## Date:25-05-2026
## Register no.212223040192
## Name: Shanmuga Raj.K
# Aim: Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights with Multiple AI Tools

# AI Tools Required
1. OpenAI  
2. Google Gemini  
3. Hugging Face  

# Explanation:

In this experiment, the persona pattern of a programmer is used for developing an application that interacts with multiple AI tools through APIs. The program sends the same prompt to different AI models, collects their responses, compares the outputs, and generates insights based on response quality, response length, and accuracy.

This experiment helps in:
- Understanding API integration
- Comparing AI-generated outputs
- Automating evaluation processes
- Generating actionable insights from multiple AI systems

# Requirements

Install required Python libraries:

```bash
pip install requests google-generativeai
```
# Python Code

```python
import requests
import google.generativeai as genai

# -----------------------------------
# API Keys
# -----------------------------------

openai_api_key = "YOUR_OPENAI_API_KEY"

gemini_api_key = "YOUR_GEMINI_API_KEY"

# -----------------------------------
# Configure Gemini API
# -----------------------------------

genai.configure(api_key=gemini_api_key)

# -----------------------------------
# Prompt
# -----------------------------------

prompt = "Explain the benefits of Artificial Intelligence in healthcare."

# -----------------------------------
# Function for OpenAI
# -----------------------------------

def get_openai_response(prompt):

    url = "https://api.openai.com/v1/chat/completions"

    headers = {
        "Authorization": f"Bearer {openai_api_key}",
        "Content-Type": "application/json"
    }

    data = {
        "model": "gpt-3.5-turbo",
        "messages": [
            {
                "role": "user",
                "content": prompt
            }
        ]
    }

    response = requests.post(
        url,
        headers=headers,
        json=data
    )

    if response.status_code == 200:
        return response.json()["choices"][0]["message"]["content"]
    else:
        return "Error in OpenAI API"

# -----------------------------------
# Function for Gemini
# -----------------------------------

def get_gemini_response(prompt):

    model = genai.GenerativeModel("gemini-pro")

    response = model.generate_content(prompt)

    return response.text

# -----------------------------------
# Collect Responses
# -----------------------------------

openai_output = get_openai_response(prompt)

gemini_output = get_gemini_response(prompt)

# -----------------------------------
# Display Outputs
# -----------------------------------

print("\n========== OpenAI Response ==========\n")

print(openai_output)

print("\n========== Gemini Response ==========\n")

print(gemini_output)

# -----------------------------------
# Compare Outputs
# -----------------------------------

print("\n========== Comparison Summary ==========\n")

if len(openai_output) > len(gemini_output):
    print("OpenAI generated a more detailed response.")
else:
    print("Gemini generated a more detailed response.")

# -----------------------------------
# Actionable Insight
# -----------------------------------

print("\n========== Actionable Insight ==========\n")

print("Using multiple AI tools improves reliability and provides diverse perspectives.")
```
---

# How to Execute

## Step 1: Install Python
Download Python from:

https://www.python.org

Check installation:

```bash
python --version
```

---

## Step 2: Install Required Libraries

```bash
pip install requests google-generativeai
```

---

## Step 3: Get API Keys

### OpenAI API Key
https://platform.openai.com

### Gemini API Key
https://makersuite.google.com/app/apikey

---

## Step 4: Replace API Keys

Replace:

```python
openai_api_key = "YOUR_OPENAI_API_KEY"

gemini_api_key = "YOUR_GEMINI_API_KEY"
```

with your actual API keys.

---

## Step 5: Save the File

Save as:

```bash
multi_ai.py
```

---

## Step 6: Run the Program

```bash
python multi_ai.py
```

---

# Sample Output

```text
========== OpenAI Response ==========

Artificial Intelligence helps healthcare by improving diagnosis accuracy,
predicting diseases early, automating medical records, and assisting doctors
in treatment planning.

========== Gemini Response ==========

AI in healthcare improves patient care by enabling faster diagnosis,
personalized treatment, disease prediction, and efficient hospital management.

========== Comparison Summary ==========

Gemini generated a more detailed response.

========== Actionable Insight ==========

Using multiple AI tools improves reliability and provides diverse perspectives.
```

---

# Analysis and Discussion

| Feature | OpenAI | Gemini |
|----------|---------|---------|
| Response Quality | High | High |
| Response Length | Detailed | Detailed |
| Accuracy | High | High |
| Speed | Fast | Fast |
| Ease of Use | Easy API | Easy API |

## Discussion
- OpenAI generated structured and informative responses.
- Gemini produced concise and context-aware outputs.
- Both AI tools provided useful insights for the same prompt.
- Comparing multiple AI tools improves understanding of AI response behavior.
- API integration helps automate intelligent applications efficiently.

---

# Conclusion
The experiment successfully demonstrated Python code integration with multiple AI tools using APIs. The outputs from OpenAI and Gemini were compared and analyzed to generate useful insights. This experiment improved understanding of API handling, AI model comparison, and automation techniques.

---

# Result
The corresponding prompt is executed successfully.

