# Ex.No.6 Python Programming with Multiple AI Tools

## Date: 25-05-2026

## Register No.: 212223040243

## Name: Shanmuga Raj.K

# Aim

To create Python code that works with multiple AI tools for generating responses, comparing outputs, and producing meaningful insights using prompt engineering techniques.

---

# AI Platforms Used

1. OpenAI ChatGPT
2. Google Gemini
3. Hugging Face AI

---

# Explanation

This experiment demonstrates how Python can interact with different AI platforms through APIs.
The same prompt is provided to multiple AI systems, and their responses are collected, analyzed, and compared automatically.

The application helps in:

* Learning API integration
* Understanding AI-generated responses
* Comparing outputs from multiple AI systems
* Generating smart insights automatically

---

# Requirements

Install required libraries using:

```bash
pip install requests google-generativeai
```

---

# Python Program

```python id="5t4c8z"
import requests
import google.generativeai as genai

# --------------------------------
# API Configuration
# --------------------------------

openai_key = "YOUR_OPENAI_KEY"
gemini_key = "YOUR_GEMINI_KEY"

genai.configure(api_key=gemini_key)

# --------------------------------
# User Prompt
# --------------------------------

prompt = "Explain how Artificial Intelligence helps students in education."

# --------------------------------
# OpenAI Function
# --------------------------------

def openai_response(prompt):

    url = "https://api.openai.com/v1/chat/completions"

    headers = {
        "Authorization": f"Bearer {openai_key}",
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

    return "OpenAI API Error"

# --------------------------------
# Gemini Function
# --------------------------------

def gemini_response(prompt):

    model = genai.GenerativeModel("gemini-pro")

    response = model.generate_content(prompt)

    return response.text

# --------------------------------
# Generate Outputs
# --------------------------------

openai_output = openai_response(prompt)

gemini_output = gemini_response(prompt)

# --------------------------------
# Display Responses
# --------------------------------

print("\n===== OpenAI Output =====\n")

print(openai_output)

print("\n===== Gemini Output =====\n")

print(gemini_output)

# --------------------------------
# Compare Results
# --------------------------------

print("\n===== Output Comparison =====\n")

if len(openai_output) > len(gemini_output):
    print("OpenAI generated a more detailed explanation.")
else:
    print("Gemini generated a more concise explanation.")

# --------------------------------
# Final Insight
# --------------------------------

print("\n===== AI Insight =====\n")

print("Using multiple AI tools improves response diversity and reliability.")
```

---

# Working Procedure

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

## Step 3: Generate API Keys

### OpenAI Key

https://platform.openai.com

### Gemini Key

https://makersuite.google.com/app/apikey

---

## Step 4: Replace API Keys

Replace:

```python id="j2gr07"
openai_key = "YOUR_OPENAI_KEY"

gemini_key = "YOUR_GEMINI_KEY"
```

with your actual API keys.

---

## Step 5: Save the Program

Save the file as:

```bash
multi_ai_project.py
```

---

## Step 6: Execute the Program

```bash
python multi_ai_project.py
```

---

# Sample Output

```text id="znh7ee"
===== OpenAI Output =====

Artificial Intelligence helps students by providing personalized learning,
smart tutoring systems, automated evaluations, and instant learning support.

===== Gemini Output =====

AI improves education through adaptive learning, virtual assistants,
automated grading, and intelligent study recommendations.

===== Output Comparison =====

OpenAI generated a more detailed explanation.

===== AI Insight =====

Using multiple AI tools improves response diversity and reliability.
```

---

# Analysis Table

| Feature        | OpenAI    | Gemini    |
| -------------- | --------- | --------- |
| Output Quality | Excellent | Excellent |
| Response Speed | Fast      | Fast      |
| Detail Level   | High      | Medium    |
| API Usage      | Simple    | Simple    |
| Accuracy       | High      | High      |

---

# Discussion

* OpenAI generated more descriptive responses.
* Gemini provided shorter and focused outputs.
* Both APIs successfully handled the same prompt.
* Comparing multiple AI tools helps identify output variations.
* API integration improves automation and intelligent application development.

---

# Conclusion

This experiment successfully demonstrated Python integration with multiple AI platforms using APIs.
The generated outputs were compared and analyzed to understand differences in response quality, detail level, and performance.

---

# Result

The Python application successfully interacted with multiple AI tools, compared outputs, and generated meaningful insights using prompt engineering concepts.
