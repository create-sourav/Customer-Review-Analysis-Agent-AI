Customer Review Analysis Agent
==============================

An AI-powered script that analyzes customer reviews using Google Gemini (via langchain-google-genai) and returns structured JSON summaries, positives, negatives, sentiment, emotions, and a customer email response. This repository contains a Colab-converted Python script that demonstrates how to build a small LLM pipeline and export results to a DataFrame.

Project Overview
----------------
This tool accepts a list of textual customer reviews and, for each review, generates:
- a 2–3 line summary
- lists of positives and negatives
- an overall sentiment label (Positive, Negative, Neutral)
- 3–5 emotions
- a tailored email response addressed to Dear Customer and signed Service Agent

The script uses a Pydantic model (ReviewAnalysis) as an output schema and PydanticOutputParser to enforce structure.

Features
--------
- Structured review analysis using an LLM chain
- Parser-enforced JSON output (Pydantic model)
- Batch processing of reviews
- Export to Pandas DataFrame (and easy export to CSV / JSON)
- Example prompt template and format instructions are included

Requirements
------------
Create a Python 3.8+ environment and install:
    pip install -r requirements.txt

Suggested requirements.txt:
    langchain
    langchain-google-genai
    google-genai
    pydantic
    pandas

Project Structure
-----------------
customer-review-analysis/
│
├── notebooks/
│   └── Customer_Review_Analysis_Agent_.ipynb
├── src/
│   └── customer_review_analysis_agent_.py
├── README.txt


Quickstart
----------
1. Clone repository:
    git clone https://github.com/create-sourav/Customer-Review-Analysis.git
    cd customer-review-analysis

2. Create and activate virtual environment:
    python -m venv venv
    venv\Scripts\activate    # Windows

3. Install dependencies:
    pip install -r requirements.txt

4. Set up API key:
    export GOOGLE_API_KEY="your_google_api_key"  # macOS/Linux
    setx GOOGLE_API_KEY "your_google_api_key"    # Windows

5. Run the script:
    python src/customer_review_analysis_agent_.py

Usage
-----
Script steps:
1. Builds ChatPromptTemplate with format_instructions
2. Creates LLM chain: prompt | google_studio | parser
3. Invokes chain for each review
4. Converts responses to Python dicts
5. Aggregates dicts into pandas.DataFrame
6. Displays DataFrame

Example JSON structure:
{
    "Summary": "A short 2-3 line summary",
    "Positives": ["fast performance", "good battery"],
    "Negatives": ["packaging", "speaker volume"],
    "Sentiment": "Positive",
    "Emotions": ["Happy","Satisfied","Excited"],
    "Email": "Dear Customer,...Service Agent"
}

Implementation Details
----------------------
- Model: ChatGoogleGenerativeAI(model="gemini-1.5-flash", temperature=0)
- Parser: PydanticOutputParser
- Prompt: Fixed output format and email tone rules
- DataFrame: pandas with display options to prevent truncation

Troubleshooting
---------------
- If DataFrame output is truncated, set pandas display options
- If result is a string, parse with json.loads

Improvements
------------
- Add CLI arguments
- Add logging/progress
- Add multilingual support
- Build dashboard integration

  Acknowledgements
  ----------------
This project was made possible thanks to:
- **Google Gemini** via **Google AI Studio** for providing the LLM capabilities
- **LangChain** for the framework to integrate prompts, models, and parsers seamlessly

