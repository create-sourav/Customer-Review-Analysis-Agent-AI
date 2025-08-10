

CUSTOMER REVIEW ANALYSIS AGENT
Complete Setup Instructions

TABLE OF CONTENTS
1. Prerequisites
2. Step-by-Step Setup Guide
3. Customization Guide
4. Understanding the Output
5. Troubleshooting
6. Usage Tips
7. Security Notes
8. Support
9. Next Steps

PREREQUISITES
Before you begin, make sure you have:
• A Google account
• Basic understanding of Python (helpful but not required)
• 15-20 minutes of setup time


STEP-BY-STEP SETUP GUIDE
Step 1: Get Your Google AI Studio API Key

1. Visit Google AI Studio:
   • Go to https://makersuite.google.com/app/apikey
   • Sign in with your Google account

2. Create API Key:
   • Click "Create API Key"
   • Select "Create API key in new project" (or choose existing project)
   • Copy the generated API key (it looks like: AIzaSyC7b2...)
   • IMPORTANT: Save this key securely - you'll need it in Step 3

Step 2: Access the Notebook

Option A: Google Colab (Recommended)
1. Download the notebook file: Customer_Review_Analysis_Agent.ipynb
2. Go to https://colab.research.google.com/
3. Click "Upload" and select the notebook file
4. The notebook will open in Google Colab

Option B: GitHub
1. Visit the GitHub repository: [Repository Link]
2. Click "Open in Colab" badge (if available)
3. Or download the notebook and upload to Colab

Step 3: Run the Setup

1. Install Dependencies:
   • Click on the first code cell (contains !pip install)
   • Press Shift + Enter or click the "Play" button
   • Wait for installation to complete (30-60 seconds)

2. Enter API Key:
   • Find the cell with getpass("Please enter your Google API key: ")
   • Run this cell (Shift + Enter)
   • When prompted, paste your API key from Step 1
   • Press Enter (the key will be hidden for security)

3. Initialize the Model:
   • Run the next few cells one by one
   • Look for the cell with ChatGoogleGenerativeAI
   • This sets up the AI model

Step 4: Test with Sample Data

1. Run Sample Analysis:
   • Find the cell with sample reviews (starts with reviews = [...])
   • Run this cell to load sample data

2. Test Single Review:
   • Find the cell with input_review = reviews[0]
   • Run this cell and the next one
   • You should see a JSON output with analysis results

3. Process All Reviews:
   • Run the cell with the for loop
   • This will analyze all sample reviews
   • Each review will show structured results

CUSTOMIZATION GUIDE

Adding Your Own Reviews
Replace the sample reviews with your own data:
# Replace this section with your reviews
reviews = [
    "Your first review text here...",
    "Your second review text here...",
    "Your third review text here..."
]

Modifying Output Fields

To change what the system analyzes, edit the ReviewAnalysis class:

class ReviewAnalysis(BaseModel):
    Summary: str = Field(description="Your custom description")
    # Add or remove fields as needed
    CustomField: str = Field(description="Your new field")

Changing Email Templates

Modify the prompt template to customize email responses:
prompt_txt = """
Your custom analysis instructions here...
Email guidelines:
- Use your company name
- Include specific response templates
- Add custom signatures
"""

UNDERSTANDING THE OUTPUT
Each analyzed review returns:
{
    "Summary": "Brief overview of the review",
    "Positives": ["List", "of", "positive", "aspects"],
    "Negatives": ["List", "of", "negative", "aspects"], 
    "Sentiment": "Positive/Negative/Neutral",
    "Emotions": ["Joy", "Satisfaction", "etc"],
    "Email": "Personalized response email"
}

TROUBLESHOOTING

Common Issues and Solutions:

Problem: "Invalid API key" error
Solution: 
• Double-check your API key from Google AI Studio
• Make sure you copied the entire key
• Try regenerating a new API key

Problem: Package installation fails
Solution: 
• Restart the Colab runtime
• Go to Runtime → Restart Runtime
• Run the installation cell again

Problem: "Rate limit exceeded" error
Solution: 
• Wait a few minutes between large batches
• Google has usage limits on free tier
• Process reviews in smaller batches (5-10 at a time)

Problem: Empty or strange outputs
Solution: 
• Check your review text for special characters
• Make sure reviews are in English (for best results)
• Try simpler, shorter reviews first

Getting Help:

1. Check the Error Message: Read the full error for specific details
2. Restart Runtime: Often fixes temporary issues
3. Try Sample Data First: Make sure the system works before using custom data
4. Check API Quota: Ensure you haven't exceeded Google's limits

USAGE TIPS
Best Practices:

1. Start Small: Test with 2-3 reviews first
2. Clean Your Data: Remove extra spaces, special characters
3. Batch Processing: Process 10-20 reviews at a time for best performance
4. Save Results: Export to CSV/Excel for further analysis
5. Monitor Usage: Keep track of API calls to avoid limits

Sample Use Cases:

• Product Reviews: Amazon, e-commerce feedback
• Service Reviews: Restaurant, hotel reviews
• App Reviews: Mobile app store feedback
• Survey Responses: Customer satisfaction surveys
• Social Media: Comments and mentions

Export Options:

# Save to CSV
df.to_csv('review_analysis.csv', index=False)

# Save to Excel
df.to_excel('review_analysis.xlsx', index=False)

# Save to JSON
import json
with open('results.json', 'w') as f:
    json.dump(structured_reviews, f, indent=2)

SECURITY NOTES

• API Key Safety: Never share your API key publicly
• Data Privacy: Be careful with sensitive customer data
• Rate Limits: Respect Google's usage policies
• Local Storage: Colab sessions are temporary - download results


NEXT STEPS

After successful setup:

1. Analyze Your Own Reviews: Replace sample data
2. Customize for Your Business: Modify prompts and outputs
3. Scale Up: Process larger datasets
4. Integration: Connect to your existing systems
5. Advanced Features: Explore additional AI capabilities

Congratulations! You now have a powerful AI review analysis system running. Start with the sample data, then gradually introduce your own reviews for analysis.

